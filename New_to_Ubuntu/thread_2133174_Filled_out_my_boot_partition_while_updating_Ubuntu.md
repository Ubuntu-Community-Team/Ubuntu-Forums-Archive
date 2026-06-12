---
title: "Filled out my boot partition while updating Ubuntu Server 12.04 LTS"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by dmitriano on 2013-04-07
Hi, experts!

Today while updating my **Ubuntu Server  12.04 LTS** (3.2.0-36-generic-pae)



```

aptitude update > update-output.txt
(yes '' | aptitude safe-upgrade > upgrade-output.txt)

``` I got the following errors:
[INDENT] Extracting templates from packages: 100%
Done.
dpkg: error processing  /var/cache/apt/archives/linux-image-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb  (--unpack):
**[COLOR=#ff0000]failed in write on  buffer[/COLOR]** copy for backend dpkg-deb during  `./boot/vmlinuz-3.2.0-39-generic-pae': No space left on device
No apport  report written because MaxReports is reached already
dpkg-deb: error:  subprocess paste was killed by signal (Broken pipe)
Examining  /etc/kernel/postrm.d .
run-parts: executing  /etc/kernel/postrm.d/initramfs-tools 3.2.0-39-generic-pae  /boot/vmlinuz-3.2.0-39-generic-pae
run-parts: executing  /etc/kernel/postrm.d/zz-update-grub 3.2.0-39-generic-pae  /boot/vmlinuz-3.2.0-39-generic-pae
Errors were encountered while  processing:
/var/cache/apt/archives/linux-image-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb
E:  Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to  install.  Trying to recover:
dpkg: dependency problems prevent configuration  of linux-image-generic-pae:
linux-image-generic-pae depends on  linux-image-3.2.0-37-generic-pae; however:
  Package  linux-image-3.2.0-37-generic-pae is not installed.
dpkg: error processing  linux-image-generic-pae (--configure):
dependency problems - leaving  unconfigured
dpkg: dependency problems prevent configuration of  linux-generic-pae:
linux-generic-pae depends on linux-image-generic-pae (=  3.2.0.37.45); however:
  Package linux-image-generic-pae is not configured  yet.
linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.37.45);  however:
  Version of linux-headers-generic-pae on system is  3.2.0.39.47.
dpkg: error processing linux-generic-pae  (--configure):
dependency problems - leaving unconfigured

[/INDENT] [INDENT] gzip: stdout: [B][COLOR=#ff0000]No space left on  device
[/COLOR][/B]cpio: write error: Broken pipe
update-initramfs:  failed for /boot/initrd.img-3.2.0-36-generic-pae with 1.
dpkg: error  processing initramfs-tools (--configure):
subprocess installed  post-installation script returned error exit status 1
Errors were encountered  while  processing:
linux-image-generic-pae
linux-generic-pae
initramfs-tools

[/INDENT]
Obviously this happened because my boot partition is full, and I need to cleanup  it somehow:

```
df -h
```

[INDENT]Filesystem             Size  Used Avail Use% Mounted  on
[/INDENT]
[INDENT]/dev/mapper/gate-root   35G   16G   18G  48% /
udev                    984M  4.0K  984M   1% /dev
tmpfs                  397M  324K  397M   1%  /run
none                   5.0M     0  5.0M   0%  /run/lock
none                   991M     0  991M   0%  /run/shm
/dev/sda1              228M  225M     0 100% /boot
[/INDENT]


There are 10 versions of kernel:



```
dpkg --list | grep linux-image
```ii  linux-image-3.2.0-23-generic-pae   3.2.0-23.36                  Linux kernel  image for version 3.2.0 on 64 bit x86 SMP
ii   linux-image-3.2.0-27-generic-pae   3.2.0-27.43                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-29-generic-pae   3.2.0-29.46                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-30-generic-pae   3.2.0-30.48                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-31-generic-pae   3.2.0-31.50                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-32-generic-pae   3.2.0-32.51                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-33-generic-pae   3.2.0-33.52                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-34-generic-pae   3.2.0-34.53                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-35-generic-pae   3.2.0-35.55                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-36-generic-pae   3.2.0-36.57                  Linux kernel  image for version 3.2.0 on 32 bit x86 SMP
iU   linux-image-generic-pae            3.2.0.37.45                  Generic Linux  kernel image


I tried to remove all but the last few to free up space:



```
apt-get purge linux-image-3.2.0-23-generic-pae
```but got the following:


Building dependency tree
Reading state information... Done
You might want  to run 'apt-get -f install' to correct these:
The following packages have  unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae  (= 3.2.0.37.45) but 3.2.0.39.47 is to be installed
 linux-image-generic-pae :  Depends: linux-image-3.2.0-37-generic-pae but it is not going to be  installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages  (or specify a solution).


Looks like I can’t remove old kernels until the new ones installed correctly,  but I do not have enough space on my boot partition to install them correctly.

Is there some experts who can tell me how to handle this situation?

---

### Post by schragge on 2013-04-07
Try ```
sudo dpkg -P linux-image-3.2.0-{29..35}-generic-pae
``` This should free up enough space for *apt-get* to be able to handle the rest.

---

### Post by dmitriano on 2013-04-08
Thank you, this solved the problem.

now I have 168M of free space on /boot.

The other question is how to fix my system after unsuccessful update and what is the right way to check what will happen when I reboot my system (I am not sure that the system in a bootable state now)?

---

### Post by schragge on 2013-04-08
The usual procedure is
```

sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade

``` If this doesn't help, at least you'll get more specific error messages.

---

### Post by dmitriano on 2013-04-08
I did

```

sudo apt-get clean 
sudo apt-get update

```

successfully, but

```
 apt-get -f install
```

reported the following errors:[INDENT]Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae linux-image-3.2.0-39-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-39-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 1 newly installed, 0 to remove and 57 not upgraded.
3 not fully installed or removed.
Need to get 38.2 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Get:1 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.2.0-39-generic-pae i386 3.2.0-39.62 [38.2 MB]
Get:2 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic-pae i386 3.2.0.39.47 [1,730 B]
Get:3 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-generic-pae i386 3.2.0.39.47 [2,600 B]
Fetched 38.2 MB in 43s (889 kB/s)
(Reading database ... 101010 files and directories currently installed.)
Unpacking linux-image-3.2.0-39-generic-pae (from .../linux-image-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb) ...
Done.
Setting up initramfs-tools (0.99ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-39-generic-pae (3.2.0-39.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found memtest86+ image: /memtest86+.bin
done
dpkg: [COLOR=#ff0000]dependency problems prevent configuration[/COLOR] of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-37-generic-pae; however:
  Package linux-image-3.2.0-37-generic-pae is not installed.
dpkg: [COLOR=#ff0000]error processing[/COLOR] linux-image-generic-pae (--configure):
 [COLOR=#ff0000]dependency problems[/COLOR] - leaving unconfigured
dpkg: [COLOR=#ff0000]dependency problems prevent configuration[/COLOR] of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.37.45); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.37.45); however:
  Version of linux-headers-generic-pae on system is 3.2.0.39.47.
dpkg: [COLOR=#ff0000]error processing[/COLOR] linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic-pae
[COLOR=#ff0000]Errors were encountered[/COLOR] while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

Command

```
dpkg --list | grep linux-image
```

shows the following:

[INDENT]ii  linux-image-3.2.0-35-generic-pae   3.2.0-35.55                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic-pae   3.2.0-36.57                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic-pae   3.2.0-39.62                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic-pae            3.2.0.37.45                  Generic Linux kernel image
[/INDENT]
 
so I guess that linux-image-3.2.0-37-generic-pae is not really installed but linux-image-generic-pae depends on it. Definitely something is wrong with the dependencies.

Previously I removed kernels up to 34:

```
sudo dpkg -P linux-image-3.2.0-{23..34}-generic-pae
```

---

### Post by schragge on 2013-04-08
Remove the packages, then reinstall them.
```

sudo dpkg --force-remove-reinstreq -r linux-{,image-}generic-pae
sudo apt-get install linux-generic-pae

```

---

### Post by dmitriano on 2013-04-08
Thank you! Solved the problem!

I did:

# **dpkg --force-remove-reinstreq -r linux-{,image-}generic-pae**
(Reading database ... 105386 files and directories currently installed.)
Removing linux-generic-pae ...
Removing linux-image-generic-pae ...
# **apt-get install linux-generic-pae**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  linux-image-generic-pae
The following NEW packages will be installed:
  linux-generic-pae linux-image-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 57 not upgraded.
Need to get 0 B/4,330 B of archives.
After this operation, 63.5 kB of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously unselected package linux-image-generic-pae.
(Reading database ... 105380 files and directories currently installed.)
Unpacking linux-image-generic-pae (from .../linux-image-generic-pae_3.2.0.39.47_i386.deb) ...
Selecting previously unselected package linux-generic-pae.
Unpacking linux-generic-pae (from .../linux-generic-pae_3.2.0.39.47_i386.deb) ...
Setting up linux-image-generic-pae (3.2.0.39.47) ...
Setting up linux-generic-pae (3.2.0.39.47) ...
# **apt-get -f install **
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.
# [B]dpkg --list | grep linux-image
[/B]ii  linux-image-3.2.0-35-generic-pae   3.2.0-35.55                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic-pae   3.2.0-36.57                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic-pae   3.2.0-39.62                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae            3.2.0.39.47                  Generic Linux kernel image
# **apt-get dist-upgrade**

---

### Post by jeSah8ci on 2013-04-08
Thanks! One of my Desktop computers also has this very same problem (Back in '09 I thought that 10 GB would be enough for a Distro), and for the last two upgrades I've had to remove a lot of programs and then re-install them afterwards.

---

### Post by schragge on 2013-04-08
Only for a *distro*, i.e. not counting files in */home*, */opt*, */usr/local*, 10 GB should be enough in most end user scenarios. The problem is that each kernel version installs lots of small files, so that with multiple kernels installed you may run out of [inodes](http://en.wikipedia.org/wiki/Inode) as an inode is consumed for pretty much every file on disk. Number of inodes is defined when you create filesystem (format the drive partition), and cannot be changed afterwards. You can check your current inode budget with ```
df -i
```

---

