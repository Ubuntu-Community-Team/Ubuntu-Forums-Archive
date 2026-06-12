---
title: "Cannot see all of my hard drive"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by chris_1d on 2012-02-06
Hi there,

I'm new...I have just installed ubuntu, replacing windows XP on my netbook. I was asked if I wanted to overwrite XP and I said yes. However my system now says it can only see around 6gb of my hard drive, which is 160gb. The system did so something with partitions during the install but where is the rest of my GB's and how to I get them back?

I did have a quick look plus tried search but to no avail,

Regards,

Chris D

---

### Post by QIII on 2012-02-06
Before we ask you to run a script that will return a boatload of information, could you do a quick check?

Run

```
fdisk -l
```

in the terminal and post the results.

That's a small "L" not a one.

---

### Post by chris_1d on 2012-02-06
It will no play ball (I'm probably being thick) I've opened terminal, typed in fdisk -l and it just gives me a command line again...argh!!

Got it, I think...

```
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000916d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    13686783     6842368   83  Linux
/dev/sda2        13688830    15759359     1035265    5  Extended
/dev/sda5        13688832    15759359     1035264   82  Linux swap / Solaris
chris@chrisnetbook:~$ ^C
```

---

### Post by chris_1d on 2012-02-06
Very confused! :(

---

### Post by joetait on 2012-02-06
Try 
```

sudo fdisk -l

```instead. It will ask for you password and then should give you the desired output

Edit: Sorry, saw that you worked it out for yourself.

---

### Post by QIII on 2012-02-06
Are you using an 8GB thumb drive, perchance?

---

### Post by chris_1d on 2012-02-07
Nope, AFAIK the drive inside the netbook is a 160gb hard drive...

---

### Post by mörgæs on 2012-02-07
I added CODE tags to your output in post 3. Makes it easier to read.

How big is the hard drive if you view it from BIOS?

---

### Post by chris_1d on 2012-02-07
Sorry guys, have discovered that infact I have an 8gb SSD drive not the 160gb drive I beleived was in there!!

Thanks anyway!!

---

### Post by mörgæs on 2012-02-07
OK :-) 
Please mark the thread 'solved'.

---

