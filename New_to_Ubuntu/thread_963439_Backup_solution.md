---
title: "Backup solution"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Yizi on 2008-10-30
Hi,

I'm setting up a server and i need help with the back, i have two 250GB hard drives, i want to know how i can miror in case one goes down so the other one covers and how i can take a manual weekly/monthly backup myself with ym external hard drive.

I like to know exactly how to do it.

Thanks,
Yizi

---

### Post by northern lights on 2008-10-30
If the mainboard supported [RAID]("http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks"), or you have some other RAID controller, RAID 1 would be a decent solution.

If you want to got the software route,check out [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/").

It's available from the Ubuntu repositories.

---

### Post by hyper_ch on 2008-10-30
I use rtorrent and hardlinks and a little script of mine. However if you need a 1:1 mirror you will need to use raid.

---

### Post by Yizi on 2008-10-30
What sort of mainboard will support RAID, example would be great.
Also if i only want to make a backup with a external hard drive what is the best option.

---

### Post by northern lights on 2008-10-30
> **Yizi said:**
> What sort of mainboard will support RAID, example would be great.
There's loads of boards with onboard RAID controllers out there. Here's [one]("http://www.compuvest.us/ProductDetails.aspx?productID=285847&CategoryCode=MB").
Further you can also add a PCI RAID controller to your existing machine. [Here]("http://www.compuvest.us/ProductDetails.aspx?ProductID=271855&CategoryCode=CON_SAS")'s an example.
If you choose to buy a board, make sure it's compatible with your CPU and RAM. As for the controller make sure it can handle your drives (you need two ideally identical drives for RAID 1) - are they IDE/ATA/SATA?

> **Yizi said:**
> Also if i only want to make a backup with a external hard drive what is the best option.
I'd suggest unison, as above. It's got a decent GUI and let's you specify folders to synchronize in customizable intervals.

---

### Post by Yizi on 2008-10-30
It seems you know too much LOL i need to ask more questions, all i want to do is basicaly have a LAMP server to run few script and this server is only used localy so it will never go online, plus i need the people who connect to it, to be able to share files inside a special folder somethign like share document. is that even possible?

Also is there anyway to make the server have a GUI that will make it easier to maintain?

Thanks again!

---

### Post by kpkeerthi on 2008-10-30
> **hyper_ch said:**
> I use **rtorrent **and hardlinks and a little script of mine. However if you need a 1:1 mirror you will need to use raid.
You meant rsync? Didn't you? :)

---

### Post by handydan918 on 2008-10-30
> **kpkeerthi said:**
> You meant rsync? Didn't you? :)

Well, if he didn't, I was going to suggest it. Seems like an ideal application for rsync run as a nightly cronjob.

---

### Post by Yizi on 2008-10-30
Guys anyone? the above guys just changed the subject totally LOL

---

### Post by hyper_ch on 2008-10-30
yeah, meant rsync :) I was just too much thinking of rtorrent because of the Ibex release... my seed box is seeding the 64bit ISOs nicely :)

---

### Post by biji on 2008-10-30
try simple backup restore / config it is app suite for personal backup

---

### Post by Yizi on 2008-10-30
> **biji said:**
> try simple backup restore / config it is app suite for personal backup

Do you have any source that can explain how to use this and its commands?

Thanks,
Yizi

---

### Post by handydan918 on 2008-10-30
To repeat my previous "change of subject, LOL"
Seems like an ideal application for rsync run as a nightly cronjob.

Reference man cron and man rsync.

---

### Post by mlissner on 2008-10-30
If you use rsnapshot, it gives a little more power over simple rsync setup, though it can be a bear to get completely figured out. If you decide to use it, pay very close attention to tabs and line returns in your config. That's my biggest advice.

---

### Post by biji on 2008-10-30
> **Yizi said:**
> Do you have any source that can explain how to use this and its commands?

Thanks,
Yizi

It is in standard ubuntu repository.. to install: sudo apt-get install sbackup
then go to System -> Administration -> Simple Backup Config ..

---

### Post by Yizi on 2008-10-31
> **biji said:**
> It is in standard ubuntu repository.. to install: sudo apt-get install sbackup
then go to System -> Administration -> Simple Backup Config ..

I'm sure i said server but that still helps thanks

---

