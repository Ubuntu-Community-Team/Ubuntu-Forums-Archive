---
title: "PROBLEMS installing"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by jackinfl on 2013-07-17
On a formatted hard drive I get the following error message:

[   44.088438] Kernel panic - not syncing: Attempted to kill init! exitcode+0x00000b00] 
[   44.088438] 
[   44.0885281]  drm_kms_helper: panic occurred, swithcing back to text console

Any ideas as to how to handle.

Many thanks

Jack

---

### Post by newb85 on 2013-07-17
Please give more detail about what is going on.  How exactly are you installing Ubuntu?  When in the installation process did you receive this error?

---

### Post by fantab on 2013-07-17
Do you get the Panic error after installing Ubuntu or when installing Ubuntu?

If its when trying to install then you have start from doing the [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on your dowloaded .iso then burning in properly, as recommended [HERE]("http://www.ubuntu.com/download/desktop"), to a medium like DVD or USB.

What computer are you trying to Install Ubuntu to? What are its hardware specifications?

---

### Post by newb85 on 2013-07-17
Also, what release of Ubuntu are you installing?  12.04? 13.04? 12.10?

---

### Post by jackinfl on 2013-07-17
1st thanks for all that been concerned enough to help me solve my problem.

This is a H
P DV5000 Laptop with 1 gb ram and a 80 GB hardrive. The hard drive is from another computer that I re-formatted the drive before installing in the lap top.

I first tried using ubuntu 12.04.2-desktop-i386 and had the same results after about 10 minutes I get the error message listed above.
I than tried using 13.04--desktop-i386 with the same results.

The unit was running XP. I am using Pen drive to try to laod the OS.

Thanks again for the help.

---

### Post by fantab on 2013-07-17
With only 1gb RAM you must really try [Xubuntu]("http://xubuntu.org/"). Its Ubuntu with [XFCE]("https://en.wikipedia.org/wiki/Xfce") desktop, it is very light on system resources (It needs less resources to run) than the regular Ubuntu with Unity. [Lubuntu]("http://lubuntu.net/") is even more lighter.
12.04 version is LTS and hence you can go with it. Do a MD5Sum check on your downloaded .iso then reburn it to USB using the links suggested in post #3. Then tell how it goes.

Another thing, can you install XP on the machine, after you have changed the HDD? Try and tell us what happens. If its a Hardware issue then XP install should make it clear.
If you don't want to dual boot Ubuntu and XP then check in your BIOS settings and see what mode is SATA set to. It is most probably set to IDE. If you don't want XP on the machine then change the mode to AHCI and see if it helps installing Ubuntu/Xubuntu.
Also check in BIOS to confirm that your machice is set to boot from USB.

Good Luck...

---

### Post by newb85 on 2013-07-18
Ubuntu and Xubuntu 12.04 are LTS.  Lubuntu 12.04 is not.

If you had the same problem on both 12.04 and 13.04, it's probably not a problem with the download.

---

### Post by Boab1993 on 2013-07-18
Iv'e had a look around some of the forum pages and looked at a few things about your hardware.
It appears that alot of people are having this problem with 13.04 ,especially with netbooks, so to me it sounds either like a bad install, or hardware issues.
Try booting up in safe mode on your laptop, or alternatively, try install xubuntu 13.04, it found it mentioned on the forums that it appears to install fine on laptops with these problems. As for why i dont know. Theres alot of possibilities with this issue, without more information it would be difficult to diagnose.
My thoughts are currently going towards bad installation cd/usb, as it seems to common to be hardware.
Suggestions are if you haven't already, try using linux's universal usb installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Else re-format your hard drive and try again.

Sorry i cant be more helpful!

---

### Post by jackinfl on 2013-07-19
Now I am more confused than before - what is [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM#md5sum") - do I need to (and more important how) do I it?.

I am creating a USB Pen Drive with the Xubuntu that was mentioned. I have swapped out the hard drive and now have a new freshly formatted drive (no OS - blank drive).

Will advise what happens.
thanks again to all

---

### Post by jackinfl on 2013-07-19
Just tried a fresh install with both xubuntu-12.04.2-desktop-i386 and xubuntu-13.04-desktop-i386 and in both cases (after switching Bios to laod from USB) can not get past the error message "missing NTLDR" file.

I do not have a Windows disk available. This side of going and purchasing Windows any ideas.

JAck

---

### Post by fantab on 2013-07-19
If I am not wrong then the error, "missing NTLDR file' is Windows error, which I assume you have it on. This could also mean that your computer is not booting from USB. If it did boot from USB with XUbuntu then it should be able to boot and load the USB.
Have you ENABLED USB boot in BIOS?
Do you still have XP on the the computer? If yes, and if you want to fix the error then you will need a XP installation Disk or 'Repair disc' if you have. If not then reinstalling XP is your best bet.

---

### Post by jackinfl on 2013-07-20
Thanks again for the effort - the hard drive I am using is BLANK - no OS. I do not have the Windows install disk. I do have the recovery/restore disks created for this particular unit - they will not boot.
I have changed the BIOS to force a boot from the USB - but still get the missing NTLDR message.

Going to try putting the drive in another machine and see if I can ionstall from there.

---

