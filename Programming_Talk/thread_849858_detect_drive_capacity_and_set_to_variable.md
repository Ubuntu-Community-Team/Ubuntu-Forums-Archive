---
title: "detect drive capacity and set to variable"
date: 2008-07-04
forum: Programming Talk
---

### Post by KB1LQC on 2008-07-04
I am trying to write a script to detect the capacity of a drive and set it to a variable to be used at another time.  So far I have:

```
sudo parted /dev/sdc --script print | grep 'Disk' | awk '{ print $3 }'
```

this uses the parted print command and searches for the line containing "Disk" and then prints the 3rd word in the line which is the size.  Is there a better way of going about grabing the size of the drive to use later (formatting script)... i.e. to automatically detect the correct partition size, which is my end goal.  I already have a script that formats and stuff.



[RIGHT]
Thanks!

Bryce
KB1LQC[/RIGHT]

---

### Post by ghostdog74 on 2008-07-04
it depends on what you mean by correct partition size. show a sample of your parted -print output, and describe from the output, what is the desired result you want ie your correct partition size. also, if you use awk, no need to use grep
```

sudo parted /dev/sdc --script print | awk '/Disk/{ print $3 }'

```

---

### Post by KB1LQC on 2008-07-05
> **ghostdog74 said:**
> it depends on what you mean by correct partition size. show a sample of your parted -print output, and describe from the output, what is the desired result you want ie your correct partition size. also, if you use awk, no need to use grep
```

sudo parted /dev/sdc --script print | awk '/Disk/{ print $3 }'

```

I was thinking that, because awk uses grep and another program within itself, but didn't really get a chance to see how to do it in awk, probably very similar.

for my purposes the correct size is one partition of the whole drive, which is about 1 GB but I want my code to be more robust and have the ability to work with drives that may be different size drives.  I would put a standard size in like 1024 MB but on some of the drives I get an error about not having enought cylinders so I think they tend to vary a little?  Not sure, these are SD cards.




[RIGHT]Thanks!

Bryce
KB1LQC[/RIGHT]

---

### Post by KB1LQC on 2008-07-05
sorry...bump

---

### Post by geirha on 2008-07-05
fdisk prints a bit more info ...
```
sudo fdisk -l /dev/sdc | awk '/^Disk \// {print $5;}'
```

---

