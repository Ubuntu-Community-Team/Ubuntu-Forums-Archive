---
title: "Small Distro Help"
date: 2007-10-05
forum: Other OS Talk
---

### Post by damvcoool on 2007-10-05
i was wondering if you could help me create a small distro with fltk as GUI.

Basically what i want to do is a Distro with the following base components.

ucllibc
busybox
fltk
tcc(tiny C compiler) if possible.
linux 2.6 or 2.4

that is for the basic system, tell me if I am missing anything critical.
and if someone can provide me with detailed steps on how to create the build environment.

I want this basically to know more about linux, and small systems, also to rehabilitate an old laptop i have that does not accept cd's .

---

### Post by tgalati4 on 2007-10-05
DSL is the king of small distros.  You can add or subtract as needed.  At 50 MB, you can load it on a USB stick, then make a USB-boot floppy to revive an old laptop.  

It that doesn't work--for instance no floppy or USB, then you would have to remove the harddrive and stick it in a desktop machine (with an IDE-to-notebook drive adapter) and load DSL from there and pop it back into the laptop.

I'm not familiar with fltk, but DSL comes with Fluxbox and Joe's Window Manager and you can choose your environment on the fly.

---

### Post by SuperDuck on 2007-10-05
I would suggest reading Linux From Scratch - it has details on setting up a temporary build environment and, well, building Linux from scratch!

[www.linuxfromscratch.org](www.linuxfromscratch.org)

---

### Post by damvcoool on 2007-10-05
Thank you for the suggestions, I have tried LFS before, but as far as i am concerned everything they do is based on Glibc wich has more feautures than uclibc, and some steps wont really apply making my idea unbuildable.

DSL is great i agree, but the idea is to learn how to build my own. i have tryed in the past to modified to my needs but when it comes to updating uclibc everything brakes.

---

### Post by damvcoool on 2007-10-24
*Bump**Bump**Bump**Bump**Bump*

---

### Post by LaRoza on 2007-10-24
There is a sticky on small distros, or ones on Floppies. Some of them are quite surprising.

---

### Post by damvcoool on 2007-10-26
ucllibc
busybox
fltk
tcc(tiny C compiler) if possible.
linux 2.6 or 2.4

I want to know if is possible to make a small working distro with this components and what it takes to do it. (step by step if possible)

Please HELP!! I want to learn more!!

---

### Post by kagashe on 2007-10-27
Look at [Buildroot]("http://buildroot.uclibc.org/buildroot.html") documentation.

---

### Post by saulgoode on 2007-10-27
I don't think there are C language bindings for FLTK. If your heart is set on FLTK, you will want a C++ compiler (perhaps [LWC++](http://students.ceid.upatras.gr/~sxanth/lwc/)). 

I think I would forego FLTK and go with GTK, either limiting myself to GTK+ **1.2** (which is lightweight and would allow older versions of many applications to work) or experiment with GTK+ 2.x on a framebuffer (no X Window System).

---

### Post by damvcoool on 2007-10-27
I will take a look at LWC++ to compile FLTK i want to keep everything as small and fast as possible (specially small) now i have use buildroot from uclibc.org it is helpful but since there is no stable (recent) version I don't thing there one to be release soon it kinda gets to half point in compilation and then stops with errors but it's hard to navigate through all the sources to find which one is the one with the problem.

now only if there was a soul that could help me on how to step by step very patiently guide me on how to create a working (graphical environment [i don't know where to get kdrive]) with all the componets i listed above (more can be added if needed).

I have tried LFS but it is not uclibc friendly, and there is a draft but does not work or at least does not work for me.

---

