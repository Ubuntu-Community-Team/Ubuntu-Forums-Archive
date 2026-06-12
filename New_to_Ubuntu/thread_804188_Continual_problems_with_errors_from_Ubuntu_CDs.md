---
title: "Continual problems with errors from Ubuntu CDs"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by lasvegaslinux on 2008-05-22
My last 3 burns of 8.04 have had errors and now after waiting two weeks for the copy I ordered; it too has an error. What should I do next? I already tried installing one with an error and it failed prior to loading grub then it wiped out all my Windows log in users, thus needing to reinstall Windows. What a nightmare bringing all my stuff back to the way I had it.

---

### Post by Master Grah on 2008-05-22
Do you happen to remember what the error was?

---

### Post by tamoneya on 2008-05-22
have you considered that something might be wrong with your dvd/cd drive.  It could be reading it poorly because that sounds like a very bad string of bad luck.  Do you have another drive you can try it with?

---

### Post by Gripp on 2008-05-22
could you describe the errors?

and maybe try loading the CD in windows and using Wubi to run the install... will pose less of a threat to your system until you get the install bugs worked out..

---

### Post by iaculallad on 2008-05-22
> **lasvegaslinux said:**
> My last 3 burns of 8.04 have had errors and now after waiting two weeks for the copy I ordered; it too has an error. What should I do next? I already tried installing one with an error and it failed prior to loading grub then it wiped out all my Windows log in users, thus needing to reinstall Windows. What a nightmare bringing all my stuff back to the way I had it.

You might be burning a damage ISO file. Make it a point that before burning an Ubuntu ISO file, check it for errors first by comparing it's the MD5 hash with the original one which comes on the webpage you downloaded the ISO file.
Or when using the LiveCD to boot, there's an option which let you check the medium fist before installation.

What actually are the error's you getting?

---

### Post by lasvegaslinux on 2008-05-22
When I check the disk, it doesn't tell me what the error is. Is there a way to find out. Thanks, I will try Wubi if I can't get this resolved.

---

### Post by lasvegaslinux on 2008-05-22
How do I tell? I simply checking the disk at boot.

---

### Post by Gripp on 2008-05-22
the only one thing to watch for with wubi is hard reboots (forcing the computer to turn off)

they will cause hard drive issues... but so far, for me, they haven't been anything that chkdsk /F in DOS doesn't clear up just fine

and it may even be a good idea to to start with running that from windows, and running memtest from a live boot just to eliminate those possibles...

---

### Post by Gripp on 2008-05-22
just describe how the process goes:  i.e.

it starts up and asks me install, but when i start it it doesn't do anything; or - it i get all the way to the splash screen but then it just goes black...


also, can you just boot into the live environment?

---

### Post by lasvegaslinux on 2008-05-22
Botts up and runs great in live mode, it's when I try to install it, that it fails due to errors, but then it's too late because it now has wiped out my grup and windows login users.

---

### Post by Gripp on 2008-05-22
so then did it fail when trying to partition your drive?
or did you already have that successfully done?

how far does the install get before it fails?  when it fails what happens? (aside from it messing up your windows install that is...)
how do you know that it deleted the profiles? can you still get to your windows splash screen?

just give us an over abundance of info..  i'm sure someone will be able to figure out whats up.

---

### Post by lasvegaslinux on 2008-05-22
I have two partitions Windows/DreamLinux. I simply replaced Dreamlinux with Ubuntu because Ubuntu WIFI works great (on it now with live session). It' was two weeks ago that I tried to install then about half way through I got the failed due to disk error message but by then it had removed Dreamlinux, Grub and part of Windows. Windows would laod all the way to the login splash sceen (same in Safe Mode) and the sreen would be blank with no way to log in nor could I reboot Ctrl/alt/del, so I had to reinstall Windows. I then checked my burns and all three had errors and now the one I ordered from Ubunto has one too but I'm afraid to install it.

---

### Post by friendofpugs on 2008-05-22
I know this sounds silly, but did you have the install disc do a "self check" before you ran it as a live session? I recall seeing that as an option on the iso I burned. It's at least reassuring to know that the disc will check itself before you try to run/install it. :)

---

### Post by linux phreak on 2008-05-22
Are you using a re-writable disk?.if so do a full blanking(10 minutes).Then burn the image at a slow speed(10x).Then check for errors on the CD.

---

