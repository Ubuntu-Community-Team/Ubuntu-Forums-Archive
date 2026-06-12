---
title: "Advice for total novice re installation on 2nd ssd in laptop"
date: 2020-05-10
forum: New to Ubuntu
---

### Post by h-poirot on 2020-05-10
I have a Acer aspire 5750 which runs a win10 for 2 users, my self and wife. I decided that I would love to try 20.0.4 as so much has been said about it. I bought a hard drive caddy which is to replace the disc drive and give me another drive to play with on the same pc. I have a 80GB new Intel ssd that I would like to use
I need to know how I go about putting the latest Ubuntu on it and being able to run it without affecting the main SSD Samsung evo 500gb.
I have seen that the drive must be formatted in a particular way which I am currently researching.

So...will I be able to install 20.0.4 on its own clean SSD? If so what is the correct procedure?
When I switch on the pc will I have the option to select the Ubuntu drive / system to play with?.....object being, to move over entirely to Ubuntu and escape the clutches of Win and Mac at a later stage.

At present when I use the Acer upon booting we have the choice of selecting either user....will I have a 3rd Ubuntu option.?
Having read so much about the different 'distros' Linux Mint etc, it came as a mine field and I couldn't make my mind up which way to go. I am sure I have made the correct decision but further advice would helpful.

Advice is much appreciated.

---

### Post by TheFu on 2020-05-10
First, it is **20.04**, not 20.0.4.   2020 <--- the year.   04 <--- release month (April).  The next release happens in October - so it is numbered **20.10**, not 20.1 or 20.1.0.  With Linux, details matter.  ALL details matter.

Dual booting is dangerous.  People understate the danger, but for someone unfamiliar with the different ways that Unix/Linux names hardware, it is very easy to make a simple mistake and wipe the existing system by accident.  We see that all the time here.  MS-Windows knowledge doesn't translate much for how Linux does hardware. 

If the system is faster than a Core2 Duo and has 4GB or more of RAM, I'd push for you to try it out for a few months using a virtual machine, VM.  Virtual Machines limit the access for any client OS, so unless you go out of your way to cause problems to the hostOS, you really cannot.   VMs let us setup limits for CPU, RAM, storage that the guest machine cannot break from.  You'll set these limits before attempting to install any guest, so a simple mistake can't harm the hostOS.  Most people here using MS-Windows as their hostOS would choose to use virtualbox for the virtual machine controller.  Most importantly, VMs hide the real funky hardware that many systems come with.  It is common for certain manufacturers, cough, Acer, cough, to use less supported network chips.
By using a VM, you also present the most common, most supported, hardware to the GuestOS regardless of what the system actually has inside. This means you won't have to fight with any drivers. Things will "just work."  Drivers on Linux aren't the same as with Windows.  If some hardware doesn't "just work", then either you'll have 2 possible answers.
[LIST=1]
[*]It will never work; There is hardware that just doesn't have any possible way of working with Linux, ever.
[*]You'll get to hunt down the source code for the driver, compile it into a driver file and install it into the place for the kernel to find it and make use of it. Every time there's a new kernel, either that process will happen automatically for you, OR, you'll get to do it manually again.  There's a new kernel about 2x a month.
[/LIST]

If you insist on dual booting, the boot areas will be shared by all OSes. How they are shared depends on whether UEFI or Legacy BIOS controls the booting.  If the machine came with Win10 pre-installed, then it is using UEFI.  Some changes to the BIOS settings will likely be needed for Ubuntu (or any Linux) to boot.  There are lots of articles about those at help.ubuntu.com.  
During the installation, you can specify which partitions are used for the OS.  Again, because all Linux systems name partitions and HDDs and SSDs differently than MS-Windows, it is easy to become confused, select the wrong partition and overwrite an existing partition.  That would be bad, correct?  

There are a few mitigation strategies. First that is good for safety, but terrible for convenience, is to completely unplug, disconnect, the SSD you don't want touched and only have empty storage connected to the system during the install.  Later, post-install, you can tell Ubuntu to rescan all the connected storage for OSes and setup a boot menu.  This isn't hard, but I would do it all from a command prompt.  The risk in doing this is about once a year, MSFT will push an update that wipes your Linux boot(s) from the menu. See, MSFT isn't very friendly towards other OSes.

VMs run fairly well these days and have for over a decade. 10 yrs ago, I was getting about 95% of native performance for non-GUI VMs.  GUIs screw things up.  They are much better today, but still we don't play high-end games inside VMs without lots of VM customization and usually passing through a GPU for exclusive use by the VM.  For typical office productivity apps or watching a video, the current virtual-GPU emulated by almost every VM controller is absolutely fine. 

I suspect you'll have more questions.  Please seriously consider using a virtual machine solution for a few months as you get more comfortable.
A good introduction to Linux: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)  Please read that first so you can understand many of the ways how Linux is completely different from those commercial OSes you've been using for years.

---

### Post by crip720 on 2020-05-10
It is not difficult to do, but there is always a chance of a person making a mistake.  Most people will recommend a good backup or if possible removing the main drive first.  Your best option at this point is to google installing ubuntu on second drive and read as much as you can to understand.  Ubuntu like most Linux OSs usually use the grub boot loader to let you choose OS you want at boot up.  Would suggest that you use the 'Try Ubuntu' option after you burn the ISO for some time before doing the install.  It lets you check if all hardware works well and gives you a feel for the OS.  Some programs you might use are very hard to get to use on Ubuntu/Linux(like photoshop), but there are others that can replace them.  When you go to do the install should use the 'Something Else' option, it gives you more control over installation.  The choice of Linux is usually up to what a person likes the most.  Can try quite a few since they all have a TRY option without needing to install or can use use them in a VM till you make a choice/s.

---

### Post by oldfred on 2020-05-10
Some systems will  not boot from a drive caddy that is in the DVD slot on a portable computer. Even though DVDs boot.
Those users had to have UEFI and/or /boot partition on internal drive, but then could have rest of system on drive in Caddy.

I do have full installs on SSD using USB3 port and that is almost as fast as an internal drive. Full installs to USB3 flash drive are slow especially writes, but once an apps is in RAM it runs at same speed. If lots of RAM, apps are cached in RAM and it runs reasonably well, if not writing a lot of data. I use flash drives more for emergency boot.

You must only use Something Else install option. Any other option is automatic, you may not know know what it is doing.
I prefer to partition in advance with gparted, but you can partition during install.

Default install is now just /(root) and if UEFI (most systems) an ESP. But Ubuntu's Ubiquity installer always uses the ESP - efi system partition on first drive, usually the Windows ESP. You want to be sure to have an ESP on new drive.

If installing to a full drive better to have ESP, FAT32 100 to 500MB with boot & esp flags, / as ext4 as 25 to 30GB and rest of drive as /home also ext4. You may also want data partition(s). 

All Acers have a unique requirement for UEFI boot. You have to set "trust" on the new ubuntu entry. It usually is just shown as unknown.
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

More general UEFI install info in link below in my signature.

---

### Post by h-poirot on 2020-05-11
Thank you all for your input. 
I will _take my time _with all the great advice you all have given.
Much appreciated.

---

