---
title: "how to format portable HDD- Maxtor OneTouch Mini"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by scotcella on 2008-06-16
My portable HDD is giving me a headache!

I use it for Hardy and occasionally I take it to work (XP) and transfer Open Office documents to take home.

How I format the HDD to FAT or whatever the format is called?

Many thanks in advance.

---

### Post by ettercap on 2008-06-16
hey...
in xp after the HDD is detected right click on it and then select format.
similar procedure in ubuntu...

---

### Post by scotcella on 2008-06-16
It only gives me the NTFS option if i reformat the HDD, no other option..

I have XP and Vista at home also.

---

### Post by rraj.be on 2008-06-16
Just use Gparted.
really a powerfull tool

Go hetre for further info

```
[gparted.sourceforge.net/larry/livecd/main/livecd.htm]("gparted.sourceforge.net/larry/livecd/main/livecd.htm")
```

```
[www.howtoforge.com/partitioning_with_gparted]("www.howtoforge.com/partitioning_with_gparted")
```

---

### Post by prshah on 2008-06-16
> **scotcella said:**
> 
How I format the HDD to FAT or whatever the format is called?


You should format it to NTFS. You can format it either in XP or in ubuntu. If you choose to use XP, click start-run, then give the command```
diskmgmt.msc
``` for ubuntu, as suggested use gparted```
sudo apt-get install gparted ntfsprogs
sudo gparted
```

Remember that mucking around with partitions is dangerous work so be very careful.

---

