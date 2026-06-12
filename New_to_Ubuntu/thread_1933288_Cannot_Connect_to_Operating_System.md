---
title: "Cannot Connect to Operating System"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by trealo on 2012-02-29
I am extremely new to Linux, and due to conflicts with Gateway and Windows vista decided to switch to Ubuntu. I played around with it while it was running on the disc and liked what I saw, so I installed the OS and removed Vista (It wouldn't boot off of Vista any ways). It wouldn't connect to the OS so I put the disc back in, and behold it could start up as long as I was using the disc. Went to re-install and it recognized that I already had the software on my hard drive, but it still won't boot unless I use the disc. I have the Ubuntu x64 and my system has these specs. 

Mobo: Gigabyte Z68MA
CPU: Intel i5 2500k 
Ram: Gskill 8g
PSU: Rosewill 550W
HDD: 7200 RPM 450GB (not sure of brand) 

Any help with this issue would be much appreciated

---

### Post by Bucky Ball on 2012-02-29
Disregard post #2. Reported.

Welcome. Now, let's get this straight. You have Windows installed? You are trying to install Ubuntu to a partition(s) on the hard drive side-by-side with Windows?

Or you have a Wubi disk and you are attempting to install that to a partition beside the Windows install? Not sure what's meant by 'It wouldn't connect to the OS'. What wouldn't?

Sorry, little confused. We need whether Wubi or Desktop disk you are using and what release; 11.10, 10.04 LTS. Please give a clear explanation of what you are attempting to do. ;)

---

### Post by trealo on 2012-02-29
I apologize for being unclear; I am using an Ubuntu 11.10 disc to start up and install. Windows Vista WAS on the computer, but I did a clean install of Ubuntu 11.10 and wiped Vista off because it was not compatible with the new motherboard I got. I simply want Ubuntu on the HDD as my OS and nothing else, but when I try and boot without the disc it never finds or connects to the OS, eventually leading to a blank black screen with a blinking underscore. 

Thanks in advance, 

Trealo

---

### Post by chipbuster on 2012-02-29
Erm...how did you remove Vista? I'm suspecting that whatever uninstall method you used went rogue and wiped the bootloader right now...although that's a really far-fetched guess based off of what we know.

Do you ever get to a GRUB screen when you boot without the disk? (my guess is not)

If not, boot into Ubuntu and install GRUB to your first hard drive. Unfortunately, someone else will have to help you with that (if it truly is the problem) because I've never figured out how to install grub properly..............

---

### Post by trealo on 2012-02-29
I let the Ubuntu install take care of it, I just ran the installation and let it do all of the work for me, I never un installed anything myself. What I did find out though is that my HDD is GPT partition style, I don't know if that makes a difference though.

---

### Post by MARP1961 on 2012-02-29
Good morning Trealo! If you have no data on your hard drive there is no harm in trying this installation again.

Insert and boot from your Ubuntu disk again. Select 'Install Ubuntu' and then select the option for manual partitioning 'Something Else'. The partition editor will show you the partitions already on the hard drive. You can click on each of them and delete them all if you have nothing on the hard drive that you want to keep. If you start from scratch with unallocated space, it might then be easier to think what you are doing.

You can then create **3  partitions **manually in the following way:

**15 GB    mount point /   ext4 journallng file system **  (This is for the Ubuntu system)
**2GB      SWAP**      ** partition  at the end **     (Having a 'Swap' helps installation and hibernation)
**Then all the rest in GB   mount point /Home   ext4 journaling file system** (This is a separate Home partition which will store your data and settings so that future reinstalls will be easier).

If you allow the system to install on the above partitions that you have created and it still won't boot then someone else will have to help you. Good luck!

---

### Post by Mark Phelps on 2012-02-29
> **appypaddy said:**
> I have use Ubuntu OS.It is totally different from other OS.But it is prevent virus.....

Both are not true ...

Ubuntu is not an OS, it is a distribution -- a collection of apps packaged with a Linux kernel.  And while it's somewhat different from others, given that there are nearly 400 Linux distros, there's no way Ubuntu could be TOTALLY different from all the otherws.

Also, Linux distros do NOT prevent viruses.  They are not antivirus agents.  And, they are also not immune to viruses.  While they don't get infected nearly as often as Windows OSs, that's primarily due to the extremely low incidence of Linux viruses in the wild.

---

### Post by Tyggna on 2012-02-29
It sounds like a BIOS/boot problem, rather than a Linux problem.  

(If he went through a clean install, Ubuntu would've put a bootloader on his MBR)

My guess is that your machine is not looking for a hard drive to boot off of.

You can check this by going into the bios.  Gateway says you can do this by hitting F1 or F2 on the keyboard repeatedly right after hitting the power button.

Inside your bios, look for something along the lines of "boot devices" or "boot order."  

Make sure your hard drive is on that list.  It'll might look something like HDD250GBSAMSUNG
Or something along those lines.  Common options that will appear on that list in addition to your hard drive is your optical drive, USB removable devices, and a network boot option.

Really, you just need to make sure your hard drive is appearing on the list.

---

### Post by grahammechanical on 2012-02-29
The OP has said this:

> What I did find out though is that my HDD is GPT partition style, I don't know if that makes a difference though.

And it does make a difference. See the link.

[http://msdn.microsoft.com/en-us/windows/hardware/gg463524]("http://msdn.microsoft.com/en-us/windows/hardware/gg463524")

And now my paranoia is returning

[http://en.wikipedia.org/wiki/BIOS_Boot_partition]("http://en.wikipedia.org/wiki/BIOS_Boot_partition")

[http://www.rodsbooks.com/gdisk/booting.html]("http://www.rodsbooks.com/gdisk/booting.html")

This link might have the answer, which is to use the Do something else option and create a boot partition as well as a / partition, a /home partition and a /swap partition.

[https://wiki.archlinux.org/index.php/GRUB2]("https://wiki.archlinux.org/index.php/GRUB2")

See this quote under the heading **BIOS Systems**

> GRUB2 in BIOS-GPT configuration requires a BIOS Boot Partition to embed its core.img in the absence of post-MBR gap in GPT partitioned systems (which is taken over by the GPT Primary Header and Primary Partition table). This partition is used by GRUB2 only in BIOS-GPT setups. No such partition type exists in case of MBR partitioning (at least not for GRUB2). This partition is also not required if the system is UEFI based, as no embedding of bootsectors takes place in that case. Syslinux does not require this partition.

Finally from the people who should know

[http://www.gnu.org/software/grub/manual/html_node/BIOS-installation.html]("http://www.gnu.org/software/grub/manual/html_node/BIOS-installation.html")

Regards.

---

