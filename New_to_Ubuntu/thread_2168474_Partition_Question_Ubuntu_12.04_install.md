---
title: "Partition Question Ubuntu 12.04 install"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by Andy_Browning on 2013-08-18
Trying to install Ubuntu 12.04LTS on a friends DELL Inspiron 5305.
The Windows OS is on dev/sda3, not dev/sda1.
How exactly would I go about resizing the Windows OS on dev/sda3 partition from 138.36GB to 78.36GB, leaving 60GB for the Ubuntu partition. I think I know how to do it, but I'm not 100% sure.

Note: I'm an overthinker, so I need as much details as humaly possible to give. The more detailed and exacting the info the better.

Thanks.

---

### Post by carl4926 on 2013-08-18
Assuming there isn't also a sda4? Because if there is. It would likely mean you already have 4 Primary partitions and would need to delete one.
But assuming sda3 is it and you have already defraged windows!, You can use the windows partition manager to shrink sda3 and leave free space as required. Be warned, it may not let you shrink it as much as you would like, which is why I use Gparted from a Parted Magic CD: [http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)
But I only ever take Half the Free space!
Once you have the free space, create a Extended partition to fill it all. You now create Logical Partitions in the Extended space.

If you are still unsure. Take a screenshot (PrtSc) of your HD in Gparted and post it here...

---

### Post by Andy_Browning on 2013-08-18
I tried Gparted thru Ubuntu 12.04LTS live first. When I try to resize the partition it wont allow me to unless I put 1-2 mib infront of the Windows partition. Is this OK?
Wouldn't worry at all if it was my own computer (I have plenty of rescue type cd's in my arsenal), but it being a friends I do not want to mess up.
Primary partitions are just the C: NTFS (138.96GB), the recovery NTFS(10GB), and a hidden partition FAT (47.03MB). No 4th primary, so I should be able to create an extended partition with a logic partition inside. 

I have never initially partioned a Windows partition that wasn't a dev/sda1, and have always used the suplied sliding partitioner from the first partition option. I have used the third option many times, but after having initially used the first option to create the extended partition with the logic, and swap, inside. Which reminds me: I also need to make the swap partition for a 3GB RAM system. What size swap would be optimal?

Note: Have been a member since middle of last year, but I could not get Ubuntu One to allow me to login with my login info from the forum, so I had to change everything in both (AndyOpie150).

---

### Post by carl4926 on 2013-08-18
You should contact a member of the Mod/Admin team about your account.

> [COLOR=#000000] it wont allow me to unless I put 1-2 mib infront of the Windows partition.[/COLOR]1-2MB of what?

Like I said, a screen would help

3GB RAM = 3GB swap IMO, but some would say 6GB swap. If you just use suspend and not hibernate 3GB will be fine

---

### Post by oldfred on 2013-10-16
Post these from terminal of liveCD, and/or as suggested above a screen shot from gparted.:

sudo fdisk -lu
       sudo parted /dev/sda unit s print

Use Windows disk tools to shrink Windows but it really wants 30% free space, so do not shrink too much. Then reboot into Windows so it can run chkdsk and make whatever repairs it does for its new smaller size.
Do not create any partitions with Windows as it will want to convert to dynamic which does not work with Linux and not even some Windows repair tools.

---

### Post by Andy_Browning on 2013-10-17
Thanks for all the help. Now I just have to wait and see if he want's to get ride of a whole lot of useless data. He has 100GB used out of 138GB (didn't realize this till now). I might end up putting Puppy on a stick for him.

---

### Post by Andy_Browning on 2013-10-18
Ended up putting LazY Puppy on a Flash Drive for his Desktop.
He now would like me to put Lubuntu 12.04 LTS or Ubuntu 12.04 LTS on his Toshiba Sattelite with the OS being on /dev/sda2.

Sorry, sorry, sorry. I was not aware that the 12.04 distros had a screen shot utility. DUH! Will pull head out, so I can see the light and check to see if Lubunt 12.04 has a screen shot utility (I think this is the one he would like the best since all he has known is Windows).

Might take a few days before I can get to his laptop again though.

---

