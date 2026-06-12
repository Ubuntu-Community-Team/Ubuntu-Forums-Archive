---
title: "Trouble Installing Quickcam Messenger"
date: 2005-10-17
forum: Programming Talk
---

### Post by penguinchrissy on 2005-10-17
I've been trying to get my quickcam messenger up and running and 5.10 I got it working on 5.04 but there is something up with 5.10 I dl the driver from this site
[http://home.mag.cx/messenger](http://home.mag.cx/messenger)
SO I know it works but when I go though with the installiton or compiling which ever one its called I get this error message 
/bin/readlink
gcc version: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
gcc version: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.16.1 Debian GNU/Linux
Kernel compiler: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->
I had to install some gcc and gnu files to get the first part of this to work could it have been that and what can I do to fix this problem?
Thanks

I've been reading the threads and found that some people haven't been able to locate the source code. This was orgianlly a problem for me I did the add programs to get some source codes and headers thats what the program said it needed I just dl them intill it worked.

---

### Post by mvandeg on 2005-10-19
Installing gcc-3.4 helps, in combination with

```
export CC=gcc-3.4
```

Then run the quickcam.sh script. I could however not get the camera to work, due to missing a missing symbol 'remap_page_range'.

---

### Post by penguinchrissy on 2005-10-23
I've tried this and it didn't work I still need the latest kernel compiler
I have the lastest gcc version 4.0.2 20050808 as you can see
but my kernel complier isn't up to date how do I get them to match up
I've tried to do an export CC=gcc-4.0 but it doesn't work neither does CC=gcc-4.0.2

---

### Post by crane on 2005-12-30
Has anyone beed successful with the Messenger?

---

