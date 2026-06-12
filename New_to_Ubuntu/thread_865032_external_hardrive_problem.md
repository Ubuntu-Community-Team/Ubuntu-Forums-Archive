---
title: "external hardrive problem"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by georgeadey1 on 2008-07-20
I have just installed ubuntu, but when i plug my usb external hardrive in it recognises it but when i try to open the folder to view files i get an error message: Cannot mount volume

is there a fix?

---

### Post by georgeadey1 on 2008-07-20
anyone?

---

### Post by Ekolost on 2008-07-20
Help

---

### Post by pi.boy.travis on 2008-07-20
> **georgeadey1 said:**
> I have just installed ubuntu, but when i plug my usb external hardrive in it recognises it but when i try to open the folder to view files i get an error message: Cannot mount volume

is there a fix? 


Have you ever had the drive plugged into a Windows computer?  If it was, and you didn't eject it properly, Linux won't mount it.  If this is the case, plug the drive back into a Windows computer, then eject it.

---

### Post by wariskampar on 2008-07-20
pi.boy.travis may be right. in my case, the drive is mounted but it was empty even though i know for sure i got a lot in it  before. found that, the drive was corrupted and have to run chkdsk in XP to recover all the all files/data. After that, make sure, it was safely disconnected from XP. If error message appear maybe because the drive is busy, wait until it finish and try disconnect again. That was how I solved my problem. Hope it helps:)

---

### Post by georgeadey1 on 2008-07-20
kk thanks not ejecting it properly whilst in xp is definetly the problem but now when i try and safely remove hardware in xp it says 'a program that requires this drive is still running, close program and try again' i have closed loads of programs and cannot find one that would be interfearing with the external hardrive

---

### Post by bumanie on 2008-07-20
Unlug and then replug it back into windows and 'safely remove' without opening anything up - sometimes works.

---

### Post by coffeecat on 2008-07-20
Plug the drive in while you are using Windows and close Windows down with the drive still plugged in. Hopefully, Windows will close whatever app it thinks it hogging the drive, cleanly unmount the drive and shut down gracefully.

I've had to do that myself with a NTFS-formatted drive. Be aware that Windows can seem to stay stuck on the close-down screen for a very long time when you have this sort of situation. Don't be tempted to to a hard shutdown. Just leave it to close down in its own time and hopefully this will sort the problem out.

---

