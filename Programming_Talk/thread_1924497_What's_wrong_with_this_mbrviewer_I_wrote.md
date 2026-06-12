---
title: "What's wrong with this mbrviewer I wrote?"
date: 2012-02-12
forum: Programming Talk
---

### Post by venom104 on 2012-02-12
Here is the program [http://pastebin.com/yawwCSSA](http://pastebin.com/yawwCSSA)

Before the mods merge this with my old thread, I would like to state that it deals with a different problem. My old thead was about how to determine something was wrong with a previous version of my program, this thread is about how to fix it. 

EVERYTHING on my program is correct execpt for a few small details. On my virtual machine's mbr.bin file, the CHS addresses of all of them are correct, except for the second and third sectors which are off. I'm not sure why this is, because it works fine for the first one, and I think the offsets I used are correct.

I need someone else to create their own mbr.file and look it it, if you don't know how you use this command [FONT=courier new]sudo dd bs=512 count=1 if=/dev/sda of=mbr in the same folder as the mbrviewer.c file. 

Hopefully you guys can help me out, it's due tomorrow so I don't have much time.
[/FONT]

---

