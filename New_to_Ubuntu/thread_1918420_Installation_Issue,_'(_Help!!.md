---
title: "Installation Issue, :'( Help!!"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by mbconoly on 2012-01-31
Okay, so I have to use ubuntu 11.10 because my Window's is messed up, I have been using safe mode with networking for the past several months. I tried ubuntu yesterday, installed it easily using wubi, no problems. I thought it was great, superior to Windows. Well, today, I decided I wanted to try out kubuntu. So I get back on windows safe mode, and download kubuntu 11.10, and try it out. Well, then I got this thing (see picture). This is my second time installing a Ubuntu type software, and this command line thing pops up, it starts off being that first small paragraph only its large, then the ubuntu logo comes up with dots under it loading screen with purple backdrop. Then it goes back to the command prompt with smaller font. After a few seconds.. it comes to the picture with the rest of the text. I can't get past this part of the installation. I cannot install kubuntu. The same thing happened with Ubuntu when I tried to go back to it. I cannot use a cd because my computer doesn't have an optical drive. How do I fix this? My problem is I can't install anything, it all comes to that screen, where it stops.
*I use to have the Motorola Droid, and I would switch Roms everyday, this is kinda like that to me.

---

### Post by sudodus on 2012-01-31
Welcome to the Ubuntu Forums,

I guess you have downloaded the iso files for Ubuntu and Kubuntu. If you have no CD drive, you can make a USB boot drive. There are several tools for that. I have good experience with Unetbootin, a small program, that you can download to Windows (or [k]ubuntu, when you have it running). Use Unetbootin to make a boot USB drive of a USB flash drive 'stick or pen-drive'!

Then change your BIOS settings so that you can boot from it. Some BIOS systems sees it as a USB device, some see it an a hard disk drive. It it is inserted, while you are in the BIOS menus, you can probably see or at least guess, how to change the boot order.

Finally reboot your computer from the new USB boot drive. When successful, you will be running a 'live' system, testing [k]ubuntu.

Good luck (and come back with more questions if necessary, or even better: describe your computer, it makes it easier to help) :-)

---

### Post by QIII on 2012-01-31
Have you tried to follow the instructions with regard to what you need to do in Windows first?

---

### Post by mastablasta on 2012-02-01
> **QIII said:**
> Have you tried to follow the instructions with regard to what you need to do in Windows first?
 
 
to explain i think he is talking that you should run ```
chkdsk /f
``` in windows.
 
the problem is because using wubi to install is to NTFS and if NTFS is corrupted then wubi will have problems. this is also yet another limitation of Wubi.
 
so use a USB to test it/try it out as suggested or do a checkdisk & repair first. maybe your windows problems will also go away like that.

---

### Post by mbconoly on 2012-02-01
I cannot use a USB Drive, my usb ports have been broke for a long time. My computer has issues. None of the usb ports work,... and I got a HP Tm2t Custom Made touch screen.

---

### Post by mbconoly on 2012-02-01
How do you do the chkdsk things? I tried but the command prompt said it was invalid or something, how do I do it?

---

### Post by QIII on 2012-02-01
It looks like you will need to run them from Windows, so you will have to boot to Windows.

Depending on which version of Windows you are using, you should be able to click "Start" or the Windows globe, click "Run" and type "cmd" (without quotes).  That should bring up the Windows "terminal" and you should be able to run things from there.

---

