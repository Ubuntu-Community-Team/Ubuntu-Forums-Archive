---
title: "Dual Boot Nightmare"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by Nick_Martinez on 2014-07-15
:mad: Alright where do I begin...

Decided I would dual boot my laptop so that I had both Windows 8 and
Ubuntu. I did some research and used information from several online guides to assist me. I first downloaded and put Ubuntu 14.04 32-bit (I would later realize that I should have downloaded 64 bit) on a USB drive. I created some space (partition) for Ubuntu. I decided to go against the advice of literally every single online guide and not ensure that I had a recovery of Windows 8 for two reasons: I was confident that nothing was going to go wrong, and also because I noticed I had a recovery partition and assumed that would save my ass if something did. 

I properly shut down my system and first went into BIOS and switched to Legacy mode instead of UEFI mode. Then I booted into Ubuntu from the USB and proceeded to install the OS alongside Windows 8 in the free space I created earlier. Everything was going smoothly. After the install completed I realized that I could only go into Windows under UEFI mode and Ubuntu under Legacy mode. One guide in particular mentioned to fix this to run boot-repair software in the terminal on linux. I honestly can't remember exactly what error message boot-repair gave me, but I do remember it told me I needed to get the 64 bit ISO. I downloaded that, put it on a CD, and booted into it. I then get another message from them stating that my version of linux is 32 bit, and that I needed a 64 bit version of linux to do a proper boot repair. 

Okay so damn. I find out that the best way to do this is to just download the 64 bit and replace the 32 bit version and then run boot-repair and hopefully everything would be ready to go. So I put that on the USB, replacing the 32 bit version, pop that sucker in and start the process over again. Part way through the install I get a message - "input/output error" and that the install couldn't be completed. I decide to say **** it for the night, and just go back to good ol' Windows. I restart, change the BIOS settings, and ...what!? It's not there. Windows 8 is gone. I change the BIOS setting again, and ...I can't get back into Ubuntu. OoooK so I manage to get in under the "try Ubuntu" on the USB. I look at the partition and there is only one huge partition for Ubuntu 14.04 LTS. No recovery partition, no Windows 8 partition, nothing. 

So at the point I'm feeling helpless. No clue what to do. I keep trying to get back into my Ubuntu 32 bit to no avail. I keep trying to install Ubuntu 64 bit to no avail. I try messing around with the partitions - nothing changes. I google "partition recovery software linux" and try using "testdisk" to no luck. At this point I'm desperate so I go searching around and find an older CD with Linux Mint 15 on it which I then proceed to install on my system over the Ubuntu 32 bit which is still there even though I can't boot into it. Guess what happens - yep I can't boot into Linux Mint 15 either.

I have an expensive two year warrenty on my laptop that supposedly covers everything. Should I look into that? Should I take my laptop to a professional and see what they can do for me? I need some advice here. 

I apologize if I'm not making the best sense. It's early in the morning, I'm out of it, I'm not too good at articulating myself sometimes and I don't have a lot of experience dealing with installing new operating systems.

---

### Post by veddox on 2014-07-15
OK, sounds like a bit of a mess :-)

My advice: use GParted from the 14.04 live CD to completely wipe your drive. It seems like your Windows 8 is already gone anyway, so that won't make too much of a difference. (If you have any really important data that you need to recover, you should look for another solution though.) Next, use a Windows 8 recovery disk (should have come with your laptop) to reinstall Windows. Then set up a Linux partition. Now reinstall Ubuntu 14.04 64 bit again, taking care to choose the "install alongside Windows" option.

If possible, install Windows in legacy mode (not sure if you can do that, but give it a shot).

---

### Post by grahammechanical on 2014-07-15
This guide says this

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note point #1. 

The guide also says this

> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[FONT=inherit][/FONT][/FONT]

[*=left]Then:[FONT=inherit][/FONT][FONT=inherit][/FONT]
[LIST]
[*=left]nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others" or "Erase the disk and install Ubuntu"). Important: if you have a pre-installed Windows and you want to keep it, do not choose "Erase the disk and install Ubuntu".[FONT=inherit][/FONT][FONT=inherit][/FONT]
[*=left][FONT=inherit]if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition. And if there was not any EFI partition on your HDD, you first will have to create it (see the "[Creating an EFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition")" paragraph below)[/FONT]
[/LIST]
[/LIST]


Regards

---

### Post by yancek on 2014-07-15
I haven't used windows 8 on a real machine only virtual but, with windows 7 you are prompted to create a Recovery disk on first boot.  I expect the same with 8 but may be wrong.  The recovery CD/DVD is needed to access the recovery partition, at least it was on earlier windows and have no reason to expect that to change.   A windows installation DVD will usually not come with an OEM install but we don't know if that is what you have.  If you have the windows 8 installation medium, you can obviously easily install it again.  If it was an OEM and you did not get an installation medium, you should be able to purchase it from the manufactuer for substantially less than it would cost to get from a retailer.

---

