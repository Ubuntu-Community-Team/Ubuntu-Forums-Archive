---
title: "how to format hard disk?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-06-16
I have an corupted MBR in my hard disk i want to format my hard disk as an new one. 

how to make an hard disk as new as company manufactured one?
[COLOR="Red"]note: i don't need any data's in that..[/COLOR]

i have an ubuntu live cd.

how i can do a complete format with it?

is there any other method to fix  MBR in my hard disk?

---

### Post by hyper_ch on 2008-06-16
just reinstall a bootload (e.g. with supergrub disk) and the MBR will be fixed.

---

### Post by RSingh on 2008-06-16
You can also get a Gparted live cd. Download, burn to disk, reboot your comp with it.
[URL="http://gparted.sourceforge.net/livecd.php"]
http://gparted.sourceforge.net/livecd.php[/URL]

I always keep one handy.

---

### Post by housam on 2008-06-16
[[COLOR="Red"]_DBAN_[/COLOR]]("http://dban.sourceforge.net/") will wipe your HDD completely

---

### Post by Wynne G Oldman on 2008-06-16
> **sxytrillian said:**
> I have an corupted MBR in my hard disk i want to format my hard disk as an new one. 

how to make an hard disk as new as company manufactured one?
[COLOR="Red"]note: i don't need any data's in that..[/COLOR]

i have an ubuntu live cd.

how i can do a complete format with it?

is there any other method to fix  MBR in my hard disk?

If you boot the live CD and go to "system>administration>partition editor" (Gparted) you should be able to delete all the partitions on your HDD from there.

---

### Post by indytim on 2008-06-16
> 
how to make an hard disk as new as company manufactured one?
note: i don't need any data's in that..


1.  Zero fill the hard drive (will restore it to manufacturer's state (per your request above).
2.  Partition (LiveCD or GParted Live etc.).

IndyTim

---

