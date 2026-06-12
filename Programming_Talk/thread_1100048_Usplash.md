---
title: "Usplash"
date: 2009-03-18
forum: Programming Talk
---

### Post by Linux000 on 2009-03-18
Is there anyone who could provide basic steps to writing a Usplash theme for Intrepid, or point to an non-compiled example? I have never really done graphical stuff outside of Visual Basic in Windows. I would like to build a basic theme and was looking for help(Specify X,Y vars?How?)

---

### Post by cabalas on 2009-03-18
Seeing as I'm pretty sure we haven't changed the USplash since edgy this howto should be of use to you:

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by Linux000 on 2009-03-18
The problem is I can't find any files(examples)on my computer, which is a big problem for me, I have no clue where to start. Did a login window by modifying the files in Human, so if anyone could point me to the files that go into it, that would help to.

---

### Post by geirha on 2009-03-19
```
# list all installed (~i) packages containing usplash in the name
~$ aptitude search '~i usplash' 
i A libusplash0                     - userspace bootsplash library              
i   usplash                         - Userspace bootsplash utility              
i   usplash-theme-ubuntu            - Usplash theme for Ubuntu                  

# usplash-theme-ubuntu sounds like a package containing an usplash theme
# lets list the files it installs
~$ dpkg -L usplash-theme-ubuntu
... snipp ...
/usr/lib/usplash/usplash-theme-ubuntu.so
... snipp ...
# only contains a compiled library file and the standard copyright notice. 

# Let's check the source instead
~$ cd /tmp
/tmp$ apt-get source usplash-theme-ubuntu
... snipp ...
dpkg-source: extracting usplash-theme-ubuntu in usplash-theme-ubuntu-0.18
dpkg-source: unpacking usplash-theme-ubuntu_0.18.tar.gz
/tmp$ cd usplash-theme-ubuntu-0.18
/tmp/usplash-theme-ubuntu-0.18$ ls
... several .png-files ...

```

---

### Post by Linux000 on 2009-03-19
Thank you very much! That is all I need.

---

### Post by Linux000 on 2009-03-19
Sorry to keep pushing, but how do I go about compiling ```

```gcc usplash-theme-ubuntu```

```yields about 300 or so errors the first two are about the includes at the top of the code, apparently my computer doesn't have usplash-theme.h or usplash_backend.h. what do I need to get these?

---

### Post by geirha on 2009-03-19
```
sudo apt-get build-dep usplash-theme-ubuntu
```

That should install the necessary development packages, containing, amongst others, those header files it's complaining about.

---

### Post by Linux000 on 2009-03-19
Should I be compiling it with GCC? Now that I think about it, GCC dosen't seem to be the right program for the compile. It wields this

```
root@michael-laptop:/home/michael/usplash-theme-ubuntu-0.19# gcc usplash-theme-ubuntu.c 
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
/tmp/ccXTBJ8h.o: In function `t_init':
usplash-theme-ubuntu.c:(.text+0x14): undefined reference to `usplash_getdimensions'
/tmp/ccXTBJ8h.o: In function `t_clear_progressbar':
usplash-theme-ubuntu.c:(.text+0x8d): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x99): undefined reference to `usplash_put'
/tmp/ccXTBJ8h.o: In function `t_clear_progressbar_16':
usplash-theme-ubuntu.c:(.text+0xbb): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0xc7): undefined reference to `usplash_put'
/tmp/ccXTBJ8h.o: In function `t_draw_progressbar':
usplash-theme-ubuntu.c:(.text+0xd6): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x119): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x125): undefined reference to `usplash_put'
usplash-theme-ubuntu.c:(.text+0x138): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x164): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x17b): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x181): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x186): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x1b9): undefined reference to `pixmap_throbber_fore'
usplash-theme-ubuntu.c:(.text+0x1cd): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x1d8): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x204): undefined reference to `pixmap_throbber_fore'
usplash-theme-ubuntu.c:(.text+0x21b): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x221): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x226): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x259): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x26d): undefined reference to `usplash_put_part'
/tmp/ccXTBJ8h.o: In function `t_draw_progressbar_16':
usplash-theme-ubuntu.c:(.text+0x281): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x2c4): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x2d0): undefined reference to `usplash_put'
usplash-theme-ubuntu.c:(.text+0x2e3): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x30f): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x326): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x32c): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x331): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x364): undefined reference to `pixmap_throbber_fore_16'
usplash-theme-ubuntu.c:(.text+0x378): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x383): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x3af): undefined reference to `pixmap_throbber_fore_16'
usplash-theme-ubuntu.c:(.text+0x3c6): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x3cc): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x3d1): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x404): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x418): undefined reference to `usplash_put_part'
/tmp/ccXTBJ8h.o: In function `t_animate_step':
usplash-theme-ubuntu.c:(.text+0x42d): undefined reference to `pixmap_throbber_fore'
usplash-theme-ubuntu.c:(.text+0x482): undefined reference to `pixmap_throbber_fore'
usplash-theme-ubuntu.c:(.text+0x4ca): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x4f6): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x50d): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x513): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x547): undefined reference to `pixmap_throbber_fore'
usplash-theme-ubuntu.c:(.text+0x55b): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x561): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x566): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x599): undefined reference to `pixmap_throbber_back'
usplash-theme-ubuntu.c:(.text+0x5ad): undefined reference to `usplash_put_part'
/tmp/ccXTBJ8h.o: In function `t_animate_step_16':
usplash-theme-ubuntu.c:(.text+0x5e1): undefined reference to `pixmap_throbber_fore'
usplash-theme-ubuntu.c:(.text+0x636): undefined reference to `pixmap_throbber_fore_16'
usplash-theme-ubuntu.c:(.text+0x67e): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x6aa): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x6c1): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x6c7): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x6fb): undefined reference to `pixmap_throbber_fore_16'
usplash-theme-ubuntu.c:(.text+0x70f): undefined reference to `usplash_put_part'
usplash-theme-ubuntu.c:(.text+0x715): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x71a): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x74d): undefined reference to `pixmap_throbber_back_16'
usplash-theme-ubuntu.c:(.text+0x761): undefined reference to `usplash_put_part'
/tmp/ccXTBJ8h.o:(.data+0xc): undefined reference to `pixmap_usplash_640_400'
/tmp/ccXTBJ8h.o:(.data+0x6c): undefined reference to `pixmap_usplash_640_480'
/tmp/ccXTBJ8h.o:(.data+0xcc): undefined reference to `pixmap_usplash_800_600'
/tmp/ccXTBJ8h.o:(.data+0x12c): undefined reference to `pixmap_usplash_1024_768'
/tmp/ccXTBJ8h.o:(.data+0x18c): undefined reference to `pixmap_usplash_1365_768_scaled'
collect2: ld returned 1 exit status
```

as the response to the command
```
gcc usplash-theme-ubuntu.c
```
after I install the dependencies (about 52 of them) with the command
```
sudo apt-get build-dep usplash-theme-ubuntu
```
I think gcc is not using the makefile, is there a way to make gcc use it, or another compiler to use.

---

### Post by geirha on 2009-03-19
gcc has no idea what a makefile is. Makefile is read by the make program, and the Makefile should provide the proper commands needed to build and install it. Typically you run "make" to compile and link, and then "sudo make install" to copy the files to their intended locations in the filesystem.

---

