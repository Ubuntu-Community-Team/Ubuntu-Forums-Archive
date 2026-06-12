---
title: "configuring boot loders"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2008-08-08
I have 3 partitions on my main drive
1 is XP32
1 is XP64
the other is ubuntu
installed in that order
Ubuntu boots fine with GRUB as the boot loader.
When I select windows it boots straight into xp32 even if I set it to XP64 in boot.ini
I want 2 entries in grub 1 for xp32 and one for XP64 and both to boot straight in.
The windows boot loader was offering me the choice of 32 or 64 before I setup ubuntu
Any ideas where I'm going wrong

---

### Post by Het Irv on 2008-08-08
Do you have the GRUB entry for windows set up for CHAINLOADER?

I am not sure exactly what you need to do to make it work, but I do remember seeing the boot option "Chainload +1" on some Windows Grub Entries.

---

### Post by bigmonmulgrew on 2008-08-09
yes I do so I did expect to see the windows boot loader

---

### Post by Herman on 2008-08-09
:) Hello bigmonmulgrew,
Try with GRUB's 'hide' and 'unhide' commands. If both Windows OSes are complete with their own boot loaders and they are both in primary partitions, they should both boot now.
I only guessed your partition numbers, (a stab in the dark), so you might need to play with them a little.
```
title     Microsoft Windows XP32
hide      (hd0,1)
unhide    (hd0,0)
root      (hd0,0)
savedefault
makeactive
chainloader +1

title      Microsoft Windows XP64
unhide     (hd0,1)
hide       (hd0,0)
root       (hd0,1)
savedefault
makeactive
chainloader +1 
```

---

