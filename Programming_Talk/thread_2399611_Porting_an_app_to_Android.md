---
title: "Porting an app to Android"
date: 2018-08-27
forum: Programming Talk
---

### Post by phma-a on 2018-08-27
I need to get an app I wrote running on Android. I have installed the SDK and the NDK but don't know what to do next. I've seen instructions saying to run "./android", but I don't know what directory to run it in. As far as I can tell, the steps are:
1. Get an Android emulator working. I've tried installing anbox with snap, but (after I figured out what to add to PATH) it gave me the error "Application manager service is not running yet".
2. Compile something (even if it's in Java) and run it on the emulator.
3. Install Qt5 on the emulator.
4. Install Qt5 development libraries for Android on Ubuntu.
5. Set up a toolchain for cross-compiling for Android.
6. Compile the project for Android.
7. Run it on the emulator.

I'm running Artful but will probably upgrade to Bionic soon. My development setup is like this:
*CMake for all C++ projects
*Qt5
*Out-of-source build: ~/src/foo contains source code, ~/build/foo/dbg contains debug build for Linux
*Toolchain is set up for Windows cross-compiling (but not Qt on Windows): ~/build/foo/w64 contains Windows build (with mingw)
*android-sdk and google-android-ndk-installer installed with apt.

---

