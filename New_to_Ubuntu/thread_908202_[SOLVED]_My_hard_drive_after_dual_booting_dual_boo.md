---
title: "[SOLVED] My hard drive after dual booting dual booting"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by irishy on 2008-09-02
Can anyone help again please
 with a lot of help from you all I set up a dual boot system xp and Hardy Heron can anyeone have a look at the following and tell me if what I did was right and please explain it to me
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47954794

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4216    33864988+   7  HPFS/NTFS
/dev/sda2            4217       30401   210331012+   5  Extended
/dev/sda5           17300       30047   102398310   83  Linux
/dev/sda6           30048       30401     2843473+  82  Linux swap / Solaris
/dev/sda7            4217       17299   105089134+   7  HPFS/NTFS

Partition table entries are not in disk order
```
```

```
thanks in anticipation

---

### Post by LowSky on 2008-09-02
Nothing looks wrong, but are you experiencing problems? Please explain what your looking to do. From the looks of it you partitioned the hard drive with one primary and one extended, added 4 logical partitions to the extended (I assume the extra NTFS is for a Windows install or shared space?).

---

### Post by Victormd on 2008-09-02
Everything looks fine. You have 1 linux partition (where hardy is installed), a swap partition for hardy and 2 NTFS partitions. What kind of problems are you having (if any)? What would you like explained? :)

---

### Post by Victormd on 2008-09-02
> **LowSky said:**
> one extended, added 4 logical partitions to the extended (I assume the extra NTFS is for a Windows install or shared space?).

minor observation, I think he only created 3 partitions in the extended partition space... :)

---

### Post by irishy on 2008-09-02
I thank you for your answers
my problem is only one of confusion everything seems to work correctly I don't have any issues with Hardy Heron and xp seems reasonably ok I have 2 partitions show up in ubuntu one I think is c drive in xp and another at 104 gb which I assume is the one Hardy Heron is on However if I deposit anything on this drive ie new images it shows up in xp on e drive this being the drive I set up to share between the os's. So if I haven't put you to sleep yet in xp I have 2 partitions or drives show up c at 32 gb which is xp(the only one I am sure of)and f at 100gb which is the shared one I think if what I am saying is correct how does the content in hardy heron get into the shared partition after placing it in ubuntu's partition also my thought onthe size of partitions is that I got that wrong to much for hardy and to little for xp thanks for your patience I hpe you can make sense of this
thank you all again

---

### Post by dracayr on 2008-09-02
to resize the partitions: insert your liveCD and boot from cd as you did to install ubuntu. then, from the liveCD, do: System&#8594;Administration&#8594;partition manager (It might also be called gparted)

then you can resize your partitions...

to access your linux partitions from window$, install fsdriver in window$:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

dracayr

---

### Post by Victormd on 2008-09-02
I think I understood what you're trying to say:
104 Gb hardy
32 Gb xp
100 Gb shared

When you save anything to your hardy partition, windows will not see it because windows cannot recognize the linux file system (i.e., ext2 and ext3) unless you've installed an ext-reader in XP. However, ubuntu CAN and will read/write NTFS.

With that said, in your example, if you save an image to the Hardy partition, windows won't see it, so, if you can see it in XP, that means that you're saving them directly into the shared partition and not your Hardy partition (hope I didn't confuse you too much... :)).

---

### Post by irishy on 2008-09-02
Thanks again for the replies that I think is my confusion if as you say it is not the hardy partition but the shared partition  how do I display the hardy partition
thanks

---

### Post by Victormd on 2008-09-02
The Hardy partition, under Hardy, shows up as "File System" and you can access it by going to PLACES>HOME FOLDER (this is where all your information is stored in the hardy partition, and you can browse through it normally) or go to PLACES>COMPUTER and it should show up there.

To access your Hardy partition under windows, you'll need to install a program such as [this]("http://www.fs-driver.org/index.html").

---

### Post by irishy on 2008-09-03
Thanks for all your help I am a lot wiser and understand a lot better now could I ask a couple more questions please in the shared partition showing in Hardy there are 2 more folders recycler and system volume info these are not visible in xp what are they and if it becomes neccessary to increase the xp partion is this easy to do
thanks again

---

### Post by Victormd on 2008-09-03
The **recycler** and **system volume information** folders are windows system folders. The recycler folder is your windows trash can and system volume information is used for the system restore under windows. You can't see them in Windows because they are marked as hidden.

As for increasing your windows partition, that's pretty easy, if you need help with that, let me know.

---

### Post by irishy on 2008-09-03
Thank you very much I do understand a lot more now, you have been very patient
thanks

---

### Post by Victormd on 2008-09-03
No problem, that's what we're here for! :)

---

