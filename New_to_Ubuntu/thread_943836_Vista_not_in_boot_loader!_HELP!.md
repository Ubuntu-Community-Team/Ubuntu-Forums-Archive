---
title: "Vista not in boot loader! HELP!"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by anders.berg on 2008-10-10
Hello!

I have had Vista and ubuntu installed on my laptop but then I messed up ubuntu and decided to reinstall ubuntu, and something went wrong!

When I start the computer I press esc to view boot loader, and there is only ubuntu to choose from. Vista was in boot loader before i reinstalled ubuntu.

Please help me boot vista!

---

### Post by Ryadt on 2008-10-10
Do this```
 gksu gedit /boot/grub/menu.lst
```
then add this
```
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by anders.berg on 2008-10-10
Then this happens:


root		(hd0,0)
 Filesystem type unknown, partition type 0x27
savedefault
makeactive
chainloader	+1

BOOTMGR is missing

:confused:

---

### Post by SunnyRabbiera on 2008-10-10
I hope you didnt erase vista by mistake.

---

### Post by anders.berg on 2008-10-10
No i did not erase vista, i can see the windows partition in ubuntu and access files. I have tried vista recovery cd but no luck.

---

