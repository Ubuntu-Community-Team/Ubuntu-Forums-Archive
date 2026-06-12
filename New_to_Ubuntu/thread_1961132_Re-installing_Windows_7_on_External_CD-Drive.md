---
title: "Re-installing Windows 7 on External CD-Drive"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by TheSpookyKids87 on 2012-04-18
Hi everybody, I'm trying to put Windows 7 back on one of my netbooks, it is a Dell Inspirion Mini.  I am currently running 11.10. I switched the boot order in the bios and have the Windows 7 CD in, but it does not boot from CD and runs Ubunutu.  The external CD-Drive does work when I put another CD in it, such as a music CD.  If anybody could help that would be great.

Thanks

---

### Post by Nessto on 2012-04-18
Have you tried f12 during startup to get the boot sequence and select cd drive?

---

### Post by TheSpookyKids87 on 2012-04-18
Yup, tried that a few times

---

### Post by Nessto on 2012-04-18
Id recommend trying that windows 7 cd on another pc, possibly it could be scratched or burned wrong if you made it. Doesnt sound like you have a bad cd rom drive. And make sure that its a dvd drive too because im pretty sure windows 7 is on a DVD not a CD

---

### Post by TheSpookyKids87 on 2012-04-18
I do believe it is the disc ](*,)

Thanks!

---

### Post by Mark Phelps on 2012-04-18
Either the Win7 disk is a CD or a DVD.  

If it is actually a CD, that is too small to hold an install setup of Win7, so most likely, it is a Restore CD that will only allow you to run the Restore function on your Dell Netbook.  And THAT will only work if (1) the recovery partition is still there and intact, and (2) you did not repartition your hard drive.

Since you're running Ubuntu, I'm presuming that you DID repartition your drive, and even if you did not remove the Recovery partition, the Restore is still likely NOT to work.  Why? Because it's looking for the original Win7 partition that was there, and when it sees Linux filesystem partitions, it's not able to do the restore.

If that case, if you STILL have the Recovery partition, you should REMOVE the Linux filesystem partitions, and then, you should then be able to boot from the CD and do a Restore.

If you don't have the original Recovery partition, your only recourse then is to contact Dell, tell them something like the hard drive crashing, and see if they will sell you full-restore media (probably, a DVD). They will likely charge you $20 or so for that, but it's a lot cheaper than buyint Win7 Retail.

If it's a genuine Microsoft Win7 DVD, you should not be having this problem -- but you would need to confirm that before we continue.

---

