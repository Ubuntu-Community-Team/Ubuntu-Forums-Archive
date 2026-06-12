---
title: "Overwrote my Win OS"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by tilai on 2008-08-25
More of a comment than a question.

I wanted to install Ubuntu on a dual-boot basis, and ended erasing the whole Windows OS. When I was got to the partitioning stage (4 of 7?) I clicked on the first option where it automatically allocates space to Ubuntu. However, I didn't realise that you had to slide the memory size to get space for the file system. I saw no mention of file system/dvsa on the screen at the time :(

I saw Windows (XGB), free space (Ubuntu 30GB) and assumed it was the 'first' part in accepting to use the free space for Ubuntu. I clicked Forward/Ok. It said 'too small'. I thought it strange that 30GB is not big enough but still persisted in trying to install it.

That's when it wiped out what was the C drive.

I am a dumb noob, although I did use Ubuntu 'successfully' a couple of years ago. But at that time I had already created a separate partition for Ubuntu.

I will try using vlmware later. Hopefully I can install windows again as there are certain apps that I prefer to use on that OS.

---

### Post by kansasnoob on 2008-08-25
What's your question?

---

### Post by SunnyRabbiera on 2008-08-25
> **kansasnoob said:**
> What's your question?

I think he is wondering if he wiped off XP, it happens to newcommers thats why its best to read installation guides all the way through.

---

### Post by RuleMaker on 2008-08-25
Ok, it's good that you mentioned this, but it's not the fault of ubuntu, you wasn't careful.
Next time choose manual partitioning and everything will be fine.

---

### Post by cybrsaylr on 2008-08-25
I've done the same in the past. Its' a common problem and the directions are confusing when you are only used to Windows. It took me awhile to understand the linux way of doing things and now I seldom use Windows.

---

### Post by tuxxy on 2008-08-25
I dont know if you lost data but you could say it was a good thing to get rid of windows and virtualbox will run it fine anyway.

---

### Post by tilai on 2008-08-25
> **SunnyRabbiera said:**
> I think he is wondering if he wiped off XP, it happens to newcommers thats why its best to read installation guides all the way through.
I did read about needing to have a file system and a swap partition. I just thought that I was choosing the free space to install Ubuntu (it said Free space Ubuntu!) when Ubuntu is not actually being installed just on that free space. I thought it was first select the space to be used for Ubuntu, then will select the file systme partition and finally the swap partition on a step by step move... never mind I don't really know what I'm talking about myself. I wrote the initial post out of sheer annoyance at what happened.

---

### Post by Ebritno on 2008-08-26
I had  done something not as crutial but similar twice with my ipod video. I had forgtten to unplug it during both a windows reinstallation and a ubuntu reinstallation. no Idea exactly why it happened but i lost all my data on it and i had to reformmat it with itunes... didn't really matter though i had most my music on my iphone and was using my ipod video to store other files that at both times amounted to but an hour of redownloading software executables or debian packages online and the real important stuff was either backed up or borrowed from a friend who had a copy :)

---

### Post by BGFG on 2008-08-26
Are you sure you deleted your win drive ? If you open gparted in ubuntu 
System>>Administration>>Partition Editor is there any mystery NTFS partition in there ?

---

### Post by Gregmond on 2008-08-26
> **BGFG said:**
> Are you sure you deleted your win drive ? If you open gparted in Ubuntu 
System>>Administration>>Partition Editor is there any mystery NTFS partition in there ?

I tend to use Partition Editor to configure my partitions first anyway, just seems easier to me. Only issue I have with it is, if you mount NTFS/Fat32 drives you may have to CTRL+ALT+BACKSPACE and re-log into the desktop to unmount them.

As for the comment about using VM to run XP, well thats good if you don't need 3D/Directx etc. No VM I know of will do that so Games etc that can't be run via WINE/CEDEGA/Whatever need an XP install.

---

