---
title: "Uninstalling Ubuntu"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Yorkie49 on 2008-11-10
I made a huge mistake and installed ubuntu 8.1 as a stand alone operating system on my laptop. How do I undelete it and start again by installing Vista so I can then run ubuntu from a cd?
Please help

---

### Post by keplerspeed on 2008-11-10
IF you installed ubuntu on the entire disk you will have to boot the win installation cd and install vista on the entire hd.

However, you could partition the hd, and install vista on the newly created partition.

So firstly:

Do you have the vista installation cd and key?

And your options are:

boot the vista installation cd, format the hard drive, and install vista. After that you can play with ubuntu, partition the drive, install ubuntu, or stick to a live cd to play with.

OR download gparted live cd iso image, burn it to cd, partition your drive, and install vista on the partition. after this you will have to reload the grub bootloader, but more on that later...

---

### Post by Yorkie49 on 2008-11-14
I cannot load the vista disk my cd drive doesn't recognise it.

---

### Post by maybeway36 on 2008-11-14
In that case, ouch. :/
Maybe you could find someone with a Vista disk that works on your laptop (and is the same edition so the key works.)

---

### Post by oilchangeguy on 2008-11-14
> **Yorkie49 said:**
> I cannot load the vista disk my cd drive doesn't recognise it.

are you booting the computer from the cd? or trying to run it while in ubuntu?

---

### Post by MasterSander on 2008-11-14
make sure your BIOS boots the cd drive first and then the hard drive

---

### Post by JumpForJoy on 2008-11-14
I'm not sure if this will work, but what I did when it happend to me was:
1. reinstall ubuntu.  (I know you want to get rid of it, but if you but it back, you get your /boot/grub files back.  This lets you boot up your computer again.)
2. Just keep the Grub and get rid of all the files that aren't under /boot


Hope that helps some.  The first step should help the most.  Once you can get backinto an os do whatever you want to get rid of ubuntu.  good luck

---

