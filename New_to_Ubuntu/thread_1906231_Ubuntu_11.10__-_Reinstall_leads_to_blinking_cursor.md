---
title: "Ubuntu 11.10  - Reinstall leads to blinking cursor"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by Cyb3rtr1x on 2012-01-08
Hello all,
Here's my story:
A few days ago I took the plunge to remove windows 7 and replace it with Ubuntu 11.10.
I had a few errors during the install including acpi errors and the blinking cursor but I think I did some tweaks and a fresh install (from USB) which got me going.
Today I made what I know see as I mistake and reinstalled 11.10 as I felt i made a few mistakes and wanted to start fresh.
The install went fine but then, towards the end I went off for a drink and I come to find the computer off, to my knowledge the installer is ment to reboot.
Now, when I boot the computer it comes up with a black screen and blinking cursor; holding shift not working.

MORE INFO:
Acer Apire 5740g (Laptop)
ATI Graphics 

Any help appreciated.
Kind regards,
Cyb3rTr1x

---

### Post by jjex22 on 2012-01-08
Hello! welcome to the forums! sorry to hear you're having problems.

First of all go into your bios and check that your default boot device is your hard drive?
if not change this and try again.

Failing this, get out your live usb or cd and boot it up so we can find out more about your system.

Once in the live environment go to a terminal by pressing ctrl+alt+T, then enter the following command

```

sudo fdisk -l

```
the -l is a little L btw.

in your reply highlight the text and click on the # symbol at the top of the reply box :)

---

### Post by critin on 2012-01-08
> and I come to find the computer off, to my knowledge the installer is ment to reboot.The installer doesn't reboot by itself, you must choose to 'reboot now', and then it will tell you to remove the usb stick, hit enter and it will continue to reboot.

You mentioned errors, tweaks and mistakes.  If you tweaked the live usb stick, it won't save them for the install.  If you tweaked the bio, perhaps you'll need to check it again.

If it was me, (and I've done it plenty of times--lol)  I would create a new iso image on the stick from your saved image.  I use unetbootin.  Install again and choose format--(again).  Try to stay with the computer and make sure it loads and configures grub toward the end of the install.  You may have to download a new image.

---

### Post by Cyb3rtr1x on 2012-01-09
Good news ... And bad news.
Thank you so much for all your help guys, in the end I resulted to a fresh install and...boom, it works; although not sure why.
However the bad news is that when the laptop gets remotely hot it shuts down? Any ideas appreciated.

---

