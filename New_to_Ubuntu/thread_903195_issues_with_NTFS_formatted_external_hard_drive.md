---
title: "issues with NTFS formatted external hard drive"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by SunmanXII on 2008-08-28
I am having issues with an external NTFS-formatted hd.

I used to use it all the time, for both reading and writing, so I had all the necesary libraries installed. However, I started using it after a long break recently and it is exhibiting very odd behavior, which I will try to describe.

-When I plug the drive in everything works - I can read everything on the hard drive.
-When I try to write a file to the hard drive, the system lets me copy the file from my internal to my external hard drive.
-When the file is done moving, half or most of my files become "corrupted". They appear to be "locked" and I cant view them.
-When I unmount and unplug my external hard drive, and then plug it back in the file that I have copied disappears and everything is back to normal. I can view everything again.

Can anyone tell me what is wrong?

Thank you

---

### Post by mdsmedia on 2008-08-28
I had a similar issue with a USB flash drive. The drive was only 512MB and it kept giving me errors that I didn't have permission to write to the drive.

I took the drive to work and read it on a Windows machine (could have done the same on Ubuntu but hadn't). I found a 750MB file on it and that was giving me problems.

I copied all files from the flash drive to hard drive, formatted it, and copied the "real" files back. It was fine then. 

It wasn't formatted NTFS, but similar issue.

---

### Post by SunmanXII on 2008-08-28
Unfortunately, I have about 80GB of stuff on that HD so reformatting it would be the last option I want to go through. Are there any other ways?

---

### Post by vanadium on 2008-08-28
THe first ting to do is to check the file system. Because it is an ntfs drive, you do this best from within a Windows system.

Before using the disk on an Ubuntu system again, make sure it has been properly "closed" by Windows. This means yuo must either * disconnect the drive using the "safely remove hardware" icon in Windows or * shut down Windows completely before disconnecting the drive (no hibernate or standby!).

The same care in properly connecting/disconnecting the drive applies to Ubuntu. Always use the drive's icon right-click "Unmount" command before disconnecting the drive, or have your system fully shut down.

---

