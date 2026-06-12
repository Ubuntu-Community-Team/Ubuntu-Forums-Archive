---
title: "grub loading error"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by sleggy_allen on 2008-07-15
can't load ubuntu 7.10 it says grub loading error...it happened when i removed the 2nd hard drive that has ubuntu and i leaved the primary hd where i had my xp...when i fired up my pc it gives me that grub loading error..when i reconnected my 2nd hard drive still doing the same thing...now i can't use neither ubuntu nor xp...can someone help me out?thanks a lot :(

---

### Post by dracayr on 2008-07-15
try reinstalling grub on the MBR: Boot from liveCD, open a terminal, and execute:

sudo grub

a grub prompt("grub>") will appear. enter 
root (hd0,1) 
(or whichever disk it is that has ubuntu installed, if you're not sure run 
find /boot/grub/stage1
)
then execute 
setup (hd0)
(in this case it will most likely be (hd0) ) and try booting ubuntu again

dracayr

---

### Post by bumanie on 2008-07-15
Should work once the second hard drive is wired in again. Anyway, to get xp working you will have to boot with xp disc and go into recovery console. Type in username password or whatever it asks. When it asks which OS you want to fix, choose 1. Then at the C> prompt type FIXBOOT --> enter FIXMBR -->enter. Answer Y to questions it asks. Xp should then boot. If you want a dual boot, reinstall grub.

---

### Post by sleggy_allen on 2008-07-16
thanks for the help..i'll give it a shot and i'll let you know what happened...thanks again!

---

