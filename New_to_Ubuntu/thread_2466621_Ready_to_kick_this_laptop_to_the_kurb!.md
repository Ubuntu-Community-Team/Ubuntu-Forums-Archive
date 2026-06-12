---
title: "Ready to kick this laptop to the kurb!"
date: 2021-09-01
forum: New to Ubuntu
---

### Post by popnippon on 2021-09-01
Hi Guys,

I've just installed the latest version of Ubuntu for a 5th time now to this laptop. Lenovo Ideapad S130-11IGM (possibly the worst laptop ever made)

Installs find off a USB. Runs smoothly without problem. Restarted it via the menu and rebooted no problem.

Powered off then powered back on again... and I am stuck at the Lenovo Boot-up screen and nothing seems to happen.

Then I cut the power, in GRUB power up (Recovery Mode)….

I then get watchdog bug: softlockup -CPU#1 stuck for 22s!

So turn it off again... then reboot again... letting it boot naturally into Ubuntu...

Then back to the Lenovo Splash Screen where nothing happens.

This is like a never-ending nightmare!

Any help or advice before I bin this machine.

Update - If it Play around with the Boot Settings in the Bios and just enable/disable the USB Boot and move the HDD to just under 'Ubuntu' when I reboot it seems to load!

I then restart and it loads again...

I then shutdown properly... then restart the machine and get stuck on the LENOVO boot screen again.

I'm guessing the BIOS is screwed somehow.

---

### Post by yancek on 2021-09-01
Is Ubuntu the only OS installed on this machine?
Is this an EFI or Legacy/CSM install of Ubuntu?
When you access the BIOS, what Boot Options do you have?  You  indicate you have an Ubuntu option, is that what you are selecting to try to boot Ubuntu?

---

### Post by grahammechanical on 2021-09-01
I am confused. Is Ubuntu installed onto the hard drive? Or, is this problem happening when running the try/install Ubuntu session from the USB memory stick.

> Update - If it Play around with the Boot Settings in the Bios and just  enable/disable the USB Boot and move the HDD to just under 'Ubuntu' when  I reboot it seems to load!

That seems to me to be changing the boot priority from the hard drive to the USB memory stick. What is the 'ubuntu' on? The HDD? Or USB memory stick?

Regards

---

### Post by popnippon on 2021-09-01
Ubuntu is the only OS installed. 

EFI

Correct. Trying to boot to Ubuntu in the bios

---

### Post by oldfred on 2021-09-01
These lightweight systems, need a lightweight operating system.
Full Ubuntu is probably too much.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

If you want better performance, install Ubuntu to an external SSD.

Older threads with older model Ideapad & older Ubuntu. Is your system just an update to these?
Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)
LENOVO Ideapad 100 Laptop 16.04 Dual Boot 
[https://ubuntuforums.org/showthread.php?t=2336544](https://ubuntuforums.org/showthread.php?t=2336544)

---

### Post by popnippon on 2021-09-01
> **grahammechanical said:**
> I am confused. Is Ubuntu installed onto the hard drive? Or, is this problem happening when running the try/install Ubuntu session from the USB memory stick.



That seems to me to be changing the boot priority from the hard drive to the USB memory stick. What is the 'ubuntu' on? The HDD? Or USB memory stick?

Regards

I'm confused as you are! haha... Ubuntu is installed on the HDD.

Ubuntu installs fine to the HDD when you complete install and take out USB stick and press enter.. It boots fine into Ubuntu.

If you the 'Restart' the machine... again, it boots up perfectly.

However... if you POWER OFF the machine then Power it back on again... then LENOVO Splash screen gets stuck and you don't get any UBUNTU Loading graphic. 

I'm assuming when Powering down the machine fully, something changes somewhere (which does not change on a restart)

> **oldfred said:**
> These lightweight systems, need a lightweight operating system.
Full Ubuntu is probably too much.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

If you want better performance, install Ubuntu to an external SSD.

Older threads with older model Ideapad & older Ubuntu. Is your system just an update to these?
Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)
LENOVO Ideapad 100 Laptop 16.04 Dual Boot 
[https://ubuntuforums.org/showthread.php?t=2336544](https://ubuntuforums.org/showthread.php?t=2336544)

I followed the thread ending is 2350394. Adjusted the Boot options to match these. Rebooted the machine and it logged straight into Ubuntu.

However, when I powered down and powered back up again... I'm stuck at the Lenovo Splash screen once again. 

Has to be something to do with when turning the computer on for the first time i'm assuming?

---

### Post by tea for one on 2021-09-01
> **popnippon said:**
> 
Installs find off a USB. Runs smoothly without problem. Restarted it via the menu and rebooted no problem.

Powered off then powered back on again... and I am stuck at the Lenovo Boot-up screen and nothing seems to happen.

Then I cut the power, in GRUB power up (Recovery Mode)….

I then get watchdog bug: softlockup -CPU#1 stuck for 22s!

So turn it off again... then reboot again... letting it boot naturally into Ubuntu...

Then back to the Lenovo Splash Screen where nothing happens.

Having cut the power, which can cause file system damage, it would be sensible to boot into a live session and run fsck on your disk.

> **popnippon said:**
> I'm guessing the BIOS is screwed somehow.

Try setting the UEFI firmware back to default

---

### Post by oldfred on 2021-09-01
UEFI has a one time boot setting & default boot setting.
It looks like one time setting is working, but default is not.

Can you change default in UEFI settings (not UEFI boot menu)?
Most systems support boot order change with efibootmgr, but a few only keep the setting if you change it in UEFI settings.
When installing with grub, it uses efibootmgr to add entry for ubuntu & reset boot order to make that entry first.
see also 
man efibootmgr

Shows entries:
sudo efibootmgr -v

Some older systems only wanted to boot a "Windows Boot Manager" entry.
If only booting Ubuntu, not dual booting, you can create a new entry saying Windows but booting Ubuntu's files. Check in UEFI seems to be only on description not on actual files.

---

### Post by grahammechanical on 2021-09-01
I would like to offer a wild guess. Is the CMOS battery holding its charge?

My desktop machine has a BIOS motherboard, When I power off there is still electrical power going into the motherboard and it keeps the CMOS battery charged. If I disconnect the plug from the mains socket then electrical power is no longer going into the motherboard and as the CMOS battery on my machine needs replacing the BIOS settings reset to default settings. I need to enter the BIOS settings utility and set the boot options to my choice.

From my experience I am wondering if the CMOS battery in your machine needs replacing. I know you have a UEFI system. I guess that laptops are not continually connected to the mains. Wild guesses are often all I am left with when I am trying to fix things.

Regards

---

### Post by popnippon on 2021-09-01
> **grahammechanical said:**
> I would like to offer a wild guess. Is the CMOS battery holding its charge?

My desktop machine has a BIOS motherboard, When I power off there is still electrical power going into the motherboard and it keeps the CMOS battery charged. If I disconnect the plug from the mains socket then electrical power is no longer going into the motherboard and as the CMOS battery on my machine needs replacing the BIOS settings reset to default settings. I need to enter the BIOS settings utility and set the boot options to my choice.

From my experience I am wondering if the CMOS battery in your machine needs replacing. I know you have a UEFI system. I guess that laptops are not continually connected to the mains. Wild guesses are often all I am left with when I am trying to fix things.

Regards

Its good thinking but I tried that and same issue.

> **oldfred said:**
> UEFI has a one time boot setting & default boot setting.
It looks like one time setting is working, but default is not.

Can you change default in UEFI settings (not UEFI boot menu)?
Most systems support boot order change with efibootmgr, but a few only keep the setting if you change it in UEFI settings.
When installing with grub, it uses efibootmgr to add entry for ubuntu & reset boot order to make that entry first.
see also 
man efibootmgr

Shows entries:
sudo efibootmgr -v

Some older systems only wanted to boot a "Windows Boot Manager" entry.
If only booting Ubuntu, not dual booting, you can create a new entry saying Windows but booting Ubuntu's files. Check in UEFI seems to be only on description not on actual files.

It sounds like a one time setting of some kind that's for sure. As after shutting down properly and then trying to reboot it just gets stuck on the splash screen for 'LENOVO' and no Ubuntu Load animation which makes me think it's not even getting to it for some reason..

I can change the Boot Menu to Default which is what I am trying now. I've just changed it to LEGACY and pressed F10 to save changes and it has loaded into UBUNTU.

... Now let's see what Happens when I turn off the machine via the Shutdown Command...

...Okay powering down now....

...Lets Power it back up...

..Loading GRUB...

...AAAAND back to the LENOVO SPLASH SCREEN FEEZE...

BIOS Screens shots


Apologies about the size of the images. I did not realise there was not % size option.

Oh.. Hold on.. I just left it for like 10mins on the Splash Screen and it's Finally decided to load UBUNTU?

What could be causing this then? hmm.. something seems not right somewhere.

Logged in and it's frozen on me... so still not right.

Its logged in finally but running like a Dog.

---

### Post by tea for one on 2021-09-01
Boot mode - Legacy Support
Boot Priority - Legacy First

Did you not say you installed in UEFI mode?
Also, which drive contains your Ubuntu installation - eMMC or NVME?

---

### Post by popnippon on 2021-09-01
This is a paste from the efibootmgr

> 
[LIST]
[*][COLOR=#000000]mark@UbuntuLaptop:~$ sudo efibootmgr -v[/COLOR]

[*][COLOR=#000000][sudo] password for mark: [/COLOR]

[*][COLOR=#000000]BootCurrent: 000D[/COLOR]

[*][COLOR=#000000]Timeout: 0 seconds[/COLOR]

[*][COLOR=#000000]BootOrder: 000D,000A,000B,0000,0003,0005,0004,0006,0007,0008,000C,0009[/COLOR]

[*][COLOR=#000000]Boot0000* Windows Boot Manager	HD(1,GPT,916e28c6-a8a4-4b30-80eb-028586e57da8,0x800,0x100000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................[/COLOR]

[*][COLOR=#000000]Boot0001  Setup	FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)[/COLOR]

[*][COLOR=#000000]Boot0002  Boot Menu	FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)[/COLOR]

[*][COLOR=#000000]Boot0003* NVMe:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a4)[/COLOR]

[*][COLOR=#000000]Boot0004* ATA HDD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)[/COLOR]

[*][COLOR=#000000]Boot0005* ATA HDD1:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)[/COLOR]

[*][COLOR=#000000]Boot0006* ATAPI CD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)[/COLOR]

[*][COLOR=#000000]Boot0007* USB CD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)[/COLOR]

[*][COLOR=#000000]Boot0008* PCI LAN:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)[/COLOR]

[*][COLOR=#000000]Boot0009* USB FDD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)[/COLOR]

[*][COLOR=#000000]Boot000A* eMMC Card: SanDisk iNAND DF4032	PciRoot(0x0)/Pci(0x1c,0x0)/eMMC(0)/Ctrl(0x0)c.J8.p[H...S....[/COLOR]

[*][COLOR=#000000]Boot000B* USB HDD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)[/COLOR]

[*][COLOR=#000000]Boot000C* USB LAN:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322)[/COLOR]

[*][COLOR=#000000]Boot000D* ubuntu	HD(1,GPT,0eb39de6-2016-4053-b575-ce0fec88c3f0,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)[/COLOR]
[/LIST]


---

### Post by popnippon on 2021-09-01
> **tea for one said:**
> Boot mode - Legacy Support
Boot Priority - Legacy First

Did you not say you installed in UEFI mode?
Also, which drive contains your Ubuntu installation - eMMC or NVME?

Done this
Boot mode - Legacy Support
Boot Priority - Legacy First

Also, moved NVME to boot first. 

I thought it had resolved it! As when F10'd it... then it booted straight into fast Ubuntu.

Shut the machine down and started back up again... BANG! Straight into fast Ubuntu again.

3rd time shutting down and starting back up again... FREEZE on the Lenovo screen again.

---

### Post by tea for one on 2021-09-01
Well, that's progressed somewhat?

I would change the UEFI Boot mode and Boot priority to UEFI and see if there is another improvement.

Also, did you run [COLOR="#0000FF"]fsck[/COLOR] from a live session after your earlier hard shutdown episode?

---

### Post by popnippon on 2021-09-01
> **tea for one said:**
> Well, that's progressed somewhat?

I would change the UEFI Boot mode and Boot priority to UEFI and see if there is another improvement.

Also, did you run [COLOR=#0000FF]fsck[/COLOR] from a live session after your earlier hard shutdown episode?

Changed it back to UEFI Boot mode and it booted into fast Ubuntu.

Shut down (properly)... loaded up again with GRUB. Pressed enter and BANG! straight into Ubuntu.

Third Shutdown (properly)... loaded it up again with GRUB.. allowed the timer to go through and Frozen on the Splash Screen.

Forth Time Shutdown (properly)... loaded it up again with GRUB... Pressed enter and Frozen on the Splash Screen.

I will try a live USB and run fsck (If I can remember how)

---

### Post by popnippon on 2021-09-01
[COLOR=#1F2937][FONT=&amp] Ran the following in Live CD Mode sudo fsck -p /dev/sda1

It said there was differences but nothing it was going to fix automatically?

Rebooted the installed version and BANG! Straight back to the Splash screen Freeze[/FONT][/COLOR]

---

### Post by tea for one on 2021-09-01
If you have a UEFI installation, you must have a minimum of two partitions?

Is sda1 your EFI System Partition?

Can you run this command in the terminal and post the output between code tags:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```

---

### Post by popnippon on 2021-09-01
Sure, Here is the command reulst

```
NAME                 SIZE TYPE FSTYPE      FSUSE% FSAVAIL MOUNTPOINT
mmcblk0             29.1G disk                            
&#9500;&#9472;mmcblk0p1          512M part vfat            2%  503.2M /boot/efi
&#9492;&#9472;mmcblk0p2         28.6G part LVM2_member                
  &#9500;&#9472;vgubuntu-root   27.7G lvm  ext4           22%   19.9G /
  &#9492;&#9472;vgubuntu-swap_1  976M lvm  swap                       [SWAP]
mmcblk0boot0           4M disk                            
mmcblk0boot1           4M disk   
```

---

### Post by tea for one on 2021-09-01
That looks like a 32GB eMMC disk with LVM.
Also you have a swap partition where a regular installation of Ubuntu automatically creates a swapfile.

Your earlier attempt at fsck with sda was acting on an incorrect/missing device.

I have zero experience of using fsck with LVM but you can try this via a live session:-

For your EFI partition
```
sudo fsck /dev/mmcblk0p1
```
For your Ubuntu partition
```
sudo fsck /dev/mmcblk0p2
```

Out of curiosity, why did you choose to install with this partition scheme?

---

### Post by popnippon on 2021-09-01
Should there be so many partitions? Or should some of these be deleted?

[IMG]https://i.ibb.co/94nTzpb/Screenshot-from-2021-09-01-22-36-22.png[/IMG]

---

### Post by popnippon on 2021-09-01
> **tea for one said:**
> That looks like a 32GB eMMC disk with LVM.
Also you have a swap partition where a regular installation of Ubuntu automatically creates a swapfile.

Your earlier attempt at fsck with sda was acting on an incorrect/missing device.

I have zero experience of using fsck with LVM but you can try this via a live session:-

For your EFI partition
```
sudo fsck /dev/mmcblk0p1
```
For your Ubuntu partition
```
sudo fsck /dev/mmcblk0p2
```

Out of curiosity, why did you choose to install with this partition scheme?

I think its because I tried to install with a secure install and had the same issues so reinstalled again and expected Ubuntu install to clear-down things it had created. Obviously not so maybe this is part of the issue?

---

### Post by oldfred on 2021-09-01
Please attach screen shots.

You are using LVM which is required if using encryption, but otherwise is a bit more advanced as it uses volumes inside one large partition. The ESP must be outside the LVM as that is the only way UEFI can read it.
LVM offers some advanced features but at a bit more complexity. Often better not to use unless somewhat familiar with Linux, partitions & command line.

---

### Post by tea for one on 2021-09-01
> **popnippon said:**
> I think its because I tried to install with a secure install and had the same issues so reinstalled again and expected Ubuntu install to clear-down things it had created. Obviously not so maybe this is part of the issue?

Quite possibly part of the issue.
Are you using encryption now?

---

### Post by popnippon on 2021-09-02
Sorry guys, UK based here so went to bed.

I cleared the multiple partitions and reinstalled Ubuntu via USB completey standard not changing anything.

Again... After first reboot logged in without issue. Shutdown and it powered up okay.

2nd shutdown and powered up it got stuck again on splash screen.


I will attempt to login this morning take some scrrenshots of what the BIOS is looking like and also what the script now shows with regards to what partitions are where. 


Thankyou for all your help so far. Feels like we might be finally getting somewhere.

---

### Post by popnippon on 2021-09-02
Good morning guys,

Before doing anything I just tried to boot it up and I get this message.

```
[ 0.440184] x86/cpu: SGX disabled by BIO/dev/mmcblkop2: clean, 139842/1875968 files, 1822792/7502336 blocks
[ 112.474154] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0]
[ Number changes...] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0]
[ Number changes...] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0]
```

and it just seems to sit there for many iterations and not do anything...

Quick update... this just popped up also...

```
[93.634644] rcu INFOL rcu_sched self-detected stall on CPU
```


**Update - I've left it for over and hour and it looks like it hobbled into Ubuntu, running slow as hell and hardly useable but at least it did eventually boot.... Kinda.**


Now that I got into the system I re-ran the same code after the re-install of UBUNTU and the results are below:

```

[LIST]
[*][COLOR=#000000]NAME          SIZE TYPE FSTYPE FSUSE% FSAVAIL MOUNTPOINT[/COLOR]
[*][COLOR=#000000]mmcblk0      29.1G disk                       [/COLOR]
[*][COLOR=#000000]&#9500;&#9472;mmcblk0p1   512M part vfat       2%  503.2M /boot/efi[/COLOR]
[*][COLOR=#000000]&#9492;&#9472;mmcblk0p2  28.6G part ext4      23%   20.2G /[/COLOR]
[*][COLOR=#000000]mmcblk0boot0    4M disk                       [/COLOR]
[*][COLOR=#000000]mmcblk0boot1    4M disk   [/COLOR]
[/LIST]

```

A screenshot of the Disks in Ubuntu currently. Should match up with what is above.
[IMG]https://i.ibb.co/bz1gC0k/Screenshot-from-2021-09-02-10-13-22.png[/IMG]

BIOS Screenshots as they are are the moment...

[[IMG]https://i.ibb.co/XZX3XfW/BIOS1.png[/IMG]]("https://ibb.co/XZX3XfW") [[IMG]https://i.ibb.co/34NMfVY/BIOS2.png[/IMG]]("https://ibb.co/34NMfVY") [[IMG]https://i.ibb.co/3TL9jcn/BIOS3.png[/IMG]]("https://ibb.co/3TL9jcn") [[IMG]https://i.ibb.co/3BS1XCj/BIOS4.png[/IMG]]("https://ibb.co/3BS1XCj") [[IMG]https://i.ibb.co/t47hT1S/BIOS5.png[/IMG]]("https://ibb.co/t47hT1S")

**Just a note **- I did just move the emmC Card: Sandisk 1NAND DF4032 up to the Number 1 Spot and rebooted the machine. It booted into UBUNTU without issue.

However... I have done this a number of times and after several correct shutdowns and restarts it will go back to freezing again.

---

### Post by tea for one on 2021-09-02
In your UEFI set-up:-

[COLOR="#0000FF"]Intel Virtual Technology[/COLOR] - Disable is worth a try
[COLOR="#0000FF"]Boot mode and Boot priority[/COLOR] - Can you change to UEFI

Partitions look OK now.

```
[ 112.474154] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0]
[ Number changes...] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0]
``` 
```
[93.634644] rcu INFOL rcu_sched self-detected stall on CPU
```
I've never seen those two messages before so I do not know what to suggest.

---

### Post by popnippon on 2021-09-02
> **tea for one said:**
> In your UEFI set-up:-

[COLOR=#0000FF]Intel Virtual Technology[/COLOR] - Disable is worth a try
[COLOR=#0000FF]Boot mode and Boot priority[/COLOR] - Can you change to UEFI

Partitions look OK now.

```
[ 112.474154] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0]
[ Number changes...] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0]
``` 
```
[93.634644] rcu INFOL rcu_sched self-detected stall on CPU
```
I've never seen those two messages before so I do not know what to suggest.

Tried the above mentioned in the BIOS.. and when it Saved and Exited BIOS is boots into UBUNTU No problem.

When shutting down... and restarting after 10 seconds I get the following:

```
BusyBox v1.30 (Ubuntu 1:1.30.1-4ubuntu6.3) built-in shell (ash)
Enter 'help for a list of built-in commands.

(initramfs)

```

---

### Post by tea for one on 2021-09-02
Here is some info [https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/](https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/)

In post 25, the image shows SD Card Reader DF 4032 - Is this an eMMC storage device soldered to the motherboard or an SD card inserted into the Card Reader slot?

---

### Post by popnippon on 2021-09-02
> **tea for one said:**
> Here is some info [https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/](https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/)

In post 25, the image shows SD Card Reader DF 4032 - Is this an eMMC storage device soldered to the motherboard or an SD card inserted into the Card Reader slot?

Its an eMMC soldered to the motherboard.

---

### Post by popnippon on 2021-09-02
> **tea for one said:**
> Here is some info [https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/](https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/)

In post 25, the image shows SD Card Reader DF 4032 - Is this an eMMC storage device soldered to the motherboard or an SD card inserted into the Card Reader slot?

This this... and this was the result...

[[img]https://i.ibb.co/h7jBRYK/20210902-132713-Small.jpg[/img]](https://ibb.co/h7jBRYK)

---

### Post by oldfred on 2021-09-02
Have you updated UEFI?
Many systems need that even just for security patches, but update often fixes many issues not listed in what update fixes.

Are you installing Ubuntu or a lightweight flavor?

---

### Post by popnippon on 2021-09-02
> **oldfred said:**
> Have you updated UEFI?
Many systems need that even just for security patches, but update often fixes many issues not listed in what update fixes.

Are you installing Ubuntu or a lightweight flavor?

I will be honest I've never needed to or know how to update UEFI. So I've not touched it since the machine was new a few years back.

I'm installing full Ubunutu but without all of the applications. Just the browser and a few bits.

I downloaded the driver for the machine from the Lenovo site but only allows you to update it from Windows (This is a single OS machine, Ubuntu)

---

### Post by oldfred on 2021-09-02
Most systems have multiple ways to update UEFI.
Many will directly read an update file from within UEFI if update file in FAT32 formatted partition as that is all UEFI reads.
Can you download just the update file?

HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

Some older systems also updated with DOS bootable flash drive to run the exe file. 
They even offered a download of the DOS executable to make the bootable DOS flash drive.

---

### Post by popnippon on 2021-09-02
> **oldfred said:**
> Most systems have multiple ways to update UEFI.
Many will directly read an update file from within UEFI if update file in FAT32 formatted partition as that is all UEFI reads.
Can you download just the update file?

HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

Some older systems also updated with DOS bootable flash drive to run the exe file. 
They even offered a download of the DOS executable to make the bootable DOS flash drive.


Not with this one it seems.

[https://pcsupport.lenovo.com/gb/en/products/laptops-and-netbooks/100-series/130s-11igm/downloads/ds504763-bios-update-for-windows-10-64-bit-notebook](https://pcsupport.lenovo.com/gb/en/products/laptops-and-netbooks/100-series/130s-11igm/downloads/ds504763-bios-update-for-windows-10-64-bit-notebook)

Also in the BIOS there is no option I can see for updating from local media.

---

### Post by popnippon on 2021-09-02
Interesting... Was just looking at the logs in UBUNTU as it has marked one as

```

System - FAT-fs (sda1): unable to read boot sector to mark fs as dirty

```

Whether or not that has anything to do with the very strange and odd sporadic booting on this machine?!

---

### Post by tea for one on 2021-09-02
> **popnippon said:**
> Interesting... Was just looking at the logs in UBUNTU as it has marked one as

```

System - FAT-fs (sda1): unable to read boot sector to mark fs as dirty

```

Whether or not that has anything to do with the very strange and odd sporadic booting on this machine?!

I don't think so because your device has two partitions:-

/dev/mmcblk0p1 - Fat32
/dev/mmcblk0p2 - Ext4

Do you have any other devices plugged in to a USB port?

In your position now, I would be tempted to try a lighter version of the Ubuntu family such as Xubuntu 20.04LTS.

Alternatively, you can download a Windows 10 ISO, install Windows 10 and then try to update the UEFI firmware within Windows.
You do not need a product key to install Windows 10 but it may complain when trying to update UEFI.
This is a bit of a stretch so I would give Xubuntu 20.04 LTS a spin first.

---

### Post by popnippon on 2021-09-02
> **tea for one said:**
> I don't think so because your device has two partitions:-

/dev/mmcblk0p1 - Fat32
/dev/mmcblk0p2 - Ext4

Do you have any other devices plugged in to a USB port?

In your position now, I would be tempted to try a lighter version of the Ubuntu family such as Xubuntu 20.04LTS.

Alternatively, you can download a Windows 10 ISO, install Windows 10 and then try to update the UEFI firmware within Windows.
You do not need a product key to install Windows 10 but it may complain when trying to update UEFI.
This is a bit of a stretch so I would give Xubuntu 20.04 LTS a spin first.

Installed xUbuntu... up and running fine.

Shut the machine down.... turned it back on... LENOVO Splash Screen frozen again.

I think this laptop is heading to the tip.

---

### Post by popnippon on 2021-09-02
Ah.. I have found a similarity...

Each time I go into the BIO boot options and move the eMMC to the top to boot first and then F10 out... It boots into xUbuntu without an issue.

If I reboot the machine (not shutdown) it boots back into Xubuntu...

However if I shutdown the machine fully... it will Freeze On me.

Reboot and check BIOS... Ubuntu is back at the top and not eMMC!

Maybe the previous commenter could be right about the CMOS battery not saving changes?

Just tested it over and over again... These seems to be it.

Whenever it freezes it's because 'Ubuntu' it set as No.1 Boot position. If I move eMMC to no.1 boot position it seems to boot no problem.

Now it's a case of find out what it's not saving my change? Could it be the CMOS?

---

### Post by popnippon on 2021-09-02
I've ordered another CMOS for it.. so we will see if this was the answer all along and will update this thread.

---

### Post by tea for one on 2021-09-02
> **popnippon said:**
> Ah.. I have found a similarity...
Each time I go into the BIO boot options and move the eMMC to the top to boot first and then F10 out... It boots into xUbuntu without an issue.
If I reboot the machine (not shutdown) it boots back into Xubuntu...
However if I shutdown the machine fully... it will Freeze On me.
Reboot and check BIOS... Ubuntu is back at the top and not eMMC!
Maybe the previous commenter could be right about the CMOS battery not saving changes?
Just tested it over and over again... These seems to be it.
Whenever it freezes it's because 'Ubuntu' it set as No.1 Boot position. If I move eMMC to no.1 boot position it seems to boot no problem.
Now it's a case of find out what it's not saving my change? Could it be the CMOS?

That looks like a interesting discovery on your part.
At least, you now can boot without a problem, although a bit cumbersome at the moment.

When you mention the BIOS, are you referring to:-

F2 - Enter UEFI Set Up
F12 - Boot menu

Perhaps one is misbehaving and the other one may [COLOR="#0000FF"]remember[/COLOR] your selection?

---

### Post by popnippon on 2021-09-02
Yeah, Hoping its the CMOS as it always brings up the Grub and don't remember my boot options.

When I say BIOS i'm talking about F2

---

### Post by popnippon on 2021-09-05
Okay,

Quick update... CMOS did not fix the problem.

It seems to all be down to the 'Boot Order' not saving.

Kind of at a loss at the moment. If any one has ideas that would be a great help.

---

### Post by oldfred on 2021-09-05
Are you changing Boot Order in UEFI/BIOS, or the f2 & then boot tab?

---

### Post by popnippon on 2021-09-06
> **oldfred said:**
> Are you changing Boot Order in UEFI/BIOS, or the f2 & then boot tab?

I have changed it in F2 and when you have the option to change the UEFI option on the screen, it reboots the system and logs you straight into the BIOS where you can also change the Boot Order but nothing saves.

It keeps the option for 'Ubuntu' at the top.

1. Ubuntu
2. eMMC Sandisk.

I have the move No.2 to No.1 Position.. F10 then it boots fine.

---

### Post by tea for one on 2021-09-06
F2 is the key for your UEFI/BIOS but you should also have another Boot Menu?

Does not F12 after power on give you another Boot menu (without entering the UEFI set up)?

---

### Post by popnippon on 2021-09-06
> **tea for one said:**
> F2 is the key for your UEFI/BIOS but you should also have another Boot Menu?

Does not F12 after power on give you another Boot menu (without entering the UEFI set up)?

Sorry Yes, that Boot menu does appear.

1. ubuntu
2. emmC Card: SanDisk iNAND DF4032
3. Windows Boot Manager

I need No.2 to be in place of No.1 for it to boot but cannot make changes to save in BIOS.

Note to add: Selecting option 2 from the F12 Menu also freezes the machine and won't boot.

---

### Post by tea for one on 2021-09-06
> **popnippon said:**
> Sorry Yes, that Boot menu does appear.

1. ubuntu
2. emmC Card: SanDisk iNAND DF4032
3. Windows Boot Manager

I need No.2 to be in place of No.1 for it to boot but cannot make changes to save in BIOS.
Yes, I understand that the UEFI firmware does not remember your desired settings.
I wonder why the Windows Boot manager is present when you only have Xubuntu installed?
> **popnippon said:**
> Note to add: Selecting option 2 from the F12 Menu also freezes the machine and won't boot.
That is very odd - together with being unable to save your desired boot option in UEFI settings...........

Can you boot into Xubuntu, open a terminal and post the result of this command:-
```
sudo efibootmgr -v
```

---

### Post by popnippon on 2021-09-06
> **tea for one said:**
> Yes, I understand that the UEFI firmware does not remember your desired settings.
I wonder why the Windows Boot manager is present when you only have Xubuntu installed?

That is very odd - together with being unable to save your desired boot option in UEFI settings...........

Can you boot into Xubuntu, open a terminal and post the result of this command:-
```
sudo efibootmgr -v
```

Thanks for your reply

I actually removed xUbuntu and put Ubuntu back on as the problem did not seem to be to do with the Machine not being able to run Ubuntu as it runs fine, just a very confused Boot menu! Haha!

Here are the results

```

[LIST]
[*][COLOR=#000000]mark@UbuntuLaptop:~$ sudo efibootmgr -v[/COLOR]
[*][COLOR=#000000]BootCurrent: 000A[/COLOR]
[*][COLOR=#000000]Timeout: 0 seconds[/COLOR]
[*][COLOR=#000000]BootOrder: 000D,000A,000B,0003,0000,0005,0004,0006,0007,0008,000C,0009[/COLOR]
[*][COLOR=#000000]Boot0000* Windows Boot Manager    HD(1,GPT,916e28c6-a8a4-4b30-80eb-028586e57da8,0x800,0x100000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................[/COLOR]
[*][COLOR=#000000]Boot0001  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)[/COLOR]
[*][COLOR=#000000]Boot0002  Boot Menu    FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)[/COLOR]
[*][COLOR=#000000]Boot0003* NVMe:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a4)[/COLOR]
[*][COLOR=#000000]Boot0004* ATA HDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)[/COLOR]
[*][COLOR=#000000]Boot0005* ATA HDD1:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)[/COLOR]
[*][COLOR=#000000]Boot0006* ATAPI CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)[/COLOR]
[*][COLOR=#000000]Boot0007* USB CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)[/COLOR]
[*][COLOR=#000000]Boot0008* PCI LAN:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)[/COLOR]
[*][COLOR=#000000]Boot0009* USB FDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)[/COLOR]
[*][COLOR=#000000]Boot000A* eMMC Card: SanDisk iNAND DF4032    PciRoot(0x0)/Pci(0x1c,0x0)/eMMC(0)/Ctrl(0x0)c.J8.p[H...S....[/COLOR]
[*][COLOR=#000000]Boot000B* USB HDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)[/COLOR]
[*][COLOR=#000000]Boot000C* USB LAN:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322)[/COLOR]
[*][COLOR=#000000]Boot000D* ubuntu    HD(1,GPT,4e6b50b1-b8d1-4f12-b539-13421d2e6f95,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)[/COLOR]
[/LIST]

```

---

### Post by tea for one on 2021-09-06
You could try to change the boot order in efibootmgr.
You need [COLOR="#0000FF"]000A[/COLOR] to be first in the list.

Here is a tutorial/guide [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

It might even be worth removing every other entry to see what happens?

You have backed up your data, haven't you?

---

### Post by popnippon on 2021-09-06
> **tea for one said:**
> You could try to change the boot order in efibootmgr.
You need [COLOR=#0000FF]000A[/COLOR] to be first in the list.

Here is a tutorial/guide [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

It might even be worth removing every other entry to see what happens?

You have backed up your data, haven't you?

tried to remove the 'UBUNTU' entry and it seemed to work for a moment, then on the 2nd attempt to restart it magically came back! haa!

---

