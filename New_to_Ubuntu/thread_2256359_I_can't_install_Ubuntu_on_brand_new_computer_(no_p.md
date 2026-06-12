---
title: "I can't install Ubuntu on brand new computer (no previous OS)"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by eeeark1 on 2014-12-11
Hello,

I decided I would try and build a new system myself. As far as I can tell I’ve successfully done so as it boots into the BIOS just fine. I’m having trouble getting Ubuntu 14.04 to install from a usb though. I was just getting a black screen. I've looked into this “nomodeset” stuff here:

 [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

and that doesn’t seem to be helping. It does scroll a bunch of nonsensical (to me) text (wasn’t doing this before) but still ends up telling me this:

"BusyBox v1.21.1…blah blah
Enter ‘help’ for…blah blah
(initramfs) Unable to find a medium containing a live file system" and the keyboard does nothing any longer, I end up having to use the physical power button to turn machine off.

How would one go about fixing this? I have searched around and not found anything that's actually worked thus far. I'm sure I'm just not searching for the correct terms or am just missing the right page but I'm beginning to get fed up. Any help would be greatly appreciated.

---

### Post by eeeark1 on 2014-12-11
the internals of the machine I've built might be useful...sorry. Bought all of this from Newegg:

MB GIGABYTE|GA-970A-UD3P AM3+ R           
 
VGA ASUS|GTX750TI-OC-2GD5 RT      
 
PSU RAIDMAX | HYBRID2 RX-530SS 530W   
 
CPU AMD|8-CORE FX-8350 4.0G 8M R
 
MEM 8G|KINGSTON HX316C10FB/8 R
 
HDD 1T|WD WD10EZEX SATA6G %

---

### Post by oldfred on 2014-12-11
UEFI or BIOS, And planning on dual booting?
How you choose to boot flash drive is how it will install.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Gigabyte motherboards need a setting in UEFI/BIOS for IOMMU.
      
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

You may have to use a ppa to install a newer nVidia driver than is in the repository. Do not download from nVidia as ppa are pre-configured and will work better.
      
 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---

### Post by eeeark1 on 2014-12-11
Not sure of the difference between UEFI and BIOS but from the link you gave I'm not sure it matters since this will be the only/first OS installed, correct?
 Not planning on dual booting as I don't have any other OSs to install and don't want to pay for one.

---

### Post by oldfred on 2014-12-11
Advantages are not huge, but you may want gpt partitioning regardless of UEFI or BIOS.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by eeeark1 on 2014-12-12
I sincerely appreciate all the help but I'm very new to linux/Ubuntu and don't understand half of what you've written. I read and tried the IOMMU setting stuff and finally got the installer to run. Internet worked fine so I went ahead with the install. It finished and I rebooted but now I seem to be stuck with a plain purple screen whenever I try and boot. Perhaps I've just not waited long enough but after 20 minutes of nothing but purple I got bored and hit the power button. 

Then I tried booting into *try* Ubuntu again and tried editing the grub file and the "sudo update-grub" command but it gave me an error. I'm not even sure if this has anything to do with my issues as, like I said, I'm pretty new to this.

Feel free to give up on me, I'll probably be more coherent if I give it a rest and try tomorrow...just don't want to.

---

### Post by eeeark1 on 2014-12-12
Anyone have any suggestions for my just purple screen? Graphics card problem?
Should I just try a 32-bit install?

---

### Post by oldfred on 2014-12-12
Do not use 32bit install, it will not help.
Issue is nVidia card.

I have nVidia and screen would always go black, but system was still booting in back ground. So I have always had to use nomodeset on live installer, and on first boot or until I installed the nVidia driver.

If you only have Ubuntu installed, you have to hold shift key  from BIOS until menu appears if booting in BIOS mode, or press escape key (perhaps several times) to get menu to appear if booting in UEFI mode.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Go back and review the links on nVidia 750 as it is new enough that it needs a newer driver than the default in the Ubuntu repository.

---

### Post by eeeark1 on 2014-12-12
You keep talking about UEFI vs BIOS booting and I've no clue which I'm doing. If I hit F12 right after boot I get a boot menu with options. There I can choose to boot with the usb, UEFI usb, or just ubuntu. I assume just ubuntu is the installed version. When I boot into that and try the nomodeset thing nothing changes, I still get a plain purple screen. Do I need to boot into one of the liveusb options and then install the nvidia drivers? I assume I should be trying to boot into just ubuntu and trying to install drivers there but I can't make it do anything. At the grub menu do I need to choose advanced options for ubuntu? Do I need to somehow boot into a command line version to install driver? 

Again, thanks

---

### Post by eeeark1 on 2014-12-12
I figured out how to get into recovery mode and thereby a terminal/command line. Seems as though I have no internet connection now. It worked from the live USB...this is a pain in the butt.

---

### Post by oldfred on 2014-12-12
One of the recovery mode options is to enable the Internet.
The recovery mode uses the nomodeset option by default.

---

### Post by eeeark1 on 2014-12-13
So I boot, @ grub menu I select Advanced options for Ubuntu, select "Ubuntu with Linux 3.13.0-43-generic (recovery mode)", enter passphrase, @ recovery menu I choose network--Enable networking (correct?), I choose <Yes> to "continue and remount my / filesystem...etc.", it then scrolls some stuff @ bottom of screen and gets to "mountall: fsck /boot [879] terminated with status 1" and nothing else happens. Just the blinking cursor and nothing I enter here does anything. What am I doing wrong?

---

### Post by eeeark1 on 2014-12-13
What if I download drivers on this (working computer) and transfer them to new Ubuntu comp. with a usb? Can I then use the "Drop to root shell prompt" and install them that way?

---

### Post by eeeark1 on 2014-12-13
If I download drivers on another computer and put them onto a usb for install in new computer how do I install them via command line?

---

### Post by oldfred on 2014-12-13
That it wants to do a fsck is a bit unusual on a new install. But try a full fsck on all your Linux partitios.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

