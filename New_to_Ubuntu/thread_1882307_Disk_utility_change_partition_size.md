---
title: "Disk utility change partition size"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by LukaHr on 2011-11-17
Is there way to change partition size with disk utility? I got 200 gb non system partition (just for documents) and wonna to make it 190 gb to install backtrack 5 on other 10 gb.

---

### Post by |{urse on 2011-11-17
yes, boot to the livecd and open a terminal
run this
> sudo gparted
if gparted is not found then 
> sudo apt-get install gparted

It's fairly easy to use but if used improperly it'll trash your box. be sure to have a look at the gparted howtos on sourceforge
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by LukaHr on 2011-11-17
Did it! Thanks man!

---

### Post by |{urse on 2011-11-17
^5 enjoy :)

---

