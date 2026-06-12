---
title: "Loading problem..."
date: 2008-09-01
forum: New to Ubuntu
---

### Post by yogen on 2008-09-01
Its only a week that i am using ubuntu...so guys i need your help...

whenever i start my pc...and select ubuntu as the OS(i hav windows too)...instead of the usual ubuntu logo loading itself...i can see a list of files loading itself...as if in terminal...
though this hasnt affected me anyway...still i would like if my loading ubuntu logo comes back again...any suggestions please...!!!

---

### Post by swoll1980 on 2008-09-01
> **yogen said:**
> Its only a week that i am using ubuntu...so guys i need your help...

whenever i start my pc...and select ubuntu as the OS(i hav windows too)...instead of the usual ubuntu logo loading itself...i can see a list of files loading itself...as if in terminal...
though this hasnt affected me anyway...still i would like if my loading ubuntu logo comes back again...any suggestions please...!!!

I would say it's the frame buffer is set to the wrong resolution
```
sudo apt-get install startupmanager
```
this will let you fix all that stuff in a handy GUI

---

### Post by kansasnoob on 2008-09-01
Really need more info. Are you dual-booting with Windows or some other operating system? Have you done some repartitioning? Have you changed the size of the swap partition or anything like that?

If you'd post the output of:

```
sudo fdisk -lu
```

And some history would be helpful.

This is my fdisk -lu: (that's a lower case L, not a one)

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63056305

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sda2        61432560   156296384    47431912+   5  Extended
/dev/sda5        61432623   111394709    24981043+  83  Linux
/dev/sda6       111394773   115266374     1935801   82  Linux swap / Solaris
/dev/sda7       115266438   156296384    20514973+  83  Linux


You see from that you can tell I have two linux os's and a win os!

---

### Post by kansasnoob on 2008-09-01
> **swoll1980 said:**
> I would say it's the frame buffer is set to the wrong resolution
```
sudo apt-get install startupmanager
```
this will let you fix all that stuff in a handy GUI

I wonder if he's not in UUID hell!

Not really hard to fix if that's the case.

Edit: I should also have said that startupmanager is an excellent tool! I always use it because I do a lot of playing and it makes selecting a default OS easy as can be!

---

### Post by kansasnoob on 2008-09-01
Should this end up being a UUID thing look at these links:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

Just read it all before jumping in!

---

### Post by swoll1980 on 2008-09-01
> **kansasnoob said:**
> Should this end up being a UUID thing look at these links:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

Just read it all before jumping in!

the uuid thing happens when the frame buffer resolution is wrong

---

### Post by yogen on 2008-09-01
though the startupmanager has worked...it hasnt totally solved my problem...
still ubuntu displays loading of some files...it also checks swap file...

i have installed a firewall program 'FIRESTARTER'...
after installing this program...on booting...ubuntu displays initializing of many files successful...but it shows loading of filrestarter failed... i dont think this should be because of firestarter...but i am not sure...!!!

---

### Post by yogen on 2008-09-02
i just wanted to know that cant we change the splash screen with startupmanager...???
because my splash screen manager is not working...

---

