---
title: "Want to install Ubuntu 14.04 on SSD (Samsung Evo 840)"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by snowmobiler on 2014-09-16
This is my first post and I am totally new to the Linux world. I have recently installed Ubuntu 14.04 on a Dell Optiplex 620. I have an 80 GB HD but did not do any partitioning. Just installed. I have 2GB RAM. Haven't run into any issues and all I plan to do is surf really until I learn more about Linux. I did copy 28GB of music to PC which copied much faster than to a Win7 pc. Haven't tried installing Chrome which I use on Windows PCs, I am fine with Firefox at the moment.

So now I have (or will have) an older Dell Latitude laptop running XP. I want to updgrade the RAM to 4GB and I want to put in a 250GB SSD drive (most likely the Samsung EVO 840 which seems to get great reviews). Since I am new, I see  there is so much conflicting info on what to do with an SSD drive, turning journaling on or off etc. 

For what I plan on using it for, as a spare laptop for surfing, youtube, maybe some music and Libre office (which I haven't tried on the Optiplex yet) what should be my best install procedure? Just install 14.04 like on the other machine and not worry about anything? Should I install in say a 20GB home partition, followed by 4-8GB swap partition, followed by the rest as an open space partition (I bookmarked a document on how to do the partitioning during install so I don't need that info, just whether or not its needed). Then do I need to worry about Journaling, adding noatime (which i need to learn more about). And finally, do I need to worry about TRIM, whatever that is? It's in the document I bookmarked, but I think I read somewhere that 14.04 handles it automatically now. 

Hope I didn't ask too much. A lot of info out there is about typing in code and saving which I haven't tried yet, so just looking for a starting point for the new SSD setup.

---

### Post by Tadaen_Sylvermane on 2014-09-16
I use my ssd as a regular drive, I don't do anything special with it or for it. *buntus run trim automatically once a week and that is all there is to it. I think people and the "limited writes" argument tend to forget that with normal use those so called limited writes are enough for a couple decades of average use.

It's generally understood in the circles I travel that a quality ssd will live longer than the computer you use it in barring any electrical failure... at which point amount of writes didn't matter anyway.

*EDIT* Side note. I agree with you on the 840 EVO series. Have yet to be disappointed both in speed and reliability. Use them in my laptop and my server.

---

### Post by snowmobiler on 2014-09-16
> **Tadaen_Sylvermane said:**
> I use my ssd as a regular drive, I don't do anything special with it or for it. *buntus run trim automatically once a week and that is all there is to it. I think people and the "limited writes" argument tend to forget that with normal use those so called limited writes are enough for a couple decades of average use.

That's what I have been trying to read up on, where to add Trim,noatime etc,. Did you make separate partitions or is it just one partition without a 'swap" partition? Did you add noatime to fstab file or do you think its unnecessary?

---

### Post by Tadaen_Sylvermane on 2014-09-16
I haven't touched the fstab except to add my server mount. I think its all unnecessary. Older ssds used to be a real problem but they got the kinks worked out pretty good these days.

I have a 20gb root, 2gb swap, and rest (93gb) mounted at /media/data.

On my server which is also ubuntu server version I think it's got a 10gb root, 110gb /var and I keep /home and swap on the 1tb spinner drive. The 110gb /var partition is where my kvm virtual machines run from.

---

### Post by snowmobiler on 2014-09-16
Thanks so much for the info. I think my thoughts agree with what you have said. I understand how to create a separate /home partition. I just have to understand how I would 'mount' it as you say as /media/data (or something else if possible). But for now I will just keep it as /home as I know I am not going to do anything intensive with the old laptop I will be using. Is there much of an advantage by having the separate partition apart from the boot partition? I have never had a need in windows to create separate partitions so what do I gain in Linux, especially on a drive with no moving parts, compared to conventional HDDs? I guess that's why on my current PC, I didn't partition because I wasn't even thinking it was necessary, like with my recent Win7 installs.

I just used the command   sudo parted -l  to see how my pc drive is formated. It seems the boot is the 1st partition (77.9GB). the second is 2.1GB extended and the third (#5) is the same start end as the extended partition and is called "linux-swap", so I guess version 14.04 creates the swap partition automatically.

---

### Post by maxinstuff2 on 2014-09-16
Samsung Evo (1TB :-| ), installed kubuntu with default settings + lvm (the second option in the installer).

Here's a good case for not worrying about write cycles - a "torture test" was done on the previous generation Samsung 840, and it held up to an amount of write cycles that equate to 75 YEARS of normal use, and 25 years under above average load.
[http://uk.hardware.info/reviews/4178/10/hardwareinfo-tests-lifespan-of-samsung-ssd-840-250gb-tlc-ssd-updated-with-final-conclusion-final-update-20-6-2013](http://uk.hardware.info/reviews/4178/10/hardwareinfo-tests-lifespan-of-samsung-ssd-840-250gb-tlc-ssd-updated-with-final-conclusion-final-update-20-6-2013)

It will fail in some other way long before write cycles become a problem.

---

### Post by snowmobiler on 2014-09-17
Thanks maxinstuff. Then I guess the question is moot but I'll ask anyway. Do you even care about the Firefox cache then? Read a lot about setting that to 0MB. I have a stack of scavenged 80GB HDDs from old work computers that were being recycled. I might just try installing Ubuntu on a few of them (using the same machine), with different partitions just to get a feel for how things pan out. I'm not a do something first, then try and fix it later kind of guy. I like to know what will or won't happen. Being a newbie, there is a lot out there on "how to care for SSDs" but with something like the new Samsungs and others, those things seem to be a pure waste of time and effort/research. Thanks all for helping the newbie!

---

### Post by sandyd on 2014-09-17
> **snowmobiler said:**
> That's what I have been trying to read up on, where to add Trim,noatime etc,. Did you make separate partitions or is it just one partition without a 'swap" partition? Did you add noatime to fstab file or do you think its unnecessary?

Trim is setup by default if your SSD is compatible (Which it is, Intel/Samsung SSDs are supported)

---

### Post by rolkin on 2014-09-17
Totally agree with the above posts. Modern OSes all support the trim operation (as does your ssd), so you really don't have to do too much tinkering. If you REALLY want to tinker around, here's a great link that outlines some useful configurations: [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by redrumrogue on 2014-09-17
I have a 128GB Samsung EVO 840 which has a standard ubuntu gnome install. It's an awesome drive.  I just used the automatic partitioning scheme.  Not changed any mount options in fstab and there is weekly TRIM that runs.  Here is the contents of the /etc/cron.weekly/fstrim file ...

```
#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  https://launchpad.net/bugs/1259829). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
exec fstrim-all


```

So ... should run on your Samsung SSD then! :D

---

### Post by snowmobiler on 2014-09-17
Thanks Red. When you say auto partitioning, do you mean you are using the whole drive for boot and home? That's what I did with my desktop and 80GB drive (and install created a small swap partition).  I guess I could take or leave creating a separate /home partition.

---

### Post by snowmobiler on 2014-09-17
> **rolkin said:**
> Totally agree with the above posts. Modern OSes all support the trim operation (as does your ssd), so you really don't have to do too much tinkering. If you REALLY want to tinker around, here's a great link that outlines some useful configurations: [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Thanks for the input. Already have that link bookmarked!

---

### Post by redrumrogue on 2014-09-18
Hi Snow - yes I installed ubuntu and used the entire drive for root and swap.  Although my home directory is on the SSD I store all my video, download, documents, pictures, music data on a large HDD based volume (using LVM) and then bind mount those folders to their counters parts in /home on the SSD.  You have to edit the fstab file to do this.  I found it just made installation (and re-installation!) a lot easier as I didn't have to change anything for partitioning during the OS install. If you want more info let me know.

---

### Post by snowmobiler on 2014-09-18
Thanks for all the help everyone. Now here is why I ask questions "before" I run into a problem. I was also researching whether I needed to order the Samsung SSD with the spacer kit for the Lattitude D820 I was going to be putting it in. The drive is easy to install. 2 screws on the bottom and the drive slides out like an SD card. Seems the Samsung is 7mm and the HD space is 9mm. Could probably still get away without the spacer as the mounting bracket would hold the drive up to make the Sata connections or could use anything for spacer. BUT ... in my research, I found out the D820 doesn't support AHCI which means the laptop would run in IDE emulation mode with the SSD. Still faster say those who have done it but not worth the expense, if not getting the full use of the SSD!

---

### Post by redrumrogue on 2014-09-18
Hmmm ... build a new machine I say!  Any excuse ...

---

### Post by snowmobiler on 2014-09-18
haha .. . that's the point. Where I work, I get to scavenge when things get upgraded so I was going to 'acquire' this laptop. All MAJOR plans down the drain, but I will still load Ubuntu and see what I can do. At least for the short term I saved a few bucks (if you want to call that the silver lining).

---

