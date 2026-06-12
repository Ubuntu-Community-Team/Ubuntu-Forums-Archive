---
title: "Grub problems with vista"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by jimjesus on 2008-08-09
I had a system set up to dual boot windows xp and ubuntu 8.04. I recently got a copy of windows vista ultimate from a friend and figured I'd try it out. I installed it to be separate from xp so I could boot into vista, xp or ubuntu. The problem is that after installing vista, the grub screen doesn't come up and instead another boot screen comes up letting me choose between vista and xp. How do I get grub to come up again so I can boot into ubuntu?

---

### Post by st33med on 2008-08-09
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

---

### Post by jimjesus on 2008-08-09
> **st33med said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

That is very helpful but I have run into another problem. When I put in a live cd and try and boot from it, it just sits with a "boot from cd..." message like its trying to read the cd and then just boots right into vista.

---

### Post by SlalomMan on 2008-08-09
It might be one of those "press any key to boot from cd...."

Have you tried pressing F12 or whatever key at the bios screen to select your boot source? sometimes that works better.

---

### Post by jimjesus on 2008-08-09
> **SlalomMan said:**
> It might be one of those "press any key to boot from cd...."

Have you tried pressing F12 or whatever key at the bios screen to select your boot source? sometimes that works better.
Yea, that's what I did. I pressed f11 at boot and selected my cd drive containing my ubuntu cd. It gave the dialogue it usually does when I boot from a cd, but took longer than usual. Eventually it just went into vista.

---

### Post by pi.boy.travis on 2008-08-09
You may have to enter BIOS settings and change the boot order settings there.

---

### Post by jimjesus on 2008-08-09
> **pi.boy.travis said:**
> You may have to enter BIOS settings and change the boot order settings there.

I'll try that next. I had this problem with my friend a few months ago. We installed vista on his computer but the install failed, leaving a non functioning vista residue on his drive. We decided to just install ubuntu on his computer but it did the same thing my computer is doing now, only when it tried to boot to vista, it crashed. I don't know if this is a known issue with vista or if we both had a unique experience.

---

### Post by st33med on 2008-08-09
Hrmm... Try checking the MD5 sums on that disc and try another LiveCD, eg: [Knoppix]("http://www.knoppix.net/")

---

### Post by pi.boy.travis on 2008-08-09
A buddy of mine had this problem with his ancient laptop.  He had barely enough RAM to boot it, but his BIOS wouldn't allow it even from the one time menu.  It worked after I changed his BIOS permanent settings.

---

### Post by pi.boy.travis on 2008-08-09
> **st33med said:**
> Hrmm... Try checking the MD5 sums on that disc and try another LiveCD, eg: [Knoppix]("http://www.knoppix.net/")

It's also a good idea to select "check CD for defects" from the CD's boot menu once you get that far, especially if you plan on installing.

---

### Post by jimjesus on 2008-08-09
> **pi.boy.travis said:**
> It's also a good idea to select "check CD for defects" from the CD's boot menu once you get that far, especially if you plan on installing.

Yea, the problem is getting that far first. But I definitely plan on doing that once I can get that far. Luckily I already have ubuntu installed and I'm just trying to repair grub.

---

### Post by pi.boy.travis on 2008-08-09
Once you get GRUB restored to the MBR, you are probably going to have to edit /boot/grub/menu.lst.  If you post it's existing contents, we can help you edit it.

---

### Post by jimjesus on 2008-08-09
So I tried setting my bios to boot from disc before it will boot from the hd and I still have it sit on the boot from disc dialogue and go right into vista.

---

### Post by pi.boy.travis on 2008-08-09
At this point I would try out Knoppix or another live CD.

---

