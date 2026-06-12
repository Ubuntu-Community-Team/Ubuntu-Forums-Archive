---
title: "how to run memtest86 from ubuntu cd on windows8 machine with uefi"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by jflinux on 2013-05-06
Trying to run memtest86 from DVD.
Went into windows8(tm microsoft) and turned off secure boot,
turned on boot from CD.
BUt when I boot ubuntu13.04, I only get 4 options and none are to run memtest.
Booting off my ubuntu10.04 cd, it just boots to windows.
Help????
Thanks in advance.

---

### Post by fantab on 2013-05-06
You have to hold down any key when Ubuntu live is booting then F6, select your language, then you get the menu from where you can run 'memory test'.

Here: [http://askubuntu.com/questions/187573/memtest-with-ubuntu-12-04-live-cd](http://askubuntu.com/questions/187573/memtest-with-ubuntu-12-04-live-cd)

---

### Post by squakie on 2013-05-06
Make sure it's the 64-bit version of Ubuntu, not the default 32-bit.  When I was having problems with UEFI I had to use that to get it recognized, and I also had to go into the BIOS boot menu (F12 on my laptop) and then select the UEFI Ubuntu DVD.  Mine for whatever reason didn't just automatically boot Ubuntu - I had to select it.

---

### Post by jflinux on 2013-05-06
So, usb ubuntu12.04 64 bit desktop, 
presents a grub menu that says
try ubuntu without installling
Intall ubuntu
check disk for defects
..., 'e' to edit commands, 'c' for command line.

Holding return down or space down just boots to ubuntu cd try without installing.
DVD burn of ubuntu13 desktop 64bit also boots to ubunut cd try without installing.
So still can't boot a memtest86 image....???

---

### Post by sanderj on 2013-05-06
I found this 2012 quote:

> Please also remember that if you have a UEFI motherboard, you can't UEFI boot memtest86+
You need to use the BIOS/legacy mode, not any sort of EFI mode.

HTH

---

### Post by jflinux on 2013-05-06
Yep, sanderj, you may be right:[URL="http://askubuntu.com/questions/258991/where-is-the-memtest-option-on-the-12-04-64-bit-live-cd"]
http://askubuntu.com/questions/258991/where-is-the-memtest-option-on-the-12-04-64-bit-live-cd[/URL]
That may be the problem, although above is about 12.04, not ubuntu 13.

---

### Post by sanderj on 2013-05-06
> **jflinux said:**
> Yep, sanderj, you may be right:[URL="http://askubuntu.com/questions/258991/where-is-the-memtest-option-on-the-12-04-64-bit-live-cd"]
http://askubuntu.com/questions/258991/where-is-the-memtest-option-on-the-12-04-64-bit-live-cd[/URL]
That may be the problem, although above is about 12.04, not ubuntu 13.

Can you temporarily switch your system from UEFI to BIOS (it's a setting, right?), and then boot again to test if memtest86 is there?

(I'm still a bit puzzled: the menu shown must thus depend on the boot mode the system is in ... ? That would mean that the very first boot sequence can recognize that state. If so, that would be good news for unclarity in the boot process on UEFI systems. But let's first wait for your result)

---

### Post by jflinux on 2013-05-06
I don't see a boot to old bios in UEFI menus for Toshiba laptop C855-S5194  (which looks just like the old BIOS on the screen).

As to why the menus look different,
they are at different run levels I think?   
The menu I get is TEXT for UEFI boot which is the text GRUB menu.  Boot the same on a Non_UEFI (old bios on older desktop computer)
and you get a GRAPHICs UBUNTU boot menu like:
[http://askubuntu.com/questions/129116/12-04-wont-boot-from-live-cd-or-usb]("http://askubuntu.com/questions/129116/12-04-wont-boot-from-live-cd-o")

So the menus are from:
uefi boot:   gets grub menu
Bios boot:  boots up to ubuntu and gets ubuntu advanced menu

My guess now it that holding down any key is not getting the key stroke to ubuntu in uefi boot.
It therefore always boots to full running demo of cd (actually a burned dvd) based ubuntu and skips branching
to the advanced F6 ubunut boot menu because something (maybe uefi) is blocking the keystroke from getting to ubuntu.

---

### Post by sanderj on 2013-05-06
> **jflinux said:**
> I don't see a boot to old bios in UEFI menus for Toshiba laptop C855-S5194  (which looks just like the old BIOS on the screen).



... and "legacy boot"?

---

### Post by jflinux on 2013-05-06
Didn't see legacy boot in UEFI bios menus.   I might check if flashing the bios to a newer version helps.
Seem UEFI breaks memtest86.
Even download from memtest86.com and burning a cd from there gives the result that it skips booting from 
cd and goes to windows.
Might just be a problem with toshibas???

---

### Post by jflinux on 2013-05-07
Ok.  Finally burned a memtest86 cd from memtest86.com .
(New edit: I have not tried ubuntu cd boot to memtest86+ as of yet.)
Found the legacy boot option inside uefi bios.
FIRST you MUST turn off secure boot or you can't change to csm from UEFI boot.
Then go to ADVANCED and then to boot mode like instructed here:
[http://www.top-password.com/blog/set-windows-8-pc-to-boot-with-legacy-bios-mode-instead-of-uefi-mode/](http://www.top-password.com/blog/set-windows-8-pc-to-boot-with-legacy-bios-mode-instead-of-uefi-mode/)

Finally can upgrade to 16GB in my new laptop and test to see it it works.

---

### Post by sanderj on 2013-05-07
So, conclusion: memtest86 on CD/DVD is only in the boot menu if (UEFI-secure-boot is off and) legacy-boot is on?

Wow.

The good news: that means the Linux CD/DVD boot sequence *does* know which boot/mode the system is in: UEFI or Legacy. And that is good news in general: that means the Linux CD/DVD can signal that, for example when someones tries to boot 32-bit Linux on a UEFI-enabled system (which doesn't work; you need 64-bit on a UEFI-enabled system).

---

### Post by jflinux on 2013-05-07
OK, I tested it with the ubuntu13.04 cd just now with the mode
legacy boot (CSM mode)
secure boot off
an the keystroke goes thru and allows running memtest86+ off the ubuntu CD.
Before, it seemed holding down the key did not work or the keystroke was not making it
to the ubuntu software at boot time??

The one thing I hate about my new laptop is that it seems you have to boot into windows to 
edit the UEFI bios settings.

---

