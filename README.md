# RustClassicDllInjection
Classic DLL injection POC in Rust leveraging Windows API hashing.

Injection approach:
- `OpenProcess` for the given process ID
- `VirtualAllocEx` to allocate RW memory in the target process to write the DLL path
- `WriteProcessMemory` to write the DLL path into the buffer allocated by `VirtualAllocEx`
- `CreateRemoteThread` to create a remote thread in the target process that will execute `LoadLibraryW` using the DLL path from the buffer as the argument

Usage:
```text
rust_classic_dll_injection.exe [target PID] [DLL path]
```

Example screenshot:
![classicdllinjection](https://github.com/uruwhy/RustClassicDllInjection/assets/58484522/988a6632-24b7-499c-aba6-9c3c1b0b5d97)

## Build
```PowerShell
# debug
cargo build

# release
cargo build --release
```

## References:
- [DLL Injection](https://www.ired.team/offensive-security/code-injection-process-injection/dll-injection)
