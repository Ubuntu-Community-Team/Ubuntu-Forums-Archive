---
title: "disk usage analyzer miscalculated my hdd capacity"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by lumix700i on 2008-07-02
I'm currently installing ubuntu 8.04 LTS 32 bit version in my notebook (acer aspire 5580) with hardware spec:
processor intel core 2 duo T5500
1,5 gigs of RAM
60 gb hd
the problem is, the disk usage analyzer identifies that my hd capacity is 106.3 gb ? Is there anyway I can correct this ?

---

### Post by drs305 on 2008-07-02
> **lumix700i said:**
> I'm currently installing ubuntu 8.04 LTS 32 bit version in my notebook (acer aspire 5580) with hardware spec:
processor intel core 2 duo T5500
1,5 gigs of RAM
60 gb hd
the problem is, the disk usage analyzer identifies that my hd capacity is 106.3 gb ? Is there anyway I can correct this ?

Disk usage analyzer is sometimes confusing. Rather than explain how it reports things, run this command and see if it matches what you think you have. If it doesn't, post the results and we'll take a look:
```
df -Th
```

---

### Post by lumix700i on 2008-07-02
Great!! The command shows exact calculation of my hdd capacity. So, does the disk usage analyzer always miscalculated, or is it happen only in my machine?

---

### Post by drs305 on 2008-07-02
> **lumix700i said:**
> Great!! The command shows exact calculation of my hdd capacity. So, does the disk usage analyzer always miscalculated, or is it happen only in my machine?

Without seeing the image I can't say definitively, but DUA's graphic often confuses people, especially where the 100% issue is concerned (people think DUA is reporting a specific partition is full when, in fact, it always reports 100% full).

The chances are good that DUA is correctly reporting what it sees, it's just that sometimes it has a hard time communicating that to us normal users. ;-)

---

### Post by lumix700i on 2008-07-02
I dont even pay attention to the image (graphic). It's written in the DUA..

---

### Post by drs305 on 2008-07-02
> **lumix700i said:**
> I dont even pay attention to the image (graphic). It's written in the DUA..

I dont' use the written values on the main page. If you go into Edit, Preferences, do the values of each partition match (more or less) the "df -Th" values? Those numbers generally are accurate on my computers.

---

### Post by lumix700i on 2008-07-02
I see the problem now. I go to preferences like you say, and found out that DUA also scan gvfs fuse daemon in the filesystem scan, and doubles my hdd capacity. After I unchecked this item, the DUA gives nice accurate capacity of my hdd.. Wonder what exactly gvfs fuse daemon means...?

---

### Post by stchman on 2008-07-02
> **lumix700i said:**
> I'm currently installing ubuntu 8.04 LTS 32 bit version in my notebook (acer aspire 5580) with hardware spec:
processor intel core 2 duo T5500
1,5 gigs of RAM
60 gb hd
the problem is, the disk usage analyzer identifies that my hd capacity is 106.3 gb ? Is there anyway I can correct this ?

Your actual hdd capacity is 55.88GB not 60GB.

---

### Post by drs305 on 2008-07-02
> **lumix700i said:**
> I see the problem now. I go to preferences like you say, and found out that DUA also scan gvfs fuse daemon in the filesystem scan, and doubles my hdd capacity. After I unchecked this item, the DUA gives nice accurate capacity of my hdd.. Wonder what exactly gvfs fuse daemon means...?

gvfs is the Gnome Virtual File System. There is a .gvfs folder on your home partition and is the future of mounting things. It works with FUSE. In layman's terms (the only kind I know), gvfs is used to 'virtually' mount file systems and it's virtual contents can be reported as if they really exist. I've read about it but obviously can't explain it very well ;-)

---

