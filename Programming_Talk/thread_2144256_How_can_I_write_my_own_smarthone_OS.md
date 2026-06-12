---
title: "How can I write my own smarthone OS?"
date: 2013-05-11
forum: Programming Talk
---

### Post by stamatiou on 2013-05-11
I would like to create my own smartphone OS. I know C, C++ and I am currently working with assembly. I am completely clueless, how can I get started?

---

### Post by tgalati4 on 2013-05-11
I would study Android and build a toolchain to run and develop Android on your desktop or laptop.  If that is not hardcore enough, I would look into webos, maemo, or meego, or any of a handful of OS's that are Waiting for Godot.

(Hint:  [Godot]("http://en.wikipedia.org/wiki/Waiting_for_Godot") never comes.)

---

### Post by stamatiou on 2013-05-11
So what you are suggesting is taking the source code of an existing smartphone OS and tweaking it? Also I did not understand that part with waiting for Godot :P

---

### Post by shawnhcorey on 2013-05-11
I suggest you start by learning [MINIX]("https://en.wikipedia.org/wiki/MINIX"). MINIX was created by [Andrew S. Tanenbaum]("https://en.wikipedia.org/wiki/Andrew_S._Tanenbaum") to teach the concepts used in operating systems.

And for those with insatiable appetites for trivia, here is Linus Torvalds 's [announcement of Linux]("https://groups.google.com/forum/?fromgroups=#!msg/comp.os.minix/dlNtH7RRrGA/SwRavCzVE7gJ") on the MINIX newsgroup.

---

### Post by stamatiou on 2013-05-11
Thanks for the reply, but can you be more specific about "learning MINIX?" I found this book [102-1327526-9316154]("http://www.amazon.com/gp/product/0131429388/qid=1137005040/sr=8-1/ref=pd_bbs_1/102-1327526-9316154?n=507846&s=books&v=glance") and it sesms like a good introduction in operating systems but I don't know if it will help me on developing for mobile.

---

### Post by shawnhcorey on 2013-05-11
> **stamatiou said:**
> Thanks for the reply, but can you be more specific about "learning MINIX?" I found this book [102-1327526-9316154]("http://www.amazon.com/gp/product/0131429388/qid=1137005040/sr=8-1/ref=pd_bbs_1/102-1327526-9316154?n=507846&s=books&v=glance") and it sesms like a good introduction in operating systems but I don't know if it will help me on developing for mobile.

It's a great book; I have the 1st edition of it. All OSes are essentially the same. Learn one will give you a solid foundation to understanding how they might work on mobiles.

---

### Post by stamatiou on 2013-05-11
So I could for example study the code of MINIX and add support for phone hardware?

---

### Post by shawnhcorey on 2013-05-11
> **stamatiou said:**
> So I could for example study the code of MINIX and add support for phone hardware?

With effort. The reason for studying MINIX is to understand OSes in general. I don't know enough about mobile to know how big a task it would be. But from what I know about OSes and programming in general, I can definitely say it's not a weekend project.

---

### Post by tgalati4 on 2013-05-11
Since Android has a large user base and will probably be around for a while, it's worth spending some time to understand the Linux-like kernel that Android runs on.  Ubuntu phone will probably run on the Android kernel as well, so that is another phone OS to study.  Once you understand Android, you can compare it to Maemo, Meego, WebOS and several other phone operating systems so you can see the similarities and differences.  When you have that knowledge, then you can start writing your own phone OS.

Or start with a blank page and just start coding.

---

### Post by King Dude on 2013-05-11
Well, first off, finish learning Assembly and then practice using Assembly in home-made hardware using transistors, resistors, etc. Once you have some experience under your belt with using Hardware AND Assembly, then you could begin learning how to implement C alongside Assembly properly. Once that step is accomplished, and you have a bare-bones computer, you could develop a GUI for your machine.
Check out this link: [http://www.homebrewcpu.com/construction.htm](http://www.homebrewcpu.com/construction.htm)

Of course, that process above might take years, and as much of a painstakingly hard time it is to get such a meager harvest (4-8bit CPU @ ~1Mhz) you'll have a new found respect for the old fogies back in the 70's and 80's that had to put up with this crap.

However, fortunately for you there is such a thing as an internet with bountiful information to save you from this hell. what is this thing that will save me you ask? Why, it's LinuxFromScratch of course!
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Remember, Android uses the same kernel as Linux, so do not think for one second that LFS is only for desktops. And most importantly, patience is important and DO NOT CUT CORNERS! 

Goodluck!

---

### Post by CptPicard on 2013-05-12
You're pretty much completely out of your depth, but I would suggest you take a look something like Sailfish, the new Linux-based phone OS (derived from MeeGo)...

---

### Post by trent.josephsen on 2013-05-12
While digital electronics is nice to have, a homebrew CPU is a lifetime project on its own. The overlap between digital logic and OS development isn't so great that an aspiring OS developer can't start with an ARM dev board and reasonably modern hardware. At least, that's what I think.

---

