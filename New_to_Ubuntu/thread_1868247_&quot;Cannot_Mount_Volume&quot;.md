---
title: "&quot;Cannot Mount Volume&quot;"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by missrachel on 2011-10-24
I really need some help.  Currently my Dell Mini 9 has 476.3 MBs on it.  I can't hold much of anything.  I have an external hard drive which is 164.7 GBs.  It would be a HUGE blessing to be able to use it, but when I plug it in, it says a bunch of things about not being able to mount the volume and directions for safely removing it in Windows but I don't have windows.  I couldn't copy the text in the error so I've attached a screen shot of it.  Pleeeease please someone help me with this.

---

### Post by missrachel on 2011-10-24
Please.. I'll take anything.  I need space.

---

### Post by dave0109 on 2011-10-25
As you don't have windows, did you try the instructions in that dialog to clear the in use flag?  That is run the command: 'mount -t ntfs-3g /dev/sdb1 /media/disk-2 -o force'.

---

### Post by missrachel on 2011-10-25
Thank you thank you thank you!!!!  So stupid to miss that! lol

---

### Post by dave0109 on 2011-10-26
Easily done. :) Glad you're sorted.

---

