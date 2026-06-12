---
title: "Eliminating vista / ubuntu duel boot to create a linux only machine"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by madrobber23 on 2008-04-29
00

---

### Post by bilal.17 on 2008-04-29
boot from the live CD and run the partition editor in System->Administration and remove the vista partition and resize the ubuntu one to take over the vista one

---

### Post by madrobber23 on 2008-04-29
Great.

---

### Post by iSplicer on 2008-04-29
Or, if you dont want to waste time booting into the live cd, you can simply go into your ubuntu and type:

sudo apt-get install gparted

And do it from within ubuntu, and then modify your GRUB settings to accomodate.

---

