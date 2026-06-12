---
title: "gtk and gcc/g++"
date: 2007-01-28
forum: Programming Talk
---

### Post by SirBob1701 on 2007-01-28
I'm new to linux but not programming and have significant windows programming behind me.  Right now i'm trying to get gtk to compile with gcc or g++ and it appears that he linker is not getting the dependencies right.  (I did download all the gtk libs thru synaptic and apt-get)  here is the exact output i get 
> 
gcc: pkg-config --libs gtk+-2.0: No such file or directory
gtk1.cpp:1:21: error: gtk/gtk.h: No such file or directory
gtk1.cpp: In function ‘int main(int, char**)’:
gtk1.cpp:6: error: ‘GtkWidget’ was not declared in this scope
gtk1.cpp:6: error: ‘window’ was not declared in this scope
gtk1.cpp:8: error: ‘gtk_init’ was not declared in this scope
gtk1.cpp:10: error: ‘GTK_WINDOW_TOPLEVEL’ was not declared in this scope
gtk1.cpp:10: error: ‘gtk_window_new’ was not declared in this scope
gtk1.cpp:11: error: ‘gtk_widget_show’ was not declared in this scope
gtk1.cpp:13: error: ‘gtk_main’ was not declared in this scope


Can anyone give me any help (the tutorials i've found have been pretty usesless on telling one how to manually set dependencies.)

---

### Post by jblebrun on 2007-01-29
> **SirBob1701 said:**
> I'm new to linux but not programming and have significant windows programming behind me.  Right now i'm trying to get gtk to compile with gcc or g++ and it appears that he linker is not getting the dependencies right.  (I did download all the gtk libs thru synaptic and apt-get)  here is the exact output i get 


Can anyone give me any help (the tutorials i've found have been pretty usesless on telling one how to manually set dependencies.)

Can you show us the entire script of the commands you typed and the output that the compiler gives you? Did you use ./configure && make?

---

### Post by WW on 2007-01-29
> **SirBob1701 said:**
> ...  (I did download all the gtk libs thru synaptic and apt-get) ...
Does that include the package libgtk2.0-dev?  You will need that package to compile GTK2 programs.

---

### Post by lnostdal on 2007-01-29
You are missing the` characters?

```
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
```

(from: [http://www.gtk.org/tutorial/x111.html](http://www.gtk.org/tutorial/x111.html) )

try to run pkg-config --cflags gtk+-2.0 by itself from the terminal btw .. just so you see what their output (point) are

edit:
i assume pkg-config was installed as a dependency when build-essential was installed

---

### Post by jblebrun on 2007-01-29
> **lnostdal said:**
> You are missing the` characters?

```
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
```


Good call!

---

### Post by WW on 2007-01-29
Inostdal: good call! I bet that is the problem.

SirBob1701: Be sure the quote marks around the pkg-config command are *single backquotes*.

For example,
```
$ gcc junk.c `pkg-config --cflags gtk+-2.0`
$
```
With the wrong quotes:
```
$ gcc junk.c 'pkg-config --cflags gtk+-2.0'
gcc: pkg-config --cflags gtk+-2.0: No such file or directory
```
which is the first error that appears in your output.

---

### Post by SirBob1701 on 2007-02-08
Sorry it took so long to reply guys been busy with this and other stuff just got it working better and now  this is the only error I get 
```

undefined reference to `__gxx_personality_v0' collect2: ld returned 1 exit status

```

---

### Post by lnostdal on 2007-02-09
* if you're compiling c++-code and get this error use g++ to compile and link, not gcc

* if you're compiling c-code and get this error, rename your file from `somename.cpp' to `somename.c'

* ..or you have some error similar to this.. with a solution similar to the two above

---

### Post by Nethar on 2009-12-04
Hi, I had the same problem :-) i fixed it how it was described here:

```
g++ -Wall -g main.cpp -o anc `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
```I am building tutorial Hello world from GTK site - [http://library.gnome.org/devel/gtk-tutorial/stable/c39.html#SEC-HELLOWORLD](http://library.gnome.org/devel/gtk-tutorial/stable/c39.html#SEC-HELLOWORLD)

So I built it, when i simple run it, it works. But I have problems with debugging. I had them in Eclipse, so i tried it just from command line. It was also not working. It stops when the GTK is initialized, line 45, gtk_init (&argc, &argv);
Error message from gdb is "Cannot find new threads: generic error"
What could be the problem? I am running my helloworld app from gdb (i call my program anc), set breakpoint to line 45 and then step - error, same in Eclipse. Here is detailed output of gdb and my work, thanks for any hint:

```

mdolezal@nb-mdolezal:~/workspace/ancestry2/Ancestry2/src> gdb
GNU gdb (GDB) SUSE (7.0-27.2)
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-suse-linux".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
(gdb) file anc
Reading symbols from /home/mdolezal/workspace/ancestry2/Ancestry2/src/anc...done.
(gdb) break 45
Breakpoint 1 at 0x400cc8: file main.cpp, line 45.
(gdb) run
Starting program: /home/mdolezal/workspace/ancestry2/Ancestry2/src/anc 
Missing separate debuginfo for /lib64/ld-linux-x86-64.so.2
Try: zypper install -C "debuginfo(build-id)=591af1afa33f255704fb6a60859b93d00e205302"
Missing separate debuginfo for /usr/lib64/libgtk-x11-2.0.so.0
Try: zypper install -C "debuginfo(build-id)=3ef68407a0d2fd8402e30c3510ba77665fc32156"
Missing separate debuginfo for /usr/lib64/libgdk-x11-2.0.so.0
Try: zypper install -C "debuginfo(build-id)=b790d45d12271f7de80fc24169ecf82071cb832d"
Missing separate debuginfo for /usr/lib64/libatk-1.0.so.0
Try: zypper install -C "debuginfo(build-id)=6b1b562a685377458d2ba24ef2e3080517bddbde"
Missing separate debuginfo for /usr/lib64/libgio-2.0.so.0
Try: zypper install -C "debuginfo(build-id)=08ca9202ff9c75bc7271ef47e5bbad43a2a0c36d"
Missing separate debuginfo for /usr/lib64/libpangoft2-1.0.so.0
Try: zypper install -C "debuginfo(build-id)=ff6ab6a12ac30c66bca001b897d454b901a759cd"
Missing separate debuginfo for /usr/lib64/libgdk_pixbuf-2.0.so.0
Try: zypper install -C "debuginfo(build-id)=20edddb566b82a691512c3bc94f4d6ae4167192c"
Missing separate debuginfo for /usr/lib64/libpangocairo-1.0.so.0
Try: zypper install -C "debuginfo(build-id)=92f8e672ab08d6acb437334716aa34af3006624c"
Missing separate debuginfo for /usr/lib64/libcairo.so.2
Try: zypper install -C "debuginfo(build-id)=eff393400f13166189b42ccd85c24395cb62901a"
Missing separate debuginfo for /usr/lib64/libpango-1.0.so.0
Try: zypper install -C "debuginfo(build-id)=1afe045ecc021366c0515b4dad6e66fe0ebe771e"
Missing separate debuginfo for /usr/lib64/libfreetype.so.6
Try: zypper install -C "debuginfo(build-id)=548e35b1efff83633f9244c84f02d37571e8ac19"
Missing separate debuginfo for /usr/lib64/libfontconfig.so.1
Try: zypper install -C "debuginfo(build-id)=91c40a3235e928f04acc6b7d9c308f9db5502b20"
Missing separate debuginfo for /usr/lib64/libgobject-2.0.so.0
Try: zypper install -C "debuginfo(build-id)=f19847d70b70328d99de6303ce77402c1c0ad267"
Missing separate debuginfo for /usr/lib64/libgmodule-2.0.so.0
Try: zypper install -C "debuginfo(build-id)=8e6cb0d3af9508ac2bfb8db5157694ba8fac5cd9"
Missing separate debuginfo for /usr/lib64/libglib-2.0.so.0
Try: zypper install -C "debuginfo(build-id)=7e3842ab0a347df5f56a0697077f4eca83bfe5fe"
Missing separate debuginfo for /usr/lib64/libstdc++.so.6
Try: zypper install -C "debuginfo(build-id)=62220ad5c8941afb5d332c0c47d32f8beec8ac50"
Missing separate debuginfo for /lib64/libm.so.6
Try: zypper install -C "debuginfo(build-id)=57fc1891d8d9f419fb8c7fc06a8285563b53a47e"
Missing separate debuginfo for /lib64/libgcc_s.so.1
Try: zypper install -C "debuginfo(build-id)=0206e11fa8ca0db0633073adcbf1349a7871e1dc"
Missing separate debuginfo for /lib64/libc.so.6
Try: zypper install -C "debuginfo(build-id)=c5a3dfd66bf61fcdec9bc22153b2fbd0d6697960"
Missing separate debuginfo for /usr/lib64/libX11.so.6
Try: zypper install -C "debuginfo(build-id)=5fa84adc30db95abcbaea20ed7ec1c8dd94dfff2"
Missing separate debuginfo for /usr/lib64/libXfixes.so.3
Try: zypper install -C "debuginfo(build-id)=6495446f04c2f9a4fa3021f7322d6f12c4017305"
Missing separate debuginfo for /usr/lib64/libXext.so.6
Try: zypper install -C "debuginfo(build-id)=a14cd41f23af7f31d0ac2bd8eada730888690b27"
Missing separate debuginfo for /usr/lib64/libXrender.so.1
Try: zypper install -C "debuginfo(build-id)=55f90cfa8482fae594e59cce00c20937e7257446"
Missing separate debuginfo for /usr/lib64/libXinerama.so.1
Try: zypper install -C "debuginfo(build-id)=c7af2457b235b84f26ce24f1c4d260ec7eeb9f88"
Missing separate debuginfo for /usr/lib64/libXi.so.6
Try: zypper install -C "debuginfo(build-id)=d278c56b4359f6a219af5e13576873a38581c25c"
Missing separate debuginfo for /usr/lib64/libXrandr.so.2
Try: zypper install -C "debuginfo(build-id)=6a1fccee186ebf368f2d6a7d5ccd582943fd1953"
Missing separate debuginfo for /usr/lib64/libXcursor.so.1
Try: zypper install -C "debuginfo(build-id)=56d901d8946aefda2e4b5e12dba24c13ac3f61a9"
Missing separate debuginfo for /usr/lib64/libXcomposite.so.1
Try: zypper install -C "debuginfo(build-id)=04bac2797b48183b0534d8ab8a481383e12680aa"
Missing separate debuginfo for /usr/lib64/libXdamage.so.1
Try: zypper install -C "debuginfo(build-id)=650d88fdf900daadd8ba1c9134c21b4e68b560bc"
Missing separate debuginfo for /lib64/libresolv.so.2
Try: zypper install -C "debuginfo(build-id)=75e330be16e086696f5aac505e30e9628abc9ca9"
Missing separate debuginfo for /lib64/libselinux.so.1
Try: zypper install -C "debuginfo(build-id)=e2a1d921e5eb705fc1e51c5651c04fea1e31bcfd"
Missing separate debuginfo for /usr/lib64/libpixman-1.so.0
Try: zypper install -C "debuginfo(build-id)=e2796f6ce8e24789f258c0047a7ad1c47eeae67d"
Missing separate debuginfo for /usr/lib64/libpng12.so.0
Try: zypper install -C "debuginfo(build-id)=67ebdd04bd0be9a64a35354cb80d8ba2b0221f8f"
Missing separate debuginfo for /usr/lib64/libxcb-render-util.so.0
Try: zypper install -C "debuginfo(build-id)=c316459cc02a8eb148173af72236bfa034acd17b"
Missing separate debuginfo for /usr/lib64/libxcb-render.so.0
Try: zypper install -C "debuginfo(build-id)=7fdad8a2768f53c44f378b1ce0b4747f045b0ffb"
Missing separate debuginfo for /usr/lib64/libxcb.so.1
Try: zypper install -C "debuginfo(build-id)=54a77c10d44b40080d6d8e65d277ccb7ab2a5b4a"
Missing separate debuginfo for /lib64/libz.so.1
Try: zypper install -C "debuginfo(build-id)=763926681ebc75fcd9de7b99f7229ff15c7d1754"
Missing separate debuginfo for /lib64/libexpat.so.1
Try: zypper install -C "debuginfo(build-id)=377d4d1802e40c055be37bbf4bde9fcf0a6c9e4e"
Missing separate debuginfo for /lib64/libdl.so.2
Try: zypper install -C "debuginfo(build-id)=44e66ebae672563bd496f290e08d316bc3bf0ac7"
Missing separate debuginfo for /lib64/libpcre.so.0
Try: zypper install -C "debuginfo(build-id)=faf1aba9b565a29c99ce1d3944978347d6209cc3"
Missing separate debuginfo for /usr/lib64/libXau.so.6
Try: zypper install -C "debuginfo(build-id)=72341bb9d8a1ad2ca2bbced007f3a785121aac28"

Breakpoint 1, main (argc=1, argv=0x7fffffffded8) at main.cpp:45
45        gtk_init (&argc, &argv);
(gdb) step
Missing separate debuginfo for /usr/lib64/gtk-2.0/2.10.0/engines/libmurrine.so
Try: zypper install -C "debuginfo(build-id)=281f2d6f682e55779804b151acddfa890ca3efc7"
Missing separate debuginfo for /usr/lib64/gtk-2.0/modules/libcanberra-gtk-module.so
Try: zypper install -C "debuginfo(build-id)=dacf2811996d88f90019992dfbe65fd1c6db581b"
Missing separate debuginfo for /usr/lib64/libcanberra-gtk.so.0
Try: zypper install -C "debuginfo(build-id)=a8fff5fc36b17cd05f1c76819fb58c15b7a33b3b"
Missing separate debuginfo for /lib64/libpthread.so.0
Try: zypper install -C "debuginfo(build-id)=7bcbabc9da24424f1f5ef7be77b575fd3d796288"
[Thread debugging using libthread_db enabled]
Missing separate debuginfo for /usr/lib64/libcanberra.so.0
Try: zypper install -C "debuginfo(build-id)=4559edae1f73d4230667c627ce758222be306f02"
Missing separate debuginfo for /usr/lib64/libvorbisfile.so.3
Try: zypper install -C "debuginfo(build-id)=1ec4ca8fb5fd2f0f836e1312d225ce748307dd4b"
Missing separate debuginfo for /usr/lib64/libltdl.so.7
Try: zypper install -C "debuginfo(build-id)=c0d151a6ac881b1d40daf180284ae1a980b6930b"
Missing separate debuginfo for /usr/lib64/libvorbis.so.0
Try: zypper install -C "debuginfo(build-id)=b6e9c3afdefda8b972a34597c9de8303c03fd6e2"
Missing separate debuginfo for /usr/lib64/libogg.so.0
Try: zypper install -C "debuginfo(build-id)=b7a08f86d1b2980454dda0225550ffc0eefbf390"
Cannot find new threads: generic error
(gdb) step
Cannot execute this command while the selected thread is running.


```Do I need to install that additional debuginfo files or what could be the problem? Thanks.

---

