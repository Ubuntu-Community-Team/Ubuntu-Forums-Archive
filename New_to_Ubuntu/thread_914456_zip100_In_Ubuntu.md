---
title: "zip100 In Ubuntu?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by D3M0L1$H3® on 2008-09-08
Hello,
I have a zip100 drive that is currently hooked up in an external enclosure. The port on the back of it is that of a Hard Drive's. 
I am planning on switchin out a hard drive (there is 2) from my old box with (hopefully) Ubuntu 8.04 on it. I was wondering if I put the zip drive in the box in place of the HDD, and set it up in the BIOS, if it would be supported in Ubuntu? Or maybe where (and what to do with) I could find the appropriate driver setup?
Thanks in advance,
D3M0L1SH3R

---

### Post by anewguy on 2008-09-09
Try these links, noting that they are not Ubuntu specific.  If you have questions on how to incorporate the information to use with Ubuntu, post back with specific questions and hopefully someone can help:

[http://www.linux.com/base/ldp/howto/ZIP-Drive-4.html]("http://www.linux.com/base/ldp/howto/ZIP-Drive-4.html")

[http://gentoo-wiki.com/Zip_Drive]("http://gentoo-wiki.com/Zip_Drive")

[http://cyberelk.net/tim/parport/parport.html]("http://cyberelk.net/tim/parport/parport.html")

These are just a few of what was found doing a search on Yahoo!.

Also, I assume you still have the cable for connecting the drive to the PC? 

Dave :)

EDIT:  I know of these are just for the parallel port version, but at least one also covers the IDE version.

---

### Post by cariboo on 2008-09-09
The simple answer is yes, I have usb ,parallel and ide zip drives. They are all supported without any extra configuration.

Jim

---

### Post by D3M0L1$H3® on 2008-09-09
thanks guys, i need to physically install it and check out everything, and if it works, its solved.
ill be sure to check out the sites before i screw something up.
thanks so much.

---

### Post by bodhi.zazen on 2008-09-09
Zip drives work just fine, there is but one odd behavior ...

The partition number will be "4" (without quotes). So most flash drives, usb devices will be /dev/sdb1

your zip drive will be /dev/sdb4

It helps to know this if you have to manually mount the device. You can mount the device by label or uuid.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by D3M0L1$H3® on 2008-09-09
> **anewguy said:**
> 

Also, I assume you still have the cable for connecting the drive to the PC? 



i hope so. last time i checked, the cable was left in the tower. I have to put the cage back in for it and the HDD, though.
=D
and thanks, bodhi.zazen, that is useful to know.
:)

---

