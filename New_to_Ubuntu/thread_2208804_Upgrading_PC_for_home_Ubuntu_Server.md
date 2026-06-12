---
title: "Upgrading PC for home Ubuntu Server?"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by brockolicosmique on 2014-03-02
Hello, I'm not sure this post belongs here, but I guess I'm still a newbie at Linux, so here goes...

I'm following a guide I found on the web to make a home media server and to store all my files in one place ([http://linuxhomeserverguide.com](http://linuxhomeserverguide.com)). I was planning to do this cheaply, a buddy of mine gave me an old PC he was no longer using. It only has 2 sata ports and I am using both of them, one for a 500gb hdd and the other for a 3tb hdd, although the case itself is one of those tall ATX towers that have lots more room in it.

I am currently setting up the logical volumes with Webmin and the question I am having right now (a yes or no answer would be fine, I'm fine on doing research later on the feasibility of this): in the future, lets say all of those hard disks get full and I wanted to add more, I guess I would have to change the motherboard to one that has more sata ports. Now, doing this, would I have to reinstall Ubuntu Server from scratch? Would Webmin allow me to reuse my full hard disks (both are set up with LVM) without wiping them? Should I not worry about those sorts of things as I'll learn from doing this project? I have been installing Ubuntu desktop on my main PC and using it for a while, but haven't really learned how it "works", and having to do this really puts things in perspective.

Thanks!

JF

---

### Post by Zavation on 2014-03-02
Hi brockolicosmique,

May I reccomend you install a OS called OpenMediaVault on your Server? To be honest I'm going to be installing it this afternoon my old Dell Dimension 5100. OMV (Open Media Vault) supports software RAID, so you simply go in their add a new hard drive all via the nice web interface. This saves you from installing Ubuntu Server, Webmin and any other applications. So it turns everything you want to do into one OS Distro. Here's a link to their site: [http://www.openmediavault.org/](http://www.openmediavault.org/) it's only about 250MB so you can run it off a memory stick. Here is a link to a youtuber (Quidsup) who uses it on his server: [http://www.youtube.com/watch?v=fIFM1tH24V0](http://www.youtube.com/watch?v=fIFM1tH24V0) he shows you all the features it supports. 

As far as upgradeability, if the PC you have has a PCI slot, you maybe able to install a SATA PCI card allowing more SATA connections for more Hard Drives. You should just be able add your new drives no problem. You might want to think about putting them in RAID tho, as I have lost 3TB of data before and its not a nice feeling. 

I hope this answers your question, and if you have any issues just let me know.

---

### Post by joebutton64 on 2014-03-02
No, as long as you installed the OS (in this case Ubuntu Server) as an ISO image you can change out the mother board and be able to reuse those hdds.

---

### Post by brockolicosmique on 2014-03-02
> **b-josh said:**
> Hi brockolicosmique,

May I reccomend you install a OS called OpenMediaVault on your Server? To be honest I'm going to be installing it this afternoon my old Dell Dimension 5100. OMV (Open Media Vault) supports software RAID, so you simply go in their add a new hard drive all via the nice web interface. This saves you from installing Ubuntu Server, Webmin and any other applications. So it turns everything you want to do into one OS Distro. Here's a link to their site: [http://www.openmediavault.org/](http://www.openmediavault.org/) it's only about 250MB so you can run it off a memory stick. Here is a link to a youtuber (Quidsup) who uses it on his server: [http://www.youtube.com/watch?v=fIFM1tH24V0](http://www.youtube.com/watch?v=fIFM1tH24V0) he shows you all the features it supports. 

As far as upgradeability, if the PC you have has a PCI slot, you maybe able to install a SATA PCI card allowing more SATA connections for more Hard Drives. You should just be able add your new drives no problem. You might want to think about putting them in RAID tho, as I have lost 3TB of data before and its not a nice feeling. 

I hope this answers your question, and if you have any issues just let me know.

Thanks! I'll look into OMV as well. Initially I wanted to make a linux server to learn the process as well... I've got too many files spread out through too many devices at home.

---

### Post by Zavation on 2014-03-02
> **brockolicosmique said:**
> Thanks! I'll look into OMV as well. Initially I wanted to make a linux server to learn the process as well... I've got too many files spread out through too many devices at home.

No Problem. Even if you did install OMV, you can still SSH into it and controll it like a Ubuntu Server. I.e. install other applications like Webmin etc...

---

### Post by Odyssey1942 on 2014-03-02
Assuming that you have a parallel connector available, there is this possibility also:

> [http://www.meritline.com/serial-parallel-ata-translation-converter-ide-sata-bilateral-adapter---p-79488.aspx](http://www.meritline.com/serial-parallel-ata-translation-converter-ide-sata-bilateral-adapter---p-79488.aspx)

(advertisement provided just to illustrate what I am talking about, I haven't had personal experience with this particular product.)

It enables using a SATA HDD on a parallel cable with this (or in cases where there are unused IDE HDD's and spare SATA ports, the reverse). At least I think that is how this product is used. Please correct me if wrong.

---

### Post by sandyd on 2014-03-02
If you have PCI-E ports, you can get a PCIE sata card as well - something like
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816124064](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124064)

---

