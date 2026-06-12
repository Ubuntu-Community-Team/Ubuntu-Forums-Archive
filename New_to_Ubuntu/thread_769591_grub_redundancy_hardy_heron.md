---
title: "grub redundancy hardy heron"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by GeneticFlea on 2008-04-26
yesterday i upgraded to Hardy Heron, and Im running a dual boot system with Ubuntu and Windows Xp. however now that i have upgraded when i boot up grub shows redundant entries for Ubuntu, displaying this Kernal version and the gutsy gibbon one. Both boot to hardy heron, but id like to get rid of the redundancy. any suggestions?

---

### Post by frup on 2008-04-26
take a look at /boot/grub/menu.lst

You can remove the redundant entries there. Best if you do a backup first in case to do something wrong :)

---

### Post by ALex! on 2008-04-26
you should use this in the terminal

```
 sudo gedit /boot/grub/menu.lst 
```

I'd this problem also! and this worked for me :mrgreen:

although sometimes my boot to the new kernel fails! :( :cry: (apparently many others are having the same issue/bug and we havn't found a solution!!!

---

### Post by frup on 2008-04-26
> **ALex! said:**
> 
although sometimes my boot to the new kernel fails! :( :cry: (apparently many others are having the same issue/bug and we havn't found a solution!!!

Just for the OP can you clarify that you mean after a new update a kernel might fail and not that editing menu.lst can make the kernel fail. The only kernel failures I have experienced have been related to non-free drivers.

---

### Post by ALex! on 2008-04-26
> **frup said:**
> Just for the OP can you clarify that you mean after a new update a kernel might fail and not that editing menu.lst can make the kernel fail. The only kernel failures I have experienced have been related to non-free drivers.

excuse me.. I didn't get you :???:

---

