---
title: "patulong mag dual boot"
date: 2008-02-02
forum: Philippine Team
---

### Post by redenjaja on 2008-02-02
[IMG]http://img181.imageshack.us/img181/1262/mypcwe2.jpg[/IMG]

ayan yung current set up ng pc ko:
yung C: eh yung 40Gig kong ide hdd, wala pang nakainstall dyan....
yung D: at E: eh yung 2 partition ng 120Gig kong SATA hdd, sa D: nakainstall currently yung windows xp ko.

ngayon gusto ko sana idual boot yung xp at ubuntu, kakaformat ko lang ng pc at sakto naman na kakarating lang ng ver 7.10 ko kaya now is the best chance to dual boot habang wala pang laman pc ko. last week sinubukan ko na kaya lang after ko mainstall ubuntu di na makita ng grub yung windows ko, i ended up re installing windows... 

yoko na ulit sapitin yung nangyari kaya hingi muna me advice:)

---

### Post by .::welemski::. on 2008-02-02
Rule of the thumb ng dual booting is install mo muna ung Windows then ung Linux after...

Pero sa case mo may windows na ung D: mo install mo nalang ung Ubuntu tapos piliin mo ung C: drive mo ( sda1 )...

If hindi madetect ng grup ung xp mo... edit mo nalang ung grub mo tulad sa example :


[B]title          Microsoft Windows
root        (hd1,0)
savedefault
makeactive
map          (hd0) (hd1)
map          (hd1) (hd0)
chainloader    +1[/B]

Ung grub editing is for scenario na hindi talaga madetect ng grub ung windows mo

---

### Post by ragadanga63 on 2008-02-05
A good utility for recovering Windows NTLDR and/or GRUB is SuperGRUB Disk-a bootable CD made for just that.

---

### Post by pinoyskull on 2008-02-05
> **ragadanga63 said:**
> A good utility for recovering Windows NTLDR and/or GRUB is SuperGRUB Disk-a bootable CD made for just that.
i use supergrub too, very effective

---

