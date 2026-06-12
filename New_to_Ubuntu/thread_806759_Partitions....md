---
title: "Partitions..."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-25
I'm currently dual booting with XP but i haven't used it for about 2months now so last night i decided i would delete all my unwanted files on the XP partition and i reduced it's size to about 20GB so i have roughly 50Gigs of free space on my hard drive, i was planning to then make my ubuntu partition larger but when i was using gparted on the livecd it couldn't make my ubuntu partition any larger only smaller:confused:

Is there anyway to extend my ubuntu partition?

---

### Post by muted1987 on 2008-05-25
have you tried creating a new partition with the free space and setting the mount point to /media/extrastorage of something equivilant?


sry but i think your sig says it all for me

---

### Post by carloslosgrande on 2008-05-25
[FONT="Comic Sans MS"]Have you tried using the GParted live CD? Its very useful, isn't too big to download and seems, to me, to be more effective. I had your problem once before and got the GParted CD - presto, problem solved.[/FONT]

---

### Post by sayakb on 2008-05-25
There is a Windows software you might use on a 30-day trial, and then get rid of it. Its partition magic pro. Download the 8.0 version and resize the ubuntu partition using that. Might just work for you.

---

### Post by bodhi.zazen on 2008-05-25
It depends on the version of gparted. You need Ubuntu 7.10 or 8.04.

Then defragment your windows partition.

Then, in gparted, resize your partitions in two steps. First reduce the size of your windows partition, then apply changes.

You should now have unformatted free space in front of your Ubuntu partition ans should be able to resize increase) it.

---

### Post by kamitsukai on 2008-05-25
> **bodhi.zazen said:**
> It depends on the version of gparted. You need Ubuntu 7.10 or 8.04.

Then defragment your windows partition.

Then, in gparted, resize your partitions in two steps. First reduce the size of your windows partition, then apply changes.

You should now have unformatted free space in front of your Ubuntu partition ans should be able to resize increase) it.

gparted wouldnt let me make it bigger and the gparted live cd wouldnt boot properly on my system...i will try partition magic..:lolflag:

---

### Post by housam on 2008-05-25
You can still use the ubuntu live cd partition editor to do what you want but first you have to unmount ubuntu partition to allow resizing. read [[COLOR="Red"]_this guide _[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by kamitsukai on 2008-05-25
well it cant be mounted because I'm using the livecd :( here's a screenshot of me trying to resize my ubuntu partition as you can see it says that its maximum size is 70 something gig and i cant make it bigger

---

### Post by housam on 2008-05-25
> **kamitsukai said:**
> well it cant be mounted because I'm using the livecd :( here's a screenshot of me trying to resize my ubuntu partition as you can see it says that its maximum size is 70 something gig and i cant make it bigger

Because the unallocated space is in the front end of Ubuntu partition , only the[[COLOR="Red"]_ new version of Gparted _[/COLOR]]("http://gparted.sourceforge.net/livecd.php")that will allow you to resize from that side.download and burn the new version ISO using [[COLOR="Red"]_infra recorder burning tool_[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto#head-5f36c46dbbdd2bd773ae1f5d361be66c6553babf")

---

### Post by kamitsukai on 2008-05-25
> **housam said:**
> Because the unallocated space is in the front end of Ubuntu partition , only the[[COLOR="Red"]_ new version of Gparted _[/COLOR]]("http://gparted.sourceforge.net/livecd.php")that will allow you to resize from that side.download and burn the new version ISO using [[COLOR="Red"]_infra recorder burning tool_[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto#head-5f36c46dbbdd2bd773ae1f5d361be66c6553babf")

Thanks but unfortunately ive tried it, but it wont boot up on my PC, i think it's probably because i have an nvidia graphics card ive even tried it in safe graphics mode but still no luck

---

### Post by kamitsukai on 2008-05-25
i have also tried partition magic but it doesn't support ext2

---

### Post by louieb on 2008-05-25
you can't grow sda5  because its a logical partition and has to be in an extend partition. Yours is in extended partition sda2. You will have to grow sda2 first. then it will allow you to grow sda5. 

The GParted live CD has given me problems in the past. I now use either the SystemRescueCD or the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic"). Both have the latest version of GParted.

Don't worry if resizing takes a while. Growing or moving a partition to the left can take hours. It a lot faster to backup the partition with partimage.  Then delete, recreate and restore.  The down side is it a little harder to do be sure to read the partimage documentation 1st if you go that route.

---

### Post by bodhi.zazen on 2008-05-25
gparted was updated on Ubuntu as of 7.10, so the Ubuntu desktop live CD 7.10 or 8.04 will resize your partitions.

As louieb indicated, you need to resize the extended partition first, then the logical partition. This will need to be done in two steps.

Resize extended partition - > apply changes

Resize logical partition -> apply changes

The gparted live CD is a nice tool, I have one too, BUT it is not necessary and it does not always boot (usually this is solved by selecting safe graphics mode).

If you would like to advise the gparted live CD, or any other tool, that is fine, BUT **please do not give misinformation about the ubuntu live (desktop) CD (the desktop CD has an updated version of gparted as of 7.10)**

---

### Post by kamitsukai on 2008-05-25
tried what you both said but it wont let me resize anything to do with ubuntu because it says one or more of the logical partitions is being used...although none are mounted :(

---

### Post by bodhi.zazen on 2008-05-26
You need to unmount the swap partition as well.

```
sudo swapoff /dev/sdxy
```

where sdxy is your swap partition.

---

### Post by |Eric| on 2008-05-26
i see now !!!


you cant change your linux partition size as it is a logical partiton in the Extanded partition (sda5 & more are logical partitions)

:-) 
try creating another partition in those 50 mb & mount that somewhere 

i unfortunatly dont know if you can expand the extended partition

EDIT: sry didnt read  you can also do a df in a terminal  & unmount all the Extended partitions that are mounted with umount

---

### Post by kamitsukai on 2008-05-27
Thankyou to louieb & bodhi.zazen, My partitions are all sorted now thanks to you :)

---

