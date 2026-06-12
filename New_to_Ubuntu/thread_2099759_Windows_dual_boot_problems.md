---
title: "Windows dual boot problems?"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by sendy on 2012-12-30
hi guys, im having trouble with dual boot windows 7, so heres what i did:
- i installed windows 7 first in my laptop dell inspiron 5420 14r
- installed ubuntu 12.04 etc 
- tried to upgrade windows7 ultimate with crack
- the crack said "restart required"

then i restart, i can pick which OS to use at boot options, but when i pick "windows 7" it restarted again, if i pick another OS(ubuntu 12.04) it works..

i think the problem is because i installed the crack for windows 7 ultimate. everytime i pick windows 7 , it just restarts and go back to boot options again.

---

### Post by sendy on 2012-12-31
bump, anyone? i have searched google ,, it says i need to run windows repair, but this has big risks that i cant boot ubuntu, it means i have to reinstall grub and i dont have bootable ubuntu cd

---

### Post by adityamagadi on 2012-12-31
you dont need a ubuntu cd use unetbooting software to create a bootable pendrive with ubuntu image in it... windows upgrade patch is the problem for it to keep restarting. 


[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)    

download the linux version and follow the steps from the pendrive u can either install a fresh copy of ubuntu or if you have partitioned out your hardrive install already re-install windows in a empty partition or by formatting your previous windows partition , then use your pendrive boot into ubuntu's live session and install the grub and update it.

---

### Post by adityamagadi on 2012-12-31
or if you have not performed partitioned your hard disk no problem, just get into ubuntu's live session(you can do it by select " try ubuntu without installing" option ) open the dash n search for gparted open it n create your partitions and follow the procedure that i have posted previously.

---

### Post by howefield on 2012-12-31
Thread closed.

---

