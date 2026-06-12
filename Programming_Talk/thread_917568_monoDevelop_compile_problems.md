---
title: "monoDevelop compile problems"
date: 2008-09-12
forum: Programming Talk
---

### Post by ShadowMaster22 on 2008-09-12
I have recently struggled to get a distro of monoDevelop working on Ubuntu 8.04 (Hardy Heron).  I was able to figure out what packages I needed to install to get the VB.net working, but I still am having trouble with C#/C/C++.  Everytime I compile (build), I recieve this:
Build failed. Object reference not set to an instance of an object. However, I can compile using G++, etc. via the terminal.  Does anyone know what I'm doing wrong (for monoDevelop)?  I really would like to get this working, because I'm working on my Computer Programming AAS and we do most of our work in VB.net or C#.  I've googled this all over the place and have gotten almost nothing useful.

Another Windows-master/Linux-amateur,

---

### Post by true_friend on 2008-09-12
Install latest packages from [badgerports]("http://directhex.mfgames.com/hardy.html"), unofficial repository for Ubuntu Hardy. Then also install compiler packages mono-gmcs and mono-vbnc(perhaps for vb.net), hopefully you'll get it. Otherwise [official forums]("http://www.go-mono.com/forums/") may also help.
Regards

---

