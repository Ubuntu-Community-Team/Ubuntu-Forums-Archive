---
title: "Disk Cleanup and degragmenter"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by Radical_Dreamer on 2011-10-30
So, as someone who switched recently to Ubuntu I want to ask is there some equivalent?  Because the closest thing I can find is the janitor function and there is something you can do with the synaptic package manager but not quite the same.

---

### Post by oboedad55 on 2011-10-30
You can try BleachBit. As far as defrag goes, I have not found it necessary to defrag an ext4 filesystem, nor am I aware that there exists a viable option for doing so.

---

### Post by Paqman on 2011-10-30
You shouldn't need to defragment your machine. As long as you don't fill the storage up too much Linux filesystems like Ext4 don't fragment enough for it to ever affect performance.

For cleanup you can use [Bleachbit]("apt:bleachbit") (click to install).

---

### Post by Radical_Dreamer on 2011-10-31
Also, this is something but is pretty important.  Should I just delete everything in the not installed residual config section of synaptic?

---

### Post by wildmanne39 on 2011-10-31
Hi, I am not sure what you are talking about, can you explain more about what you want to delete? If you start deleting things and messing with configuration files you are going to destroy ubuntu.

Please remember the saying if it is not broke don't fix it.
Thank you

---

### Post by Paqman on 2011-10-31
> **Radical_Dreamer said:**
> Also, this is something but is pretty important.  Should I just delete everything in the not installed residual config section of synaptic?

You could, it might free up a little bit of disk space, but otherwise won't make any difference. The applications that those are the config files aren't even installed.

---

### Post by Johnny3 on 2011-10-31
> **wildmanne39 said:**
> Hi, I am not sure what you are talking about, can you explain more about what you want to delete? If you start deleting things and messing with configuration files you are going to destroy ubuntu.

Please remember the saying if it is not broke don't fix it.
Thank you

You will need to install synaptic package manager from the software center for 11.10. Then you can do a search for synaptic package manager or try youtube too to use it. You can install bleach from software center too. When you run bleach root at first don't check everything and if I comes up with and alert just cancel that check if you don't want to try it or take the time. Hope this make sense to you. I don't explain things well some times.
Good Luck and God Bless Johnny3 65++
If you don't brake it once in a while you not trying to learn enough.

---

### Post by Frogs Hair on 2011-10-31
Bleachbit works well for clean up . I use it after installations to remove hundreds Mb of temporary files and otherwise occasionally . If you run it as root be sure you understand to options you are selecting . 

Removing residual configurations via the synaptic package manager or terminal should not cause any problem .

---

### Post by ofnuts on 2011-10-31
> **Paqman said:**
> You shouldn't need to defragment your machine. As long as you don't fill the storage up too much Linux filesystems like Ext4 don't fragment enough for it to ever affect performance.

For cleanup you can use [Bleachbit]("apt:bleachbit") (click to install).I have filled up my home partition in a couple of occasions and there is indeed a slow down when accessing the disk. On NTFS, once you reach significant levels of fragmentation, things go from bad to worse.... But will ext4 "heal" when disk space is recovered, or will things remain fragmented?

---

### Post by Paqman on 2011-10-31
> **ofnuts said:**
> I have filled up my home partition in a couple of occasions and there is indeed a slow down when accessing the disk. On NTFS, once you reach significant levels of fragmentation, things go from bad to worse.... But will ext4 "heal" when disk space is recovered, or will things remain fragmented?

Any data that was written at the time will remain fragmented, but if there's enough space any new writes will be more contiguous. To completely get rid of all the fragmentation you'd need to take a backup of everything and then write it back to the disk.

---

### Post by varx on 2011-10-31
Isn't there supposed to be a defrag option for ext4? I've read about this off and on for several years, but haven't seen it appear yet.

---

### Post by dFlyer on 2011-10-31
From the command line run the following commands:

sudo apt-get update
sudo apt-get -f install

The apt-get -f install will list install libs that are no longer needed. It will also suggest for you to run:

sudo apt-get autoremove

The above command will clean the drive of libs no longer needed.

To clean your /var/cache/apt/archive files

sudo apt-get autoclean 

This will remove all old duplicate debs and free up more space

In over 16 years of using linux I've never needed to defrag a linux partition. 

Please be advised that removing default installed programs can brake you system if you remove too many.

---

### Post by Joreus on 2011-10-31
I always got the impression that Linux ran fine despite fragmentation. That was supposed to be one of the advantages of Linux over Windows.

---

### Post by philinux on 2011-10-31
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

