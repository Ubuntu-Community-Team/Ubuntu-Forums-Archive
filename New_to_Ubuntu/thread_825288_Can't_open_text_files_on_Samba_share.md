---
title: "Can't open text files on Samba share"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by canthus13 on 2008-06-10
Ok.  I'm running a Hardy server with several samba shares.  I can open anything, including text files, from my laptop running Gutsy.  I can open anything on the shares from a windows box.  I can open anything BUT text files from my laptop running Hardy.  If I open a text file I get this error:  Could not open the file smb://<fle>   unexpected error: internal error.

--Me

edit:  Apparently this is limited to gedit.  Open Office opens text files just fine over the network.

---

### Post by superprash2003 on 2008-06-10
did you add a sudo?

---

### Post by canthus13 on 2008-06-10
I shouldn't need to.  Besides, it's only on the Hardy laptop.  I can open the same files just fine with the Gutsy laptop.  I'm starting to suspect that it's simply a bug with gedit.

--Me

---

### Post by kcnnc on 2008-11-03
Confirm this bug ... and looks like it is not resloved according this
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/95414](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/95414)

---

