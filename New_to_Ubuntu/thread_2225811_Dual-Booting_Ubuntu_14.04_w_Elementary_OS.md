---
title: "Dual-Booting Ubuntu 14.04 w/ Elementary OS"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by HarryPannell on 2014-05-23
Hi, so as the title says, I'm wanting to dual-boot my Ubuntu 14.04 desktop with Elementary OS.

I have no experience with dual-booting any OS, so please go easy on me.

I'd prefer a step to step guide, rather than a huge paragraph so I don't get confused.

Thanks.

---

### Post by oldfred on 2014-05-23
One drive or two drives?
Post this:
sudo parted -l

You can share swap if you do not hibernate nor have encrypted /home. But do not share /boot. 
Often if booting both systems regularly a shared data partition also makes sense, even better than a separate /home but requires a bit more work to configure in both systems. I have same Firefox bookmarks, Thunderbird emails and Picasa photos in all my installs. Each app is installed in each system, but data is in one data partition.

How much space are you planning for Ubuntu and which boot loader do you want in the MBR as that will be first in grub menu and default boot.

---

### Post by LastDino on 2014-05-23
I think looking at my gparted screen-shot might help you as well.

[ATTACH=CONFIG]253396[/ATTACH]

I'm triple booting right now, as you can see I've only one swap (which is shared for all of my installed OS's), if you've separate /home; you may choose to share it with other distro's, as Oldfred pointed out, that will share all your software settings. However, I generally prefer to not do that and choose to install OS on separate 20GB partitions with SWAP being the only partition shared between OS's. 

Note: There is no need for separate /boot, so don't worry about it and the newer OS you install will be the one where you'll see boot flag as that is where your grub will be installed. You can change that later if you want to, so its nothing to worry about.
If you're using Dos partition table (like me)  which lets you keep only 4 primary partitions, don't worry, as you can see in screen shot my other OS are installed on partitions under Logical drive. However, if it is GPT, you need not worry about that.  

There is no real difference between installing process itself apart from partitions you picking to share and use. Also, it wont be possible to guide step by step, we would rather have you post whenever you face problem or are not sure about something during process.

Before doing any of this, please take back-up. Good luck!

---

### Post by HarryPannell on 2014-05-23
I am wanting around 30 GB for Elementary OS. I don't really care about having shared files, and I'd prefer if they were different as well. 

This is the result of the command 'sudo parted -l':

[I]Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4135MB  extended
 5      496GB   500GB  4135MB  logical   linux-swap(v1)


[/I]I really am not experienced at all with the partitions, and even this (^) is confusing me.

---

### Post by oldfred on 2014-05-23
You can just use gparted from Ubuntu live installer in live mode. Shrink the sda1 partition by 30GB. Create a new partition which will be sda3, they do not have to be in order on drive.

Then use Something Else to install. At partitioning screen in Installer which will be somewhat like gparted's screen click change and format as ext4, mount as / (root), you then have to decide which boot loader you want to be in charge. If you still want Ubuntu, just install grub to sda3. Normally we do not install grub to a partition but your Ubuntu install will boot Elementary also.

       And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
      
 
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I have several drives so I am installing into a partition that had an old install.
Grub boot loader shown at bottom defaults to sda, so it would be the boot loader in charge or first in menu you see. Otherwise change to new partition probably sda3.

---

### Post by HarryPannell on 2014-05-24
Thank you very much. Now just to wait for Isis to be released.

---

