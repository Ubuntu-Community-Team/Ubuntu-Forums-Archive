---
title: "How to fix damaged ntfs?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Nigmah on 2008-07-14
Ok so i have a damaged ntfs partition that has alot of files on it that i need. I damaged it by stopping a process in gparted before it was finished(yes bad move i know)
what i need to know is there a way i can fix the file system keeping the files intact.
Also im not currently using ubuntu and i've tried using chkdsk using properties in vista but it just prompts me to formate the drive.
help is much appreciated thanks!
(yes i know this shouldn't be in begginers but its gets alot of traffic)

---

### Post by iaculallad on 2008-07-14
Try to use the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") utility.

---

### Post by smo0th on 2008-07-14
have you tried booting on xp and running ```
chkdsk /f
``` in cmd?. I had problems with my 750 GB external drive, ubuntu asked me to do that and worked pretty good.

Edit: Lol... didn't read you used chkdsk the first time.. if you used it with the /f option then all I have to say is 'may the Testdisk be with you' and save your drive... good luck :S

---

### Post by Pro-reason on 2008-07-15
> **Nigmah said:**
> Ok so i have a damaged ntfs partition that has alot of files on it that i need. I damaged it by stopping a process in gparted before it was finished(yes bad move i know)
what i need to know is there a way i can fix the file system keeping the files intact.
Also im not currently using ubuntu and i've tried using chkdsk using properties in vista but it just prompts me to formate the drive.
help is much appreciated thanks!
(yes i know this shouldn't be in begginers but its gets alot of traffic)
Vista knows NTFS better than Ubuntu does.  I doubt that any Linux utility can be relied upon to do a better job of scanning for errors on that filesystem.

It sounds like you have totally screwed that partition.  I can only direct you towards [Wikipedia's article on data recovery]("http://en.wikipedia.org/wiki/Data_recovery#File_recovery_tools"), which might help you get a few files back.  After that, you'll have to reformat.

I think you've learnt your lesson about stopping GParted halfway through!

---

### Post by Nigmah on 2008-07-15
used tesdisk and it fixed things perfectly. thanks [iaculallad]("http://ubuntuforums.org/member.php?u=520984")

---

### Post by smo0th on 2008-07-15
testdisk rocks :D

---

### Post by Nigmah on 2008-07-15
well i only let it run for a few gigs so it would have been really gay if i lost everything(years worth of work on it)

---

