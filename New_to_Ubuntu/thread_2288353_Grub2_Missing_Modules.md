---
title: "Grub2 Missing Modules"
date: 2015-07-26
forum: New to Ubuntu
---

### Post by patrickmcknewportf on 2015-07-26
I am using an ASUS laptop with Windows 7 64-bit, which is installed as BIOS. I tried to install Ubuntu Server 14 from a DVD-RW. I can get to a black screen that allows me to choose between Ubuntu and Advanced Options for Ubuntu. If I choose Ubuntu, it will begin to load. However, after a few seconds, the following output is displayed:
```

[       3.115606] usb 4-2: SerialNumber: MA03EEK9
[INDENT][INDENT]Gave up waiting for root device. Common problems:
[/INDENT]
[INDENT] - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough ?)
   -  Check root = (did the system wait for the right device ?)
    - Missing modules (cat /proc/modules; ls /dev)
 ALERT! /dev/disk/by-uuid/82126b72-36ba-4776-9fbd-0afb3856f4aa does not exist . Dropping to a shell!


 Busybox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
  Enter 'help' for a list of built-in commands.

 (initramfs)[/INDENT]
[/INDENT]
 
```
Can someone help me fix this please? Thank you.

---

### Post by yancek on 2015-07-26
> ALERT! /dev/disk/by-uuid/82126b72-36ba-4776-9fbd-0afb3856f4aa does not exist

It is trying to boot a particular partition indicated by the uuid above and it apparently does not exist.  Boot any Linux Live CD/flash drive and run the command:  blkid
You may need to use:  sudo blkid
See if the uuid shown above is in the output.  If not, post your /boot/grub/grub.cfg file, at least the menuentries.

---

### Post by patrickmcknewportf on 2015-07-26
> **yancek said:**
> It is trying to boot a particular partition indicated by the uuid above and it apparently does not exist.  Boot any Linux Live CD/flash drive and run the command:  blkid
You may need to use:  sudo blkid
See if the uuid shown above is in the output.  If not, post your /boot/grub/grub.cfg file, at least the menuentries.
Thank you for your reply, but I'm not sure what you mean by LiveCD. I am trying to get Ubuntu Server, but this accourding to this page ([https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)) I should avoid using Ubuntu Server because it has no desktop.

---

### Post by sandyd on 2015-07-26
Use the "Rescue a broken system" option when booting up Ubuntu Server from the LiveCD/DVD (The medium that you used to install Ubuntu Server).
If unsure, see [http://imgur.com/a/l8Slo](http://imgur.com/a/l8Slo). Some steps are skipped after Step #2, those are self explanatory.

May look a tad different, this is on a LVM partition setup + KVM

---

### Post by patrickmcknewportf on 2015-07-26
> **sandyd said:**
> Use the "Rescue a broken system" option when booting up Ubuntu Server from the LiveCD/DVD (The medium that you used to install Ubuntu Server).
If unsure, see [http://imgur.com/a/l8Slo](http://imgur.com/a/l8Slo). Some steps are skipped after Step #2, those are self explanatory.

May look a tad different, this is on a LVM partition setup + KVM
I clicked on "Rescue a broken system" option, and then I executed a shell. Then I typed in blkid, and the output I got is below (Unfortunately I couldn't get a screenshot, so I had to make do with a camera).
[ATTACH=CONFIG]263410[/ATTACH]

---

### Post by oldfred on 2015-07-26
It looks like UUIDs match.
You may need chkdsk on partition, or rebuilding initramfs.

Several other alternatives:
 ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"
Also check that drive is hd0 and grub in same drive.
ALERT! /dev/disk/by_uuid, then missing keyboard driver, chroot install new kernel
[http://ubuntuforums.org/showthread.php?t=2245053](http://ubuntuforums.org/showthread.php?t=2245053)
[http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell](http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell)

    SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=2255888](http://ubuntuforums.org/showthread.php?t=2255888)
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

---

### Post by patrickmcknewportf on 2015-07-27
I haven't gotten to all of the suggestions yet, but I thought its worth noting that when I use the sudo command, I get a "sudo: not found" message. Also, if I type in apt-get upgrade, I get a "apt-get: not found".

---

### Post by oldfred on 2015-07-27
It has not booted, so you may be at grub2's command line. The grub command line has just a few boot related commands it supports.

---

### Post by patrickmcknewportf on 2015-07-27
I tried to find a way to get grub2 to boot, but when I typed boot a message came back saying "sh: boot: not found". At the top of the screen it says Rescue Mode.
Anyway, I tried to some of things you suggested. I went to the "Advanced" tab of my BIOS, and clicked on SATA Controller Mode. I couldn't find "[COLOR=#000000]Compatibility", so I searched online, and found IDE was close enough. It changed the screen color.
[/COLOR]Typing apt-get upgrade I got an error message saying "apt-get: not found". 
Then I decided to try mounting. I didn't get an error by typing "mount /dev/sda1 /mnt". I did get an error message from "[COLOR=#111111][FONT=Consolas]mount --bind /dev /mnt/dev", saying "bin/sh:no such directory".[/FONT][/COLOR]

---

### Post by oldfred on 2015-07-27
I do not know rescue mode with server version. 

But generally AHCI is preferred over IDE. IDE is for compatiblity with old PATA drives.

You can try with liveDVD or flash drive the Desktop version and run Boot-Repair's Summary report.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by patrickmcknewportf on 2015-07-27
> **oldfred said:**
> I do not know rescue mode with server version. 

But generally AHCI is preferred over IDE. IDE is for compatiblity with old PATA drives.
Oh all right. Thank you.
> You can try with liveDVD or flash drive the Desktop version and run Boot-Repair's Summary report.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
I need Boot Repair Disk, since I am using Windows 7, correct?

---

### Post by oldfred on 2015-07-27
Boot-Repair only runs in Linux and can only make minor repairs to NTFS or Windows installs. You can run it from any Ubuntu live Desktop installer, or it has its own Lubuntu based live CD.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    To repair Windows 7 you will need the Windows 7 RepairCD or flash drive.
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by patrickmcknewportf on 2015-07-28
I successfully created a liveUSB and got a Boot-Info report from Boot-Repair. Here it is:
[http://paste.ubuntu.com/11954079/](http://paste.ubuntu.com/11954079/)

---

### Post by oldfred on 2015-07-28
Even though you have newer UEFI hardware, both installs are BIOS/MBR. 
So better to boot Boot-Repair in BIOS mode, not UEFI.

But Boot-Repair did offer to just reinstall grub in BIOS mode.
You only have a Windows boot loader installed currently.

I do not see anything obviously wrong. Someone else may see something?

---

### Post by patrickmcknewportf on 2015-07-28
> **oldfred said:**
> Even though you have newer UEFI hardware, both installs are BIOS/MBR. 
So better to boot Boot-Repair in BIOS mode, not UEFI.
I disabled "UEFI boot" and boot Boot-Repair with failsafe. This is the result:
[http://paste.ubuntu.com/11955097/](http://paste.ubuntu.com/11955097/)

I noticed that sda6 and sdb1 have grub.cfg; sdc1 also has more files then sda6. I presume that by running Boot-Repair, more files will get placed into sda6. So what will happen to the files in sdb1?

---

### Post by oldfred on 2015-07-28
Do not know if part of issue is installing grub to goflex external drive. We have seen those before and they seem to have some proprietary data.
Also external drive starts at the old first sector of 63. That was common with XP and Linux. Windows 7 changed to 2048 to accommodate newer drives. Linux changed a year or two later, but 2048 has been the standard first sector now for years.

Space after MBR is where grub stores core.img which has more boot code. Windows and proprietary code in Windows may also use that same space and cause conflicts.

The live installer has a grub.cfg for UEFI boot only. Otherwise with  BIOS boot it uses Syslinux and its configuration files. The Ubuntu live  installer in sdb should not be modified. If you install grub to that  then it may boot your system, but would not (without manual  reconfiguration) boot installer.

---

### Post by patrickmcknewportf on 2015-07-28
I ran several times boot-repair and Ubuntu still does work.
Here's the boot-info files:
[http://paste.ubuntu.com/11955806/](http://paste.ubuntu.com/11955806/)

---

### Post by oldfred on 2015-07-28
Are you still getting same error?
Or do you get grub menu?

If you get grub menu try nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by patrickmcknewportf on 2015-07-28
> **oldfred said:**
> Are you still getting same error?
Or do you get grub menu?

If you get grub menu try nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I'm getting the same error. But just to make sure we're on the same page, when I turn on my computer, it looks similar to this:[http://cdn5.howtogeek.com/wp-content/uploads/2014/09/grub2-linux-boot-loader-menu.jpg]("http://www.omgubuntu.co.uk/wp-content/uploads/2012/09/grub2-in-ubuntu.jpg").

---

### Post by patrickmcknewportf on 2015-07-28
I can now use sudo in Repair Mode from sda6. Does that mean I should mount sda1? For example:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -u
update-grub
reboot

```

---

### Post by oldfred on 2015-07-28
Your sda1 & sda2 are NTFS partitions, you do not want to try to use Linux tools on them.
Windows tools for Windows and Linux tools for Linux.

If you are in terminal mode in your install you do not need the chroot.
You can run whatever repair commands needed with sudo on each line or sudo -i to be in administrative mode.
       #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

update-initramfs -u 
update-grub

---

### Post by patrickmcknewportf on 2015-07-29
I decided to run these command on sda6:
```

sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -u
update-grub
reboot
```
Then I tried to boot Ubuntu again, but it stopped with something like "[COLOR=#111111][FONT=Ubuntu]end kernel panic - not syncing: vfs:"
[/FONT][/COLOR]
I was able to run "sudo -i", "apt-get autoclean", and "apt-get clean". However, "apt-get update" received a list of errs and failures. I tried a permanent solution that was suggested by this page: [http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error](http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error), but it didn't work.

---

### Post by oldfred on 2015-07-29
The CHroot command are to boot with a known good kernel, either another working install or the live installer and CHange ROOT, so that you then are working inside the install you want to repair. You cannot mount the one you are in, so those commands would fail.

What errors are you getting? 
With either chroot or partially booting you have to make sure Internet is working. If it cannot download updates then you get those errors.

If booting live installer and chroot then you often also need this as last command before chroot command:
 sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)

---

### Post by patrickmcknewportf on 2015-07-29
> What errors are you getting?
InRelease and Release errors, for example
```

Err http://security.ubuntu.com trusty-security InRelease

Err http://us.archive.ubuntu.com trusty-updates InRelease

Err http://us.archive.ubuntu.com trusty-backports InRelease

Err http://security.ubuntu.com trusty-security Release.gpg
 Could not Resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com trusty Release.gpg
 Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-updates Release.gpg
 Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-backports Release.gpg
 Could not resolve 'us.archive.ubuntu.com'
Reading package lists..Done
w: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease

w: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease

w: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease

w: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease

w: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg Could not resolve 'us.archive.ubuntu.com'

w: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg Could not resolve 'security.ubuntu.com'

w: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg Could not resolve 'us.archive.ubuntu.com'

w: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backport/Release.gpg Could not resolve 'us.archive.ubuntu.com'

w: Some index files failed to download. They have been ignored, or old ones have been used instead.

```

I believe part of the problem is my network is using DHCP to configure it.

> If booting live installer and chroot then you often also need this as last command before chroot command:
 sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)

I tried that, and I got an error message saying
```
cp: cannot stat 'etc/resolv.conf': No such file or directory
```
However, if I do a "ls /etc" in [COLOR=#000000]administrative mode, I can see resolv.conf listed.[/COLOR]

---

### Post by oldfred on 2015-07-29
Are you chrooting into your install or booting to a command line?
The cp command is only if you chroot, and you would have /etc/resolv in the system you are chrooting from. But command is to use that by mounting it into chroot.

---

### Post by patrickmcknewportf on 2015-07-29
> **oldfred said:**
> Are you chrooting into your install or booting to a command line?
I'm not sure. When I use chroot, the command prompt displays "root@User-PC:/#".
> The cp command is only if you chroot, and you would have /etc/resolv in the system you are chrooting from. But command is to use that by mounting it into chroot.
But the cp command comes before chroot, correct?

---

### Post by sandyd on 2015-07-29
> **patrickmcknewportf said:**
> I'm not sure. When I use chroot, the command prompt displays "root@User-PC:/#".

But the cp command comes before chroot, correct?
The chroot should look like that, the CP command comes before chroot.

The error you are getting:
```

cp: cannot stat 'etc/resolv.conf': No such file or directory
```
is because you made a typo, there is a slash before "etc"

---

### Post by patrickmcknewportf on 2015-07-30
> **sandyd said:**
> The chroot should look like that, the CP command comes before chroot.

The error you are getting:
```

cp: cannot stat 'etc/resolv.conf': No such file or directory
```
is because you made a typo, there is a slash before "etc"
Thanks for correcting me. However, I'm getting the error
```
cp: cannot stat '/etc/resolv.conf': No such file or directory
```
Could boot-repair-disk help me figure this out?
Like, I could go into a terminal, find resolv.conf, and copy it.

---

### Post by oldfred on 2015-07-30
I thought on a full uninstall reinstall of grub, Boot-Repair walks you thru a chroot to do updates. I have not done it, so not sure.

---

### Post by patrickmcknewportf on 2015-07-30
> **oldfred said:**
> Your sda1 & sda2 are NTFS partitions, you do not want to try to use Linux tools on them.
Windows tools for Windows and Linux tools for Linux.

If you are in terminal mode in your install you do not need the chroot.
You can run whatever repair commands needed with sudo on each line or sudo -i to be in administrative mode.
       #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

update-initramfs -u 
update-grub
While in Recovery Mode, I reinstalled Ubuntu; after getting back into terminal, I was able to successfully run the above commands.
I ran Boot-Info, and its a little different from this one at [http://paste.ubuntu.com/11954079/](http://paste.ubuntu.com/11954079/). The most recent report, at [http://paste.ubuntu.com/11954079/](http://paste.ubuntu.com/11954079/), Suggested Repair section starts at line 909, and wants to "reinstall the grub2 of sda6 into the MBR of sda, using the following options:     kernel-purge". The Suggested Repair section for the other report, at [http://paste.ubuntu.com/11954079/](http://paste.ubuntu.com/11954079/), starts on line 920 and says that Boot-Repear would "[COLOR=#000000]reinstall the grub2 of sda6 into the MBR of sda."[/COLOR]

---

### Post by oldfred on 2015-07-30
You have Windows in the MBR, so unless you install grub to MBR, you cannot boot Ubuntu.
I would run the auto repair.

Do you have a Windows repairCD or flash drive?

---

### Post by patrickmcknewportf on 2015-07-31
> **oldfred said:**
> Do you have a Windows repairCD or flash drive?
Yes I do.

---

### Post by patrickmcknewportf on 2015-08-03
Firstly, I want to thank everyone for bearing with me, and helping me understand what I was doing wrong. However, when I tried to run Boot-repair disk, it couldn't find a file it needed to run.
So it looks like I need to install Ubuntu to the disk, and then repair Windows.
If this is true, then I would like to delete partitions created by Ubuntu.

---

### Post by oldfred on 2015-08-03
Make sure Windows boots, or have Windows repair flash drive handy.

You can use gparted from live installer to delete partitions. Generally better than Windows as you see the Linux partitions correctly. Some using Windows tools have deleted wrong partitions.

---

### Post by patrickmcknewportf on 2015-08-11
I thought I should update this thread about what happened. Unfortunately, I was unable to install Ubuntu Server, and I decided to upgrade to Windows 10.
 The video at [https://www.youtube.com/watch?v=uGdrQxA0E6g](https://www.youtube.com/watch?v=uGdrQxA0E6g) inspired me to install Ubuntu 15.04 Desktop. I had to use Partition Master instead of using Windows Disk Manager to move partitions, and Ubuntu detected that I have Windows 7 installed. Other then that, everything went pretty well. I was able to log into Ubuntu, and then log into Windows. I am going to continue trying to install Ubuntu Server, but I am willing to mark this thread as 'solved'.
Thank you to everyone for putting forth the effort to help me.

---

