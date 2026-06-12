---
title: "Unable to boot after formatting my second hard disk"
date: 2022-06-27
forum: New to Ubuntu
---

### Post by brokensymmetriescircus on 2022-06-27
Hello,

I recently installed Ubuntu on my computer which was on Windows 10 (no dual boot). I installed Ubuntu on my SSD and didn't touch anything else for several days without  having any problem. I then wanted to formate my HDD to Ubuntu so I could use it. I did it and from then, I could not boot my computer without the emergency mode appearing. Along with it, I could read line like "vfs can't find ext4 filesystem" . The command "exit", "systemctl" and "CTRL+D" do not work. They tell me stuff like "or "transport endpoint is not connected".   I have to  restart my PC until by luck one of the commands work. I tried to boot from a USB and use boot-repair  as well as fsck (not sure about if I used it well though). I attach the log given by boot-repair.

Thank you for any advice you could have

PS: sda is my HDD, sdb my SSD, sdb1 is the "EFI System Partition" (fat32)

---

### Post by oldfred on 2022-06-27
You show blank sda partitioned as MBR(msdos), but sdb as gpt with the typical two partitions for UEFI boot.
You have a BIOS boot loader in MBR of sda.

You boot issue could be that you are not booting in UEFI mode. Check UEFI settings that boot mode is UEFI, not BIOS/CSM/legacy.

Or since upgrade, you have not reinstalled nVidia driver.
Since only one install, grub menu is not normally shown. It just auto boots your one choice.
If you press Escape with UEFI boot right after vendor logo screen at start and before grub menu normally would show, can you get grub menu?
And then boot recovery mode or second line in grub menu. That has nomodeset boot parameter for video issues.
You then probably would need to install nVidia driver from terminal in recovery mode.

---

### Post by brokensymmetriescircus on 2022-06-28
Hello, thanks to your answer. I can get to select advanced options. I have the choices between two ubuntu boot and two recovery mode boot. Wen I select one of the recovery mode reboot and I get to  the menu (with fsck, among others options), I cannot move the light bare to select another mode. Even using the button enter does not work and I am trapped on that menu. I did install the Nvidia Drivers some days ago using :

sudo add-apt-repository ppa:graphics-drivers/ppa && sudo dpkg --add-architecture i386 && sudo apt update && sudo apt install -y nvidia-driver-510 libvulkan1 libvulkan1:i386

I also went to the BIOS-UEFI menu to make sure that every options forced UEFI.

PS: Another error showing up in emergency mode is "transaction for grahic.target/start is destructive (emergency.target has 'start' job queued, but 'stop' is included in transaction)".

---

### Post by oldfred on 2022-06-28
Why i386?
You have 64 bit system.

You may need to purge and reinstall nVidia driver.

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by brokensymmetriescircus on 2022-06-28
I am pretty sure I changed the end of that command but just in case I did :

sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

I rebooted but the problem still persist. Should I uninstall Ubuntu to install it back since it seems that even the recovery mode has issues ?

---

### Post by oldfred on 2022-06-28
See this as you want sdb as bootable drive.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

You also could just swap which SATA ports drives are plugged into. 
Typically the lowest port SATA0 will then be sda, and SATA1 as sdb. If ports are skipped or not used then lowest port is first drive.

---

### Post by brokensymmetriescircus on 2022-06-29
Before I do that, I just noticed some differences between the fstab file and the results of lsblk. The mounting point for sdb1 is not the same and  there is no sdb2 in the fstab. Moreover the fstab  seems to tell us there is an error for sdb2. Sorry if these are stupid guesses, I really am totally new to this.

[https://ibb.co/P9NVP8W](https://ibb.co/P9NVP8W)
[https://ibb.co/QnCVPj6](https://ibb.co/QnCVPj6)

---

### Post by oldfred on 2022-06-29
Are you then mounting sdb2 twice once as / and second time as /stock? that may be part of problem as I did not think that even worked.

You want to always use UUIDs or labels, not devices. Some times the devices change. With my system my sdb drive changes to sdc, when I plug in a flash drive. I now like labels as human readable. Then I manage labels, but do have to be careful not to create duplicates. I have data partitions on many flash drives and cannot just use /mnt/data for all of them.
man mount

To also see labels:
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint

Please just post terminal output or if more than a very few lines use code tags. Use # can Forum's advanced editor.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by brokensymmetriescircus on 2022-06-29
Sorry for the links. I will do as you say from now on. I will label them right now.

In the  fstab, I read that sdb1 is mounted as stock while sdb2 is marked in blue  with an error. Moreover it says that /boot/EFI was on sdb1 during  installation. In the lsblk, I read that sdb1 is mounted as /boot/EFI  while sdb2 is mounted as /. It seems to me that sdb1 is mounted twice  while sdb2 is mounted is an incorrect way. Or maybe sdb1 is in /stock  and I need to correct the fstab or vice versa ?

Gparted tells me that sdb1 is on /boot/EFI while sdb2 is on /.

Do  you think unmounting and mounting back sdb1 and sdb2 is enough to  resolve the issue ? Do I have to do it after booting from a USB ?

---

### Post by oldfred on 2022-06-29
Just comment out the mount of /stock and run this to remount from fstab.
sudo mount -a
If it returns with no errors then it is ok.

About the only time the ESP mount in Ubuntu is used is when reinstalling grub. 
UEFI finds the ESP with the GUID & then the grub in the ESP is a configfile to the full grub in your install. So mount of ESP not normally used by system for booting. But errors in fstab can cause issues.

---

### Post by brokensymmetriescircus on 2022-06-30
Thank you very much ! It resolved the issue and everything work fine now.

---

