---
title: "Can't install kubuntu."
date: 2011-12-05
forum: New to Ubuntu
---

### Post by phsopher on 2011-12-05
I've recently formatted the hard drive and installed Windows XP. I'd like to install Kubuntu 11.10 as a dual boot. However, whenever I try to install by booting from CD, I get the following error:

[i]filesystem check or mount failed
A maintenance shell will now be started
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored
/proc/self/fd/9:21 /sbin/sulogin: input/output  error
mountall start/starting
exec:12: mountall: input/output error[/i]

Nothing works after that including  ctrl-d, I just have to shut it down from the power button. I thought there might be a problem with the hard drive but I've tried reformatting it several times and Windows runs just fine. I've also tried another version of Kubuntu (10.04) burned on another CD which also didn't work (the error wasn't quite identical but I think the point was the same).

Any ideas?

---

### Post by oldos2er on 2011-12-05
Have you run the integrity check on the CD, or checked its md5sum? It sounds as though the CD is corrupt.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by phsopher on 2011-12-05
I have run md5sum and it checks out. I haven't done an integrity check on the CD (not sure how) but I doubt that this is the issue. Like I said, I've tried two different CD's with two different Kubuntu versions on them. Besides the cd seems to work fine on my other laptop.

---

### Post by phsopher on 2011-12-05
Actually I think you were right. I've only tried to launch the CD from Windows on my other laptop. Now that I have tried to boot from it I got the same error. I've now burned the image on yet another CD and the installation is now under way. Thanks.

---

### Post by phsopher on 2011-12-05
I was too quick to celebrate. Now I've gotten to the installation part but got the following error:

[i][Errno 5] input/output error

This is usually due to a faulty hard drive, CD/DVD disk or drive. Hard drive might be old and you need a new hard drive. You can also try moving your computer to a cooler place. Also cleaning CD/DVD disk or burning it with a smaller speed or cleaning the lense of the CD/DVD drive might help.[/i]

The above might not not be verbatim what would appear in English, I'm translating from Finnish. Now I also recall that this was exactly what I got with the other CD (Kubuntu 10.04). So it appears that there was indeed a problem with the CD with 11.10 on it but the underlying problem (input/output error) remains.

If the hard drive is faulty then why does Windows run without a glitch? I also installed Windows using the same CD drive. Any help appreciated.

---

### Post by wildmanne39 on 2011-12-05
Hi, can you try to install from an usb flash drive? that will get around any problems you may be having with your disc drive.

Input/output error usually does mean that the drive is failing or is not able to be read, I am unclear if it is your disc drive or your hard drive that is giving you that error. 

If it is the disk drive you can try cleaning it, I have had a dirty drive and a faulty drive give me problems installing before.

---

### Post by phsopher on 2011-12-05
Successfully installed from a USB stick. Thank you.

---

### Post by wildmanne39 on 2011-12-05
Hi, your welcome!!! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

