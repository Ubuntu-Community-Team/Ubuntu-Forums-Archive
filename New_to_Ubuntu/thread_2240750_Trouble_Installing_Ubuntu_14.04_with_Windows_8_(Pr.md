---
title: "Trouble Installing Ubuntu 14.04 with Windows 8 (Pre-install)"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by tim63 on 2014-08-22
To cut to the chase, my URL is: [http://paste.ubuntu.com/8111994/](http://paste.ubuntu.com/8111994/)

I have:
- disabled Intel Smart Connect and Rapid Start
- disabled secure boot (I've tried it enabled and disabled)
- disabled fast startup 

I created a Live USB based on the instructions given here: [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
And I've generally followed these two tutorials/posts:
1. [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
2. [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Help would be greatly appreciated!

---

### Post by Gordonbp531 on 2014-08-22
OK. You are trying to install 64 bit Ubuntu and not 32 bit?
1. There is absolutely no need to disable Intel Smart connect and Rapid Start, or secure boot or fast startup.
2. Yiou need to create the unallocated space for Ubuntu IN WINDOWS - do NOT use GParted to do this.
3. You need to install Grub on the EFI partition. To find out what partition that is, when booted from the lice CD/USB, use the Disks utility.

That worked OK for me.

---

### Post by guccimucci on 2014-08-22
I had to disable secure boot and fast startup because of the new UEFI thing. I followed the instructions I found in everydaylinuxuser, but my Ubuntu installer didn't recognize my pre-installed Windows, so I had to follow the steps I found in here before being able to continue with manual partitioning: [http://www.linuxbsdos.com/2013/02/26/zap-gpt-data-structures-from-a-disk-while-preserving-existing-mbr-partitions/](http://www.linuxbsdos.com/2013/02/26/zap-gpt-data-structures-from-a-disk-while-preserving-existing-mbr-partitions/)

I think it is easier to partition my disk in Ubuntu installer, but it's jut my opinion.

---

### Post by Gordonbp531 on 2014-08-22
No, if you use 64 bit 14.04 Ubuntu then you do NOT have to disable UEFI. Trust me.
Secondly, if you use Gparted to create the space to install Ubuntu you run a great danger of borking your Windows 8 install.
Thirdly the Ubuntu installer has a bug re pre-installed Windows 8.
You need to choose the "Other" option on the install screen.

---

### Post by grahammechanical on 2014-08-22
That Boot Repair report is out of date. It gives the state of the system before Boot Repair carried out any repairs. Please run Boot repair again. At least to generate a report that describes the situation at present and not what the situation was. For example, the report states that Grub is not installed in the MBR of either sda or sdb but Boot Repair should have re-installed the Grub of sda7 into the MBR of sda. So, there should be changes that are not in the report that you have linked to.

Also running Boot Repair more than once might fix things. Furthermore, it helps us to imagine what is happening on your machine if you describe what you see when the machine loads. Would I be right in assuming that you can no longer load Windows? You do say that Windows is loading. This is information that Boot Repair does not provide. Not knowing the accurate state of your machine I might give you inaccurate advice.

---

### Post by oldfred on 2014-08-22
It does show ubuntu folder in the efi partition. 

But HP has modified its UEFI to only boot Windows.
Most find copying grubx64.efi to /efi/Boot and replacing bootx64.efi and booting hard drive then works. 
Backup efi partition before making any changes.

The Intel SRT often adds complexity. I have been suggesting turning that off as it is seen as RAID and grub did not install correctly. But now grub still installs. One user said it worked without issue.

Not sure why you have so many hard drive entries. Ubuntu should boot first but with HP it will not.
 BootOrder: [COLOR=#ff0000]0000[/COLOR],3004,3000,3002,3003,3005,3006,3007,3008,2001,2002,2003
Boot0001* USB Hard Drive (UEFI) - SanDisk
Boot0004* [COLOR=#ff0000]Windows Boot Manager[/COLOR]
Boot2001* USB Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot3004* Internal Hard Disk or Solid State Disk
Boot3005* Internal Hard Disk or Solid State Disk
Boot3006* Internal Hard Disk or Solid State Disk
Boot3007* Internal Hard Disk or Solid State Disk
Boot3008* Internal Hard Disk or Solid State Disk
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR].

      It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

 HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

       sudo mount -t vfat /dev/sda2 /mnt
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by tim63 on 2014-08-24
That is odd, I reported the webpage that was given to me after running boot repair. 

Either way, I did the boot repair again and here is the new link: [http://paste.ubuntu.com/8134379/](http://paste.ubuntu.com/8134379/)

Thanks!

---

### Post by oldfred on 2014-08-24
You show Intel SRT which caches Windows fast boot into the 32GB SSD. But it looks like you have 8GB of RAM so it only is using 8 of the 32GB. 
Several users have just created a 16GB / (root) partition on SSD to make all of Ubuntu fast not just the fast boot. You might be able to fit all of Windows in 32GB, but they only use part to make booting fast.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

Older instructions (including mine) may say to remove RAID to get grub to install. Some have posted that with 14.04 grub will install correctly without removing RAID. Not sure if just turning off fast boot or fast boot and Intel SRT while installing or not.

But you have an HP, so you can only boot Windows without a work around.

---

