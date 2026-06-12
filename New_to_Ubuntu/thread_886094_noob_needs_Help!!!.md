---
title: "noob needs Help!!!"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by imput1234 on 2008-08-10
Hey guys, 

I'm having some problems with Ubuntu, I don't know if this happens to anyone else but the OS laggs like crazy idk, and sometimes it just dies. It freezes and idk what to do. Is there something like Ctrl+Alt+Delete command from windows in Ubuntu.

And

How do I make the partition for Ubuntu bigger? and how can I remove the windows partition completely without destroying some files?

Is there a nero (CD/DVD/ISO burner) substitute for linux? 


Thanks.

---

### Post by lisati on 2008-08-10
Before you go tinkering with disk partitions, make sure that you make a backup of your important data!

For burning disks (e.g. like with Nero), have a look here: [https://help.ubuntu.com/8.04/musicvideophotos/C/index.html](https://help.ubuntu.com/8.04/musicvideophotos/C/index.html)

---

### Post by spiderbatdad on 2008-08-10
ubuntu installs brasero for disk burning, and ther are command line tools.
we'll need some system specs to help you with freeze ups...you probably need boot options.
check out gparted live cd for resizing your partitions.

---

### Post by OutOfReach on 2008-08-10
Hmm what applications are you running when your system laggs/freezes etc..
And the thing that you are looking for that is like the Task manager for Windows is System Monitor (System>Administration>System Monitor)

---

### Post by imput1234 on 2008-08-10
> **OutOfReach said:**
> Hmm what applications are you running when your system laggs/freezes etc..
And the thing that you are looking for that is like the Task manager for Windows is System Monitor (System>Administration>System Monitor)

Every time the OS freezes is when I'm running firefox, but it happens arbitrarily. For example, I tried to reply to this thread and it froze and I needed to reboot. 

The specs: I'm currently using a laptop: Acer Aspire 5102

AMD 64 x2 TL50 1.6ghz, 512kb l2 cache
ATI Radeon Xpress 1100
120GB HD
1GB DDR2

Is there a short cut to bring up System Monitor, is there also a short cut to bring up the terminal.

---

### Post by imput1234 on 2008-08-10
> **lisati said:**
> Before you go tinkering with disk partitions, make sure that you make a backup of your important data!

For burning disks (e.g. like with Nero), have a look here: [https://help.ubuntu.com/8.04/musicvideophotos/C/index.html](https://help.ubuntu.com/8.04/musicvideophotos/C/index.html)

I want to move my files to the Ubuntu partition, but there is not enough room. But there is plenty of room in the MS partition.

---

### Post by OutOfReach on 2008-08-10
Interesting, you can just press ALT+F2 and type in 'gnome-terminal' for the terminal and 'gnome-system-monitor' for the System Monitor.

---

### Post by lisati on 2008-08-10
> **imput1234 said:**
> I want to move my files to the Ubuntu partition, but there is not enough room. But there is plenty of room in the MS partition.

You have a number of options. 

If you can afford it (or if you have a friend with a spare one that you can borrow) one option is a separate hard disk that you use as a temporary storage area while you are moving things around and resizing your partitions.

Another option is to copy everything to a data CD or DVD.

---

### Post by hyper_ch on 2008-08-11
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by imput1234 on 2008-08-11
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.


Alright, I'll remember that in the future. Well, it is still happening, the whole damn OS freezes and no key stroke and no mouse clicks works.

Does anyone have a clue why this is happening?

Also 1 update does not work:

linux-image-2.6.24-19-generic

anyone know how to fix that.


thanks.

---

### Post by imput1234 on 2008-08-11
And also how can I put 4 separate backgrounds on the 4 workspaces.


thanks.

---

### Post by Sinkingships7 on 2008-08-11
I have one suggestion and one trick.

**The Suggestion**
I somewhat recommend that you perform an alternate command-line installation, and build your way up from there. In my testing, I've noticed that the default Ubuntu install can be much more error prone than a minimal install worked up to a full install. You should only undertake this if you have at least a moderate knowledge of computers, but it certainly doesn't take any form of expertise. My blog on [how to perform a minimal-installation of Ubuntu]("http://christopherstechcorner.blogspot.com/") may be of some assistance.

**The Trick**
Instead of hard rebooting, which can be dangerous to your system, here's a little key combo that should get you out of such a situation, and allow you to reboot your computer safely whenever it locks up. Simply hold Alt+SysRq (also knows as Prt Scr), and press these keys: R, E, I, S, U, B.

---

### Post by imput1234 on 2008-08-11
> **Sinkingships7 said:**
> I have one suggestion and one trick.

**The Suggestion**
I somewhat recommend that you perform an alternate command-line installation, and build your way up from there. In my testing, I've noticed that the default Ubuntu install can be much more error prone than a minimal install worked up to a full install. You should only undertake this if you have at least a moderate knowledge of computers, but it certainly doesn't take any form of expertise. My blog on [how to perform a minimal-installation of Ubuntu]("http://christopherstechcorner.blogspot.com/") may be of some assistance.

**The Trick**
Instead of hard rebooting, which can be dangerous to your system, here's a little key combo that should get you out of such a situation, and allow you to reboot your computer safely whenever it locks up. Simply hold Alt+SysRq (also knows as Prt Scr), and press these keys: R, E, I, S, U, B.

Alright, cool. I might give that a try

---

### Post by imput1234 on 2008-08-11
My processor is AMD Turion 64 X2 

so should I download the 64bit amd install instead.

---

