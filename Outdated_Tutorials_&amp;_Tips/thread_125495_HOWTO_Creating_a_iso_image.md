---
title: "HOWTO: Creating a iso image"
date: 2006-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Virogenesis on 2006-02-04
This is a simple howto on creating a ISO. 
Without the use of any programs just simple command line. 
Very basic very useful.
Great for making back up images

Open up a terminal window into this window type: dd if=/dev/cdrom of=$HOME/cdrom_image.iso

I'll now explain what this all means in the key below

**dd** - disk duplicate
**if** - input file
**of**- output file
**$HOME** - system variable that points to your user directory.

*Ps:*Change cdrom_image to what ever you want the iso to be called.

---

### Post by daredevil on 2006-03-01
Simple and sweet. nice tip

---

### Post by RaptorRaider on 2006-03-01
And the following would work too, right (as in "Is dd limited to (CD-)drives?")?
```
dd if=/etc/home/me/stuff of=$HOME/imageofstuff.iso
```

---

### Post by ounas on 2006-03-01
Thanks, I needed that..

-Ounas :-D

---

### Post by Nate53085 on 2006-03-02
I believe you can also

sudo cat /dev/hdc > outputfile

---

