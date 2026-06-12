---
title: "Trouble installing Ubuntu on an old Sony Vaio laptop"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by XenonType on 2008-07-28
Hi guys, I hope I'm posting this in the right place.

I am trying to install Ubuntu for the first time, on a Sony Vaio laptop (Pentium 3, 128MB ram), through an external CD drive connected with PCMCIA.

After choosing "Install Ubuntu" from the setup screen, it starts loading (gui loading screen), but after a few seconds of loading it just tosses me into command line mode, prompting for (initramfs) ?

The exact text which is displayed after is tosses me into command line mode:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```


Any help would be greatly appreciated.

---

### Post by Nikitas350 on 2008-07-28
Try download the alternate desktop CD. (I would also suggest xubuntu for this notebook...)

---

### Post by spiderbatdad on 2008-07-28
You'll need to install Xubuntu. 128MB RAM is far short of the 384-512 recommended minimum for Ubuntu.

I believe with the Vaio, you'll want to use the noapic nolapic boot options by pressing F6 "Other Options" at the start up screen.

---

### Post by bumanie on 2008-07-28
You should manage to get xubuntu to work on those specs. but ubuntu needs 384 to run. Xubuntu will work on 128mb ram, but you will have to install with the alternate cd (text-based install cd) as the live xubuntu cd needs 192mb ram to install with.

---

### Post by northern lights on 2008-07-28
That machine seems to be on the very low-end of the spectrum of PCs capable of running Ubuntu smoothly.

Check [help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for reference.

128megs of RAM is fishy and you didn't let us know the nature of the graphics device either, which probably is also gonna be troublesome.

I'd say go for Xubuntu or FLuxbuntu if you wanna stay in the Ubuntu family. Otherwise check Damn Small Linux or Puppy.

---

### Post by spiderbatdad on 2008-07-28
There is a screencast here :[http://screencasts.ubuntu.com/Installing_Xubuntu](http://screencasts.ubuntu.com/Installing_Xubuntu)
including a demo installing Xubuntu with the alternate cd...a slightly more technical process.

---

### Post by gjoellee on 2008-07-28
you should also check out wattOS (a lightweight Ubuntu. Still in alpha i think) read more about it here: [http://polishubuntu.co.nr/](http://polishubuntu.co.nr/)

---

### Post by XenonType on 2008-07-28
Thanks for the fast replies. :)

I didn't know the 128MB was the issue. Kinda hard to upgrade it though.

Basically I want that machine to have some use, without having to install Windows 98 on it. :\ 
So what I'm looking for is a friendly linux distro with low reqs.... I have no previous experience with linux so I need the installation to be relatively easy (or bundled with a good guide).

I'll try the alternate Xubunutu =)

---

### Post by bumanie on 2008-07-28
> **XenonType said:**
> Thanks for the fast replies. :)

I didn't know the 128MB was the issue. Kinda hard to upgrade it though.

Basically I want that machine to have some use, without having to install Windows 98 on it. :\ 
So what I'm looking for is a friendly linux distro with low reqs.... I have no previous experience with linux so I need the installation to be relatively easy (or bundled with a good guide).

I'll try the alternate Xubunutu =)

As said, xubuntu alternate cd should work, you could also use puppy linux or damn small linux - they are both designed to work on 'low-end' computer hardware.

---

### Post by halitech on 2008-07-28
I've got a compaq armada (P3, 192meg Ram, 120gig hard drive, ATI video card) and it wouldn't install Ubuntu either using the cd but Xubuntu works fine on it using the alt install cd. It won't be a powerhouse but will certainly be usable (and more stable and secure then win98)

---

### Post by eriqjaffe on 2008-07-28
I have a Vaio laptop which sounds like it's pretty much identical to yours (except mine's a Pentium 2), and I used the Alternate installer without issue.

Well, almost without issue - I had to do a bit of juggling to get it to recognize the PCMCIA optical drive after the install start - you need to add "ide2=0x386,0x180" (at least, I had to) to the end of the boot string, otherwise the install will fail.

---

