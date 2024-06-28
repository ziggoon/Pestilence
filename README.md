# Pestilence
### What is this?
Pestilence is a shellcode loader designed for evasion. Coded in Rust. Forked from: https://github.com/cr7pt0pl4gu3/Pestilence
### How does it work?
It loads AES-128-CBC encrypted shellcode (including the key and IV) into the .text PE section during the build stage.
During the execution, it first checks for "activate" cmdline argument. If present, it decrypts the shellcode stub, copies it gradually (mixed with custom sleeps) and proceeds to execute it in memory by using NTDLL.DLL functions (mixed with custom sleeps). I plan on modifying this down the line to support additional injection methods.
# Installation
### Requirements
* python3 (tested with 3.10) + pycryptodomex
* rust (nightly-x86_64-pc-windows-msvc toolchain)
* visual studio 2019 build tools
### How to install them
#### vs2019 build tools
Download and install vs2019 build tools from here:
```
https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019
```
Make sure that you select "Desktop development with C++" option.
#### python3 + pycryptodome
Download and install python using this link (do not forget to add it to PATH):
```
https://www.python.org/ftp/python/3.10.0/python-3.10.0-amd64.exe
```
Install pycryptodomex:
```shell
pip3 install pycryptodomex
```
#### rust
Install rust using rustup from this link:
```
https://static.rust-lang.org/rustup/dist/x86_64-pc-windows-msvc/rustup-init.exe
```
* Install the C++ build tools if asked.
* Be sure to choose "customize installation".

Modify install settings:
```
Default host triple? [x86_64-pc-windows-msvc]
Default toolchain? [nightly]
Profile? [default]
Modify PATH variable? [Y]
```
Proceed with installation.
# Build & Usage
### Build
Open powershell and thrive:
```shell
git clone https://github.com/ziggoon/Pestilence/
cd Pestilence
generate the shellcode
python encrypt_shellcode.py
cargo build --release
```
Note: shellcode must be named "shellcode.bin"!
### Usage
On target, execute:
```shell
pestilence.exe activate
```
Done!
#### Good luck! I hope that pestilence helped you.
