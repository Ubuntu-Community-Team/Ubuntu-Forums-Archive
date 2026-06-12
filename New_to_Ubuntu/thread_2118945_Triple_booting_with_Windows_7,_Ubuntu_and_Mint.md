---
title: "Triple booting with Windows 7, Ubuntu and Mint"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by bentoman1974 on 2013-02-22
I am currently dual booting with Windows 7 and Ubuntu 12.10.  Is it possible to triple boot and add Mint?  If yes, then is it just a matter of doing the same steps involved with dual booting w/ Ubuntu and creating a partitioned swap drive or are there additional steps involved when adding yet another operating system?

---

### Post by oldfred on 2013-02-22
You can just install to another / (root) partition. If just testing that is all you have to do. Of course good backups are important with any system change.

But issues are which boot loader is in charge. Only one MBR so only one Boot loader. Ubuntu usually does not give a choice, default installs just install grub to MBR of sda, so manual install or Something Else (not sure how this is handled with Mint).

And if multi-booting where is data? I have many Ubuntu installs and used to have XP so I created a shared NTFS data partition and moved my Firefox, Thunderbird & Photos to that shared partition. Then my install of Firefox is changed to use the profile in the shared data and I have the same book marks in every system. I now do not boot XP and all new data is in a shared Linux formatted partition.

If Mint installs its boot loader to MBR and you want Ubuntu you should be able to boot Ubuntu from Mint and reinstall Ubuntu's grub to MBR.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

    
Often good to document system and uses a gui to reinstall grub.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by bentoman1974 on 2013-02-22
As of right now I seem to be spending most of my computing time on Ubuntu so most, if not all, of my data is kept there.  I only switch back to Windows for reasons related to media as I have yet to research options for video conversion on linux.  I don't have a real need for shared data right now and I only want to try Mint to experiment a bit so I'll partition a small part of my main drive and just install there.  I guess the issues you raise could become my own concerns as I become more familiar with all the operating systems, but I suppose that encountering such problems and learning how to solve them is part of this whole process.

---

### Post by DuckHook on 2013-02-23
> **bentoman1974 said:**
> ...I only want to try Mint to experiment a bit...

If only experimenting, consider a VM. I have numerous OSes installed as VMs and there is no better way to play with them. You can hack to your heart's content, break the system and recover easily by rolling back to the last good snapshot. Insanely useful.

Major Caveat: requires decently powerful system.
Minor Caveat: must install and set up VM software. Of course, once done, it is absurdly simple to try as many different flavours and distros as you like.

---

### Post by bentoman1974 on 2013-03-15
Thanks for the replies guys.  I ended up creating a third partition much like the way I did for my second Ubuntu 12.10 partition and that did the trick.  I'm fairly new to all this so it was actually more interesting when I decided to get rid of both partitions and install Ubuntu 12.04.  My intent was to delete the 12.10 partition, merge that back with my main Windows partition then install 12.04 over the one that I installed Mint on.  I did this under "My Computer" in windows and had assumed that once 12.10 was deleted the Mint partition would remain and its bootloader would automatically take over.  I'm not quite sure what happened but I think deleting the 12.10 also affected the Mint partition and made it no longer bootable.  I ended up then deleting that Partition and I think I now just had an unallocated space with no operating system on it what so ever.  At this point I wasn't even sure if Windows would boot back up if I restarted the computer.  I figured that if I installed 12.04 on the unallocated partition, then everything would boot properly.  Thank god I was right about that.  I suppose this is how most people learn and I probably have to risk messing up a few things here and there before I get the full hang of it, if ever.

---

### Post by oldfred on 2013-03-15
Glad it worked, but generally best to use Windows tools for Windows & Linux tools for Linux. And you need to know which partition the MBR refers to, to continue booting or else you get into trouble.

---

### Post by jemvyc on 2013-03-16
I guess I don't know enough about Linux and Grub to have been worried, but I have 3 computers running triple boot.  I just stuck the .iso disk in the drive and told it to put the operating systems in new partitions where they should not have done any harm and watched.  I have 2 systems with Ubuntu 12.10 and Mint 14 and Windows, one with W7 and one with XP.  Also I have a system with Ubuntu 12.10 and an old mint and Ubuntu 10.04 and XP.  I am currently trying to figure out how do delete an operating system without crashing everything.

Meanwhile, on each of the systems Grub offers me a list of operating systems, with the most recent installation defaulted.  It is a simple change to edit /etc/default/grub and correct the default to the op system you want to start automatically.

It does get to be a problem figuring out where the data went when you are changing things, but if you watch partition sizes you can identify which operating system is using which partition.

Jim

---

### Post by oldfred on 2013-03-16
When every you have more than one drive or operating system, it is best to run the BootInfo report from Boot-Repair or just the bootinfoscript which is part of boot repair.

       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
    
       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

