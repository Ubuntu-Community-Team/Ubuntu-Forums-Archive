---
title: "unable to install ubuntu in dual boot mode with win 7"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by idom on 2012-09-22
Hi 

I have toshiba Z835 and I am trying to install ubunut 12.04 along side 
windows. It has only 128 GB.

I shrunk the main partition of windows and partition table is attached. now I have 50GB space where I can install ubuntu. however it is refusing to take that option.

Please advise..

I have tried resizing partition inside windows and as well as while installing ubuntu and still it says 50GB is unusable.
idom

---

### Post by krishna.988 on 2012-09-22
> **idom said:**
> Hi 

I have toshiba Z835 and I am trying to install ubunut 12.04 along side 
windows. It has only 128 GB.

I shrunk the main partition of windows and partition table is attached. now I have 50GB space where I can install ubuntu. however it is refusing to take that option.

Please advise..

I have tried resizing partition inside windows and as well as while installing ubuntu and still it says 50GB is unusable.
idom


In the 50 GB .. You'll have to add partition table and choose 2048 MB for swap area and the rest 48 GB as ext4 and choose / as mount partition and then click on ext4 partition and choose install

See these links for more info:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by NikTh on 2012-09-22
> **idom said:**
> Hi 

I have toshiba Z835 and I am trying to install ubunut 12.04 along side 
windows. It has only 128 GB.

I shrunk the main partition of windows and partition table is attached. now I have 50GB space where I can install ubuntu. however it is refusing to take that option.

Please advise..

I have tried resizing partition inside windows and as well as while installing ubuntu and still it says 50GB is unusable.
idom

Hi , 

the partition is unusable due to already 4 primary partitions you have. This is a restriction when use MBR (msdos). 

So you must boot in Windows again and convert this partition to EXTENDED. Then you will be able to create as many logical (and not primary) partitions as you want and you will install Ubuntu without a problem. 

Thanks

---

### Post by coffeecat on 2012-09-22
> **idom said:**
> 
I shrunk the main partition of windows and partition table is attached. now I have 50GB space where I can install ubuntu. however it is refusing to take that option.

That is because you have four primary partitions with an mbr partition table. Four is the maximum. If you can remove one primary partition, you will be able to create an extended partition. An extended partition is simply a special type of primary used only as a container for so-called logical partitions. You can create as many logical partitions within the extended as you need. (There is a theoretical limit, but much larger than you'll ever need.)

You'll need to give us more information on what those four partitions are before you can decide which (if any) is safe to delete. Do you know what the "unknown" sda3 partition is?

Open Gparted in the live session and take a screenshot by pressing alt+Prtscr. Post the screenshot. It gives more information than the installer window.

---

### Post by idom on 2012-09-22
> **coffeecat said:**
> That is because you have four primary partitions with an mbr partition table. Four is the maximum. If you can remove one primary partition, you will be able to create an extended partition. An extended partition is simply a special type of primary used only as a container for so-called logical partitions. You can create as many logical partitions within the extended as you need. (There is a theoretical limit, but much larger than you'll ever need.)

You'll need to give us more information on what those four partitions are before you can decide which (if any) is safe to delete. Do you know what the "unknown" sda3 partition is?

Open Gparted in the live session and take a screenshot by pressing alt+Prtscr. Post the screenshot. It gives more information than the installer window.

Attached is the screen shot. In windows it shows as hibernate partition.
now what should I do

I don't need the recovery partition as well as hibernate partition. I will be perfectly ok not to hibernate windows as I will be mostly using ubuntu only.  Can I just go ahead and delete those partintions ? 

Please advise.

---

### Post by newb85 on 2012-09-22
sda4 is the recovery partition your machine's manufacturer put on there.  Usually, the manufacturer gives you the option of creating recovery discs (probably DVDs) which you could use instead of sda4.  If you've created said discs, sda4 would be a prime candidate for removal.

Edit: oops, sorry, didn't notice you already knew this.  ;)

sda3 might be your Windows swap space, but I don't know that for sure.

---

### Post by coffeecat on 2012-09-22
> **idom said:**
> Attached is the screen shot. In windows it shows as hibernate partition.
now what should I do

I don't need the recovery partition as well as hibernate partition. I will be perfectly ok not to hibernate windows as I will be mostly using ubuntu only.  Can I just go ahead and delete those partintions ? 

To be honest, I've not had experience of a Windows hibernate partition. That's new on me. My Windows systems have always hibernated to a hibernation file within the C: partition. If you delete that partition it's possible that Windows will throw some errors, even if you never hibernate. You might want to research that.

The HDDRECOVERY partition is probably a partition from which you can set the computer back to its factory state by re-installing Windows. Before you delete it, I suggest you create a set of recovery DVDs. Most manufacturers include a utility to create the DVD set.

---

### Post by NikTh on 2012-09-22
It is not necessary to delete anything. You can install Ubuntu as it is. The only change you must make is the conversion of 50GB partition to Extended. 

Gparted is unable to create the partition cuz an Extended partition is a Primary partition too.  

So boot in Windows and use this free tool ==> [http://www.partitionwizard.com/download.html](http://www.partitionwizard.com/download.html)
to convert the 50GB partition to Extended. The conversion will take place during boot , cuz the filesystem must be UN-mounted. 

Thanks

---

### Post by idom on 2012-09-22
> **coffeecat said:**
> To be honest, I've not had experience of a Windows hibernate partition. That's new on me. My Windows systems have always hibernated to a hibernation file within the C: partition. If you delete that partition it's possible that Windows will throw some errors, even if you never hibernate. You might want to research that.

The HDDRECOVERY partition is probably a partition from which you can set the computer back to its factory state by re-installing Windows. Before you delete it, I suggest you create a set of recovery DVDs. Most manufacturers include a utility to create the DVD set.


I already have recovery USB created. so I guess I can delete that and hibernate partition I will do research and see.

---

### Post by idom on 2012-09-25
> **idom said:**
> I already have recovery USB created. so I guess I can delete that and hibernate partition I will do research and see.

I could not delete hibernate partition either in windows or linux.
I deleted recovery partition and installed ubuntu and now with dual boot it 
is working

idom

---

