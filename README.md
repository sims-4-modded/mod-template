# The Sims 4 mods: mod template

The template of a DLL mod for the Sims 4 mod loader (`mod_loader`). Copy it to make a new mod.

## Build

Requirements: Visual Studio with the C++ tools, and the vcpkg checkout of the workspace (`<workspace>\vcpkg`, where
the workspace is the folder that holds `projects`).

```bat
git submodule update --init
tools\preset.bat x64-release
```

Make sure to initialise and clone submodules (we need `common`): `git submodule update --init`.

## Tests

`ctest --preset x64-release` runs the GoogleTest tests. `python tools\rename_mod.py --self-test` tests the rename
tool.

## How to install

Clone the template and rename it to make a new mod. The install tool of the mod loader puts the DLL into the DLL mods
folder of the loader.

```bat
git clone <workspace>\projects\mod_template <workspace>\projects\<mod_id>
python tools\rename_mod.py <mod_id> "<Mod name>"
python ..\mod_loader\tools\install.py mods add build\x64-release\<mod_id>.dll
```
