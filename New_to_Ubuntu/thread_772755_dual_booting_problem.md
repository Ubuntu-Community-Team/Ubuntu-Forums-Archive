---
title: "dual booting problem"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Niklas93 on 2008-04-28
Hi. I have recently installed ubuntu as dual boot with vista on my computer. I installed version 7.10 and I used the tool that is build into ubuntu's installer to resize my vista partition and make a new ex3/swap partition for my ubuntu. It installed and everything was fine. Just until I found out that my vista partition wasn't viable from the grub menu. So now I can't make the vista partition active and thus boot my vista system and this is bad as I use vista far more than i use ubuntu. Could anyone please help me?

---

### Post by birddog165 on 2008-12-20
Let me redirect you to [this thread.]("http://ubuntuforums.org/showthread.php?t=303202") Hopefully it will help.

---

### Post by kansasnoob on 2008-12-20
The first thing we need to see is the output of this command in Terminal:

```
sudo fdisk -l
```

That's a lower case L.

Then the output of:

```
cat /boot/grub/menu.lst
```

Yes, it's long and we need it all.

---

### Post by kansasnoob on 2008-12-20
Oh, and any (boot) errors displayed!

---

