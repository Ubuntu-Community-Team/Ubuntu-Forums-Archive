---
title: "How do I make terminal command programs run?"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by kcldr1 on 2013-12-22
I am completely new to Ubuntu, actually any form of Linux, and I can run commands to add programs to my files, but after that I'm not sure how to make them run, or execute in order to use them. Any help would be appreciated greatly.

---

### Post by Iowan on 2013-12-22
> **kcldr1 said:**
> ... and I can run commands to add programs to my files... I'm not quite sure what you mean. :confused:

---

### Post by kcldr1 on 2013-12-22
I'll try to be  a little clearer if I can. I downloaded a program package that is supposed to make my cannon 5200 series printer run on Linux, and the file shows up in the downloads folder, but what do I do after that to make it work, or install it on the operating system so my printer will print?

---

### Post by deadflowr on 2013-12-22
> **kcldr1 said:**
> I'll try to be  a little clearer if I can. I downloaded a program package that is supposed to make my cannon 5200 series printer run on Linux, and the file shows up in the downloads folder, but what do I do after that to make it work, or install it on the operating system so my printer will print?

What is the name of the package?

By that, I mean(really) what is the end suffix.
is it something like .sh, or something like .deb?
Or perhaps, .targz?
Most of those should be easy to work with.

As long as it isn't .rpm, which is a different packaging system than Ubuntu.
An rpm package would have to be converted, so it would be a little more difficult to work with.

---

### Post by cincibluer6 on 2013-12-22
> **kcldr1 said:**
> I'll try to be  a little clearer if I can. I downloaded a program package that is supposed to make my cannon 5200 series printer run on Linux, and the file shows up in the downloads folder, but what do I do after that to make it work, or install it on the operating system so my printer will print?

If it is a .deb file, you're on the right track. Either double click and let Ubuntu handle it or go into the terminal and..
1) cd (change directory) to where it's at. So if you are in a standard terminal as the user, just type
```
cd Downloads
```
I find it is easy for new users to also just install "open in terminal" in Nautilus. I can't remember the exact name of the package but if you install it, you can just be going through Files (nautilus) and right click in whatever directory and there'll be a context menu for "Open in Terminal" at that location.
2) Anyway, once you're in there, if it's a .deb, simply input
```
dpkg -i packagename.deb
```
dpkg is telling the terminal that it's a .deb file and -i is simply the option for installing it.

3) If it's a .tgz or other kind of compressed file, you can do it in the terminal (varies based on type of zip) or just double click it and Ubuntu will extract it for you. Then just install it once you get to the .deb file.

Hope this helps. Good luck on your first foray into Linux.

Also, not sure if you really need that file or not but CUPS (the printer package on Linux) is very good and might be all you need.

---

