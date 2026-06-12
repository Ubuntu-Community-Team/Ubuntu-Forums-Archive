---
title: "Grub not starting up"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by dttk0009 on 2012-01-23
It's been about 5 years since my last Ubuntu installation, and it somehow popped into my head that I'd like to give it another whirl after all that time, so I downloaded Ubuntu 11.10 and popped the dvd in. To make a long story short, here's the chain of events that led to my dilemma now. I'll highlights the issues I have and what I've tried to fix them below:

1) Installed Ubuntu next to Windows 7 from within Windows. Grub was working here, but I had an error when loading into Ubuntu (No root file system defined), so I uninstalled Ubuntu from Windows.

2) Decided to install directly off the dvd from boot. I have a 2TB hard drive and created 3 partitions, one root, one swap, and one home. 

3) After the initial installation, grub wouldn't load at all, and Ubuntu wouldn't mount my initial Windows partition anymore when inside Ubuntu. I only get a purple screen when the computer loads up, and then the Ubuntu loading screen. I tried removing and re-installing Grub, but it didn't help.

4) I reinstalled Ubuntu again, this time creating a /boot partition, 200MB and ext4 and set it as the device for the boot loader. This may have been colossally wrong as now I just get a black screen that loads into nothing when my computer starts up. :D


Any way to fix this? I don't mind reinstalling Ubuntu again, though I'm a bit concerned over the fact that I can't see my Windows and other files anymore. Any of you guys have any idea what I may have done to screw up? I'd still like to get a dual-boot system in place, though if all else fails I'll just reformat my harddrive and reinstall windows.

Thanks in advance for taking the time to read my post.

---

### Post by SuaSwe on 2012-01-23
Hi dttk0009!

When you say that you created three partitions, was that alongside the already existing Windows partition, or could you have overwritten it? If you drop into the LiveCD (boot from disc > Try Ubuntu) and do 'fdisk -l', what is displayed there? Can you mount the Windows partition from the LiveCD, if indeed it shows up?

---

### Post by dttk0009 on 2012-01-23
Yep, I made them alongside the 2TB partition, which is basically my entire hard drive. It shows up as 'unallocated space' or something in gparted, and not as ntfs. 

I'm at work right now and the computer in question is at home so I can't do anything at the moment. Earlier I tried looking for the windows partition on the Live CD, but I couldn't find it. 

Initially, before the installation, the Live CD did actually automatically find and mount my windows partition and I could see all my files.

---

### Post by SuaSwe on 2012-01-23
I'm perhaps speaking too soon but that sounds a lot like the Windows partition is gone. :( If you had nothing you can't lose on there, might I suggest using Gparted on LiveCD to wipe the whole thing clean until you have one mass of unallocated space, then installing Windows on one part (say half or whatever you need), then use the Ubuntu installer to split up the rest into / , /home and swap. :) 

If you need to recover data on your Windows partition, that's a whole different kettle of fish - probably best get back on the forums once you're in front of your ailing PC if so!

---

### Post by dttk0009 on 2012-01-23
Haha, yeah I figured. I tried repairing it with my Windows CD, but it said that it was 'incompatible' with my version of Windows installed. Certainly made me raise an eyebrow. I didn't really have much on my computer save for a few games, but I can re-download those on steam anyway, so no worries about recovering, unless of course, it IS possible. If my data is already gone then whatever. I'll be back in this thread later tonight as well, but for now I'll keep an eye on it. :)

Would I need to make a /boot partition as well? What do I set as the device for the boot loader in the installation? Should I install Ubuntu first and the simply just install Windows 7 on the other NTFS partition? 

Thanks again for helping out with this.

---

### Post by SuaSwe on 2012-01-23
You don't need a boot partition, and Ubuntu will automatically install the boot loader where it sees fit (I've yet to see the location picked by Ubuntu cause any trouble!). Because Windows' boot loader doesn't recognise Ubuntu whereas Ubuntu's recognises Windows, I would suggest installing Windows first, then Ubuntu. The only reason why I suggest using Gparted to do the initial partition-erasing is because I just think it's nicer than the equivalent Windows tool. :)

This is the method I used when installing a dual-boot Windows/Ubuntu system, and it worked wonderfully for me:

1. Remove all partitions using Gparted on LiveCD
2. Run Windows install and give it a partition of whatever size you desire - keep in mind that you can view NTFS partitions from Ubuntu so you can even use Windows as your regular storage space for large media and suchlike if you wish, meaning you can then access these from either Windows or Ubuntu; this would mean that the Windows partition would need to be large to accommodate them
3. Once Windows is fully installed, run the LiveCD again and select Install Ubuntu, then when it asks how you want to install it, select the manual option (I forget the wording but not the 'alongside Windows' one)
4. In the 'unallocated space', create a primary partition at the "beginning", give it 20gb or so, and set mount point as /
5. In the remaining 'unallocated space', create a logical partition, place it at the "end", give it 2x the size of your RAM, and set mount point as swap
6. In the remaining 'unallocated space' at the "beginning", create a primary partition using as much space as you want (the remainder if you like), and set mount point to /home
7. Don't touch the boot loader location, just leave it as Ubuntu suggests

Then go through the install and hopefully you should now have a lovely dual-boot system! At least, this setup never failed for me. :)

---

### Post by dttk0009 on 2012-01-23
Awesome, thanks! If all else fails I'll give this a try tonight.

In regards to saving my current Windows partition, what are my options?

---

### Post by SuaSwe on 2012-01-23
Well, if the partition is really gone (so you've been in the live environment and 'sudo fdisk -l' shows no Windows partition, you can't see/mount it, it cannot be recovered using the Windows recovery utility, etc), I think your only option might be trying an application such as Stellar Phoenix or similar to get it back. I really have no experience in that area though and would definitely recommend doing some research before attempting it - the more changes that are made to the space Windows previously occupied, the harder it will be to recover data from it!

---

### Post by dttk0009 on 2012-01-24
What should my Windows partition look like in sudo fdisk -l? I'll try it tonight. If it's not there, which it certainly looks like it's not, I'll just reinstall everything the way you proposed. I guess this pretty much clears up my issues though, for the most part.

Thanks! :)

---

### Post by SuaSwe on 2012-01-24
I've tried to recall directly from my foggy, 5am memory but can't remember exactly what it will look like, however I'm 99% certain the System column (far right) will contain 'NTFS' to denote the filesystem type, whereas any Ubuntu partitions will be called 'Linux' something or other. :)

---

### Post by oldfred on 2012-01-24
This is from my old XP install. You can tell it is old as it starts at sector 63 where all new installs for Vista/7 and now Ubuntu start at sector 2048.

```
fred@fred-LT-A105:~$ sudo fdisk -lu
[sudo] password for fred: 

Disk /dev/sda: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312576705 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   113595614    56797776    7  HPFS/NTFS
/dev/sda2       113595615   175028174    30708247    7  HPFS/NTFS
/dev/sda3       175028236   312062624    68509192    5  Extended
/dev/sda5       175028238   205744454    15350107   83  Linux
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda6       205744518   211881284     3060382   82  Linux swap
Warning: Partition 6 does not end on cylinder boundary.
/dev/sda7       211881348   312062624    50082637   83  Linux
Warning: Partition 7 does not end on cylinder boundary.

```

If you install Ubuntu first to a 2TB drive it will convert from MBR to gpt. But Windows only works with gpt if you boot with UEFI not BIOS and have 64 bit Windows.

There used to be (have not checked recently) a bug in grub that very large root partitions would not boot. Drives over 500GB with just root & swap seemed to have the problem. Best to keep / at 25GB and then make /home large. Also if sharing with Windows a separate NTFS partition for data is recommended. Then you do not write directly into the Windows system install which can cause issues.

---

