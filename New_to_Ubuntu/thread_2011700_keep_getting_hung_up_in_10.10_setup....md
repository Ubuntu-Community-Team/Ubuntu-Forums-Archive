---
title: "keep getting hung up in 10.10 setup..."
date: 2012-06-27
forum: New to Ubuntu
---

### Post by Pat Petit on 2012-06-27
hey guys im having problems downloading ubuntu 10.10. yea i know its not the most recent but i was planning to update. but ive tryed installing it twice on 2 different hard drives, it gets stuck on: "creating ext4 file system/in partition #1 of SCSI1S. i was just wonder if it took that long to get past this part cause i choose jut to overwrite the previous info on the hard drive and make a new partition. is this a major problem or is it just taking a while?

---

### Post by wildmanne39 on 2012-06-27
Hi, for the least amount of issues reformat the partition and install 12.04LTS since 10.10 is no longer supported and updating from that version or older would most likely cause issues.

It could take awhile if does not mean it is stuck.
But how long have you been at that message.
Thanks

---

### Post by Basher101 on 2012-06-27
> **Pat Petit said:**
> hey guys im having problems downloading ubuntu 10.10. yea i know its not the most recent but i was planning to update. but ive tryed installing it twice on 2 different hard drives, it gets stuck on: "creating ext4 file system/in partition #1 of SCSI1S. i was just wonder if it took that long to get past this part cause i choose jut to overwrite the previous info on the hard drive and make a new partition. is this a major problem or is it just taking a while?

it does need some time, but not more than 20-30 minutes. You could also just manually partition your Hard drive before installing Ubuntu so the installer does not need to do it. 


regards


p.s. To partition manually, Run the Live CD and open Gparted. Delete all partitions and use all space, but remember to make a second partition for SWAP. Your SWAP partition should be as big as your RAM (e.g. you have 2 GB RAM, your SWAP partition must be 2 GB big)

p.p.s. after you partitioned it manually, you must also set the Mount Points manually. To do so choose "Something Else" at the installer instead of "use all space" (or whatever the first option is). Now you get to your partitions again, choose the large one and hit "change". Set the filesystem to **[COLOR="Red"]ext4[/COLOR]** and the mount point to **[COLOR="Red"]/[/COLOR]**. After that you just need to set your SWAP partition as swap, click on it and hit "change". Here you just need to set it from the dropdown menu to SWAP and you are set.

---

### Post by Pat Petit on 2012-06-27
yea its been going for 30-45 mins now. its not frozen cause i can easily go from slide to slide on the downloading screen. and the hd dosnt even seem to be under load, its just sitting there in idle.

---

### Post by jmfal on 2012-06-27
Did you select "update after installation is complete"??

If you did the installation is probably done but it is trying to update and there is nothing to update because 10.10 is at "END OF LIFE" you cannot get updates for it except through the archives and ther is no option for that during installation.

---

### Post by Pat Petit on 2012-06-27
actually no, but i stopped the download and im just going to burn a cd. cause that pc isnt hooked up to the internet. would that have something to do with it?

---

### Post by jmfal on 2012-06-27
Probably

---

### Post by Pat Petit on 2012-06-27
oh alright when i put 12.04 on it ill put it on the web. dose 12.04 use the ext4?

---

### Post by uRock on 2012-06-27
> **Pat Petit said:**
> actually no, but i stopped the download and im just going to burn a cd. cause that pc isnt hooked up to the internet. would that have something to do with it?

You may want to try a newer release. 10.10 is no longer recieving updates.

---

### Post by Pat Petit on 2012-06-27
> **uRock said:**
> You may want to try a newer release. 10.10 is no longer recieving updates.

i know getting 12.04 now. ^ comments above

---

### Post by jmfal on 2012-06-27
Yes you can use ext.4 with 12.04

---

### Post by Pat Petit on 2012-06-28
guys after a while it loaded it, and everything is working fine, it updated to 12.04 but dose ubuntu support a slave drive cause it never shows up

---

