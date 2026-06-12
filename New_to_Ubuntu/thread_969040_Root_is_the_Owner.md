---
title: "Root is the Owner"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Kenzo on 2008-11-03
I'm trying to copy and paste files (about 100) from one drive to another.  I cant do it.  I get permission denied. On checking the permissions on the files it says root is the Owner (no read, no write). sudo su and sudo -i don't work.  How can I change the permissions so I can copy these files in bulk please?  Or is there an easier way to copy them over?

---

### Post by nothingspecial on 2008-11-03
The easiest way is to type ```
gksudo nautilus
``` which will allow you to open the drives as root. Don`t forget to close it though or you may do some damage.

---

### Post by Kenzo on 2008-11-03
Thanks Nothingspecial.  It seems to be working okay - might take a while Ihave 120gb of file to copy.  Cheers!

---

