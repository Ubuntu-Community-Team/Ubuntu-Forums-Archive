---
title: "New to Ubuntu and have some questions."
date: 2018-06-28
forum: New to Ubuntu
---

### Post by arkay99 on 2018-06-28
Hello! I've owned and operated a freeBSD server some time ago as a pre-live proof of a website I was writing and operating from. That being said, I'm a newb as far as Ubuntu and Linux. I've also been programming on Windows since 3.11, I know, I'm dating myself...I was programming in 6502 assembler on my Apple 2 before that... 

I've been a design engineer for the last 20 years but have worked exclusively, except for the freeBSD thing on Windows. Lately I've been working with Lattice FPGA's and all their tools are pretty much Windows. I've recently purchased a Xilinx development board for learning to work with their FPGA's (they are much more powerful than the Lattice one's) and have been working with their Windows 7 tools. One of the options for the FPGA on my board is to run Linux on the dual processors contained within it. To do so, there is a requirement that certain parts of the build process be done in Linux, so here I am.

I'm currently running a Windows 7 Pro SP1 64 bit OS on my development machine. I've just ordered another 500GB SSD and Windows 10 to load on it. I also plan to install VMware Workstation Pro 14 and install Ubuntu Linux 16.04.3 LTS (64 bit) in there. The idea is that I won't have to reboot to go between the Linux OS and the Windows 10 OS while working on code.

It's also in my plan to have a 3rd drive dedicated to Just Linux in the future. My motherboard has a dual BIOS. One of which is UEFI for running Linux or whatever you can get to run in there.

That's the background and the plan. The software requirements (OS) are: Windows 7 SP1 Professional (64 bit), Windows 10 Professional versions 1709 and 1803 (64 bit),  Linux support: Red Hat Enterprise Workstation/Server 7.3-7.4 (64 bit), Red Hat Enterprise Workstation 6.7, and 6.8, CentOS 7.2 CentOS7.3-7.4 (64 bit), Ubuntu Linux 16.04.3 LTS (64bit) - Linux kernel 4.4.0 is supported, Ubuntu LTS enablement (also called HEW or Hardware Enablement) is not supported.

So, Using the Red Hat and CentOS installs would be like using a cannonball to kill a fly (to me), since I'm the only guy using this stuff.

My questions at this time are:

I searched for an install of 16.04.3 LTS and only found 16.04 LTS. Since this Xilinx environment is so picky (my current Win 7 install doesn't work very well) and the version is specific, I want to make sure I at least start out with that OS version, so I know I have a recommended environment. What steps would I need to take to obtain that particular version?

Is the Linux kernel 4.4.0 in that version?
If not, how would I obtain it?

What the heck do they mean by, Ubuntu Linux 16.04.03 LTS (64 bit) is supported, and Ubuntu LTS enablement (also called HWE or Hardware Enablement) is not supported?

Thanks in advance for any help and knowledge in getting this new direction going.

---

### Post by oldfred on 2018-06-28
While 16.04 is LTS or long term support, you only get the full 5 years with either the original kernel in 16.04 or 16.04.1. Then they start the enablement stack process, so newer hardware which requires a newer kernel will work. But each upgrade is only supported for a short time and only final 16.04.5? will be the long term version fro the remaining support or 5 years from original 16.04. Or specifying 16.04.3 makes no sense as it is already obsolete.
And kernel 4.4 is only in 16.04.1, 16.04.3 has 4.10, see link.

       [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
Because so many had issues with the short term kernels and not updating as they thought they were LTS, with 18.04.2 or later it will automatically upgrade kernel.
 
Windows 7 is normally BIOS/MBR, but installer can be converted to flash drive and some files renamed to make it UEFI bootable. How you boot install media UEFI or BIOS is then how it installs.
Windows only boots with BIOS from the now 35 year old MBR(msdos) partitioning.
And Windows only boots with UEFI from the newer gpt partitioning.

---

### Post by arkay99 on 2018-06-29
> **oldfred said:**
> While 16.04 is LTS or long term support, you only get the full 5 years with either the original kernel in 16.04 or 16.04.1. Then they start the enablement stack process, so newer hardware which requires a newer kernel will work. But each upgrade is only supported for a short time and only final 16.04.5? will be the long term version fro the remaining support or 5 years from original 16.04. Or specifying 16.04.3 makes no sense as it is already obsolete.
And kernel 4.4 is only in 16.04.1, 16.04.3 has 4.10, see link.

       [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
Because so many had issues with the short term kernels and not updating as they thought they were LTS, with 18.04.2 or later it will automatically upgrade kernel.
 
Windows 7 is normally BIOS/MBR, but installer can be converted to flash drive and some files renamed to make it UEFI bootable. How you boot install media UEFI or BIOS is then how it installs.
Windows only boots with BIOS from the now 35 year old MBR(msdos) partitioning.
And Windows only boots with UEFI from the newer gpt partitioning.
Thank you for that link as it clears up many questions and concerns regarding the versioning of Ubuntu. However,  that info leads me to the same conclusion you have...specifying 16.04.3 makes no sense, and specifying the kernel being 4.4 on 16.04.3 is confusing and wrong. I'm wondering if these are minimum requirements and later versions will be ok. Also, it seems like there is a hint that the ga version is the one to use, and not the hwe versions. Armed with this info, I will revisit the forums at Xilinx and see if I can stitch together the answers as to what they mean. It's also possible that the User Guide these requirements refer to were written by a technical writer that doesn't fully understand what they've recommended...but it's most likely confusion on my part as to what the implementation should be. When I get a good answer, I will report back.

---

### Post by oldfred on 2018-06-29
Since wanting two versions of Windows, you have to be careful of drive partitioning.
How you boot install media it then how it installs which then determines partitioning.
When Windows 8 was released in 2012, Microsoft required all vendors to install it with UEFI/gpt.

With a new system Windows 10 installer should offer two boot options in UEFI, one clearly UEFI and other not UEFI. With Ubuntu you see UEFI:flash or flash where flash is name or label on flash drive installer.

You can only have Windows 7 in BIOS mode on a separte MBR partitioned drive. But could install Windows 10 to that drive in BIOS mode. But only one partition will be bootable, unless you change boot flag.
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth + words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

With UEFI, you can only have one ESP per drive or device.  Windows BCD can be updated to boot multiple versions of Windows. With Linux, grub will boot most other install from one default install.
But some create multiple FAT32 partitions, and move boot flag (which indicates whether ESP or just standard FAT32 partition). Then they can have more than one direct boot with some effort.

---

### Post by arkay99 on 2018-07-03
Hello oldfred. I haven't been ignoring this thread, it's been a very busy weekend and the new drive and OS arrived today. It looks like I have a bit more research to do before I continue on with this. Thanks again for the new links. I am planning on installing Win 10 on it's own drive by removing the Win 7 drive's cable, and therefore it's presence from the system and installing Win 10 on it's own fresh drive. But before I do that I will have a look at the links and make sure the caveats are understood and the implementation is sound. This way, there may be less surprises to deal with when I plug the Win 7 drive back in...

Once all that is in place then it's on to installing VMware and Ubuntu...which version is still to be determined.

---

### Post by oldfred on 2018-07-03
Your Windows 7 is probably BIOS/MBR configuration. Only a very few installs are UEFI from vendors just before they started issuing Windows 8 and confirming their UEFI replacement for BIOS worked.

If you have some drives as UEFI/gpt and some as BIOS/MBR you can still dual boot, but only from UEFI boot menu. And grub only boots other systems installed in same boot mode. UEFI and BIOS are not compatible, they write data to hard drive differently for operating system to use.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by HermanAB on 2018-07-03
Hi Oldfred,

We are likely about the same age.  Anyhoo, in my humble experience, when a specific version of something is required by some cranky/crummy software, then it is usually best to make a virtual machine for the experiment.  

That way, you can install the host with the latest and greatest Linux and Virtualbox/VmWare/KVM/Qemu/Virtualizer-of-choice and make a virtual machine with all the version specific, cranky software and then turn auto-updates OFF on that VM, so that it stays frozen in time and continues working for many a year.

---

### Post by mastablasta on 2018-07-04
> **HermanAB said:**
> 
That way, you can install the host with the latest and greatest Linux and Virtualbox/VmWare/KVM/Qemu/Virtualizer-of-choice and make a virtual machine with all the version specific, cranky software and then turn auto-updates OFF on that VM, so that it stays frozen in time and continues working for many a year.

i second that option.

also you would want to install 16.04 or 16.04.1. focus on the kernel needed not the OS version.

---

### Post by arkay99 on 2018-07-05
> **mastablasta said:**
> i second that option.

also you would want to install 16.04 or 16.04.1. focus on the kernel needed not the OS version.
Ok...that would make sense as to running kernel 4.4.0 as one of the requirements. I am going to do the update today, so, hopefully I'll have some real info to report back. Thanks to all who've been so forthcoming of all the info.

---

### Post by arkay99 on 2018-07-13
To all who chimed in and helped. Thank you! I have my new hardware installed, installed Windows 10, VMware, downloaded 16.04.3 and loaded the iso into VMware... I'm up and running with it as I type this. installing Ubuntu was so easy. Now all I have to do is learn a whole new environment. ;-)

---

