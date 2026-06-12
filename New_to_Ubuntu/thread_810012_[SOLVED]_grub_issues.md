---
title: "[SOLVED] grub issues"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-27
gurb loading stage 1.5

GRUB loading please wait.....
Error 17


yes i was playing with my partitions (making new ones)

now how do i get my gurb working agian..

boot off live cd...

then what???

nutz

---

### Post by sharks on 2008-05-27
try this.i had the same problem and solve it on my own
[http://ubuntuforums.org/showthread.php?t=804696](http://ubuntuforums.org/showthread.php?t=804696)

---

### Post by nutpants on 2008-05-27
thanks for the info..
but after my error i dont have the grub menu so i cant hit 'e" to edit it..
i have booted into the live cd and i KNOW
that my problem is tat my linux boot partition went from sda7 to sda8  as i added a partition..
i found that i had to change "root (hd0,6)" to "root (hd0,7)"

but that is not fixing my problem.. ( or i read the instructions wrong)

i am still stuck.. and still looking for an answer..
 btw i am working with only one drive so it should make it easier  to fix but not easier to find the answer
nutz

---

### Post by nutpants on 2008-05-27
found it...

You will have to re-write grub to (hd0,0) via the live cd. Boot live cd.
In terminal

sudo grub

root (hd0,0)

setup (hd0)

quit

---

