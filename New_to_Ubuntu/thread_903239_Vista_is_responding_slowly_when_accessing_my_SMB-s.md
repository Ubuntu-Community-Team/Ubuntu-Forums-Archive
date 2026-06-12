---
title: "Vista is responding slowly when accessing my SMB-share on Ubuntu"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by telekarlsen on 2008-08-28
I have set up my Ubuntu 8.04.1 Desktop with a SMB share which I access from both my XP and Vista machines.
Both Windows can browse the share easily, but when I try to go into Properties for the shared files and folders (right-click -> Properties) Vista goes on holiday. The browser window freezes.
After some waiting (1-2 minutes) the Properties menu appears.

Obviously, this is a M$-problem, and with Vista in particular.
However, someone in here might hold some info about the share which can help me. ;-)

I've seen something on various forums about oplock, auto-tuning and so on. Don't know where to begin... :?:


Any ideas?

---

### Post by eightmillion on 2008-08-28
I think that when you click properties, Vista calculates the total size of all the files and the number of files and folders. This can take some time over a network link and I don't think that there's anything you can do about it.

---

