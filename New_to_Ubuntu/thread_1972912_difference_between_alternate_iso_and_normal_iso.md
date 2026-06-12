---
title: "difference between alternate iso and normal iso"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by m.mohan100 on 2012-05-04
What is the difference between alternate iso and normal iso? Which is better?
Will I lose my installed softwares while upgrading to newer Ubuntu?
If so, Can I import OS installed under Virtual-box in previous Ubuntu version into upgraded one?


Thanks in advance!

---

### Post by Bucky Ball on 2012-05-04
Alternate ISO is text based install. Will generally install on low spec machines which don't handle the bells and whistles of the graphic install (Desktop or 'normal'). 

You will only lose software that isn't included in the new release. All other existing software will be upgraded (if it needs to be).

---

### Post by Cheesemill on 2012-05-04
The alternate iso contains all of the packages (.deb files) needed to install a new system using the standard 'apt-get install' commands. Because all of the packages exist in this format on the CD it can also be used to update a system to the newest version.

The Live CD, however, doesn't contain any installable packages. Instead it contains a compressed image (the .squashfs file) of an already installed system which is simply uncompressed to the target drive or run directly from the CD if you are using the 'Try Ubuntu' option.

You can think of it as being the difference between installing Windows in the usual manner and then running the separate installers for all of the applications (Alternate CD), or simply restoring a Windows system from a drive image backup (Live CD).

Also as Bucky Ball mentioned above, because the Alternate CD runs a text mode installer it can be used to install Ubuntu onto a system that for some reason (usually lack of RAM) cannot run the Live CD.

---

