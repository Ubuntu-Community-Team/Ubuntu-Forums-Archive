---
title: "Dual boot XP / Ubuntu partition question"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by noiseordinance on 2008-04-25
Hi there, I'm trying to find a thread on the following topic but I can't seem to find one.

I'm trying out 8.04 on my Dell Vostro 1500 laptop. My 150GB drive is partitioned as follows:

/dev/sda1 ntfs 104855MB (This is my XP partition)
/dev/sda5 ntfs 26213MB (This is to become my Ubuntu partition)
/dev/sda6 fat32 28961MB (This is my storage partition to be accessible with both XP and Ubuntu)

My question is this: How to I prepare the Ubuntu partition? If I select /dev/sda5 and choose "forward" it says "no root file system is defined." What is the best way to set this partition up for Ubuntu? Do I delete it and create a new partition with the free space? Any help would be great. I'm a total newb...

Thanks!

---

### Post by Monicker on 2008-04-25
Delete the ntfs partition (/dev/sda5).  Then Ubuntu will see it as free and automatically want to use that for its install.

---

### Post by noiseordinance on 2008-04-25
Ok, I deleted it. Of course I can't move forward still without making a new partition out of the free space. Should I keep it as follows?

Type of new partition: Logical
New partition size: 26213 (entire space of partition)
Location for new partition: Beginning
Use as: Ext3 journaling file system
Mount point: [blank]

---

### Post by axor1337 on 2008-04-25
you want to set the Ubuntu part as ext3  and then set its mount point to "/" that means root. as for the shared space you don' need it Ubuntu will read ntfs parts what you do need is a swap part  Ubuntu uses this like the page file in windows i recommend twice the size of the ram you have

---

### Post by Monicker on 2008-04-25
Change the mount point to /

After that, you should be fine.  You really don't need to create a partition there, because Ubuntu installer searches for unused space.  It won't hurt either, but its something I usually let the installer do.

---

### Post by noiseordinance on 2008-04-25
> **axor1337 said:**
> you want to set the Ubuntu part as ext3  and then set its mount point to "/" that means root. as for the shared space you don' need it Ubuntu will read ntfs parts what you do need is a swap part  Ubuntu uses this like the page file in windows i recommend twice the size of the ram you have

how do i set up the swap partition? that makes me think that i shouldn't use the entire 26213MB for ubuntu... I have 2GB of RAM, so what you're saying is I should make a 4GB swap partition... 

So if I understand this right, should I make a logical partition that is 22213MB using Ext3 and / as the mount point, then a second logical partition using 4000MB set as "swap area" and / as the mount point?

---

### Post by friendofpugs on 2008-04-25
I just did this and I recommend that you let the Ubuntu installer handle all the swap partitioning from the install screen. Once you select "install from largest free partition" the installer will create a swap partition automatically, as part of the installation process. Just clear a space for Ubuntu to install itself and it will do the rest. Cheers!

---

### Post by noiseordinance on 2008-04-25
For some reason, when I select "Guided, use the largest continuous free space" is says that there isn't enough space. It's trying to use the 8MB of free space on my disk that Windows XP left...

---

### Post by noiseordinance on 2008-04-25
In fact, even though I deleted the 26GB NTFS partition, when I hit back to use the free space, and then went back to manual, the 26GB NTFS partition is back.... I think I need to manually set this thing up...

---

### Post by Monicker on 2008-04-25
If you created a partition after deleting /dev/sda5, then there actually isn't any free space for it to use.  Which is why I recommended letting the installer handle it.  You can still delete the partition from within the installer and then let it use it.

---

### Post by noiseordinance on 2008-04-25
Let me rephrase what is happening...

I select manual, I delete the 26GB NTFS partition. It lists it as free space. Then, I hit back, and let Ubuntu install on the most continuous free space. It says there isn't enough free space. I go back to manual, and the free space has been re-converted to NTFS.

---

### Post by Paqman on 2008-04-25
> **noiseordinance said:**
> I have 2GB of RAM, so what you're saying is I should make a 4GB swap partition... 


If you want to be able to hibernate your machine then create a 2GB swap. Otherwise 1GB is plenty (more than enough, in fact)

---

### Post by noiseordinance on 2008-04-25
> **Paqman said:**
> If you want to be able to hibernate your machine then create a 2GB swap. Otherwise 1GB is plenty (more than enough, in fact)

I definitely want to hibernate my machine. How do I create this swap partition? I was inquiring at the beginning of this thread but someone said let Ubuntu do all the partitioning, which is doesn't appear to want to do...

Thanks for everyone's help, btw.

---

### Post by Paqman on 2008-04-25
> **noiseordinance said:**
> I go back to manual, and the free space has been re-converted to NTFS.

Have you hit "apply" after queuing up your changes? The partition manager doesn't actually make any changes until you tell it you're ready.

---

### Post by sandysandy on 2008-04-25
have a look at these sites

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.linux.com/feature/114157](http://www.linux.com/feature/114157)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by noiseordinance on 2008-04-25
> **Paqman said:**
> Have you hit "apply" after queuing up your changes? The partition manager doesn't actually make any changes until you tell it you're ready.

There is no apply. I choose the partition, I hit delete, it immediately scans the disk and applies the changes and suddenly, my NTFS partition is free space.

---

### Post by sandysandy on 2008-04-25
see the links above.

regards

---

### Post by noiseordinance on 2008-04-25
> **sandysandy said:**
> have a look at these sites

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.linux.com/feature/114157](http://www.linux.com/feature/114157)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

Hmm, I appreciate the links. Unfortunately, it appears as though the first three assume I want to resize the XP partition, and I don't understand the last link.

---

### Post by Paqman on 2008-04-25
> **noiseordinance said:**
> There is no apply. I choose the partition, I hit delete, it immediately scans the disk and applies the changes and suddenly, my NTFS partition is free space.

If you're using Gparted "apply" is at the top of the window, next to "undo".

---

### Post by noiseordinance on 2008-04-25
Ok, so I followed sandysandy's second link and guestimated some partitioning. This is how I have it set up:

/dev/sda1 ntfs 104855MB (XP Partition)
/dev/sda6 ext3 / 3997MB
/dev/sda7 ext3 /home 20003MB
/dev/sda8 swap 2212MB
/dev/sda5 fat32 28961MB
free space 8MB

If I understand this correctly, this would be a good configuration to allow me to have both Ubuntu and XP, whilst have a FAT32 drive to share files (I know, I could share files by storing them on Ubuntu, but I just feel more comfortable this way) and having the /home and / separate so that I can upgrade Ubuntu versions later, yes? Can someone please tell me if this is a decent setup?

Thanks!

---

### Post by sandysandy on 2008-04-25
increase root to about 8 gb.

also fat 32 is just not required, as ubuntu 7.10 and later can read and write to NTFS. so u can convert FAT 32 to NTFS.

regards

---

### Post by Paqman on 2008-04-25
Looks good. I'd personally go for a bigger root partition, 4GB is a little tight. You might need extra space for temp files during operations like copying DVDs.

/home probably won't need to be anywhere near 20GB if you're not using it to store data. I'd chop 10GB off that and give it to root.

You shared data partition doesn't _have_ to be FAT32 either. NTFS is a much better file system.

---

### Post by noiseordinance on 2008-04-25
> **sandysandy said:**
> increase root to about 8 gb.

also fat 32 is just not required, as ubuntu 7.10 and later can read and write to NTFS. so u can convert FAT 32 to NTFS.

regards

Thank you very much. I appreciate your help! I only used fat32 cause 7.04 didn't see my NTFS partition that I shared files with.

---

### Post by noiseordinance on 2008-04-25
It's finally starting to install after much newbiness. Will this automatically install the grub loader?

Thanks. :)

---

### Post by Paqman on 2008-04-25
> **noiseordinance said:**
> Will this automatically install the grub loader?

Yep! Glad you've got it sorted.

---

### Post by axor1337 on 2008-04-25
I would scrap the fat 32 part use ntfs  once ubuntu is loaded youacan add ntfs read write support if works much better ubuntu can be hit or miss with fat 32
any q's im me aim [COLOR="Yellow"]axor1337[/COLOR]

---

