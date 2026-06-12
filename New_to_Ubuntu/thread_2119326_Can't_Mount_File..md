---
title: "Can't Mount File."
date: 2013-02-23
forum: New to Ubuntu
---

### Post by jiffylube58 on 2013-02-23
Hi Everyone,

I've been browsing through the forums and couldn't find an exact solution for my issue. I have a Samsung N150 that I booted using Ubuntu 12.10. Upon trying to access my files in my hard drive, I got the 

"Unable to Mount Location" Can't Mount File error. 

It's a miracle I got Ubuntu to boot up at all. Any help would be greatly appreciated.

---

### Post by DuckHook on 2013-02-23
Hi, and welcome to the forums.

No way to help without much more info. Please look through [this]("http://ubuntuforums.org/showthread.php?t=1422475") sticky at top of forum page and provide info it asks for. In your specific case, you must also tell us what type of file you were trying to access, where it is on your disk, etc.

On a more general note, your netbook is drastically underpowered for a full Ubuntu 12.10 install. You would be much better off with one of the lighter weight distros like Lubuntu. You will likely not enjoy your Ubuntu experience long-term whereas Lubuntu will be fast and responsive.

---

### Post by jiffylube58 on 2013-02-23
Thank you for replying. I'll try to add as much information as possible per the link you sent.

**Level Of Experience:** Super Beginner. This is my first time using Ubuntu.

**Topic of Problem:** My computer wasn't shut down properly and the next time I tried to start it back up, it posted an error saying "Operating system not found". I want to retrieve a folder of photos (I believe JPG) from my desktop before I set the netbook back to factory standards. 

**How I installed Ubuntu: **Being a Netbook, there is no CD drive, so I booted Ubuntu using a USB. I have not downloaded Ubuntu on the netbook yet, I did this primarily to retrieve some files I had on my desktop.

**Netbook Information:**
Samsung N150
I hope the rest of the information is in the photo below. I can't access the internet with the netbook right now, so I took a photo with my phone. The photo should be attached to this post.

Thanks again for your help!

---

### Post by fdrake on 2013-02-23
let's first get your pics backed up and then we can try to fi your ubuntu install.
using the ubuntu USB install , press ctrl + alt + t ant type into the terminal:
```

sudo fdisk -l

```

---

### Post by jiffylube58 on 2013-02-23
Hi fdrake thanks for your input.

I typed in what you said, and this is what was displayed. (picture attached)

---

### Post by fdrake on 2013-02-23
to mount your hard disk type:
```

mkdir /mnt/vfat
sudo mount /dev/sdb1 /mnt/vfat
sudo nautilus /mnt/vfat

```

---

### Post by jiffylube58 on 2013-02-23
@fdrake So I gave that a shot, but it looks like I don't have permission to make that directory.

---

### Post by fdrake on 2013-02-23
> **jiffylube58 said:**
> @fdrake So I gave that a shot, but it looks like I don't have permission to make that directory.

try "sudo mkdir /mnt/vfat"

---

### Post by jiffylube58 on 2013-02-23
OK so I typed it in with and without the quotation marks and this was what I got.

---

### Post by fdrake on 2013-02-23
you have to follow my other 2 commands

---

### Post by fdrake on 2013-02-23
are you getting some errors?

---

### Post by steeldriver on 2013-02-23
Am I missing something - or is fdisk only seeing the live USB (16GB fat32)?

---

### Post by jiffylube58 on 2013-02-23
Ah sorry about that. OK I added the other 2 commands. 
In the vfat folder, I see the files that are located in my USB drive, not the internal hard drive.

---

### Post by jiffylube58 on 2013-02-23
@Steeldriver

I think you're right. That is the USB drive I booted Ubuntu from.

---

### Post by fdrake on 2013-02-24
> **jiffylube58 said:**
> Ah sorry about that. OK I added the other 2 commands. 
In the vfat folder, I see the files that are located in my USB drive, not the internal hard drive.

i am sorry . I was busy helping other and I totally lost the problem of this thread. Yes I made you mount by mistake your usb. I did not notice that. Too distracted.

---Anyway this is the status:

Your notbook(or at leas for what we know it is only UBUNTU) does not seee any internal HDD.

---What to do?

you can still do few things. 
1-check the bios and see if the hdd is present in there.

2-you said in the first post that you where able to boot into ubuntu (even with some problems). That would be more than enoguht.

3.check that the driver is not disconected from the connector. Sometimes moving and carrying the notbook around does casue this problems.

----------------------------------------------
keep us posted and let us know how it goes.

---

### Post by jiffylube58 on 2013-02-24
@fdrake That's alright I appreciate the help.

I checked the BIOS before, the hard drive can be seen there.
It can be seen in Ubuntu as well. In the Computer section, I could see the 160 gb internal hard drive. It was only when I clicked on it to try to open it, when I received the Can't Mount File error.

So essentially, it looks like I can see it, and it doesn't look like a connection problem. I just can't open it.

---

### Post by DuckHook on 2013-02-24
If the partition is corrupted, it won't mount or show on fdisk and will firstly have to be repaired.

Some of us just assumed that you are trying to recover a previous Ubuntu install, but are you actually trying to recover a Windows OS? This is a very significant distinction that you must tell us about. If so, then the best tools for Windows partition recovery are Windows tools. See [this]("http://ubuntuforums.org/showthread.php?t=2116091&highlight=corrupted+windows+partition") thread. Recovering from a corrupted Ubuntu partition can be done following [these]("https://help.ubuntu.com/community/DataRecovery") instructions.

It's sadly after the fact, but the best way to recover from bad stuff like this is to backup your data.

---

### Post by jiffylube58 on 2013-02-24
@Duckhook 

Ah I'm really sorry I didn't know what information to put on here. I was just trying to recover some photos from my hard drive, and my netbook was running a Windows OS at the time.

Backing stuff up is something I do regularly now, sadly after this incident had already occurred.

---

### Post by DuckHook on 2013-02-24
> **jiffylube58 said:**
> ...I'm really sorry I didn't know what information to put on here

No worries at all. It wasn't meant as any sort of reproach (it's too bad tone doesn't come across well in forums). Try the techniques in the linked threads. If you have any questions or problems, we are all more than willing to help.

---

### Post by bijupp on 2013-02-24
I do not have much expertise in ubuntu but my suggestion is that

Please check whether the windows is hybernated.  if not check for errors with chkdisk and try.. 

in ubuntu latest versions have much problem with accessing windows drives if you have time try other distributions like linuxmint, zorin, Lubuntu, Kubuntu etc.  that might solve your problem...

---

### Post by fdrake on 2013-02-24
> **DuckHook said:**
> If the partition is corrupted, it won't mount or show on fdisk and will firstly have to be repaired.

Some of us just assumed that you are trying to recover a previous Ubuntu install, but are you actually trying to recover a Windows OS? This is a very significant distinction that you must tell us about. If so, then the best tools for Windows partition recovery are Windows tools. See [this]("http://ubuntuforums.org/showthread.php?t=2116091&highlight=corrupted+windows+partition") thread. Recovering from a corrupted Ubuntu partition can be done following [these]("https://help.ubuntu.com/community/DataRecovery") instructions.

It's sadly after the fact, but the best way to recover from bad stuff like this is to backup your data.

yes, but fdisk should at least show the disk device. Nothing is showing up .
Cna you try with parted:
```

sudo apt-get install parted
sudo parted -l

```

just to add a note:

Try another distribution / linux mint/fedora live disk and see if that shows up

Check that your bios has an option to enable or disable you internal hdd/ssd.
.........................................................
can you also provide the out put of these comands:
```

lshw | less

```

---

### Post by DuckHook on 2013-02-24
> **fdrake said:**
> yes, but fdisk should at least show the disk device...

Did not know this. I thought fdisk had to read its info from the partition table and no partition table means no info. But disk info may be from another source. Interesting.

@OP

According to some [reports]("http://www.kubuntuforums.net/archive/index.php/t-58445.html"), Ubuntu has problems recognizing some HDDs based on bioses, type of drives and type of connections. I know this doesn't help your current situation, but as per my link, you may be better off trying to recover Windows data/partitions with Windows utilities. The comments by *@Mark Phelps* in the earlier linked thread may help.

---

### Post by fdrake on 2013-02-24
> **fdrake said:**
> yes, but fdisk should at least show the disk device. Nothing is showing up .
Cna you try with parted:
```

sudo apt-get install parted
sudo parted -l

```

just to add a note:

Try another distribution / linux mint/fedora live disk and see if that shows up

Check that your bios has an option to enable or disable you internal hdd/ssd.
.........................................................
can you also provide the out put of these comands:
```

lshw | less

```

just quoting myself to update the changes in my post

---

