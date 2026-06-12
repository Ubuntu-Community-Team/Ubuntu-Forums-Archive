---
title: "Code::Blocks and SDL"
date: 2007-05-24
forum: Programming Talk
---

### Post by ART_Adventures on 2007-05-24
I have a fresh install of Code::Blocks (latest version of nightly build). I want to make an SDL application using this IDE.

Can somebody list a simple, step by step, process of what I need to do in order to get an SDL app to compile, please?

For example, do I need to download the SDL source code from the SDL web site and put it in a directory locally, or is there some kind of shell command to do this? etc...

Your help is appreciated.

---

### Post by Paul820 on 2007-05-24
Hi, i have codeblocks and i'm having a go at SDL aswell. You need to got to synaptic and download these:

libsdl1.2-dev
libsdl-image1.2
libsdl-image1.2-dev
libsdl-mixer1.2
libsdl-mixer1.2-dev
libsdl-ttf2.0-0
libsdl-ttf2.0-dev
libsdl-gfx1.2.4
libsdl-gfx1.2-dev

I don't know if you need them all, but you never know when you are going to need them. All i did was install them with synaptic and built the default SDL project supplied with codeblocks and it built fine. Codeblocks found SDL, there was no configuring. Hope this helps you a bit. :D

---

### Post by ART_Adventures on 2007-05-24
Thank you. That worked :-)

---

