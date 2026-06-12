---
title: "Booting issue on Ubuntu 13.04"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by bloouuno on 2013-05-05
Hi!
I had some issues with my win 7 so I decided to change it to Ubuntu.
I used a live USB key to get to the installation manager or whatever it is called.
At this point there is no problem. I chose the delete everything and install linux option and went on 'til the end.
The fact is that when i take out my USB key and boot, I receive the message: Reboot and select proper boot device.
This even though I have only one hard disk. Choosing this very one in the Bios won't change a thing.
Also, when I let my USB key on my computer, it somehow manages to get to the ubuntu loading page and turns to console mode with the text "Kernel panic: Not syncing attempted" on it.
It seems my live CD is fine and that it corresponds to my computers settings (X 64).
I tried it numerous time ( no data to lose so...) using the "take all disk option" and the other one by creating a boot partition, a /, a /home (both in ext4) and a swap. 
It always end up the same way.
As for now i'm using the live CD to post this, I can't use any windows tools (which by the way are the one that led to ir crashing).
This is what gparted shows of the job done by ubuntu install. I don't get the use of Lvm2 pv file sytem. When i look at the file system support this looks wrong.

[ATTACH=CONFIG]242241[/ATTACH]
Well, since I haven't got a clue about what's goin' ont, i'd be **really** delighted to receive some help.
I don't know the console's command to get more info so I'll will give a try later.
Thanks anyway and sorry for my english!

---

### Post by oldfred on 2013-05-05
I do not know encryption, but it uses lvm for full disk encrytion.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by bloouuno on 2013-05-06
I tried the "Repair usual issues" option and got this link;
[http://paste.ubuntu.com/5638962/](http://paste.ubuntu.com/5638962/)
And... it doesn't work.

---

### Post by oldfred on 2013-05-06
I do not know LVM and whether that really works with UEFI or not.

You have grub in separate /boot partition so you should get grub menu, but with one system installed it will not show it by default. If you hold shift down from UEFI/BIOS do you get menu. Some with UEFI have to use escape key instead.

Some systems need extra boot parameters which you need to add onto grub menu linux line.
       [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

    
You can boot Ubuntu with BIOS on gpt partitioned drives but then need a bios_grub partition instead of the efi partition. A bios_grub is only 1MB unformatted space anywhere on drive. You can set bios_grub using gparted and manage flags.

---

### Post by bloouuno on 2013-05-06
Hi! thanks for your reply.
I tried the shift down thing as well as escape and it doesn't do anything.
What seems wrong to me is that I can get to the grub menu when my Usb device is in. May Ubuntu have installed the boot or some needed files on it.
Also when I get to the Menu i can change the language and that's it. F# keys won't work so I can'tt access the other options.
Finally the lvm part is bothering me as I can't change the partition in another system file nor modify its size.

Looking as the many issues I have I will probably try a new install ( another one..) and try to partition everything by myself.
Can you confirm what I need?
A ext4: /  (40 go)
A ext4: /home   ;not necessary but I want one (454 go)
A swap:  ( 5 go) (I have 4 of DDR 2 or 3)
A bios partition with the boot flag ( 1 mo)
?

---

### Post by oldfred on 2013-05-06
Those partitions should be ok. I use 25GB for / as I put all data in other partitions and with lots of apps use about 9GB of the 25GB.

I would leave efi partition in case later you want UEFI. It is difficult to add a partition at the beginning of the drive later. Be sure to keep it gpt, not MBR(msdos).

       If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Windows only boots in UEFI mode from gpt partitioned drives.

---

### Post by bloouuno on 2013-05-06
So it would be:
All primary partitions:
sda1: efi  ; 1 mb  
sda2:swap  ; 5 gb
sda3: ext4: /    ; 25gb
sda4: ext4: /home ; 469 gb
sda5: BIOS booting reserved area ( translated from french): 1 mo. !!! Is this really the bios grub partition????? (Just wanna be sure about it)
Can I really create more than four primary partitons in one hard disk?
Is that it?

---

### Post by oldfred on 2013-05-06
The efi needs to be 250 or 300MB FAT32 and a bios_grub is 1MB unformatted. 

With gpt you can only have 128 partitions, there is only one type so in effect they all are primary.

       In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

---

### Post by bloouuno on 2013-05-08
Hi.
So I made it like this:
25 gb ext 4 :  /
436 gB ext 4: /home
237 mb: fat 32 : boot
6 gb: swap
1 mb: bios grub
And I still have got the same problem that I used to have.
Which means that the computer will start and show the bios (F2 choice page)  (not the grub one) and then write "reboot and select proper boot device".
I really don't get it anymore. I have Bios grub as well as a boot partition, the / and swap ones as well. What more doest it needs?
Well, whatever. I WILL have Ubuntu on my computer.
So, here is the last link:
[http://paste.ubuntu.com/5644275/](http://paste.ubuntu.com/5644275/)
Thank you.

---

### Post by oldfred on 2013-05-08
You are still trying to boot in UEFI mode. You need grub installed to protective MBR and UEFI set to BIOS/CSM/Legacy  not UEFI.
Boot-Repair should convert install to BIOS mode by uninstalling grub-efi and installing grub-pc which will put grub2's boot loader into the MBR. Then you have to have BIOS use MBR not efi partition.

It can convert from/to BIOS or UEFI.
 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

---

### Post by bloouuno on 2013-05-11
So, to make sure.
Since my previous installation have damaged the generic Mbr that i had (am I right?), I should use boot repair to restore it on /sda.
When looking at the diagnostic that I posted, I saw no boot loader in the MBR of sda. Is that what caused the booting issues.
Just wainting for confirmation now.
Processus: Using boot-repair:
Select restore Mbr. At this point in the Mbr options must I keep in the  "partition booted by the mbr" choice, sda2 which is my /  ("linux core partition")?
Lauch the repair. Boot-repair will restore my mbr, uninstall grub from its current location and then reinstall it into the Mbr.
Finally, my computer should boot on my Mbr which will boot the ubuntu partition.
Sorry if it takes time but I 'm quite strarting from scratch here when it comes to Ubuntu.
Also thanks for helping!

---

### Post by oldfred on 2013-05-11
The new UEFI does not use the MBR, it uses folders in the efi partition for booting. It needs the new gpt partitioning to boot, but gpt has a protective MBR just so old disk tools see a partition table not an unformatted drive that they may damage.

The 30 year old BIOS uses the MBR which is just the first sector on a drive. 
Ubuntu will boot from a gpt partitioned drive with either UEFI (with efi partition) or BIOS (using MBR).  
Or it will boot from a MBR(msdos) partitioned drive with BIOS.

You do have to have UEFI/BIOS set to the mode you want either UEFI or BIOS but also have to boot Ubuntu installer in the mode you want. Live installer offers either UEFI or BIOS boot and then installs in that mode. But the selection is only from the UEFI menu as you boot installer.

---

### Post by bloouuno on 2013-05-11
I know that I can change the UEFI to BIOS in my Bios in boot section.
However I don't remeber having had the choice when booting the installer.
As far as I remember the first menu I get give me 4 choices: Try without installing; Install; check cd for errors; a fourth one I can't remember. When in the install I haven't seen any pages mentioning the UEFI or BIOS.
Practically what should I do to make my computer stop booting in UEFI mode? Firstly, change it in the bios so goes from UEFI to BIOS/legacy.
Secondly? Run boot-repair so it restores my Mbr partition on the first section of my HDD ?

---

### Post by oldfred on 2013-05-11
Once you get to the Ubuntu install or live mode menu you have booted in either BIOS or UEFI mode. It is from the UEFI menu that you should see two choices to boot flash drive. One is UEFI and the other Legacy/CSM/BIOS or whatever. Then that is how it installs. Maybe if your system is set for CSM, then it will only boot flash in BIOS mode? Some still give both alternatives.

But however you install if it does not boot, Boot-Repair should be able to fix. It can also convert a UEFI install to BIOS or a BIOS install to UEFI if drive is gpt partitioned and you have either or both the efi partition and the bios_grub partition.

---

### Post by bloouuno on 2013-05-11
Ok. 
So for now I will run boot-repair. I will see what happens and report it here.

---

### Post by bloouuno on 2013-05-11
Mmm.
Nope.
Afer using boot repair succesfully (so it said) I rebootted my computer. After my usual efi bios page I got a black one. Actually a console if not for the fact that I couldn't write in it.
Also I went into the bios to see if i could choose to boot my Usb stick another way. Actually I can't change it from UEFI. There is no menu allowing me to do so.
Should I restore my Mbr even when I can't boot from a gpt partitionned drive with BIOS.
Here is the link:
[http://paste.ubuntu.com/5655412/](http://paste.ubuntu.com/5655412/)

---

### Post by oldfred on 2013-05-11
You are still configured for UEFI boot. You have no boot loader in the MBR and have a mount of the efi partition in fstab.
You should be able to boot in UEFI mode with secure boot off?

Do you get a grub menu or you will not normally get grub menu as you only have one system installed. Does hoelding shift or escape from UEFI give you grub menu.
If so it may be a video issue.
What video card/chip do you have?

---

### Post by bloouuno on 2013-05-11
When I boot from my USB stick, it is wrtitten that the secure mode is off.
When I boot froom my HDD without my USB in I get to the console (blach screen with the typing pointer) wich allows me no action. So I have to shut down my computer and restart.

My video chip is : Gallium 0.4 on AMD PALM
I checked for it and it runs well with ubuntu 10.04 and 10.10. So it more likely isn't the issue.
Also it my paste link it is written that there is a boot loader installed on my Usb stick and none on the mbr of my HDD. I take it it must be installed in efi in my case so I might be wrong but can that change anything or is the boot loader the one from the live cd?

---

### Post by oldfred on 2013-05-11
The old Ubuntu installs do not even have UEFI, so they would be BIOS if the even work. Usually they are too old to have the newer drivers required by UEFI systems.

I do not know AMD.
 ATI/Radeon ----------------------------------------------------
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

edit
I did not recognize Gallium, so I assumed AMD, it may be nVidia?
[http://ubuntuforums.org/showthread.php?t=2107105](http://ubuntuforums.org/showthread.php?t=2107105)

If nVidia then nomodeset should work.

---

### Post by bloouuno on 2013-05-16
Sorry. Not beeh here for some time.
Actually when i press Escape ( or SHIFT, actually both) I get a simple menu which allows me to choose between my HDD and then :
1) USB device
2) UEFI USB Device
Since I used to launched in UEFI I picked the first one.
I was half surprised in fact when I saw that the same occurs as when I boot on my HDD with my USB stick (live Ubuntu) in it.
So how come my Ubuntu version which was installed on my HDD boot from my USB device? This even though I am booting in EFI mode and I have one EFI partition on my HDD. Shouldn't it be bootable at least? I mean the HDD without the USB stick with live Ubuntu on it.
I'm wondering now if my USB stick is ok. I may should have begun by this but I'm going to create another USB live and try to reinstall. Also I'll be very careful on wich version I'll install.
I'll surely do it by this evening so I'll post to tell you the changes it may bring.

---

### Post by shanal on 2013-05-16
> **bloouuno said:**
> Hi! thanks for your reply.
I tried the shift down thing as well as escape and it doesn't do anything.
What seems wrong to me is that I can get to the grub menu when my Usb device is in. May Ubuntu have installed the boot or some needed files on it.
Also when I get to the Menu i can change the language and that's it. F# keys won't work so I can'tt access the other options.
Finally the lvm part is bothering me as I can't change the partition in another system file nor modify its size.

Looking as the many issues I have I will probably try a new install ( another one..) and try to partition everything by myself.
Can you confirm what I need?
A ext4: /  (40 go)
A ext4: /home   ;not necessary but I want one (454 go)
A swap:  ( 5 go) (I have 4 of DDR 2 or 3)
A bios partition with the boot flag ( 1 mo)
?

I had problem similar to yours. I think that the live cd has put the MBR file (Master boot record ) on your USB device.That is why you get the grub menu when your usb device is in.
try reinstalling the OS. 
and while you are manually specifying the details please check that the MBR file is created at the hard drive(sda) not the USB drive(sdb). 
Better still, first change the boot order from the BIOS kepping the hard disk above the USB device before installing. You can boot using usb device by accessing boot options at the time of start up.

Tell me whether it solved your problem or not.

---

### Post by bloouuno on 2013-05-17
I'll answer by this evening. Thanks.

---

### Post by bloouuno on 2013-05-28
Hi. sorry for the delay. Installing another live Ubuntu fixed my issues. However I couldn't choose my partitions and had to use auto install.
 I managed to get to Ubuntu desktop. Also I had to use boot repair cause it wouldn't launch another time. It worked!
Well that was a short relief. Two days later: RIP graphic chip.
Damn it.
Whatever. The issue was only the booting device.
Thanks everyone.

---

