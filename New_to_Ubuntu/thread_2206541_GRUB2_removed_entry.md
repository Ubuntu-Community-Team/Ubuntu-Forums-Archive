---
title: "GRUB2 removed entry"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by hugodaniel2 on 2014-02-19
Hi, 

I've just installed the latest kernel, 3.11.0-18-generic, and after rebooting the system, one of the distros that I use on my laptop just disappeared.

I already used the command, ```
update-grub
``` and, ```
grub-mkconfig
``` following some older threads suggestions, but although the distro name appears during the update process, it doesn't show up at the boot loader menu.

What can I do?

Thanks!

---

### Post by deadflowr on 2014-02-19
Try reinstalling grub
```
sudo grub-install /dev/sdX
```
changing X to the disk letter, typically "a".
Then rerun the update-grub command.

---

### Post by oldfred on 2014-02-19
I seems like you updated grub in a different install than the one you have booted with.
Deadflowr's instructions will have you installing the grub of the system you have booted install its boot loader to the MBR.
If you have multiple installs you may have to keep track of which install has its grub in the MBR.
And some updates may auto reinstall grub to MBR.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by hugodaniel2 on 2014-02-20
Hi oldfred, 

I used the commands you've suggested to check the install directory for the Grub2 bootloader installed on my system (the drive ata-WDC_WD6400[etc.]), and it seems that it's installed on the Ubuntu partition (/dev/sda10), as you can see by the output below.

[I][B]sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub[/B][/I]

```
grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD6400BEVT-80A0RT0_WD-WXD1A80X7152
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

```

```
/dev/sda10
```

In fact, Ubuntu was my first Linux distro, so it matches with what I thought it would be, but when I do the other command you suggested (***sudo dpkg-reconfigure grub-pc***), so that Grub2 remembers on which drive it should reinstall, drive sda appears and the partition sda10. In that case, I should choose the partition sda10, correct? Otherwise nothing will change, or am I wrong?

Thanks

---

### Post by oldfred on 2014-02-20
You almost never install grub2 to a partition like sda10.
BIOS based systems only boot from MBR.

This says it is installed currently to the drive not a partition.
 grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD6400BEVT-80A0RT0_WD-WXD1A80X7152

---

### Post by hugodaniel2 on 2014-02-21
Ok, that means that Grub2 is installed on the drive and that it uses the bootloader from the partition sda10, correct? In my case, that would be the one with Ubuntu.

But, why does the other Linux distro doesn't appear on the menu? 

Is there a limited number of distros and kernels that grub2 can show? Or, do I need to recover the boot folder for this distro, or something like that.
That distro was installed with LVM, and got problems booting after I installed Debian on my machine, and I was trying to recover it, before Ubuntu was upgraded to it's new kernel and the option to boot from that distro simply vanished...

It's strange because when I do the ***update-grub*** command, the distro shows up, but when I reboot the system, it doesn't.

Why could that be happening?

Thanks

---

### Post by oldfred on 2014-02-21
Lets see details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If other install is LVM, you have to install lmv2 drivers in Ubuntu and mount that partition for sudo update-grub to find it. Or you just copy the boot stanza from that install into 40_custom, but then you have to manually maintain it.

---

### Post by hugodaniel2 on 2014-02-21
Ok oldfred, here is the link for my BootInfo Summary on DropBox.

[https://dl.dropboxusercontent.com/u/62030208/Boot-Info_2014-02-21__12h34.txt](https://dl.dropboxusercontent.com/u/62030208/Boot-Info_2014-02-21__12h34.txt)

I don't know if those drivers are already installed on my Ubuntu, but I believe that they are, but take a look at the BootInfo and please give me your opinion.

Thanks

---

### Post by oldfred on 2014-02-21
Lots of installs.
Some do not use default LVM with Fedora when installing a multi-boot drive, just manual install to ext4 partition. The advantage of LVM is when it has the entire drive. 

BootInfo does not show which is default boot as MBR says partition 94. Since an update to grub, it bootinfoscript just does not parse core.img correctly.

So which system is currently default boot? Or the one that is first in boot order when you first boot.

I have multiple installs and find os-prober and each version of grub starts to get confusing. So I just install grub for the main install I use to MBR, and manually add other installs to 40_custom. With Ubuntu & Debian it is easy as they put links to most current kernel in / (root), so you do not have to re-edit on update. With multiple installs you otherwise have to run the equivalent of sudo update-grub in install you have updated so its grub.cfg or config file has latest entry, then boot into install that controls booting and run sudo update-grub in it to find the new entry in the other install's config file. Easy to get out of sync.

Select which system you want in control and install its version of grub to MBR.
       sudo grub-install /dev/sda

Then with all other systems, in the dpkg command uncheck the reinstall location of grub, so it will not auto re-install. Then only your main working install will be in MBR and auto updated to MBR, but you still have to coordinate sudo update-grub commands.
Not sure of equivalent commands in other distributions.

---

### Post by hugodaniel2 on 2014-02-27
> **oldfred said:**
> Or you just copy the boot stanza from that install into 40_custom, but then you have to manually maintain it.

Hi oldfred, just to give you some feedback, the last suggestion that you've given to me, to copy the boot stanza into 40_custom and then to use the update-gub command on my main distro, just solved my problem... Thanks! :D

---

