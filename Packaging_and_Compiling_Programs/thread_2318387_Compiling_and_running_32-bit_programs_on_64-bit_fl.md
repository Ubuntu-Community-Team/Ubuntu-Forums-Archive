---
title: "Compiling and running 32-bit programs on 64-bit flavor"
date: 2016-03-25
forum: Packaging and Compiling Programs
---

### Post by UCyborg on 2016-03-25
I noticed something strange when you try to compile 32-bit program on 64-bit Ubuntu, it won't find 32-bit libraries. For some reason, no proper symlinks to real libraries' .so files get created in /usr/lib/i386-linux-gnu, while everything is okay in corresponding 64-bit folder. You can get around it by manually creating symlink for every library you need or tweaking the makefile, but that shouldn't be necessary. It should work straight out of the box as it works for 64-bit stuff, install all dependencies and it works. I run Ubuntu 15.10 MATE.

---

### Post by UCyborg on 2016-03-27
Ok, I have partially figured it out, you must install 32-bit versions of dev packages to get those links. Still, can't get libsdl2-dev:i386 to install...

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsdl2-dev:i386 : Depends: libegl1-mesa-dev:i386 but it is not going to be installed
                    Depends: libgles2-mesa-dev:i386 but it is not going to be installed
                    Depends: libmirclient-dev:i386 but it is not going to be installed
                    Depends: libwayland-dev:i386 but it is not going to be installed
                    Depends: libxkbcommon-dev:i386 but it is not going to be installed

This is what I'm trying to build and can't do it without manually creating symlinks: [https://github.com/UCyborg/BerserkerQuake2](https://github.com/UCyborg/BerserkerQuake2)

---

### Post by G4143 on 2016-03-31
You'll note that your filesystem(on a 64 bit installed system) will have two directories off of root - lib and lib64. The lib directory is for 32 bit libraries and the lib64 is for 64 bit.

---

