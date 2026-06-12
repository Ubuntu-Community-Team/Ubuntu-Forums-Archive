---
title: "RAID 1 under Windows and Ubuntu"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by k_zurawski on 2016-01-04
Hi,
I'm thinking of setting up RAID1 under Windows but as I have written in title I'd like to have that RAID 1 working on both systems. Workstation will have 3 HDD's, 1 dedicated for both systems, dual-boot of course. Have anyone of You tried this before?

---

### Post by mastablasta on 2016-01-04
so what is the problem? did you get any errors while setting it up?

---

### Post by SeijiSensei on 2016-01-04
I've never tried using RAID on Windows, but if, as I suspect, it requires a proprietary driver and uses a proprietary disk format, then you won't be able to share it between operating systems.  You could try installing the drives and Linux on some disused older machine if you have one and making it a network server.  If you did that, and ran both nfs-kernel-server and Samba, then client workstations could mount the array over the network from either operating system.

The only way I could this working on a single machine is if you're using a well-supported hardware RAID device like those supporting the [SAS standard]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022629&IsNodeId=1&bop=And&Order=PRICE&PageSize=30").  Both operating systems have drivers for those, but decent cards cost around $100 or more.

---

### Post by k_zurawski on 2016-01-05
mastablasta, I didn't get any errors, I'm thinking of buying a workstation and use both systems on it. The data will be quite important, thus mentioned RAID.

Well, I do have a NAS with RAID1 and communicate with it via Samba. I want to run some calculations which require lots of data. That's why it should store it locally. Some of the data I must prepare under Windows, rest under Linux. Forget about migrating PC-NAS-PC. It takes too long.

---

### Post by mastablasta on 2016-01-05
raid doesn't protect against corrupted data. it protects only against disk failure. you still need a backup solution if data is important. good luck.

---

### Post by CharlesA on 2016-01-05
> **SeijiSensei said:**
> I've never tried using RAID on Windows, but if, as I suspect, it requires a proprietary driver and uses a proprietary disk format, then you won't be able to share it between operating systems.  You could try installing the drives and Linux on some disused older machine if you have one and making it a network server.  If you did that, and ran both nfs-kernel-server and Samba, then client workstations could mount the array over the network from either operating system.

The only way I could this working on a single machine is if you're using a well-supported hardware RAID device like those supporting the [SAS standard]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022629&IsNodeId=1&bop=And&Order=PRICE&PageSize=30").  Both operating systems have drivers for those, but decent cards cost around $100 or more.

Another option is to get one of those NAS in a box type deals that plug into a USB3 or esata port and go to town. That would be pretty much the same as having the array in a separate box and accessing it over the network or locally.

> **mastablasta said:**
> raid doesn't protect against corrupted data. it protects only against disk failure. you still need a backup solution if data is important. good luck.

This x 1000. The whole idea behind RAID is redundancy so you are not down if one of the disks goes out. If you want to protect against data corruption, you need to have a backup scheme in place. RAID is not a replacement for backups.

---

