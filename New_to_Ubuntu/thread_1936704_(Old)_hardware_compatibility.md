---
title: "(Old) hardware compatibility ?"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by malep on 2012-03-06
Hello everyone,

New to this forum, new(ish) to Linux / Ubuntu
As many people seem to be doing these days, I've decided to setup a small file server at home, (re)using an old PC that was laying around the house.
The PC is based on an ECS KT600-A (V1.0) MB with an AMD Athlon XP 2200+ processor and 512MB RAM. I have installed Ubuntu 10.04 server on a brandnew WD 320 GB PATA HDD and everything works like a charm :) (SSH, Samba, Mediatomb, Transmission). The mobo has 2 builtin Sata (1.5Gb/s) ports and I added a PCI-SATA controller board that has 4 ports available(also 1.5Gb/s). The extra controller is a bit redundant, don't ask (I was intending to use another, older mobo initially). Now, here is my question : I want to use some 2TB HDD's to expand storage space, but the mother board manufacturer says this mobo only recognizes HDD's up to 400GB in size [see their website]("http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=1&DetailID=360&DetailName=Feature&MenuID=24&LanID=0"). Is this limitation due to the onboard Sata controller chipset, or will my newer Sil3114 controller chipset (the one on the PCI Sata controller board) be able to see bigger disks? 
Second question : the HDD's I can find on the market nowadays are either SataII (3Gb/s) or SataIII (6Gb/s). Will any work flawlessly with this controller (Sil3114) or should I look for/avoid some models ?

Many thanks for answers, sorry for the long post

All the best !

Malep

---

### Post by jailbait on 2012-03-06
> **malep said:**
> Hello everyone,

New to this forum, new(ish) to Linux / Ubuntu
As many people seem to be doing these days, I've decided to setup a small file server at home, (re)using an old PC that was laying around the house.
The PC is based on an ECS KT600-A (V1.0) MB with an AMD Athlon XP 2200+ processor and 512MB RAM. I have installed Ubuntu 10.04 server on a brandnew WD 320 GB PATA HDD and everything works like a charm :) (SSH, Samba, Mediatomb, Transmission). The mobo has 2 builtin Sata (1.5Gb/s) ports and I added a PCI-SATA controller board that has 4 ports available(also 1.5Gb/s). The extra controller is a bit redundant, don't ask (I was intending to use another, older mobo initially). Now, here is my question : I want to use some 2TB HDD's to expand storage space, but the mother board manufacturer says this mobo only recognizes HDD's up to 400GB in size [see their website]("http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=1&DetailID=360&DetailName=Feature&MenuID=24&LanID=0"). Is this limitation due to the onboard Sata controller chipset, or will my newer Sil3114 controller chipset (the one on the PCI Sata controller board) be able to see bigger disks? 
Second question : the HDD's I can find on the market nowadays are either SataII (3Gb/s) or SataIII (6Gb/s). Will any work flawlessly with this controller (Sil3114) or should I look for/avoid some models ?

Many thanks for answers, sorry for the long post

All the best !

Malep
SATA3 is backwards compatible with SATA2, and should be compatible with SATA1 as well.

The storage depends on the controller. If your using an expansion card, its the SIL3114 controller that sets the limits.

---

### Post by malep on 2012-03-09
Thanks, Jailbait, for your answer. I'll try it out soon and post feedback here.
Regards

Malep

---

### Post by grahammechanical on 2012-03-10
>  this mobo only recognizes HDD's up to 400GB in size

It is most probably due to a limitation in the BIOS.  Flashing the BIOS with a later version might remove this restriction.

Regards.

---

