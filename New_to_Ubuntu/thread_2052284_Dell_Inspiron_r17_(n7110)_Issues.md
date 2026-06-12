---
title: "Dell Inspiron r17 (n7110) Issues"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by GingerSmurfs on 2012-09-02
I recently tried to install Ubuntu 12.04 alongside Windows 7 on my Inspiron r17 with an Intel i3 processor & nVidea GeForce GT 525 M video card, and immediately ran into issues. This is my first experience with Ubuntu or even Linux but as always I did my home work and tried to solve the issue myself. Truthfully I was over whelmed by the amount of information and just can't seem to fix it. Sorry if this was explained before but here is my issue:

I enter GRUB and choose to boot into Ubuntu 12.04. The screen goes black the brings up the keyboard icon on the bottom. After this though the screen simply returns to black and remains there.

If I understand correctly it has to do with my hybrid chipset? I am truly lost but want to to try Ubuntu, if someone could provide a simplistic explanation and guide I would be grateful.

---

### Post by veroslav on 2012-09-03
Hi,

I am guessing you are trying to boot of the Live USB.

I have exactly the same computer and I also experienced the same issue when trying to boot of the Live USB for the first time.

In my case, the problem was that I trtied booting it from a USB3 port, that is why it wouldn't work.

Have you tried booting of any of the other (USB2) ports?

Kind Regards,
Veroslav

---

### Post by veroslav on 2012-09-03
Sorry, didn't see you mentioned that you was choosing Ubuntu 12.04 from GRUB, which would indicate that you've already installed Ubuntu and not booting of the Live USB.

---

### Post by anewguy on 2012-09-03
Did you do a true dual-boot install, or is this a wubi install (ubuntu within Windows)?

Have you tried nomodeset as a boot option?  Some nVidia chipsets require that to get around various problems at boot - I don't if it will help you or not.  Search the forums with nomodeset as the search string and you should find the information you need.

---

### Post by GingerSmurfs on 2012-09-03
It was a true dual boot. I made the the disc, partioned the hard drive, and did an install from within the "try ubuntu..." option.

It is probably no worthy that I needed to use F6 and choose nomodeset, acpi=no, and nolapic. While I'm not sure what they are exactly for (new to Linux) I read they can help when you are experiencing a black screen when trying to install, which I was. Now though it just goeas black when I boot as well.

---

### Post by Bashing-om on 2012-09-03
--smurfs;
  You are almost there.... try to boot with only "nomodeset" as a boot option.
Here is a howto ...to get you started:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Questions/help....==> we are here.

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by GingerSmurfs on 2012-09-03
> **Bashing-om said:**
> --smurfs;
  You are almost there.... try to boot with only "nomodeset" as a boot option.
Here is a howto ...to get you started:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Questions/help....==> we are here.

[INDENT]hth <==BDQ
[/INDENT]

I have tried nomodeset before with no avail but I will try this tutorial. Thanks for the help, hopefully the first time I just made a mistake and I can get it to work now.

Lets say it does boot up though, what do I need to do to get my Drivers working properly?

---

### Post by anewguy on 2012-09-03
After you get everything booting correctly, I would go to Additional Drivers and let it search.  If it comes up with something that isn't activated, activate it.  Note that for nVidia, it's normally best to use the drivers that come via the repositories or from Additional Drivers, not the drivers from nVidia itself.

---

