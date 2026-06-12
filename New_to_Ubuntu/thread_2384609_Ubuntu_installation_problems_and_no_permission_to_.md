---
title: "Ubuntu installation problems and no permission to view fix in forum"
date: 2018-02-09
forum: New to Ubuntu
---

### Post by alexdb9 on 2018-02-09
Hello, I am new to the forums and am amateur ubuntu user. I am having trouble reinstalling Lubuntu 17.10.1 on my Lenovo Ideapad 100S. 
I was already using Lubuntu 16.X until i updated recently and then the machine wouldn't start. Trying to reinstall the newer version (17.10) would give me 
"Warning: Source ID XXXXX was not found when attampting to remove it Glib.source_remove(self.xxx_id)"

When I looked it up, i thought it was due to insufficient space.The notebook only has a 32GB emmc drive. So i used gparted to delete all partitions and leave unallocated with the  exception of the EFI System Partition (used to have windows 10). After i tried installing, the same error occured. 
I also tried creating the two logical partitions for / and /home and linux-swap as suggested by a thread but the same error occured.

Finally, i tried following a different thread (solved) on this forum but i cant access the page because i do not have less than 10 posts.
Thread: [https://ubuntuforums.org/showthread.php?t=2351579](https://ubuntuforums.org/showthread.php?t=2351579)
Solution: [https://ubuntuforums.org/showthread.php?t=1543006&page=170&p=13603417#post13603417](https://ubuntuforums.org/showthread.php?t=1543006&page=170&p=13603417#post13603417)

Thanks in advance for your help.

---

### Post by coffeecat on 2018-02-09
> **alexdb9 said:**
> Finally, i tried following a different thread (solved) on this forum but i cant access the page because i do not have less than 10 posts.

Welcome to the forum.

Please re-read the error message you saw. Fewer than 10 posts is only one of several reasons given for not being able to access that page. The real reason you can't see it is that the post has been jailed. Don't worry - you haven't missed anything. The identical information is in the quote box of the last post in your first link. You will be able to read the first link.

---

### Post by alexdb9 on 2018-02-09
Hi, thank you for the reply. I managed to solve it but I'm not entirely sure why. I will post what I did in case of a similar problem.

Some background. The device already had Windows 10 pre installed when i bought it. I figured i should dual boot in case i wanted to use windows. The installation went fine but later on i wanted to erase windows as it was taking a large amount of space (only had 32 GB emmc). So i formatted the windows partition and added to my /home

Fast forward to recently. I wanted to reinstall Lubuntu but everything i tried gave me the source id error. In BIOS I disabled Secureboot set boot mode to UEFI, as mentioned in first link, however i couldn't find TPM firmware. Later when i tried to install, on the Installation type menu i chose "Something else" instead of "Erase disk and install ubuntu. Later on the partitioning menu i chose "New Partition Table". I created two logical partitions with ext4 (/ and /home) and pressed continue. Later a prompt would ask something about Force UEFI installation. I clicked continue and then the installation completed in 2 minutes.  Later i restarted the laptop and noticed that something was wrong. I booted the liveUSB, tried installing again and this time chose "Erase disk and install Ubuntu". The Force UEFI installation prompt appeared again, i clicked continue and after a successful installation, i now have a working Ubuntu machine. Finally.

Sorry if description is long and arduous, i hope someone with a similar problem might find this useful. Before you try though, i suggest you look into the force UEFI installation and make sure it will not create any problems to your machine. 
I suspect the EFI System Partition had something to do with it and it was overwritten when i created a new partition table. This would not make a working ubuntu installation so when i tried to install it with "erase disk and install", the EFI partition was rewritten and is now working correctly. Please don't take my suspicion at heart, i am only a beginner and don't know much.

---

### Post by sliser on 2018-02-09
Yeah, I think I am in the same situation. Thanks for the alternative forum, much appreciated.

---

### Post by TheFu on 2018-02-14
So, 2 partitions are not sufficient for UEFI.  For your desired configuration, 4 would be the minimum.  Thanks to GPT partitioning (not MBR/MSDOS), 4 partitions isn't a max limit anymore.

Assuming 32G total storage available .... 

* Tiny FAT partition for UEFI code/boot code (100MB). This is shared by all OSes.
* / - ext4 partition (15-25G); this leaves plenty of room for the OS and lots of apps
* Linux swap (4.1G)  Whenever running a desktop OS, a tad over 4G of swap is needed regardless of RAM. The old rules for 2x memory don't work.  2G RAM systems need the headroom.  4G RAM systems need the headroom.  For systems with more than 6G-64G of RAM, providing too much swap is a waste unless you have very specialized needs.
* /home - ext4 partition (whatever is left).

If you don't install lots of GUI applications, then / can be much smaller.  If you try out many different DEs, then you'll be fine. If you remove packages that aren't used every 3+ months, you can easily have all that you want in 15G.

However, the real power-user method would be to use LVM which allows great flexibility in adding storage where it is needed at the cost of complexity.  LVM changes the rules, so don't just "choose it" blindly. "With great power comes great responsibility." Using LVM is like that, because you can shoot yourself in the foot, arm, chest and head with it.

---

