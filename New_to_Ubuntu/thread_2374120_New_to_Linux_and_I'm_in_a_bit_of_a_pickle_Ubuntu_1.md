---
title: "New to Linux and I'm in a bit of a pickle Ubuntu 17.04"
date: 2017-10-12
forum: New to Ubuntu
---

### Post by toboe2 on 2017-10-12
I am duel booting with windows, i have partitioned my hard drive and ssd, and well done all the steps I should have.
I was unable to run it at first but after some searching I found I could get into the try ubuntu by adding the nomodeset between quick splash.

After getting in with excitement and probably half retardation I began to install it with recommended drivers button.

After the download when i try to start up ubuntu it freezes on a purple screen.

So i did some research and found you can find error details if you delete quick splash, so i did. Now I can't even get into the grub menu.

If anyone could give me any advice or heads up, on how to finally get in an enjoy ubuntu i would greatly appreciate it.

 
PC Details
1. I would like ubuntu to be on an SSD which i heard causes problems but I would really prefer it to be on the SSD.
2. I have a 1080 ti graphics card
3. i7-6850 processor
4. asus x99 delux II mother board
5. i partitioned 250gbs of ssd and 1tb of hdd for ubuntu

---

### Post by Bucky Ball on 2017-10-12
Welcome. Well done. You're getting there! 

But ... Go again, but this time, do not click the box that says 'Install third-party drivers' or 'Update during install' during the install. Leave them out. They can cause issues. 

Any drivers you need, if you indeed need any, you can take care of once installed. Same with updates/upgrades. Neither is required now. Stick with using the 'nomodeset' option for now if that gets you in.

Try that, the 'no frills' approach, and let us know how you go.

As for your questions.

1/ Non-issue. Not sure where you heard that.
2/ Fine. The drivers will be available in 'Additional Drivers' after install.
3/ Non-issue.
4/ Can't see a problem. Users of that board may be able to shed more light, but doubtful an issue.
5/ Please explain. You have two partitions for Ubuntu? One on SSD, one on HDD? There are several ways of going about this. Common is to put Ubuntu on a 25-30Gb partition on the SSD (put all OSs on the SSD) and make a big data partition (NTFS) on the HDD(s) which can be shared between Win and Ubuntu. We can help with that if you go that way.

Having personal data in Windows partitions and other personal data in Ubuntu partitions makes redundancy, and inevitable confusion, almost certain. ;) (... and Windows can not read/write Linux EXT* partitions anyway.)

* Rule of thumb tip if you have a combo of an SSD and HDDs: OSs on SSD; data on HDD. You want the OSs to be fast as they can be, so SSD it is.

---

### Post by toboe2 on 2017-10-16
I want to thank you so much for this reply, and for as quickly as you managed it. I'll give it a try tonight and let you know.

---

