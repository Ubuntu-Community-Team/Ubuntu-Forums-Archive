---
title: "Another partition size question"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Sabata on 2008-05-27
Hey gang, I have one more quick question before installing Hardy. How large should the /home partition be for the following system?

1.5GB RAM
sda is 160GB with XP
sdb is a blank 320GB drive that's going to be Ubuntu and file repository for XP and Ubuntu.

Going on advice from several of you kind souls, I planned on partitioning the 320GB drive like this:
/ = 15GB-20GB
/swap = 3GB-4GB
**/home = ?**
/data = remainder of drive, for storing docs, music, vids, etc.

Thanks.

---

### Post by Duck2006 on 2008-05-27
> **Sabata said:**
> Hey gang, I have one more quick question before installing Hardy. How large should the /home partition be for the following system?

1.5GB RAM
sda is 160GB with XP
sdb is a blank 320GB drive that's going to be Ubuntu and file repository for XP and Ubuntu.

Going on advice from several of you kind souls, I planned on partitioning the 320GB drive like this:
/ = 15GB-20GB
/swap = 3GB-4GB
**/home = ?**
/data = remainder of drive, for storing docs, music, vids, etc.

Thanks.

20Gb should be ok for your home partition.

---

### Post by quelx on 2008-05-27
I would leave home and data on the same partition

after installing make a **/home/data** directory and change the ownership (**sudo chown username /home/data**) to your user.  When I've divvied up my drives like what you are suggesting I inevitably made the partitions the wrong size.  If leave your media and home on the same partition you don't have to guess the size you might need next week/month/year.  The rest of the partitions look good in size.

---

### Post by Paqman on 2008-05-27
If /home isn't going to contain any data it shouldn't need to be any bigger than 5GB tops. Less if it's a single-user system.

---

### Post by Sabata on 2008-05-27
> **Paqman said:**
> If /home isn't going to contain any data it shouldn't need to be any bigger than 5GB tops. Less if it's a single-user system.
That's what I was looking for. /home won't contain data and I'm the only one using the system.

Thanks! :guitar:

---

### Post by Paqman on 2008-05-29
Cool. Don't sweat too much about partition sizes. You can always adjust them later if need be.

---

### Post by hyper_ch on 2008-05-29
> 
/data = remainder of drive, for storing docs, music, vids, etc.


why not in the /home partition? Not necessarily in /home/USER but e.g. /home/shared

That way you have all the user settings/docs on one partition.

---

### Post by ejb5oh on 2008-05-30
> **Paqman said:**
> Cool. Don't sweat too much about partition sizes. You can always adjust them later if need be.

That is what I am looking for.  How can I now change my partition sizes.  I have XP on 120gb and ubuntu on 30 gb and swap on 5gb.  

I want to add more gb to ubuntu and leave only 50 or so for xp.  Completely leaving xp, only keeping it for a few programs that must be ran on it.

Thanks,
Eric

---

### Post by Duck2006 on 2008-05-30
> **ejb5oh said:**
> That is what I am looking for.  How can I now change my partition sizes.  I have XP on 120gb and ubuntu on 30 gb and swap on 5gb.  

I want to add more gb to ubuntu and leave only 50 or so for xp.  Completely leaving xp, only keeping it for a few programs that must be ran on it.

Thanks,
Eric

Use the live cd of parted margic to resize your drive.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

And change your swap size from 5Gb to 2Gb at the most any more than 2Gb for swap is a wast of space.

---

### Post by ejb5oh on 2008-05-30
> **Duck2006 said:**
> Use the live cd of parted margic to resize your drive.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

And change your swap size from 5Gb to 2Gb at the most any more than 2Gb for swap is a wast of space.

Okay, but can I add about 60 to the ubuntu side from the xp side as well?

---

### Post by Duck2006 on 2008-05-30
Yes use parted magic to change the size of the partition. You will have to make one smaller and then add the space to the partition that you want it in, some info on doing that.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

---

