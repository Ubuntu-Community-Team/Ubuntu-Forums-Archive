---
title: "Don´t have live cd and I now have this problem. Error: file not found. grub rescue"
date: 2015-08-29
forum: New to Ubuntu
---

### Post by maxiplod on 2015-08-29
It´s my first time here so hello to all out there and hope someone can help me with the dilema I´m in right now. I had never used Ubuntu before so I really do not know what the H... to do now. I was updating ubuntu 12.04 lts to the 14.04 lts and once this was almost done, I was asked to restart the computer and once that was done, so I thought, instead of opening up to ubuntu I got a black screen with the following message: error: file not found. grub rescue. To make things worse, when I bought my HP 205 (G1) All-in-one, which had ubuntu already installed, they did not provide me with the live cd to install grub again. What can I do! Is there anyway to recover from this... Appreciate all help! Thank you

---

### Post by jackyboy633 on 2015-08-29
Hello maxiplod!

What's probably happened when you installed 14.04 LTS was that GRUB became corrupted during the install of 14.04, but this can be fixed fortunately. There is a LiveCD that you can use called Boot-Repair to fix this, but you'll need a spare computer and either a blank CD or USB drive to use this. If you have both of these, you can visit [http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/) and download the 64 bit (I believe) version of the Boot-Repair LiveCD. Then, you will need to burn this or copy this onto the CD or USB stick, then boot from it and run Boot-Repair.

If you reply to this, saying what things you have that you can use, then I can walk you through this process :-)

*jackyboy633*

---

### Post by Bashing-om on 2015-08-29
maxiplod; Well;

We can try and boot the system from the "grub rescue >" prompt. This may be a real trial and a learning experience for all.
By far the expedient thing is to work from a liveDVD(USB) ... but .. seeing as how we do not have, work with what we do have.

-  HP 205 (G1) All-in-one,- Is this a UEFI system ?
Can you boot to a grub boot menu ?

IF you can boot to grub's menu -
With the ubuntu kernel selected, press the 'c' key for a (C)ommand line.
At the prompt what returns from terminal command:
```

ls -lh

```
To see what grub is aware of for system configuration.

Maybe we can find enough to boot the system up.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-08-29
If you previously had 12.04 I don't think this was a UEFI system, and if you can only manage to boot to "grub rescue" I think you will have to somehow get hold of a ubuntu live system and then follow the Boot-Repair instructions in my signature below, or get the boot-repair.iso file as mentioned by jackyboy633 and burn it to disk.  Make sure you get the same 32bit or 64bit file as your original but now broken OS.

Boot to whichever live system you download and run boot-info script; do not at this stage run the default boot-repair, just boot-info script and then paste back here the link to pastebin that will tell us all about your problem.

---

### Post by maxiplod on 2015-08-29
Thank you for getting back! will take your information and apply myself to doing this before all the other recommendations given to be by you kind folk around the world! will let you know how it goes! thanks once again! I think that yes, my computer is a UEFI System as I only got this HP about 6 months ago and it came ready with ubuntu installed when I bought it... I think that´s what you mean?

---

### Post by maxiplod on 2015-08-29
Thank you for all your information, and you are so right it´s a learning experience that´s why I need you teachers! I will try and get a copy of the live Cd or a way to boot with that! but I did try doing what you mentioned and typed in ls and got this:
(hd0) (hd0, msdos7) (hd0,msdo6) (hd0,msdos5) (hd0, msdos4) (hd0, msdos2) (hd0, msdos1) thanks for all your help!

---

### Post by maxiplod on 2015-08-29
Will do as you advise, thank you so much. Now if you mean that my system wasn´t an UEFI System, I´m not sure but I think it might be as I only bought the hp 205 about 6 months ago and it came with ubuntu already installed from factory, does that give you any idea?

---

### Post by ajgreeny on 2015-08-30
It is probably a UEFI capable machine, but whether it is booting in MBR (legacy BIOS) or UEFI mode is impossible to say without more information, all of which we can get from a live system or the installed OS if we could get it to boot.

Beg, borrow or buy a DVD-R and then download a *Ubuntu system to burn to it, on someone else's computer if necessary, then we can start to get things sorted for you.

---

### Post by maxiplod on 2015-08-30
Maxiplod here, tried to burn on usb stick the boot repair and even on a cd and put it into the hp pc as instructed, and nothing changed, still have the message, file not found, grub rescue...maybe I'm doing something wrong, but I've kind of thrown in the towel. Just want to get Windows and install that and be done with it.

---

### Post by maxiplod on 2015-08-30
sorry forgot to say that once I put the usb in and waited for the thing to do something other than show me the same screen, grub rescue, I got : invalid system disk repalce the disk and then press any key...guess i'm not going anywhere fast or slow...what can one do now???

---

### Post by yancek on 2015-08-30
Are you trying to burn the boot repair iso you downloaded to a CD?  If so, you need to select the option to "burn as an image" and not simply copy it to the CD.  Same if you are using a DVD with an Ubuntu iso, it's too large to fit on a CD.  To put it on a flash drive, you cannot copy it directly to the flash drive but need to use software designed specifically for this purpose.  I don't know what you are using now, what operating system or some Live CD.  Some software you can use to create a bootable CD include unetbootin or pendrivelinux, although the latter only works from windows.

---

