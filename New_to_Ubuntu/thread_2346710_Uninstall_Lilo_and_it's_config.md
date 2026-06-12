---
title: "Uninstall Lilo and it's config"
date: 2016-12-17
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2016-12-17
While trying to remove ransomware from a friend's Win7 hdd, I had to install LILO and config it to get to the Win7 drive. I've removed the guy's user's stuff. I would now like to uninstall and de-config lilo (and ntfs-3g) **safely**, as LILO is running on my production box. 

I see that LILO runs before GRUB or that's the screen I'm seeing. Lilo's blue b.g., white letters and a chance to select Linux or Linux old as the OS. Other than it not being necessary, as I'm not dual booting, I would move towards less complication rather than more and that's the reason for this post.

---

### Post by #&amp;thj^% on 2016-12-17
[s]Never done this myself[/s]...but have a look here: [https://www.howtoinstall.co/en/ubuntu/trusty/lilo?action=remove](https://www.howtoinstall.co/en/ubuntu/trusty/lilo?action=remove)
EDIT: Just did this myself to show it works.
Here is how I reinstalled grub while booted to drive and OS I installed it to
First I removed Lilo..._**Do Not Reboot yet**_.
```
sudo apt-get purge --auto-remove lilo
```
_**Again Do Not Reboot yet**_.
Add Boot repair PPA:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
``` 
 
Then Update:
```
sudo apt update
```
Install Boot Repair:
```
sudo apt install -y boot-repair
```
Call Boot Repair:
```
boot-repair
```
wait for it to load..and_ Follow the on screen prompts_ which will go like this:
```
sudo dpkg --configure -a
```
```
sudo apt-get install -fy
```
Now remove grub:
```
sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
```
Now I just wanted to see if it did remove grub..so this step is optional.
```
sudo update-grub
```
Grub was not found.
Now Install Grub...you must know the disk you want to install it to...my case here was /dev/sda
```
sudo apt-get install -y --force-yes grub-pc linux-generic
```
Now we check again..and Update Grub:
```
sudo update-grub
```
And Now you can reboot or continue on with what you were doing

---

### Post by oldfred on 2016-12-17
You may want to install grub2 first or not reboot after removing lilo as then you may not have any boot loader.

ntfs-3g is a standard package. I would not remove it.

---

### Post by #&amp;thj^% on 2016-12-17
> **oldfred said:**
> You may want to install grub2 first or not reboot after removing lilo as then you may not have any boot loader.

ntfs-3g is a standard package. I would not remove it.

Just curious dose lilo remove grub2? He shows this "I see that LILO runs before GRUB"
But none the less installing Grub2 is a good tip.

---

### Post by oldfred on 2016-12-17
With BIOS only one boot loader can be in MBR. 
Not sure then how Lilo is configured. It uses boot flag where grub does not.
It could chain load to grub installed in PBR - partition boot sector, but grub2 does not like nor is it recommended to be installed to PBR.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Mark_in_Hollywood on 2016-12-17
I had a working grub2 in this 16.04 box. I saw that I had to install lilo to access the win7 drive which was connected to the Ubuntu computer via eSATA, just to mount the win7 drive. When I set the mount location to /home/user/Desktop, the day-to-day desktop vanished and yet I had access to the Win7 disk. On reboot LILO came up on it's own without user request/intervention.

```
mark@Lexington:~$ sudo dpkg -l | grep grub | grep ii
ii  grub-common                                           2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                                 0.7                                           amd64        GRUB gfxpayload blacklist
ii  grub-pc                                               2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                           2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                          2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader (common files for version 2)
```

---

### Post by oldfred on 2016-12-17
Lilo may then have just been on eSATA drive?
Do you still have grub then on you own drive's MBR, and then directly bootable if you choose that drive?

---

### Post by Mark_in_Hollywood on 2016-12-17
No, the eSATA was the Win7 drive.

Yes, as above:

```
mark@Lexington:~$ sudo dpkg -l | grep grub | grep ii
ii  grub-common                                           2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                                 0.7                                           amd64        GRUB gfxpayload blacklist
ii  grub-pc                                               2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                           2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                          2.02~beta2-36ubuntu3.2                        amd64        GRand Unified Bootloader (common files for version 2)
```

The LILO offers to boot from LINUX or LINUX-OLD. Doing nothing LILO counts down and boots. I'm being conservative and don't want to harm GRUB2 by removing LILO.

---

### Post by yancek on 2016-12-17
Lilo installs some code to the MBR (if you are using MBR on your drives?) which points to the /etc/lilo.conf file where boot entries similar to the grub.cfg file of Grub exist.  It seems to me that your simplest solution is just to install Grub to the MBR of the same drive overwriting the Lilo code in the MBR.  Lilo is just chainloading to the Grub of your Ubuntu install.

---

### Post by Mark_in_Hollywood on 2016-12-19
I will follow this post on reinstall of GRUB2.

As always: Thank you, Linux Community.

Case closed. (for now)

---

