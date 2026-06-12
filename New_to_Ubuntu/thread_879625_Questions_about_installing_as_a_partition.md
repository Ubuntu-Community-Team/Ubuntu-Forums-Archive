---
title: "Questions about installing as a partition"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Spops on 2008-08-04
Hi Everyone,

I am debating on installing Ubuntu as a partition on my HDD.  Currently I have it as a Wubi install with 10gb of space.  

Here are my laptop specs:

Dell Inspiron 6000
Intel(R) Pentium(R) M processor 1.60 GHz  798 MHz,  512 MB of RAM
ATI Mobility Radeon X300
HDD:  60GB

Is there any real advantage of setting up Ubuntu with its own partition vs. just using the Wubi Install?

If I do go ahead and make the partition what happens if I decide in 6 months from now that I don't want it anymore.  Can I just delete the partition and reallocate that space back to windows?  Or would I need to reformat the HDD and install everything fresh again?

Can someone also explain to me how you would go about doing a partition with Ubuntu?

Thanks in advance :)

---

### Post by hyper_ch on 2008-08-04
> **Spops said:**
> Is there any real advantage of setting up Ubuntu with its own partition vs. just using the Wubi Install?
Yes there is ;) better speed, less "wubi" troubles...

> **Spops said:**
> If I do go ahead and make the partition what happens if I decide in 6 months from now that I don't want it anymore.  Can I just delete the partition and reallocate that space back to windows?  Or would I need to reformat the HDD and install everything fresh again?
(1) reinstall windows boot loader (fixmbr)
(2) remove the ubuntu partitions
(3) assign the freed space to existing windows partitions or make them seperate partitions

> **Spops said:**
> Can someone also explain to me how you would go about doing a partition with Ubuntu?
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
defrag windows 2-3 times first and if you're on vista, use vista partitioner to free space.

---

### Post by JoneYee on 2008-08-04
> **Spops said:**
> Can someone also explain to me how you would go about doing a partition with Ubuntu?

Thanks in advance :)

If you are running XP, you do not have a native partition editor.  I would suggest looking into [Knoppix]("http://www.knoppix.net/") (the application is qtparted).  Knoppix has been my long standby partition editor with Windows XP systems.

It is a live Linux Disc, much like the Ubuntu Disk which will allow you to execute a partition editor within Knoppix

From Terminal in Knoppix
```
qtparted
```

As always, before you make a major change such as this to your file system, you should always perform a backup of any files and folders that are valuable.  Editing a Windows partition can (tho never happened to me) cause data loss.

---

### Post by hyper_ch on 2008-08-04
> **JoneYee said:**
> As always, before you make a major change such as this to your file system, you should always perform a backup of any files and folders that are valuable.  Editing a Windows partition can (tho never happened to me) cause data loss.

I think you should always make regurarly backups. Not only before "major" changes.

---

### Post by JoneYee on 2008-08-04
> **hyper_ch said:**
> I think you should always make regularly backups. Not only before "major" changes.

Oh i agree, just highlighting it is important to make sure that you have a backup of a valid system state, something that worked, before going out and editing partition tables/sizes.

---

### Post by ingeva on 2008-08-04
> **JoneYee said:**
> If you are running XP, you do not have a native partition editor. 

All Windows versions from Windows NT 3.1 have had a graphic partition editor.
It's under "Administrative Tasks","Computer Management" in Control Panel.

It's also very easy to use, although it has somewhat limited features (can't resize partitions for example), but you can format partitions to FAT32 or NTFS.

Not ***everything*** is bad or missing with Windows! :)

---

