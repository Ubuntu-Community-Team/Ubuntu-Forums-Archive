---
title: "pariion"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-10
I have downloaded gparted.
I want to shrink my swap and grow my root.
how do i do it.

---

### Post by sameer.india on 2008-07-10
Does moving a partition affect the data?
I want to move my vista partition and shrink it to will this affect it

---

### Post by forger on 2008-07-10
You better do it from a live cd, if the hard drive is the one you're using now.

You can download the latest hardy 8.04.1 cd from [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu)

gparted in the live cd, as System > Administration > Partition Editor

On the **top right** corner, you choose the device to edit, then right-click on the partition you want to edit and select "Resize/Move"

I think that you must
1) resize swap from the **left side** ("start" of partition)
2) resize the root from the **right side** ("end" of partition)
3) Press Undo if you're not happy with the change you want to make, or press Apply if you're happy with the changes and want to realise them

I'm not sure for a vista partition, but I have lately resized windows xp's ntfs partitions successfully.

---

### Post by sameer.india on 2008-07-10
I have gutsy live cd.
does it have gparted????

---

### Post by bijeeshvs on 2008-07-10
> **sameer.india said:**
> I have gutsy live cd.
does it have gparted????

Please change the spelling of "partition" in the thread name

i suggest to use the hardy live cd, for you can use the latest version of Gparted,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

---

### Post by sameer.india on 2008-07-10
I have ordered the hardy cd but i need to do this now

---

### Post by sameer.india on 2008-07-10
so does the gutsy cd have it

---

### Post by forger on 2008-07-10
It does, but don't be stubborn about it :)
It contains a newer version, much better of gparted, which would probably support the vista partitions you wanted.

If you don't want to wait for the whole cd, you could download a smaller bootcd, which contains just gparted
[http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0)

(from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

---

