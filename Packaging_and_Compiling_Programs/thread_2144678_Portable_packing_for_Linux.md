---
title: "Portable packing for Linux"
date: 2013-05-13
forum: Packaging and Compiling Programs
---

### Post by mbnoimi on 2013-05-13
Hi,

Is there any tool for creating portable packages over Linux distributions or at least for Ubuntu distributions?

PS
[LIST]
[*]I usually use [http://debreate.sourceforge.net/](http://debreate.sourceforge.net/) but it's really exhausting solution by comparing to Windows installers (installshield). 
[*]I found [http://www.magicermine.com/](http://www.magicermine.com/) it's really what I'm looking for but it's commercial solution while I'm looking for open source one. 
[/LIST]

---

### Post by mbnoimi on 2013-05-17
Bump

---

### Post by MG&amp;TL on 2013-05-19
> **mbnoimi said:**
> Bump

I've had similar issues. I realise this is likely a pain, but one of the more useful approaches I've seen is CMake's CPack. There's an introduction here: [http://www.cmake.org/Wiki/CMake:Packaging_With_CPack](http://www.cmake.org/Wiki/CMake:Packaging_With_CPack) and a list of packaging formats here: [http://www.cmake.org/Wiki/CMake:CPackPackageGenerators](http://www.cmake.org/Wiki/CMake:CPackPackageGenerators)

I can't honestly say I like CMake and I can't say whether it's worth changing your current build system for, but it might be an option.

---

### Post by mbnoimi on 2013-05-19
> **MG&TL said:**
> I've had similar issues. I realise this is likely a pain, but one of the more useful approaches I've seen is CMake's CPack. There's an introduction here: [http://www.cmake.org/Wiki/CMake:Packaging_With_CPack](http://www.cmake.org/Wiki/CMake:Packaging_With_CPack) and a list of packaging formats here: [http://www.cmake.org/Wiki/CMake:CPackPackageGenerators](http://www.cmake.org/Wiki/CMake:CPackPackageGenerators)

I can't honestly say I like CMake and I can't say whether it's worth changing your current build system for, but it might be an option.

No way, cmake isn't the solution for portable packing (I'm using qmake which is better than cmake) I'm looking for a tool can deploy my Linux application with zero dependency. **ldd** give list of needed dependency but it's not suitable enough because I've to copy all the files manually which is really painful.

As I said above [magicermine]("http://www.magicermine.com/") works fine but it's unfortunately a commercial solution:mad:

---

### Post by MG&amp;TL on 2013-05-19
> **mbnoimi said:**
> No way, cmake isn't the solution for portable packing (I'm using qmake which is better than cmake) I'm looking for a tool can deploy my Linux application with zero dependency. **ldd** give list of needed dependency but it's not suitable enough because I've to copy all the files manually which is really painful.

As I said above [magicermine]("http://www.magicermine.com/") works fine but it's unfortunately a commercial solution:mad:

Well, it was just a suggestion. (OT: why is qmake better? I use SCons or pure Make, myself...)

Having 'zero dependency' would be a really bad idea. The whole idea of **shared** libraries is that applications share them. All the packaging formats I know of for linux distributions allow you to specify the dependencies required, which is what you're supposed to do. You can of course use static libraries (.a files) but very few libraries ship like this any more.

You mention debreate, (which is debian only), but you say packing for 'linux'. You can't do both; you either pack for linux (source tarball, or make* lots* of packages for different distributions) or pack for debian/fedora/arch/whatever.

I think the ideal solution is 'let someone else do it'. Distributions will package application releases for their distribution if there is sufficient demand or someone volunteers; if you can get your application to the point where it's noticed, you might be in with a chance of that happening.

---

### Post by mbnoimi on 2013-05-19
> All the packaging formats I know of for linux distributions allow you to specify the dependencies required, which is what you're supposed to do
Unfortunately all the tools -I know- don't add that dependencies automatically which means you've to write  (in some cases) a large list of dependencies in case you want to build your package. I'm Qt developer and I faced this issue when I tried to create deb package for my Qt5 application (Qt5 doesn't exist in ubuntu repositories :mad:)

> You mention debreate, (which is debian only), but you say packing for 'linux'
I mentioned it just as example for the tools I tested

>  I think the ideal solution is 'let someone else do it'. Distributions will package application releases for their distribution if there is sufficient demand or someone volunteers; if you can get your application to the point where it's noticed, you might be in with a chance of that happening. 
I'm not sure this is a practical solution, there are millions of applications around the world and -as I know- hundreds of requests for adding some applications to Linux repositories but the approval in most cases takes months (in case some one responded) this is a painful procedure.

PS
ubuntu PPA may fix this issue but what about the other Linux distributions? and basically building deb package isn't easy as I expected specially for my case (Qt5 shared libraries doesn't exist in ubuntu repository)

---

### Post by MG&amp;TL on 2013-05-19
> Unfortunately all the tools -I know- don't add that dependencies automatically which means you've to write  (in some cases) a large list of dependencies in case you want to build your package. I'm Qt developer and I faced this issue when I tried to create deb package for my Qt5 application (Qt5 doesn't exist in ubuntu repositories :mad:)


Qt5 certainly exists in 13.04. But yeah, the tools tend to not work too well (although have you tried just adding the Qt meta-package). It's a complicated topic. Have you tried simply manually packaging, annoying as it is?

> I'm not sure this is a practical solution, there are millions of applications around the world and -as I know- hundreds of requests for adding some applications to Linux repositories but the approval in most cases takes months (in case some one responded) this is a painful procedure.


This is true, but community packagers (such as Arch's AUR) are often quite active if they see a program they want.

> PS
ubuntu PPA may fix this issue but what about the other Linux distributions? and basically building deb package isn't easy as I expected specially for my case (Qt5 shared libraries doesn't exist in ubuntu repository)


PPAs are even more of a pain than debian packages. I gave up on those a while ago.

 I completely agree with you that it's a pain, I'm just offering a single solution as a possibility.

---

### Post by mbnoimi on 2013-05-22
> **MG&TL said:**
> Qt5 certainly exists in 13.04. But yeah, the tools tend to not work too well (although have you tried just adding the Qt meta-package). It's a complicated topic. Have you tried simply manually packaging, annoying as it is?
I tried... it's truly pain in the ass:mad:

> I completely agree with you that it's a pain, I'm just offering a single solution as a possibility.

Thanks for your efforts.... [SIZE=4]Ubuntu gurus I need your help:KS[/SIZE]

---

### Post by mbnoimi on 2013-05-28
Bump

---

### Post by mbnoimi on 2013-06-09
It seems this issue really don't interesting for ubuntu gurus so I just want to ask you a simple question which will fix dependency hell of packaging:

How can I get clean list of dependencies by **ldd**?

For example the default output of **ldd** is very dirty (in case I want to modify the output for adding cp)
```
mbnoimi@mbnoimi-pc ~/Programs/synkron/x64 $ ldd ./synkron 
        linux-vdso.so.1 =>  (0x00007fffcf7c5000)
        libQt5Widgets.so.5 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libQt5Widgets.so.5 (0x00007f9d5c73e000)
        libQt5Xml.so.5 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libQt5Xml.so.5 (0x00007f9d5c502000)
        libQt5Network.so.5 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libQt5Network.so.5 (0x00007f9d5c1ae000)
        libQt5Gui.so.5 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libQt5Gui.so.5 (0x00007f9d5bbae000)
        libQt5Core.so.5 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libQt5Core.so.5 (0x00007f9d5b576000)
        libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f9d5b249000)
        libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f9d5b033000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f9d5ac74000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f9d5aa56000)
        libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007f9d5a807000)
        libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f9d5a510000)
        libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f9d5a1d5000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f9d59ed9000)
        libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007f9d59c74000)
        libicui18n.so.49 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libicui18n.so.49 (0x00007f9d59a64000)
        libicuuc.so.49 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libicuuc.so.49 (0x00007f9d596de000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f9d594da000)
        libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007f9d592d7000)
        librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f9d590cf000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f9d5cf61000)
        libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f9d58ec6000)
        libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f9d58c89000)
        libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f9d58a6b000)
        libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007f9d58844000)
        libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f9d58632000)
        libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007f9d5842f000)
        libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f9d58228000)
        libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007f9d58026000)
        libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007f9d57e0f000)
        libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007f9d57c08000)
        libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007f9d579fc000)
        libicudata.so.49 => /home/mbnoimi/.Qt5.0.2/5.0.2/gcc_64/lib/libicudata.so.49 (0x00007f9d566db000)
        libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f9d564d7000)
        libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f9d562d0000)

```

---

