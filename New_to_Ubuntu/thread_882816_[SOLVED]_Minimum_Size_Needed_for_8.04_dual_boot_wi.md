---
title: "[SOLVED] Minimum Size Needed for 8.04 dual boot with Vista?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Levitation on 2008-08-07
So, I am very happy with 8.04, even the Broadcom Wifi card is working!

What is the *minimum* size I can safely use for the Ubuntu partition?

Thanks

---

### Post by tamoneya on 2008-08-07
I would recommend that you have at least 10 GB for / and then 2 GB or so for swap depending on how much RAM you have.  Then you will need to have space for your files.  As far as vista goes I wouldnt run vista with less then 30 GB.

---

### Post by snowpine on 2008-08-07
Sweet! I would recommend 4gb minimum--a full Ubuntu installation is a little over 2gb, and 4gb will give you some room to grow. 10gb would be ideal.

Now, what about your data and personal files? Will those live in your Vista, your Ubuntu, or on a separate data partition? Something to think about before you start partitioning...

---

### Post by Tom--d on 2008-08-07
I have 5GB parition for my /
1GB Swap
and the rest is /home

---

### Post by ayampanggang on 2008-08-07
> **snowpine said:**
> 
Now, what about your data and personal files? Will those live in your Vista, your Ubuntu, or on a separate data partition? Something to think about before you start partitioning...

I second that. Plan on how you will house your data before simply paritioning the hdd. Mind you if you house your data in your linux partition, windows won't be able to read it (CMIIW). So the best solution is to house the data in one separate partition with windows-readable format (ntfs or fat32).

---

### Post by Bucky Ball on 2008-08-07
> As far as vista goes I wouldnt run vista with less then 30 GB.Argh! My Vista folder is 5.6GB and the whole shebang, programs and all, is just over 15GB. 30GB seems awfully excessive. If there is something I am missing here, please explain. I agree, Vista is bloated, but .... ;)

---

### Post by Bucky Ball on 2008-08-07
My laptop:

The Vista Partition is 30GB but half empty -NTFS
Ubuntu partition 10GB -EXT3
/Home is 25GB - EXT3
/swap is 4GB
FAT32 partition for sharing between op systems is 10GB

... and this is all on one 80GB laptop hard drive ...

My personal opinion is horses for courses; it really depends on how you work (fr'instance which op system needs to access what kind of drive and how often, what information and how much needs to be accessed by which op system). 

Before I do installs, I like to sit down with a pen and paper, have a think and make a good plan that is going to work for me (or whoever might be using the machine I am setting up).

The result of 'sudo blkid' on my machine;

> /dev/sda1: UUID="FC42EAD442EA9326" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="653d41d1-f3d8-4e3c-8fdd-a298084b754c" 
/dev/sda6: UUID="36bd7710-ca84-48c9-9011-e96d336ba192" TYPE="ext3" 
/dev/sda7: UUID="4317640b-79fe-4ee4-a761-84f84991256e" SEC_TYPE="ext2" TYPE="ext3" LABEL="bigboy" 
/dev/sda8: UUID="4893-E3A6" TYPE="vfat" LABEL="FATSO" Sure you can match the sizes I've given with the file types.

/dev/sda6 is the Ubuntu install. Hope this gives you some ideas ... :)

---

### Post by tamoneya on 2008-08-07
> **Bucky Ball said:**
> Argh! My Vista folder is 5.6GB and the whole shebang, programs and all, is just over 15GB. 30GB seems awfully excessive. If there is something I am missing here, please explain. I agree, Vista is bloated, but .... ;)

microsoft itself recommends 20-40GB and if anything they are aiming low.
[http://www.microsoft.com/windows/windows-vista/get/system-requirements.aspx](http://www.microsoft.com/windows/windows-vista/get/system-requirements.aspx)

Im not saying it is impossible to do it with less but it can get really cramped really quickly if you try to squeeze it into a small space.

---

### Post by Bucky Ball on 2008-08-07
Now, I'm getting a little confused here and don't get me wrong ... :) but if the install and your programs come to 12GB say, isn't the stuff cramping you up the files you are creating, accumulating and storing on the *same drive/partition as your operating system*? ie you add them later.

Doing this is* never* a good idea (IMHO and regardless of OS). If Windoze crashes for some reason and you get blue screened, you effectively need to lose all your data (unless you've been very contientious) when you reinstall. Which is why it is never a good idea. Your personal data should be stored and address books, bookmark folders and everything else you can possibly set to do it should be aimed somewhere away from that partition/drive.

Something else to remember is when a hard drive crashes, it is normally as trivial as one bad sector. Which means that generally, the information on the partitions on that drive apart from the one that has crashed is usually retrievable (another reason to partition drives - that age old debate).

If you really want to be safe, have a partition set for only your operating system and programs (and some people don't even store programs on the same drive as OS for reasons of speed - multimedia/gamers) and store your personal data, files, folders etc somewhere else. Much simpler and safer in the long run, trust me. ;)

---

### Post by Levitation on 2008-08-07
Wow! Such rapid response.

Snowpine and Tamoneya:

I will be keeping my data on the Vista Partition and that is at 61 GB. The remainder is Ubuntu.

Can you explain what "Swap" is?

Also, why can't I see the Ubuntu partition from Vista (or can I in some place other than "Computer").

Thanks guys!:guitar:

BTW: RAM is just under 1GB AND I also have an USB 300+ GB Drive which I remember being able to read from when I had earlier Ubuntu install, but not able to write to (do I just need to change the permissions from Vista?).

---

### Post by Bucky Ball on 2008-08-07
Windoze (any flavour) cannot see EXT3 partitions at all. Just calls 'em healthy. If you go to;

Start->Control Panels->Administrative tasks (or tools, not sure)->Disk Management

... you will be able to identify by the sizes you have set, that is about all. :)

'Swap file' exists in Windoze and Ubuntu (or pagefile); when your ram overfloweth it goes to the page file. If you check in Windoze (from memory right click on 'My Computer', then Properties->Advanced->Virtual Memory I think! Somewhere there) you can check the size of the swap file and where it is.

For a better explanation of a swap file, go here:

[http://searchwinit.techtarget.com/sDefinition/0,,sid1_gci213077,00.html](http://searchwinit.techtarget.com/sDefinition/0,,sid1_gci213077,00.html)

One this to remember is that a swap file is *not* as fast as physical RAM, so don't get too excited! :)

---

### Post by snowpine on 2008-08-07
> **Levitation said:**
> Wow! Such rapid response.

Snowpine and Tamoneya:

I will be keeping my data on the Vista Partition and that is at 61 GB. The remainder is Ubuntu.

Can you explain what "Swap" is?

Also, why can't I see the Ubuntu partition from Vista (or can I in some place other than "Computer").

Thanks guys!:guitar:

BTW: RAM is just under 1GB

Swap is like virtual memory in windows; if you run out of ram, it stores it on the hard drive. 1 or 2 GB of swap should be plenty for your needs. It is an extra partition formatted as "swap". 

Someone else will give you a more technical response, but the bottom line is that Windows doesn't support the ext2/ext3 filesystems used by Linux. However, there are utilities you can get for Windows that get around this.

---

### Post by Bucky Ball on 2008-08-07
> **snowpine said:**
> there are utilities you can get for Windows that get around this.

Most of them dodgy from the fine print on the information I've looked at. If you could find an open source program supported by the Ubuntu Community it would be the go. But something that has never quite been conquered to this point. Anyone got any thoughts? Maybe there is something in Synaptic or Add/Remove? :(

---

### Post by tamoneya on 2008-08-07
> **Bucky Ball said:**
> Now, I'm getting a little confused here and don't get me wrong ... :) but if the install and your programs come to 12GB say, isn't the stuff cramping you up the files you are creating, accumulating and storing on the *same drive/partition as your operating system*? ie you add them later.

Doing this is* never* a good idea (IMHO and regardless of OS). If Windoze crashes for some reason and you get blue screened, you effectively need to lose all your data (unless you've been very contientious) when you reinstall. Which is why it is never a good idea. Your personal data should be stored and address books, bookmark folders and everything else you can possibly set to do it should be aimed somewhere away from that partition/drive.

Something else to remember is when a hard drive crashes, it is normally as trivial as one bad sector. Which means that generally, the information on the partitions on that drive apart from the one that has crashed is usually retrievable (another reason to partition drives - that age old debate).

If you really want to be safe, have a partition set for only your operating system and programs (and some people don't even store programs on the same drive as OS for reasons of speed - multimedia/gamers) and store your personal data, files, folders etc somewhere else. Much simpler and safer in the long run, trust me. ;)

I agree.  I do this with my linux partitions but I dont trust vista to manage to understand something as complicated as a partition.  I just prefer to maintain disk images which work better anyways since that way whether it is one small sector or a full blown head crash that scrapes up the entire disk I can just reimage a new disk and I dont even need to install the OS.

---

### Post by Bucky Ball on 2008-08-08
Neat, Tamoneya. Never thought of it. I'm going to have a look at how to do that a bit later. Thanks!

Just wondering though; how often would you make a backup disk image? I like the idea for once a week data backup, or even once a day if you are creating a lot of data or working on something major. Is there a way of automatically creating a disk image of your data drive/partition when you log out/shut down? Or once an hour?? Might take a bit of time, only problem. Either way, does limit how much you lose (not 2 years worth of data if you are diligent).

I think a combination of both our methods would provide pretty good data security! ;)

---

### Post by tamoneya on 2008-08-08
> **Bucky Ball said:**
> Neat, Tamoneya. Never thought of it. I'm going to have a look at how to do that a bit later. Thanks!

Just wondering though; how often would you make a backup disk image? I like the idea for once a week data backup, or even once a day if you are creating a lot of data or working on something major. Is there a way of automatically creating a disk image of your data drive/partition when you log out/shut down? Or once an hour?? Might take a bit of time, only problem. Either way, does limit how much you lose (not 2 years worth of data if you are diligent).

I think a combination of both our methods would provide pretty good data security! ;)

Well the simplest way is to just have one drive allocated for backups and just go like this : dd if=/dev/sda of=/dev/sdb.  Then you automate it via a cron job.  So you could set it whenever you want.  And no matter how much data you have made it always takes up the same amount of space.  The only down side is that you cant revert to your backup from last week.  You can only use the most recent backup unless you use multiple drives and cron jobs.

---

