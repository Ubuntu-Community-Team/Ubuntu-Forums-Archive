---
title: "Starting over in dual boot. Recommendations?"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by buttolph on 2013-02-06
My son built for me a computer with twin SSD 180 gb drives, a third 1.5 Tbyte drive, UEFI dual bios, 8 mByte ram, 4 gHertz intel i7 processor, windows 7 SP1 professional, and am looking to load Ubuntu in dual boot. Windows is installed on one of the SSD's, set up SATA in ACHI mode. When home from college, he loaded Ubuntu on the 1.5 tByte drive 12.04 LTS. I have my old Dell on my desk for this forum. I hope to set up the ideal dual boot Win 7 Ubuntu on the new one. I have tried some things, messed some things up no doubt. For example, I tried to install a copy of 12.04 on the other SSD but can't access the internet from it. I have messed up with the grub file and boot repair when playing in the 12.04 my son installed, (picked the option to purge kernels and reinstall last kernel in a vain attempt to have grub only list active operating systems, and as a result I get the message "network disconnected", and also "System program problem, do you want to report the problem?" (but I can't because I have no internet. Boots fine into Windows 7. 

I have nothing of value yet on the new machine. Happy to reinstall windows (although it seems to work fine), download fresh copy of Ubuntu, or whatever. Is there a kind enough sole out there to help walk through what to do? How to partition the drives? (use Gparted or the Windows tool?) Recommend whether I need the 64 bit Ubuntu to get esi capability, or even help me decide if I should need to do that? I am eager to dive into ubuntu and learn how to break loose from Windows some day but having trouble getting set up.  Thank you so much!

---

### Post by saif32 on 2013-02-06
i think you can use your windows partition tool to format your ubuntu partition then install a fresh ubuntu...
(i often do like that)

---

### Post by Frogs Hair on 2013-02-06
I have also used Windows disk management to shrink the volume for the Ubuntu partition.There is an install Ubuntu before or after windows method described at the link. I use a single hard-drive though 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Bucky Ball on 2013-02-06
A classic from a guru but there are zillions of others:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

You should find everything you need there. If not, just ask, and welcome to the forums. ;)

Frankly, there are a million and one options and variations. Best to sit with the beverage of choice, a pencil and piece of paper, represent the drives you have and how you are going to divide them up.

Bottome line; if Windows is installed and booting fine, leave as is. Make free space (you only need about 15Gb if you create a /home partition for your personal data) and install Ubuntu to it. That's it. The Win install should be picked up during the Ubuntu install and added to the list of choices you have at boot. 

If you choose 'Something Else' at the partitioning section of the install, then your Win NTFS partitions will be clearly visible. Stay away from them and do what you will with the free space/everything else. Good luck.

/ = where Ubuntu lives, 15Gb fine;
/home = where your personal data lives (big as poss if that suits);
/swap = 2Gb fine unless you hibernate then as much as your installed RAM.

This is only an *_example_*. Up to you how you want to set things up.

---

### Post by buttolph on 2013-02-06
Thanks for the thoughts!  I actually had tried a number of things, carefully walked through partitioning scenarios following some of the threads (both dual boot on one drive, and on two drive scenarios), and understand that there are a bunch of options. To narrow things down a little maybe you are kind enough to ponder these two thoughts and tell me what you think:

1) With the various ill fated install attempts that I have walked through, I now find myself booting into Grub2, with one option to boot into Ubuntu that had been installed on my third drive, (note the error message in my initial post that says I have a “system program problem” in Ubuntu, but no internet to facilitate reporting it) and also an option to go into windows 7 which is on one of my SSD’s. Windows boots fine from there (not sure why Grub2 tells me I have windows installed on both SSD’s… a question for another time). I’d like, for now, to get rid of the diversion of 12.04 installed on my third drive and concentrate on getting dual boot on my SSD’s (good advice to sketch on a piece of paper and I will do that)  but I am concerned that Grub2 is probably on that third drive, (not sure) and booting up once I delete that, the system won’t know where to boot up to. Reinforcing that concern, I tried this: I went into the UEFI Bios (motherboard is Gigabyte) under the system drop down, and temporarily disabled ATA Port where the third drive is installed, tried to reboot, and sure enough, I get this: error: no such device: cae4b333-48af-45aa-925d-3af3244bb0e32 grub rescue>. So if I wipe my third drive, does this mean I would need to reinstall windows and start from scratch anyway? At present, I am enslaved into a Grub2 boot file that puts me back into a corrupt installation of 12.04 that can’t access the internet, and boot-repair has issues when I load that Ubuntu install). If I want to clean this all up, does it look like my only option is to wipe all these drives and install Windows from scratch? Or is there some other way to delete grub2, wipe the third drive, and try a clean install of Ubuntu and leave Windows alone?

2) I have a UEFI system, and the first comment out of the chute in the link [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) is that recommendations in that link may be harmful to EFI computers. Do you know anything about differences between setting up with an older computer and doing so with a system with UEFI?

---

### Post by oldfred on 2013-02-06
Your system is UEFI/BIOS. So you can install both Windows & Ubuntu in either UEFI mode or BIOS mode. But if both are not in same mode, you will have to go into UEFI/BIOS change mode UEFI on/off and choose to boot install.

With Multiple drives I do recommend separate installs on every drive. And even have a test install or backup install on the large rotating drive even if booting from the SSDs.

UEFI is a bit more complex and has issues with some systems, mostly the new pre-installed Windows 8 and secure boot. Yours should not have secure boot. Windows 7 will not work with secure boot anyway.

You will need Boot-Repair anyway so run a BootInfo report now so we can see what is installed where and how it is configured. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
Partitioning is even different between UEFI and BIOS. UEFI needs gpt partitioning and Windows only boots in UEFI mode from gpt partitioned drives. Ubuntu will boot from gpt drives in BIOS or UEFI and defaults to gpt if drive is somewhat over 1TB.
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by buttolph on 2013-02-06
One of the problems is when running boot repair and generating the info file, I run into the "network not available" issue, and I gather boot repair needs to access the internet to post this file so that you can see it. I can dump it onto a USB thumb drive and simply plug it into this other machine (that I am using now), copy and paste the text file, but the format of that is pretty rough to read. Maybe I should go backwards and troubleshoot why I can't access the internet from Ubuntu? Or might that be related to the boot issue? I can access the internet when I load windows on my new machine (I am on my old machine right now). I was previously able to access the internet on Ubuntu until I got monkeying around with boot-repair settings, trying to change my grub file (I deleted all but the most recent kernels and then couldn't get the network to work. Probably stupid, I know). I am on an ethernet cable to a Router and then onto the internet that way.  Sorry this is so difficult! Thank you so much for your help!

---

### Post by oldfred on 2013-02-06
You really need Internet to post BootInfo and to do many of the upgrades and reinstalls that may be required.
Changing Boot-Repair setting should not have changed Ethernet settings. Perhaps you deleted more than just old kernels?
You can run Boot-Repair from Live0CD/DVD/flash. Does that not work on Internet?

---

### Post by buttolph on 2013-02-06
No, the liveCD doesn't allow me to access the internet either. I've tried it via CD and USB, I've tried 32 and 64 bit. The good news is that I have no critical files on my new machine, I have installed Win 7 as I said, but no software or other time invested other than dinking around trying to get this dual boot to work, and I have spent a week and a half at it. When I first started, I left the Ubuntu 12.04 on the 1.5 terabyte drive and installed windows. (Ubuntu was on there first... maybe that is the root of my problem somehow?) Everything was fine. Then I tried liveCD (via USB) and I was able to boot into 12.04 (without altering my disk) but even then, from that liveCD, no internet. And I tried installing 12.04 to my second SSD and although it installed, or seemed to, still no internet through Ubuntu (although all was fine with the windows). I should add that my motherboard instructions had me installing drivers AFTER I installed Windows, and before I did that, I had no internet with Windows either. Finally I said to heck with it, let's just do Ubuntu from the 3rd drive, and got doing what I thought was mere houskeeping by deleting all but the most recent kernels and bam.. I lost internet on the previously installed Ubuntu 12.04 which had been working fine! (But kept internet on Windows).

---

### Post by oldfred on 2013-02-06
You may want to start a thread on Ethernet issues. Post in title exact model as there are some with known issues. Or search forum based on your model. I have not had issues recently, so am not current on best way to resolve your issue.

# you can also compare this to Windows ipconfig output
ifconfig
# To find Ethernet chip. 
       lspci -v
dmesg | grep eth
# Plug in Ethernet cable and see if errors:
dmesg | tail -n10
# Check by chipset:ie e1000e
sudo lsmod | grep e1000e

---

### Post by Bucky Ball on 2013-02-06
> **buttolph said:**
> No, the liveCD doesn't allow me to access the internet either. I've tried it via CD and USB, I've tried 32 and 64 bit. The good news is that I have no critical files on my new machine, I have installed Win 7 as I said, but no software or other time invested other than dinking around trying to get this dual boot to work, and I have spent a week and a half at it. When I first started, I left the Ubuntu 12.04 on the 1.5 terabyte drive and installed windows. (Ubuntu was on there first... maybe that is the root of my problem somehow?) Everything was fine. Then I tried liveCD (via USB) and I was able to boot into 12.04 (without altering my disk) but even then, from that liveCD, no internet. And I tried installing 12.04 to my second SSD and although it installed, or seemed to, still no internet through Ubuntu (although all was fine with the windows). I should add that my motherboard instructions had me installing drivers AFTER I installed Windows, and before I did that, I had no internet with Windows either. Finally I said to heck with it, let's just do Ubuntu from the 3rd drive, and got doing what I thought was mere houskeeping by deleting all but the most recent kernels and bam.. I lost internet on the previously installed Ubuntu 12.04 which had been working fine! (But kept internet on Windows). 

Please use paragraphs. These solid blocks of text are not easy to read and will put a lot of people off; they'll just move on rather than wade through it. Help us help you. ;)

---

### Post by buttolph on 2013-02-07
Thanks for all of the advice! Nothing worked here, and chasing this down in another thread for internet issues turned into a bit of a goose chase as well. I have reformatted all of the drives, loaded windows from scratch. This is a 64 bit windows 7 install, pristine. Any recommendations on whether I should try Ubuntu 64 bit or 32 bit? Thanks again!

---

### Post by Bucky Ball on 2013-02-07
64bit if you have a dual-core (or more) and a fair bit of RAM.

---

