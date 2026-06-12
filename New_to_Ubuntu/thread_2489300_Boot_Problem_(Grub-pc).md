---
title: "Boot Problem (Grub-pc?)"
date: 2023-07-25
forum: New to Ubuntu
---

### Post by stoneld34 on 2023-07-25
I'm 76 and have been using Ubuntu GNOME for several years. I'm dependent  on the GUI, though I have ventured (fearfully) a few times into the  Terminal world. I bought a Dell Inspiron 3593 several years ago with  Windows 8 on it, upgraded immediately to Win 10. I followed some online  instructions to make my laptop dual-boot, creating a separate area for  Ubuntu (I think at -or before?- Ubuntu 14.04), and am currently at  Ubuntu 22.04.2 LTS. I attempt to update Ubuntu each time I log on, but  several months ago updating Ubuntu from the GUI began to fail. Among the  error messages when I tried to update Ubuntu would be "Grub-pc package  may not be in working order." (I'm at Grub 2.06.) I also began to get a  Grub> prompt (only sometimes, not every time), instead of the O/S  choice menu, when I first turned my laptop on. I found if I turned it  off and back on, sometimes I would get the O/S choice menu.  Sometimes  when I chose Ubuntu it would boot, but sometimes it would offer an error  message ending with "you need to load the kernel first." This too would  sometimes go away if I turned the power off and restarted; sometimes I  would get the Grub> prompt again, or the Ubuntu error. 
Today I tried to load the Boot-Repair package from the Ubuntu Community.  Below I copy my entire Terminal session, done as the Administrator: 
[admin-user]@[admin-user]-Inspiron-3593:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
[sudo] password for [admin-user]: 
Repository: 'deb [https://ppa.launchpadcontent.net/yan...repair/ubuntu/]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/") jammy main'
Description:
Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
More info: [https://launchpad.net/~yannubuntu/+a...tu/boot-repair]("https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair")
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-jammy.list
Adding key to /etc/apt/trusted.gpg.d/yannubuntu-ubuntu-boot-repair.gpg with fingerprint 3C48D16124B50277AF10D27F32B18A1260D8DA0B
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]     
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]      
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [108 kB]   
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 Packages [631 kB]
Ign:6 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy InRelease   
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main Translation-en [148 kB]
Get:8 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy InRelease [17.5 kB]
Err:9 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Get:10 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main amd64 Packages [1,828 B]
Get:11 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main i386 Packages [1,828 B]
Get:12 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main Translation-en [1,596 B]
Reading package lists... Done                                 
E: The repository 'https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease              
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [108 kB]   
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Ign:5 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy InRelease   
Hit:6 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy InRelease
Err:7 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done                               
E: The repository 'https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
[admin-user]@[admin-user]-Inspiron-3593:~$ sudo apt install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hwinfo libffi7 libflashrom1 libftdi1-2 libhd21 libllvm13 libpgm-5.2-0
  libx86emu3 linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  boot-sav boot-sav-extra glade2script glade2script-python3 pastebinit
  syslinux-common
Suggested packages:
  boot-info cryptsetup dmraid lvm2 mdadm os-uninstaller zfsutils-linux
  gir1.2-appindicator3-0.1
The following packages will be REMOVED:
  linux-image-5.15.0-46-generic
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra glade2script glade2script-python3
  pastebinit syslinux-common
0 upgraded, 7 newly installed, 1 to remove and 14 not upgraded.
7 not fully installed or removed.
Need to get 1,997 kB of archives.
After this operation, 4,675 kB disk space will be freed.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 pastebinit all 1.5.1-1ubuntu1 [14.6 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 syslinux-common all 3:6.04~git20190206.bf6db5b4+dfsg1-3ubuntu1 [1,271 kB]
Get:3 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main amd64 glade2script-python3 all 3.2.4~ppa23 [35.9 kB]
Get:4 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main amd64 glade2script all 3.2.4~ppa23 [2,204 B]
Get:5 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main amd64 boot-sav all 4ppa2056 [512 kB]
Get:6 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main amd64 boot-repair all 4ppa2056 [16.3 kB]
Get:7 [https://ppa.launchpadcontent.net/yan...-repair/ubuntu]("https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu") jammy/main amd64 boot-sav-extra all 4ppa2056 [146 kB]
Fetched 1,997 kB in 3s (680 kB/s)   
(Reading database ... 308177 files and directories currently installed.)
Removing linux-image-5.15.0-46-generic (5.15.0-46.49) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-46-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-46-generic
Found initrd image: /boot/initrd.img-5.19.0-46-generic
Found linux image: /boot/vmlinuz-5.15.0-76-generic
Found initrd image: /boot/initrd.img-5.15.0-76-generic
Found linux image: /boot/vmlinuz-5.15.0-50-generic
Found initrd image: /boot/initrd.img-5.15.0-50-generic
Found linux image: /boot/vmlinuz-5.15.0-48-generic
Found initrd image: /boot/initrd.img-5.15.0-48-generic
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.s
o.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.15.0-46-generic (--remove):
 installed linux-image-5.15.0-46-generic package post-removal script subprocess 
returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-46-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[admin-user]@[admin-user]-Inspiron-3593:~$ 

Can someone tell me if I have a Grub problem, a BIOS problem, an Ubuntu  O/S problem, or all the above? I'm afraid to try re-installing Ubuntu  because of my dual-boot. Will I need to give up dual-boot and get a  separate laptop for each O/S?

---

### Post by oldfred on 2023-07-25
I never have had an issue reinstalling. But have good backups including list of installed apps, /home & my data partition(s).
But only use Something Else so I can choose partition to use. I actually have two / partitions, one for current which becomes previous & one for new install. I have all data in separate data partition, so just restore /home & apps & link data into new install. Old install still works, if needed.

You show proxy files, so must have used grub-customizer. Often better not to, it replaces all the grub scripts with its own proxy files. It also may not have been updated to support grub 2.06.  Best then to totally uninstall grub, & reinstall. Make sure you have a working live installer, as while grub is uninstall, and if new install not correct, then you need live installer to make repairs.

If Windows 8, installed by vendor, then you have UEFI install. Only boot system and any live installers in UEFI boot mode. Using BIOS/CSM/Legacy mode will make everything more complicated to repair.

It looks like you added a ppa for gezakovacs, which does not have a jammy version. You need to remove that. 

Resolve all update issues before trying Boot-Repair again.
Or run Boot-Repair from your jammy live installer.

Grub-pc is only for BIOS boot, you do not want that. Perhaps  you tried to boot in BIOS mode?
You want grub-efi-amd64 for UEFI boot.

---

