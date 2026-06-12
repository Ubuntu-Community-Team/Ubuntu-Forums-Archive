---
title: "What Distro is right for this task?"
date: 2008-10-13
forum: Other OS Talk
---

### Post by TheLocalGraveDigger on 2008-10-13
I love Ubuntu and the idea of the Debian system(been experimenting with Linux for about a year now), but i have an old PC that has poor specs and the Ubuntu would not work well here. 

192 MB ram
266 MHz processor

I want to turn it into a Diskless box that i can use to configure any HDDs that are present inside it.The computer will not have a CD dive but can boot via PXE. hardest part.....i want a simple GUI with Gparted(I'm used to it). I appreciate all the help i have received on this forum.:)

---

### Post by Helios1276 on 2008-10-13
What about something like Puppy Linux or Damn small running an xfce desktop?

---

### Post by zmjjmz on 2008-10-13
I would also recommend Damn Small Linux, or you could get a barebones Debian install and install other packages from the CLI.

---

### Post by SomeGuyDude on 2008-10-13
> **Helios1276 said:**
> What about something like Puppy Linux or Damn small running an xfce desktop?

Xfce might be a touch heavy, don't you think?

---

### Post by snowpine on 2008-10-13
I am not familiar with PXE. Other than that detail, I think SliTaz would work well on your hardware, and it includes GParted.

---

### Post by xebian on 2008-10-13
> **TheLocalGraveDigger said:**
> I love Ubuntu and the idea of the Debian system(been experimenting with Linux for about a year now), but i have an old PC that has poor specs and the Ubuntu would not work well here. 

192 MB ram
266 MHz processor

I want to turn it into a Diskless box that i can use to configure any HDDs that are present inside it.The computer will not have a CD dive but can boot via PXE. hardest part.....i want a simple GUI with Gparted(I'm used to it). I appreciate all the help i have received on this forum.:)

How about GpartedLive?

---

### Post by kk0sse54 on 2008-10-13
A Netinstall of most distros along with a light wm like openbox, fluxbox, awesome, dwm etc etc should work perfectly fine for your situation.

---

### Post by TheLocalGraveDigger on 2008-10-13
i have a copy of the Gparted live....anyone know how to use it? it contains no pxelinux.0 file.

---

### Post by kerry_s on 2008-10-13
custom debian, add only what you want to use.
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

at the package selection, uncheck both

log in as root

apt-get install xorg gdm fluxbox gparted etc....

reboot> ctrl+alt+delete

---

### Post by TheLocalGraveDigger on 2008-10-13
Also it is noteworthy that I mention that this cannot install to any hard drives and must be able to run from memory.

---

### Post by cardinals_fan on 2008-10-13
I recommend SliTaz.

---

### Post by snowpine on 2008-10-13
+1 SliTaz can run completely from memory with 192mb of ram. It runs equally well from Live CD, USB, or hard disk. And it has excellent "remastering" tools for creating your own variant.

---

### Post by Twitch6000 on 2008-10-16
DSL for sure.

---

### Post by zmjjmz on 2008-10-16
SliTaz is prolly too much for a 266MHz Proc, but another option is Damn Small Linux as it has a toram boot option.
So when you boot it and it has the ```
boot:
``` prompt, type ```
dsl toram
``` and hit enter.

---

