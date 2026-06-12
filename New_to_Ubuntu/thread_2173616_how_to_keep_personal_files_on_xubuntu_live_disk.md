---
title: "how to keep personal files on xubuntu live disk"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by cemenc2 on 2013-09-10
I have 150gb external usb hard drive that I made bootable xubuntu disk/live. I have some personal files and folder on the root of this hdd that I want be able to access once xubuntu live starts. 

At the moment, I am not able to find these items after booting. 
Where I can put my files so I will be able to access them later?

thanks in advance.

---

### Post by Jonathan Precise on 2013-09-10
Save them to the HDD (mount it and save them there). Then reboot, and mount the HDD. The files should still be there.

Why not install xubuntu to the external disk?

---

### Post by cemenc2 on 2013-09-10
how do you mount the drive that xubuntu booting from?

would this work? 

mount hda

---

### Post by ajgreeny on 2013-09-10
Why are you messing around with a live system when you could do a proper installation on that external disk?

However, if there really is a good reason behind this you will need to run xubuntu live with a persistent system.  I have no idea how you would do that on a hard disk, but I believe it is possible to do.  You could also make a separate casper-rw file on the disk in an ext4 partition and use that to save all your files.

See post #6 of [http://ubuntuforums.org/showthread.php?t=1629477](http://ubuntuforums.org/showthread.php?t=1629477) for some more clues.  This is for a CD or USB but should work also for you, I think.

---

