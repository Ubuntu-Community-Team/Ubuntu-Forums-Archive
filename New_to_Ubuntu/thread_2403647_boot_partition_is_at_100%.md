---
title: "/boot partition is at 100%"
date: 2018-10-14
forum: New to Ubuntu
---

### Post by far7ad on 2018-10-14
Hi all,

I've come across a problem and even though I've read almost every entry I could find in all the forums, I've not been able to solve the issue.

I'm running an Ubuntu Server 16.04.3.

My /boot is currently at 100%.
Now my last kernel update is stuck and I can't remove any of the old packages using this command:
apt-get remove linux-image-4.4.0.104-generic because of my pending update (Response shared in the picture below).

 [IMG]http://i67.tinypic.com/2ngho1z.jpg[/IMG]

I have also looked into expanding my /boot space (it is currently just 472 MB and I have more than 500 GB of free space), but seems like I can't do so without re-installing my OS (which is going to be my last option).

Appreciate it if you could help me out.

---

### Post by SeijiSensei on 2018-10-14
Let's see the output of "ls -l /boot".  You probably just need to remove some old kernel packages.  Apt is supposed to leave you with just the new and the previous kernel when done, but sometimes that doesn't work correctly.

Try running "sudo apt remove linux-image-[version]-generic" using the oldest value for [version].

---

### Post by ajgreeny on 2018-10-14
I doubt if you will be able to remove or install anything using apt if your /boot partition really is 100% full, which will be shown more clearly with command ```
df -hT
```
I think you will have to remove a few packages first using **dpkg** but to do that we need to know exactly what is installed so please show the output of ```
dpkg -l linux*
```
Once we have removed a few packages we may be able to get rid of all the other unneeded kernel packages using ```
sudo apt autoremove
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by Yellow Pasque on 2018-10-15
^If that doesn't work, you may have to manually use "update-initramfs -d" to free space: [https://help.ubuntu.com/community/RemoveOldKernels#Problems](https://help.ubuntu.com/community/RemoveOldKernels#Problems)

---

### Post by far7ad on 2018-10-15
> **ajgreeny said:**
> I doubt if you will be able to remove or install anything using apt if your /boot partition really is 100% full, which will be shown more clearly with command ```
df -hT
```
I think you will have to remove a few packages first using **dpkg** but to do that we need to know exactly what is installed so please show the output of ```
dpkg -l linux*
```
Once we have removed a few packages we may be able to get rid of all the other unneeded kernel packages using ```
sudo apt autoremove
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

Thanks a lot for your help man.
I was in fact at 100% in the beginning.
I used our friend's suggestion (posted after you) and removed some packages manually. ([COLOR=#000000]"update-initramfs -d")

[/COLOR]Currently, I'm at 73% in my /boot partition.

```


Filesystem                    Type      Size  Used Avail Use% Mounted on
udev                          devtmpfs   16G     0   16G   0% /dev
tmpfs                         tmpfs     3.2G   90M  3.1G   3% /run
/dev/mapper/MAshhad1--vg-root ext4      518G  5.5G  487G   2% /
tmpfs                         tmpfs      16G  8.0K   16G   1% /dev/shm
tmpfs                         tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs                         tmpfs      16G     0   16G   0% /sys/fs/cgroup
/dev/sda1                     ext2      472M  323M  126M  73% /boot
tmpfs                         tmpfs     3.2G     0  3.2G   0% /run/user/1000
/dev/sdb                      vfat      3.8G  2.3G  1.5G  62% /home/farzad/flashdrive


```

Here's the output to your suggested commands:

1. 
```
dpkg -l linux*
[COLOR=#000000]
[/COLOR]Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                Version            Architecture Description
+++-===================================-==================-============-==============================================================
ii  linux-base                          4.5ubuntu1~16.04.1 all          Linux image base package
un  linux-doc-4.4.0                     <none>             <none>       (no description available)
iF  linux-firmware                      1.157.18           all          Firmware for Linux kernel drivers
un  linux-firmware-snapdragon           <none>             <none>       (no description available)
iU  linux-generic                       4.4.0.130.136      amd64        Complete Generic Linux kernel and headers
un  linux-headers                       <none>             <none>       (no description available)
un  linux-headers-3.0                   <none>             <none>       (no description available)
ii  linux-headers-4.4.0-104             4.4.0-104.127      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-104-generic     4.4.0-104.127      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-108             4.4.0-108.131      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-108-generic     4.4.0-108.131      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-109             4.4.0-109.132      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-109-generic     4.4.0-109.132      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-112             4.4.0-112.135      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-112-generic     4.4.0-112.135      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-116             4.4.0-116.140      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-116-generic     4.4.0-116.140      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-119             4.4.0-119.143      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-119-generic     4.4.0-119.143      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-121             4.4.0-121.145      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-121-generic     4.4.0-121.145      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-124             4.4.0-124.148      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-124-generic     4.4.0-124.148      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-127             4.4.0-127.153      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-127-generic     4.4.0-127.153      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-128             4.4.0-128.154      all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-128-generic     4.4.0-128.154      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-130             4.4.0-130.156      all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-130-generic     4.4.0-130.156      amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31              4.4.0-31.50        all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic      4.4.0-31.50        amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-generic               4.4.0.130.136      amd64        Generic Linux kernel headers
un  linux-image                         <none>             <none>       (no description available)
ii  linux-image-4.4.0-104-generic       4.4.0-104.127      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-108-generic       4.4.0-108.131      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-109-generic       4.4.0-109.132      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-112-generic       4.4.0-112.135      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-116-generic       4.4.0-116.140      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-119-generic       4.4.0-119.143      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-121-generic       4.4.0-121.145      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-124-generic       4.4.0-124.148      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-127-generic       4.4.0-127.153      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-128-generic       4.4.0-128.154      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
in  linux-image-4.4.0-130-generic       <none>             amd64        (no description available)
ii  linux-image-4.4.0-31-generic        4.4.0-31.50        amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-104-generic 4.4.0-104.127      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-108-generic 4.4.0-108.131      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-109-generic 4.4.0-109.132      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-112-generic 4.4.0-112.135      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-116-generic 4.4.0-116.140      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-119-generic 4.4.0-119.143      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-121-generic 4.4.0-121.145      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-124-generic 4.4.0-124.148      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-127-generic 4.4.0-127.153      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-128-generic 4.4.0-128.154      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-130-generic 4.4.0-130.156      amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic  4.4.0-31.50        amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                 4.4.0.130.136      amd64        Generic Linux kernel image
un  linux-initramfs-tool                <none>             <none>       (no description available)
un  linux-kernel-log-daemon             <none>             <none>       (no description available)
un  linux-restricted-common             <none>             <none>       (no description available)
un  linux-source-4.4.0                  <none>             <none>       (no description available)
un  linux-tools                         <none>             <none>       (no description available)



```

2.
```


sudo apt autoremove

Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-130-generic : Depends: linux-image-4.4.0-130-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-130-generic but it is not installed
                       Recommends: thermald but it is not installed


```

I still need 371 MB to finish my pending updates (apt-get -f install).
Any idea how I can get rid of all these old packages?

---

### Post by Tadaen_Sylvermane on 2018-10-15
I know it's your last option, but I would reinstall and not do a small /boot. That is a perpetual problem on the forums here, people following bad advice to have a 256, or 512M boot partition. Just repartition and leave it inside of /. You will save yourself this headache in the future by doing so.

That advice on the internet about a small /boot needs to be taken down or hidden somehow. Terrible advice, nothing but a problem. Antiquated as well as it is from the time when /boot needed to be a special format to be read. No longer an issue.

---

### Post by oldfred on 2018-10-15
Actually issue is/was an Ubuntu issue.
The default install using LVM - logical volume management used a smaller /boot which was ok in old days.
But kernel and particularly kernel versions exploded with UEFI & UEFI Secure Boot signed files. But they did not expand /boot at same time.

---

### Post by ajgreeny on 2018-10-15
It looks as if you have an encrypted, or LVM formatted system, both of which mean a separate /boot partition is essential, so short of a complete restart from scratch with newly formatted partitions and install, you can not get rid of that /boot partition.

Let's try ```
sudo apt autoremove
``` to remove unneeded old kernel packages first but if that's unsuccessful we will have to remove them one at a time with ```
sudo dpkg -P linux-image-extra-4.4.0-104-generic linux-image-4.4.0-104-generic linux-headers-4.4.0-104-generic linux-headers-4.4.0-104
``` If that works fine run ```
sudo apt autoremove
``` again which may by now be able to remove all but the two most recent kernels.

If the autoremove works fine you need do nothing more but if there is still insufficient headroom run the first dpkg command again but replace the number 104 in the command with 108 then try the autoremove again.

Once you have this sorted out this problem just remember to run that autoremove program regularly (at least every time a new kernel appears in upgrades) and you shouldn't have this happen again.

---

### Post by far7ad on 2018-10-16
> **ajgreeny said:**
> It looks as if you have an encrypted, or LVM formatted system, both of which mean a separate /boot partition is essential, so short of a complete restart from scratch with newly formatted partitions and install, you can not get rid of that /boot partition.

Let's try ```
sudo apt autoremove
``` to remove unneeded old kernel packages first but if that's unsuccessful we will have to remove them one at a time with ```
sudo dpkg -P linux-image-extra-4.4.0-104-generic linux-image-4.4.0-104-generic linux-headers-4.4.0-104-generic linux-headers-4.4.0-104
``` If that works fine run ```
sudo apt autoremove
``` again which may by now be able to remove all but the two most recent kernels.

If the autoremove works fine you need do nothing more but if there is still insufficient headroom run the first dpkg command again but replace the number 104 in the command with 108 then try the autoremove again.

Once you have this sorted out this problem just remember to run that autoremove program regularly (at least every time a new kernel appears in upgrades) and you shouldn't have this happen again.

Thanks a lot for your suggestions.

Unfortunately the apt autoremove is not working for me.

```

sudo apt autoremove

Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-130-generic : Depends: linux-image-4.4.0-130-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-130-generic but it is not installed
                       Recommends: thermald but it is not installed



```

However, the other command worked like a charm.
I was able to remove a couple of old packages and free up some space.

In the end though, I think it's best for me to do the right thing and do a clean new installation.
In that case, can you point me to a guide for setting up /boot partition with enough space?

---

### Post by ajgreeny on 2018-10-16
Sorry but my knowledge of using LVM is zero so you may need to wait for others to help you with this.

Have you tried using that dpkg command on other kernel versions to get rid of more of the unneeded versions, and have you tried the autoremove command again now that you have lots of headroom in /boot?

It should work and remove all but the two most recent kernel versions, and using a reinstall to sort out this problem seems to be a "sledgehammer to crack a walnut".

You may feel differently, but if you do reinstall I would suggest you do not use LVM partitioning but standard formatting which is much easier to deal with if LVM is not needed for other reasons; it also means you can get rid of that /boot partition completely.
While reinstalling I also suggest you move to 18.04 rather than 16.04.

---

### Post by far7ad on 2018-10-16
> **ajgreeny said:**
> Sorry but my knowledge of using LVM is zero so you may need to wait for others to help you with this.

Have you tried using that dpkg command on other kernel versions to get rid of more of the unneeded versions, and have you tried the autoremove command again now that you have lots of headroom in /boot?

It should work and remove all but the two most recent kernel versions, and using a reinstall to sort out this problem seems to be a "sledgehammer to crack a walnut".

You may feel differently, but if you do reinstall I would suggest you do not use LVM partitioning but standard formatting which is much easier to deal with if LVM is not needed for other reasons; it also means you can get rid of that /boot partition completely.
While reinstalling I also suggest you move to 18.04 rather than 16.04.

Thank you sir.

I'm as well hesitant on using a reinstall.
I was in fact able to get rid of more old versions using your suggested command.

What do you think about upgrading the current system to 18.04 using [COLOR=#333333][FONT=monospace]do-release-upgrade[/FONT][/COLOR] command?  [COLOR=#333333][FONT=Ubuntu][FONT=monospace]
[/FONT]
[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-10-16
Well, you could try a upgrade that way but it is not something I have ever used, so I'm the wrong person to talk about that.

I have all my data files in a separate partition so have fewer worries about a reinstall or OS upgrade using a clean install; I just go to "Something Else" in the installation process and install the OS in the old OS partition, keeping all the data untouched.

So far I have never needed the backups that I regularly make of everything (except the OS itself) but if all did go to worms I could get everything back very easily and quickly, so please don't forget, it is essential to keep good backups that you know can be restored.

---

### Post by far7ad on 2018-10-16
If anyone else is having this problem, this is how I solved it:

1. Remove old packages using 
```
sudo dpkg -P linux-image-extra-4.4.0-104-generic linux-image-4.4.0-104-generic linux-headers-4.4.0-104-generic linux-headers-4.4.0-104
```

2. Installing the latest pending package using
```
 sudo apt-get -f install 
```

3. Removing old packages using
```
 sudo apt autoremove 
```

Now I'm up to date and have lots of free space in my /boot partition!

Special thanks to "**ajgreeny**" for his help.

---

