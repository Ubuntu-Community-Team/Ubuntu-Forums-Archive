---
title: "Compatible Hardware ID's?"
date: 2020-04-12
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2020-04-12
Are any of the following hardware ID's compatible with Ubuntu?

I'm planning to switch from Windows to Ubuntu.



============================================


Qualcomm Atheros AR5B95 Wireless Network Adapter


Hardware ID's


PCI\VEN_168C&DEV_002B&SUBSYS_663111AD&REV_01
PCI\VEN_168C&DEV_002B&SUBSYS_663111AD
PCI\VEN_168C&DEV_002B&CC_028000
PCI\VEN_168C&DEV_002B&CC_0280


Compatible ID's


PCI\VEN_168C&DEV_002B&REV_01
PCI\VEN_168C&DEV_002B
PCI\VEN_168C&CC_028000
PCI\VEN_168C&CC_0280
PCI\VEN_168C
PCI\CC_028000
PCI\CC_0280


============================================


Intel(R) HD Graphics


Hardware ID's


PCI\VEN_8086&DEV_0046&SUBSYS_06011025&REV_02
PCI\VEN_8086&DEV_0046&SUBSYS_06011025
PCI\VEN_8086&DEV_0046&CC_030000
PCI\VEN_8086&DEV_0046&CC_0300


Compatible ID's


PCI\VEN_8086&DEV_0046&REV_02
PCI\VEN_8086&DEV_0046
PCI\VEN_8086&CC_030000
PCI\VEN_8086&CC_0300
PCI\VEN_8086
PCI\CC_030000
PCI\CC_0300


============================================

---

### Post by grahammechanical on 2020-04-12
Ubuntu has a certification program that hardware vendors can submit their machines to.

[https://certification.ubuntu.com/](https://certification.ubuntu.com/)

The pages for each machine give a detailed breakdown of the hardware in the machine. As a rule of thumb, the newer the hardware the newer the version of Linux/Ubuntu that is needed.

Ubuntu is built on the Linux OS kernel. Hardware drivers are part of the Linux kernel and are continually being updated or added as hardware gets ever more advanced. The latest versions of Ubuntu contain the latest Linux hardware stack. Every two years Ubuntu releases a version that is given Long Term Support (LTS) lasting 5 years. The next Ubuntu LTS release comes at the end of this April with Ubuntu 20.04. Year 20. Month 04. The last Ubuntu LTS release was 18.04. That version will be updated with the latest Linux hardware stack because it is Long Term Support and users of multiple machines like to have the same version of the OS on all their machines.

One way to test Ubuntu is to download the ISO image and burn it to a USB memory stick and run Ubuntu from the memory stick without installing it. That way you can test to see if all the hardware works.

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

Regards.

---

### Post by TheFu on 2020-04-12
i wouldn't know how to use that data, hw-ids, to check for compatibility. Wouldn't know how to get that list. is that a Windows thing?  We usually look at chips and versions of the chips, then look them up 1 at a time.
For example, for network stuff, 
```
$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
02:00.0 Network controller: **Intel Corporation Wireless 8265 / 8275** (rev 78)
        Subsystem: Intel Corporation Dual Band Wireless-AC 8265
        Flags: bus master, fast devsel, latency 0, IRQ 128
        Memory at ef000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: **iwlwifi**
        Kernel modules: iwlwifi
```
For video:
```
$ lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
00:02.0 VGA compatible controller: **Intel Corporation UHD Graphics 620 (rev 07)** (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1d30
        Flags: bus master, fast devsel, latency 0, IRQ 126
        Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: **i915**
        Kernel modules: i915

```

A quick overview of hardware can be seen using:
```
$ inxi -Fz
```

Certain manufacturers are known to be Linux friendly.  Others are known not to be friendly.  in general, intel video and networking will work well, drivers automatically installed and have next to zero issues.

---

### Post by him610 on 2020-04-12
wyattwhiteeagle,

Recommend you boot from USB drive loaded with bootable  *buntu version of your choice then run the commands TheFu (Post #3) has suggested and post the results in a reply between the code tags.

---

### Post by wyattwhiteeagle on 2020-04-13
> **him610 said:**
> wyattwhiteeagle,

Recommend you boot from USB drive loaded with bootable  *buntu version of your choice then run the commands TheFu (Post #3) has suggested and post the results in a reply between the code tags.

I chose to install on the main drive. I hope that isn't the reason I received this message...

```
wyatt@wyatt-Aspire-5733Z:~$ inxi -Fz


Command 'inxi' not found, but can be installed with:


sudo apt install inxi


wyatt@wyatt-Aspire-5733Z:~$ sudo apt install inxi
[sudo] password for wyatt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inxi
wyatt@wyatt-Aspire-5733Z:~$ 

```

---

### Post by Impavidus on 2020-04-13
If you already installed Ubuntu, most of it must work. I'm not familiar with such hardware IDs either.

Did you update the package database?```
sudo apt update
```That refreshes the list of available software from the repositories.

Which Ubuntu release have you installed?

---

### Post by Holger_Gehrke on 2020-04-13
Those are PCI-IDs. A list of those can be found in /usr/share/misc/pci.ids and is used by the 'lspci' command. Running 'lspci -v -k' should give you a list of all pci-devices in the machine that includes the drivers / kernel modules used for them. Vendor "168c" and device "002b" is an "AR9285 Wireless Network Adapter (PCI-Express)" by Qualcomm Atheros. According to this [page]("https://wiki.debian.org/ath9k") in the Debian Wiki it should be supported by the ath9k driver. That page also links to instructions on how to identify (pci) devices. The other set of IDs (Vendor 8086, device 46) is some variant of Intel integrated graphics. Those too should be supported.

Holger

---

### Post by mörgæs on 2020-04-13
Googling Aspire 5733Z seems to indicate that it mostly comes with 2 GB of memory.

You computer could of course be upgraded but if it's the case for you then you should focus on X/Lubuntu in stead of Ubuntu.

---

### Post by grahammechanical on 2020-04-13
As a test I have just installed inxi on my 18.04 system. It should also be available for Ubuntu versions from 16.04 to the present. Make sure you have the Universe repo enabled. Software & Updates utility.

Regards.

---

### Post by wyattwhiteeagle on 2020-04-13
Ubuntu 18.04.4 Installed. (no dual boot)

How do I export a file of my current system specs?

How do I enable Universe repo?

I will post the results of "sudo apt update"

---

### Post by wyattwhiteeagle on 2020-04-13
```


wyatt@wyatt-Aspire-5733Z:~$ sudo apt update
[sudo] password for wyatt: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Fetched 252 kB in 1s (208 kB/s)                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
48 packages can be upgraded. Run 'apt list --upgradable' to see them.
wyatt@wyatt-Aspire-5733Z:~$ apt list --upgradable
Listing... Done
bsdutils/bionic-updates 1:2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 1:2.31.1-0.4ubuntu3.5]
dmidecode/bionic-updates 3.1-1ubuntu0.1 amd64 [upgradable from: 3.1-1]
fdisk/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
fwupd/bionic-updates 1.2.10-1ubuntu2~ubuntu18.04.3 amd64 [upgradable from: 1.0.9-0ubuntu2]
fwupdate/bionic-updates 12-7~ubuntu18.04.3 amd64 [upgradable from: 12-3bionic2]
fwupdate-signed/bionic-updates 12-7~ubuntu18.04.3 amd64 [upgradable from: 1.19bionic2+12-3bionic2]
gir1.2-nm-1.0/bionic-updates 1.10.6-2ubuntu1.4 amd64 [upgradable from: 1.10.6-2ubuntu1.2]
grub-common/bionic-updates 2.02-2ubuntu8.15 amd64 [upgradable from: 2.02-2ubuntu8.14]
grub-pc/bionic-updates 2.02-2ubuntu8.15 amd64 [upgradable from: 2.02-2ubuntu8.14]
grub-pc-bin/bionic-updates 2.02-2ubuntu8.15 amd64 [upgradable from: 2.02-2ubuntu8.14]
grub2-common/bionic-updates 2.02-2ubuntu8.15 amd64 [upgradable from: 2.02-2ubuntu8.14]
libasound2/bionic-updates 1.1.3-5ubuntu0.4 amd64 [upgradable from: 1.1.3-5ubuntu0.2]
libasound2-data/bionic-updates,bionic-updates 1.1.3-5ubuntu0.4 all [upgradable from: 1.1.3-5ubuntu0.2]
libblkid1/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
libegl-mesa0/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
libegl1-mesa/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
libfdisk1/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
libfwupd2/bionic-updates 1.2.10-1ubuntu2~ubuntu18.04.3 amd64 [upgradable from: 1.0.9-0ubuntu2]
libgbm1/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
libgl1-mesa-dri/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
libgl1-mesa-glx/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
libglapi-mesa/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
libglx-mesa0/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
libmount1/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
libnm0/bionic-updates 1.10.6-2ubuntu1.4 amd64 [upgradable from: 1.10.6-2ubuntu1.2]
libnss-myhostname/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
libnss-systemd/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
libpam-systemd/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
libsgutils2-2/bionic-updates 1.42-2ubuntu1.18.04.2 amd64 [upgradable from: 1.42-2ubuntu1.18.04.1]
libsmartcols1/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
libsystemd0/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
libudev1/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
libuuid1/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
libxatracker2/bionic-updates 19.2.8-0ubuntu0~18.04.3 amd64 [upgradable from: 19.2.8-0ubuntu0~18.04.2]
linux-firmware/bionic-updates,bionic-updates 1.173.17 all [upgradable from: 1.173.14]
mount/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
network-manager/bionic-updates 1.10.6-2ubuntu1.4 amd64 [upgradable from: 1.10.6-2ubuntu1.2]
network-manager-config-connectivity-ubuntu/bionic-updates,bionic-updates 1.10.6-2ubuntu1.4 all [upgradable from: 1.10.6-2ubuntu1.2]
rfkill/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
systemd/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
systemd-sysv/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
udev/bionic-updates 237-3ubuntu10.39 amd64 [upgradable from: 237-3ubuntu10.38]
unattended-upgrades/bionic-updates,bionic-updates 1.1ubuntu1.18.04.14 all [upgradable from: 1.1ubuntu1.18.04.13]
util-linux/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
uuid-runtime/bionic-updates 2.31.1-0.4ubuntu3.6 amd64 [upgradable from: 2.31.1-0.4ubuntu3.5]
xserver-common/bionic-updates,bionic-updates 2:1.19.6-1ubuntu4.4 all [upgradable from: 2:1.19.6-1ubuntu4.3]
xserver-xephyr/bionic-updates 2:1.19.6-1ubuntu4.4 amd64 [upgradable from: 2:1.19.6-1ubuntu4.3]
xwayland/bionic-updates 2:1.19.6-1ubuntu4.4 amd64 [upgradable from: 2:1.19.6-1ubuntu4.3]
wyatt@wyatt-Aspire-5733Z:~$ 



```

---

### Post by deadflowr on 2020-04-13
To enable universe either open the Program called Software and Updates
and check the option Community-Maintained in the first section ( the section marked as Ubuntu Software)
or run this
```
sudo add-apt-repository universe
sudo apt update
```
in a terminal.
[s]One the apt update finishes, if no errors are produced you can install the packages that have been recommended.[/s]

Edit: I see the output from post #11, 
It is usually best to go ahead and install all those updates first
run
```
sudo apt full-upgrade
```
to install and apply the updates.

After that you can try enabling universe.

---

### Post by wyattwhiteeagle on 2020-04-13
Ubuntu 18.04.4 Installed. (no dual boot)

How do I export a file of my current system specs?

How do I enable Universe repo?

The results of "sudo apt update" are in the previous post. Should I upgrade those 48 packages?

---

### Post by wyattwhiteeagle on 2020-04-13
> **deadflowr said:**
> To enable universe either open the Program called Software and Updates
and check the option Community-Maintained in the first section ( the section marked as Ubuntu Software)
or run this
```
sudo add-apt-repository universe
sudo apt update
```
in a terminal.
[s]One the apt update finishes, if no errors are produced you can install the packages that have been recommended.[/s]

Edit: I see the output from post #11, 
It is usually best to go ahead and install all those updates first
run
```
sudo apt full-upgrade
```
to install and apply the updates.

After that you can try enabling universe.

OK Will do. I'll post the results :)

---

### Post by TheFu on 2020-04-13
> **wyattwhiteeagle said:**
> Ubuntu 18.04.4 Installed. (no dual boot)

How do I export a file of my current system specs?

How do I enable Universe repo?

The results of "sudo apt update" are in the previous post. Should I upgrade those 48 packages?

YES!  every week, you should patch every Linux desktop.

```
sudo apt update  && sudo apt full-upgrade
```
About once a month run
```
sudo apt autoremove
sudo apt autoclean
```

There are many different ways to get an overview of the current hardware.
```
sudo inxi -F
```
is one.
```
sudo lshw 
```
is another.

People really new to Unix/Linux, need to read a primer to prevent noob mistakes.  Many "truths" for Windows do not apply, but a few do.  Start with this: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)

The next step would be to setup backups.  Backups are required.  Don't expect the OS to magically protect you from asking for bad things.  it will do what you tell it, even if that command is really stupid.  The first few times you wipe out your data or make the system not boot, you'll wish you had backups.  Don't expect the system to warn you away from doing dumb things.

---

### Post by wyattwhiteeagle on 2020-04-13
> **wyattwhiteeagle said:**
> OK Will do. I'll post the results :)


```


wyatt@wyatt-Aspire-5733Z:~$ sudo apt full-upgrade
[sudo] password for wyatt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  efibootmgr libfwup1
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  fwupd-signed libxmlb1
The following packages will be upgraded:
  bsdutils dmidecode fdisk fwupd fwupdate fwupdate-signed gir1.2-nm-1.0
  grub-common grub-pc grub-pc-bin grub2-common libasound2 libasound2-data
  libblkid1 libegl-mesa0 libegl1-mesa libfdisk1 libfwupd2 libgbm1
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglx-mesa0 libmount1 libnm0
  libnss-myhostname libnss-systemd libpam-systemd libsgutils2-2 libsmartcols1
  libsystemd0 libudev1 libuuid1 libxatracker2 linux-firmware mount
  network-manager network-manager-config-connectivity-ubuntu rfkill systemd
  systemd-sysv udev unattended-upgrades util-linux uuid-runtime xserver-common
  xserver-xephyr xwayland
48 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 102 MB of archives.
After this operation, 6,372 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 bsdutils amd64 1:2.31.1-0.4ubuntu3.6 [60.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libuuid1 amd64 2.31.1-0.4ubuntu3.6 [20.1 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libblkid1 amd64 2.31.1-0.4ubuntu3.6 [124 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libfdisk1 amd64 2.31.1-0.4ubuntu3.6 [164 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libmount1 amd64 2.31.1-0.4ubuntu3.6 [136 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libsmartcols1 amd64 2.31.1-0.4ubuntu3.6 [83.7 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 fdisk amd64 2.31.1-0.4ubuntu3.6 [108 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 util-linux amd64 2.31.1-0.4ubuntu3.6 [903 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnss-systemd amd64 237-3ubuntu10.39 [104 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libsystemd0 amd64 237-3ubuntu10.39 [206 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libpam-systemd amd64 237-3ubuntu10.39 [107 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnss-myhostname amd64 237-3ubuntu10.39 [35.4 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 systemd amd64 237-3ubuntu10.39 [2,912 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 udev amd64 237-3ubuntu10.39 [1,102 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libudev1 amd64 237-3ubuntu10.39 [56.1 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 systemd-sysv amd64 237-3ubuntu10.39 [13.9 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mount amd64 2.31.1-0.4ubuntu3.6 [107 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 uuid-runtime amd64 2.31.1-0.4ubuntu3.6 [34.8 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 dmidecode amd64 3.1-1ubuntu0.1 [50.9 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libfwupd2 amd64 1.2.10-1ubuntu2~ubuntu18.04.3 [46.3 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libxmlb1 amd64 0.1.8-1~ubuntu18.04.1 [45.6 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 fwupd amd64 1.2.10-1ubuntu2~ubuntu18.04.3 [2,484 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 fwupd-signed amd64 1.10~ubuntu18.04.3+1.2.10-1ubuntu2~ubuntu18.04.3 [26.8 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 fwupdate-signed amd64 12-7~ubuntu18.04.3 [3,032 B]
Get:25 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 fwupdate amd64 12-7~ubuntu18.04.3 [3,400 B]
Get:26 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnm0 amd64 1.10.6-2ubuntu1.4 [298 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gir1.2-nm-1.0 amd64 1.10.6-2ubuntu1.4 [54.8 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 grub-pc amd64 2.02-2ubuntu8.15 [138 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 grub2-common amd64 2.02-2ubuntu8.15 [532 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 grub-pc-bin amd64 2.02-2ubuntu8.15 [900 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 grub-common amd64 2.02-2ubuntu8.15 [1,775 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libasound2 amd64 1.1.3-5ubuntu0.4 [361 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libasound2-data all 1.1.3-5ubuntu0.4 [38.0 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libegl-mesa0 amd64 19.2.8-0ubuntu0~18.04.3 [95.1 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libgbm1 amd64 19.2.8-0ubuntu0~18.04.3 [28.1 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libgl1-mesa-dri amd64 19.2.8-0ubuntu0~18.04.3 [8,811 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libglx-mesa0 amd64 19.2.8-0ubuntu0~18.04.3 [139 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libglapi-mesa amd64 19.2.8-0ubuntu0~18.04.3 [26.5 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libegl1-mesa amd64 19.2.8-0ubuntu0~18.04.3 [6,864 B]
Get:40 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libgl1-mesa-glx amd64 19.2.8-0ubuntu0~18.04.3 [5,528 B]
Get:41 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libsgutils2-2 amd64 1.42-2ubuntu1.18.04.2 [59.8 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libxatracker2 amd64 19.2.8-0ubuntu0~18.04.3 [1,459 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-firmware all 1.173.17 [75.1 MB]
Get:44 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 network-manager amd64 1.10.6-2ubuntu1.4 [1,505 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 network-manager-config-connectivity-ubuntu all 1.10.6-2ubuntu1.4 [2,524 B]
Get:46 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 rfkill amd64 2.31.1-0.4ubuntu3.6 [24.8 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 unattended-upgrades all 1.1ubuntu1.18.04.14 [41.7 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 xserver-common all 2:1.19.6-1ubuntu4.4 [27.3 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 xserver-xephyr amd64 2:1.19.6-1ubuntu4.4 [923 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 xwayland amd64 2:1.19.6-1ubuntu4.4 [863 kB]
Fetched 102 MB in 29s (3,529 kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../bsdutils_1%3a2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking bsdutils (1:2.31.1-0.4ubuntu3.6) over (1:2.31.1-0.4ubuntu3.5) ...
Setting up bsdutils (1:2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../libuuid1_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking libuuid1:amd64 (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Setting up libuuid1:amd64 (2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../libblkid1_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking libblkid1:amd64 (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Setting up libblkid1:amd64 (2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../libfdisk1_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking libfdisk1:amd64 (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Setting up libfdisk1:amd64 (2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../libmount1_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking libmount1:amd64 (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Setting up libmount1:amd64 (2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../libsmartcols1_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking libsmartcols1:amd64 (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Setting up libsmartcols1:amd64 (2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../fdisk_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking fdisk (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Setting up fdisk (2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../util-linux_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking util-linux (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Setting up util-linux (2.31.1-0.4ubuntu3.6) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../libnss-systemd_237-3ubuntu10.39_amd64.deb ...
Unpacking libnss-systemd:amd64 (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Preparing to unpack .../libsystemd0_237-3ubuntu10.39_amd64.deb ...
Unpacking libsystemd0:amd64 (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Setting up libsystemd0:amd64 (237-3ubuntu10.39) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_237-3ubuntu10.39_amd64.deb ...
Unpacking libpam-systemd:amd64 (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Preparing to unpack .../libnss-myhostname_237-3ubuntu10.39_amd64.deb ...
Unpacking libnss-myhostname:amd64 (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Preparing to unpack .../systemd_237-3ubuntu10.39_amd64.deb ...
Unpacking systemd (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Preparing to unpack .../udev_237-3ubuntu10.39_amd64.deb ...
Unpacking udev (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Preparing to unpack .../libudev1_237-3ubuntu10.39_amd64.deb ...
Unpacking libudev1:amd64 (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Setting up libudev1:amd64 (237-3ubuntu10.39) ...
Setting up systemd (237-3ubuntu10.39) ...
(Reading database ... 163506 files and directories currently installed.)
Preparing to unpack .../00-systemd-sysv_237-3ubuntu10.39_amd64.deb ...
Unpacking systemd-sysv (237-3ubuntu10.39) over (237-3ubuntu10.38) ...
Preparing to unpack .../01-mount_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking mount (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Preparing to unpack .../02-uuid-runtime_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking uuid-runtime (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Preparing to unpack .../03-dmidecode_3.1-1ubuntu0.1_amd64.deb ...
Unpacking dmidecode (3.1-1ubuntu0.1) over (3.1-1) ...
Preparing to unpack .../04-libfwupd2_1.2.10-1ubuntu2~ubuntu18.04.3_amd64.deb ...
Unpacking libfwupd2:amd64 (1.2.10-1ubuntu2~ubuntu18.04.3) over (1.0.9-0ubuntu2) ...
Selecting previously unselected package libxmlb1:amd64.
Preparing to unpack .../05-libxmlb1_0.1.8-1~ubuntu18.04.1_amd64.deb ...
Unpacking libxmlb1:amd64 (0.1.8-1~ubuntu18.04.1) ...
Preparing to unpack .../06-fwupd_1.2.10-1ubuntu2~ubuntu18.04.3_amd64.deb ...
Unpacking fwupd (1.2.10-1ubuntu2~ubuntu18.04.3) over (1.0.9-0ubuntu2) ...
Selecting previously unselected package fwupd-signed.
Preparing to unpack .../07-fwupd-signed_1.10~ubuntu18.04.3+1.2.10-1ubuntu2~ubuntu18.04.3_amd64.deb ...
Unpacking fwupd-signed (1.10~ubuntu18.04.3+1.2.10-1ubuntu2~ubuntu18.04.3) ...
Preparing to unpack .../08-fwupdate-signed_12-7~ubuntu18.04.3_amd64.deb ...
Unpacking fwupdate-signed (12-7~ubuntu18.04.3) over (1.19bionic2+12-3bionic2) ...
Preparing to unpack .../09-fwupdate_12-7~ubuntu18.04.3_amd64.deb ...
/var/lib/dpkg/tmp.ci/preinst: 8: /var/lib/dpkg/tmp.ci/preinst: dpkg-vendor: not found
Unpacking fwupdate (12-7~ubuntu18.04.3) over (12-3bionic2) ...
Preparing to unpack .../10-libnm0_1.10.6-2ubuntu1.4_amd64.deb ...
Unpacking libnm0:amd64 (1.10.6-2ubuntu1.4) over (1.10.6-2ubuntu1.2) ...
Preparing to unpack .../11-gir1.2-nm-1.0_1.10.6-2ubuntu1.4_amd64.deb ...
Unpacking gir1.2-nm-1.0:amd64 (1.10.6-2ubuntu1.4) over (1.10.6-2ubuntu1.2) ...
Preparing to unpack .../12-grub-pc_2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub-pc (2.02-2ubuntu8.15) over (2.02-2ubuntu8.14) ...
Preparing to unpack .../13-grub2-common_2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub2-common (2.02-2ubuntu8.15) over (2.02-2ubuntu8.14) ...
Preparing to unpack .../14-grub-pc-bin_2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub-pc-bin (2.02-2ubuntu8.15) over (2.02-2ubuntu8.14) ...
Preparing to unpack .../15-grub-common_2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub-common (2.02-2ubuntu8.15) over (2.02-2ubuntu8.14) ...
Preparing to unpack .../16-libasound2_1.1.3-5ubuntu0.4_amd64.deb ...
Unpacking libasound2:amd64 (1.1.3-5ubuntu0.4) over (1.1.3-5ubuntu0.2) ...
Preparing to unpack .../17-libasound2-data_1.1.3-5ubuntu0.4_all.deb ...
Unpacking libasound2-data (1.1.3-5ubuntu0.4) over (1.1.3-5ubuntu0.2) ...
Preparing to unpack .../18-libegl-mesa0_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libegl-mesa0:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../19-libgbm1_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libgbm1:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../20-libgl1-mesa-dri_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../21-libglx-mesa0_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libglx-mesa0:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../22-libglapi-mesa_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libglapi-mesa:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../23-libegl1-mesa_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libegl1-mesa:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../24-libgl1-mesa-glx_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../25-libsgutils2-2_1.42-2ubuntu1.18.04.2_amd64.deb ...
Unpacking libsgutils2-2 (1.42-2ubuntu1.18.04.2) over (1.42-2ubuntu1.18.04.1) ...
Preparing to unpack .../26-libxatracker2_19.2.8-0ubuntu0~18.04.3_amd64.deb ...
Unpacking libxatracker2:amd64 (19.2.8-0ubuntu0~18.04.3) over (19.2.8-0ubuntu0~18.04.2) ...
Preparing to unpack .../27-linux-firmware_1.173.17_all.deb ...
Unpacking linux-firmware (1.173.17) over (1.173.14) ...
Preparing to unpack .../28-network-manager_1.10.6-2ubuntu1.4_amd64.deb ...
Unpacking network-manager (1.10.6-2ubuntu1.4) over (1.10.6-2ubuntu1.2) ...
Preparing to unpack .../29-network-manager-config-connectivity-ubuntu_1.10.6-2ubuntu1.4_all.deb ...
Unpacking network-manager-config-connectivity-ubuntu (1.10.6-2ubuntu1.4) over (1.10.6-2ubuntu1.2) ...
Preparing to unpack .../30-rfkill_2.31.1-0.4ubuntu3.6_amd64.deb ...
Unpacking rfkill (2.31.1-0.4ubuntu3.6) over (2.31.1-0.4ubuntu3.5) ...
Preparing to unpack .../31-unattended-upgrades_1.1ubuntu1.18.04.14_all.deb ...
Unpacking unattended-upgrades (1.1ubuntu1.18.04.14) over (1.1ubuntu1.18.04.13) ...
Preparing to unpack .../32-xserver-common_2%3a1.19.6-1ubuntu4.4_all.deb ...
Unpacking xserver-common (2:1.19.6-1ubuntu4.4) over (2:1.19.6-1ubuntu4.3) ...
Preparing to unpack .../33-xserver-xephyr_2%3a1.19.6-1ubuntu4.4_amd64.deb ...
Unpacking xserver-xephyr (2:1.19.6-1ubuntu4.4) over (2:1.19.6-1ubuntu4.3) ...
Preparing to unpack .../34-xwayland_2%3a1.19.6-1ubuntu4.4_amd64.deb ...
Unpacking xwayland (2:1.19.6-1ubuntu4.4) over (2:1.19.6-1ubuntu4.3) ...
Setting up libnss-systemd:amd64 (237-3ubuntu10.39) ...
Setting up xserver-common (2:1.19.6-1ubuntu4.4) ...
Setting up libnss-myhostname:amd64 (237-3ubuntu10.39) ...
Setting up dmidecode (3.1-1ubuntu0.1) ...
Setting up libfwupd2:amd64 (1.2.10-1ubuntu2~ubuntu18.04.3) ...
Setting up systemd-sysv (237-3ubuntu10.39) ...
Setting up libnm0:amd64 (1.10.6-2ubuntu1.4) ...
Setting up libasound2-data (1.1.3-5ubuntu0.4) ...
Setting up libgbm1:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Setting up mount (2.31.1-0.4ubuntu3.6) ...
Setting up libglapi-mesa:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Setting up xserver-xephyr (2:1.19.6-1ubuntu4.4) ...
Setting up libxatracker2:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Setting up libxmlb1:amd64 (0.1.8-1~ubuntu18.04.1) ...
Setting up libasound2:amd64 (1.1.3-5ubuntu0.4) ...
Setting up uuid-runtime (2.31.1-0.4ubuntu3.6) ...
Setting up libsgutils2-2 (1.42-2ubuntu1.18.04.2) ...
Setting up udev (237-3ubuntu10.39) ...
update-initramfs: deferring update (trigger activated)
Setting up grub-common (2.02-2ubuntu8.15) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up unattended-upgrades (1.1ubuntu1.18.04.14) ...
Replacing config file /etc/apt/apt.conf.d/50unattended-upgrades with new version
Setting up fwupd (1.2.10-1ubuntu2~ubuntu18.04.3) ...
Installing new version of config file /etc/fwupd/daemon.conf ...
Installing new version of config file /etc/fwupd/remotes.d/lvfs-testing.conf ...
Installing new version of config file /etc/fwupd/remotes.d/lvfs.conf ...
Installing new version of config file /etc/fwupd/remotes.d/vendor.conf ...
Installing new version of config file /etc/fwupd/uefi.conf ...
fwupd-offline-update.service is a disabled or a static unit not running, not starting it.
Setting up libegl-mesa0:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Setting up xwayland (2:1.19.6-1ubuntu4.4) ...
Setting up linux-firmware (1.173.17) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-46-generic
update-initramfs: Generating /boot/initrd.img-5.3.0-28-generic
Setting up rfkill (2.31.1-0.4ubuntu3.6) ...
Setting up libegl1-mesa:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Setting up fwupdate (12-7~ubuntu18.04.3) ...
Setting up gir1.2-nm-1.0:amd64 (1.10.6-2ubuntu1.4) ...
Setting up libpam-systemd:amd64 (237-3ubuntu10.39) ...
Setting up grub-pc-bin (2.02-2ubuntu8.15) ...
Setting up libgl1-mesa-dri:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Setting up grub2-common (2.02-2ubuntu8.15) ...
Setting up fwupd-signed (1.10~ubuntu18.04.3+1.2.10-1ubuntu2~ubuntu18.04.3) ...
Setting up network-manager (1.10.6-2ubuntu1.4) ...
Setting up libglx-mesa0:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Setting up fwupdate-signed (12-7~ubuntu18.04.3) ...
Setting up grub-pc (2.02-2ubuntu8.15) ...
Installing for i386-pc platform.
Installation finished. No error reported.
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-46-generic
Found initrd image: /boot/initrd.img-5.3.0-46-generic
Found linux image: /boot/vmlinuz-5.3.0-28-generic
Found initrd image: /boot/initrd.img-5.3.0-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up network-manager-config-connectivity-ubuntu (1.10.6-2ubuntu1.4) ...
Setting up libgl1-mesa-glx:amd64 (19.2.8-0ubuntu0~18.04.3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for dbus (1.12.2-1ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-21) ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info (6.5.0.dfsg.1-2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for systemd (237-3ubuntu10.39) ...
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-46-generic
wyatt@wyatt-Aspire-5733Z:~$ 



```

---

### Post by deadflowr on 2020-04-13
Looks good.
Now you can try enabling universe > update > install inxi.
You need to run apt update whenever you add any repositories so the system has the correct information for it.
(The graphical way using Software and Updates automatically updates it when you close the window, fwiw.
but since inxi is a command line utility it's probably quicker and easier to do it all through a terminal.)

---

### Post by wyattwhiteeagle on 2020-04-13
Should I have worked out all the Ubuntu installation kinks or is that what I'm doing right now?

Where's a good place to post my System Specs?

---

### Post by TheFu on 2020-04-13
> **wyattwhiteeagle said:**
> Should I have worked out all the Ubuntu installation kinks or is that what I'm doing right now?

Where's a good place to post my System Specs?

You never mentioned any issues.  

I'd assumed someone, probably from Windows, handed you a list of "hardware IDs" for a system you were thinking about buying.
All you've done so far is what anyone should do immediately after an install - at least the commands I posted above related to **apt** are things everyone should do every week, assuming they aren't a GUI-only user.

The best way to use these forums is to post 1 issue, in 1 thread, at a time.  
[LIST]
[*]Give it a good, short, title - lead with the specific HW item
[*]State the issue clearly.
[*]Ask if that is normal or something is broke
[*]Provide the exact HW and driver currently being used.
[*]Always say the exact version of Ubuntu and the DE being used.
[/LIST]

Show proof, using shell commands, _not images_, whenever possible.  Select/paste the output from the shell has I've shown above and wrap them in code tags so the result here are lined up just like they are in the terminal.

Most of my installs the last 10 yrs have "just worked" with a few exceptions.  Until this month, my 18.04 server installs wouldn't setup static IPs correctly.  A test install in January was broken still.  That probably doesn't matter to you.  I don't do many desktop installs. Think my last desktop install was over a year ago after getting a new-to-me laptop.  The only things I remember not working for that install was the fingerprint reader.  I'd never use it, since I know better than to use anything like that for real security.  A few quick searches and I found that the chip used for it doesn't have any Linux support at all.

For most laptops that do have any issues, a google for "maker model ubuntu install" will usually find a page where someone else already discovered all the solutions for little issues like getting a black-light to work or remapping a keyboard for those keyboards that don't have a DELETE key (CNTL-Bksp) or don't have a SUPER key (CapsLock).  Some laptops have 2 GPUs which I've always avoided. I understand getting the discrete GPU to work for some of those can be non-trivial.  

For desktops, newish AMD or nVidia GPUs are pretty easy to get working provided they aren't too new or too old.  

Some weird hardware will never work.  Cheap RAID cards usually get used as JBOD controllers, which is probably best anyways.  MB RAID is usually a complete waste of effort for a number of reasons and should be avoided.

For specific hardware, my first post showed how to get the lspci output we'd want.  **lshw** can be better - find the specific area for the specific hardware.  Nobody wants to see everything.

If you don't know how to do something. Ask.  Nobody is asking you do type more than the commands. No transcribing should ever be needed, even on a system that doesn't have networking. There are output redirection methods to capture output from commands, store them into a file that can be moved to a different system.

And please use {tab}-completion.  IF you don't know about that already, stop.  Search on youtube, find a short video about it, practice it.  People type entirely too much and end up with the wrong arguments due to spelling mistakes that {tab}-completion would easily prevent.

---

### Post by wyattwhiteeagle on 2020-04-13
> **TheFu said:**
> You never mentioned any issues.

I never mentioned any issues because I haven't had any issues happen with Ubuntu 18.04.4 LTS. I'd rather not run into any issues. It's why I'm asking now before I do run into issues.

> **TheFu said:**
> I'd assumed someone, probably from Windows, handed you a list of "hardware IDs" for a system you were thinking about buying.

The Hardware ID's in this threads first post are ID's to the Display Adapter and the Wireless Network Adapter I currently use on this Acer Aspire 5733z system I bought 7 or 8 years ago. They are original parts. The only hardware I have upgraded is the RAM sticks and the HDD.

> **TheFu said:**
> All you've done so far is what anyone should do immediately after an install - at least the commands I posted above related to **apt** are things everyone should do every week

Thank you. That's exactly what I was aiming to accomplish :)

> **TheFu said:**
> assuming they aren't a GUI-only user.

Um, what exactly is a GUI-only user and a non-GUI-only user?

---

### Post by TheFu on 2020-04-13
> **wyattwhiteeagle said:**
>  
Um, what exactly is a GUI-only user and a non-GUI-only user?

Server  installs don't have any GUi.  No mouse. No windows. No menus. Just a terminal.  The vast majority of Linux systems in the world don't have any GUi.

---

