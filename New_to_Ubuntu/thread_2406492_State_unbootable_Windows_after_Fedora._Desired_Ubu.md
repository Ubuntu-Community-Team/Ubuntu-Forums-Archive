---
title: "State: unbootable Windows after Fedora. Desired: Ubuntu + Windows"
date: 2018-11-21
forum: New to Ubuntu
---

### Post by benh7 on 2018-11-21
Hello,
I have a new windows 10 laptop (Lenovo Ideapad 330S). I  installed Elementary OS successfully, then had a change of heart and  immediately installed Fedora 28 Workstation from a live usb. As part of  the Fedora installation, I removed the Elementary partitions (and, I  believe, only those). Now Fedora works fine, but I can't boot into Windows: Windows doesn't appear in the GRUB menu. 

After a day's frustration I gave up but am now trying again. This time I'd actually like to have Ubuntu as I now also have a desktop with 18.04 and I'm very happy with it.

Disclaimer:  I have 'enough knowledge to be dangerous' - I'm  happy with command line stuff but don't actually understand how either Linux or booting works, other than what I've picked up during this process.

Ideally I'd like to end up dual-booting Ubuntu/Windows. I'd rather not lose Windows as it came preinstalled, without a Windows Product Key on packaging/paperwork.

It's  a new computer so there's no data to lose (other than the Windows installation); I'm happy to lose any Fedora partitions.

The Windows partitions are  still there; see following boot-repair output (from running Ubuntu on a live USB):

[https://paste.ubuntu.com/p/SmSHDj7YvZ/](https://paste.ubuntu.com/p/SmSHDj7YvZ/)

Both Fedora and Windows use UEFI, not BIOS. I understand that GRUB can't boot Windows directly, but can identify and chainload it. Enabling and disabling Secure Mode had no effect. Legacy boot is off. 

When I try to install Ubuntu, it doesn't detect any existing operating systems, which is what prompted me to try boot-repair. I saw a warning to ask first before running the repairs, so here I am. I really appreciate any help you can offer; I've tried to solve the problem myself and give you what information I can. Do ask if you need anything further!
Thanks
Ben

---------

In case it's useful, I ran the following commands under Fedora:

`sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg` gives:
<pre>Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.16.3-301.fc28.x86_64
Found initrd image: /boot/initramfs-4.16.3-301.fc28.x86_64.img
Found linux image: /boot/vmlinuz-0-rescue-ef31cdf6325b480087f14666722d8231
Found initrd image: /boot/initramfs-0-rescue-ef31cdf6325b480087f14666722d8231.img</pre>

`sudo efibootmgr -v` gave the following:
<pre>BootOrder: 0001,0002,0000,2001,2002,2003
Boot0000* Linpus lite    HD(1,MBR,0x3a663a44,0x1d484,0x48e0)/File(\EFI\Boot\grubx64.efi)RC
Boot0001* Fedora    HD(1,GPT,b5356b76-d745-462f-b7b9-7b02060c2681,0x800,0x64000)/File(\EFI\fedora\shimx64.efi)
Boot0002* Fedora    HD(1,GPT,b5356b76-d745-462f-b7b9-7b02060c2681,0x800,0x64000)/File(\EFI\fedora\shim.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC</pre>

---

### Post by oldfred on 2018-11-21
It looks like you booted Boot-Repair in BIOS/CSM/Legacy mode.
Since Windows & hardware are UEFI, you always want to boot in UEFI boot mode, or BIOS fixes may make it worse.

Most that install Fedora or similar systems that use LVM as default, install to standard partitions when dual booting. The advantage of LVM is when its volumes are the entire physical drive.

You may need to mount LVM volumes or depending on what live system you boot with add lmv2 driver so you can mount the volumes.

It looks like Windows is UEFI, but there is no /EFI/Microsoft folder in ESP. That normally is not erased unless some installer created all new sda1 partition as new ESP.
You will need your Windows repair flash driver or installer with repair console and run Windows fixes. Be sure to boot in UEFI mode, but I think the Windows commands are the same, just it will recognize it is UEFI.

Gparted or installer may not want to remove the LVM volumes, you will need to delete those before installing Ubuntu.

---

### Post by benh7 on 2018-11-23
Thanks oldfred! 

I'd just made a bootable Ubuntu USB (using balenaEtcher on a mac), booted from it and ran boot-repair, so I'm surprised it booted in legacy. If I get into firmware setup ('InsydeH20 Setup Utility', got there from 'fwsetup' on the grub command line), it says Boot Mode is UEFI. Any suggestions? 

So if I understand correctly, your recommendation is to boot from a Windows repair flash drive and then do whatever the Windows tools say? Unfortunately I don't have one, though I do have access to a different computer with windows 10: would a repair drive created on that work? Are there any alternatives, e.g. putting a /EFI/Microsoft folder in ESP or somehow using the Windows Recovery Environment partition?

I'm not sure I understood about the LVM volumes - why would I mount them? I take it it's safe to delete them - but how would I do that if gparted or Ubuntu installer won't want to?

Thanks again,

Ben

---

### Post by oldfred on 2018-11-23
Gparted generally does not work on LVM volumes, But I would expect you could totally delete the partition the LVM volume is inside of. Back up everything you may want before any major changes.

You should be able to use any Windows 10 repair/recovery flash drive.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

Your UEFI will have two boot modes (really 3). UEFI and CSM/BIOS/Legacy. And within UEFI is with UEFI Secure boot on or off. When Secure boot is on, CSM will not work. And you may have separate setting to allow full USB support or USB boot.
Since UEFI & BIOS/CSM are not compatible, how you boot install media is how it installs.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[URL="https://wiki.ubuntu.com/Lvm"]https://wiki.ubuntu.com/Lvm
[/URL]
 Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[URL="https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621"]https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621
[/URL] this is for Ubuntu's LVM on sda1, but Fedora would not be /dev/mapper/ubuntu, nor sda1
   sudo apt-get install lvm2
sudo vgchange -ay /dev/mapper/ubuntu--vg-root
mount /dev/mapper/ubuntu--vg-root /mnt
mount /dev/sda1 /mnt/boot 
[URL="https://wiki.ubuntu.com/Lvm"]
[/URL]

---

### Post by benh7 on 2018-11-26
Hi oldfred,

Thanks for the info - I created a windows recovery drive, and unfortunately the recovery tools didn't work. 

BUT, it did allow me to access the command line and I was able to use  BCDBoot to restore the Windows ESP - and it simply worked! 

I can now boot into Windows, and can therefore make a proper recovery  drive (e.g. to reinstall Windows), then set about deleting Fedora  partitions and installing Ubuntu. 

Huge relief, thanks again.

---

### Post by oldfred on 2018-11-26
Glad you got it working.

For lots of detail on UEFI install see link in my signature.

---

