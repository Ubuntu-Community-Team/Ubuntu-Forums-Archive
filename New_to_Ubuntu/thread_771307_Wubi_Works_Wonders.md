---
title: "Wubi Works Wonders"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by zaivala on 2008-04-27
Some of you followed my trials and travails of my HP a1020n not letting me load Linux and making me reset everything and lose my files (yeah, I need to backup more).  Well, between last night and this morning, I used Wubi to install Kubuntu, and it works fine.

Now you can expect me to ask all the stupid questions while trying to install my proggies... for some reason, K(4)ubuntu does not seem to include Firefox, or Nethack, or...

Anyhow, I now CAN dual-boot Windows & Linux.  If anyone else has this problem, they now know a solution.

Also, I asked about perhaps running LiLo or Grub from a CD-ROM and got no response... a friend of mine figured out how to do just that, and I have the disk (now that I don't need it, LOL).

Hugs,
Moss:popcorn:

---

### Post by zaivala on 2008-05-04
That install sucked... K4 is not ready for prime time...  I have since installed (Gnome) Ubuntu, and love it so much I've talked several other people into installing it.

Question:  What file do you edit (and how do you edit it) to get the bootloader to list Ubuntu ahead of Windoze? (i.e., default boot to Ubuntu, not Windoze)

Moss

---

### Post by ugm6hr on 2008-05-04
> **zaivala said:**
> Question:  What file do you edit (and how do you edit it) to get the bootloader to list Ubuntu ahead of Windoze?

Not sure what happens with Wubi, but it is normally:
/boot/grub/menu.lst

Ubuntu normally defaults to put itself as 1st in order though.

If you post the contents here, hopefully we'll be able to help.

---

### Post by aamukahvi on 2008-05-04
> **ugm6hr said:**
> Not sure what happens with Wubi, but it is normally:
/boot/grub/menu.lst

Ubuntu normally defaults to put itself as 1st in order though.

If you post the contents here, hopefully we'll be able to help.

I think Wubi adds ubuntu to the windows boot menu, so c:\boot.ini would be the place if I remember correctly.

---

### Post by angry_johnnie on 2008-05-04
Off the top of my head, it would be something like Start > Control Panel > System > Advanced. And then look for something like startup and recovery, which should have a **configure** button.  Clicking on that button will open another little window, where the very first option will be **default operating system**.  You can just change it there.

---

### Post by ugm6hr on 2008-05-04
> **angry_johnnie said:**
> Off the top of my head, it would be something like Start > Control Panel > System > Advanced. And then look for something like startup and recovery, which should have a **configure** button.  Clicking on that button will open another little window, where the very first option will be **default operating system**.  You can just change it there.

From memory, that uses a GUI to edit boot.ini

So that seems likely.

Sorry about my earlier post - no experience with Wubi :(

---

### Post by zaivala on 2008-05-06
Worked like a dream, thanks angry_johnnie.

---

