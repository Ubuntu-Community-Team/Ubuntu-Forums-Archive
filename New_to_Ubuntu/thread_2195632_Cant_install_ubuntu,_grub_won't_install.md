---
title: "Cant install ubuntu, grub won't install"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by roma24ster on 2013-12-25
I have an acer travel mate p253-E which came with Win8 on it. I disabled secure boot, and am trying to install ubuntu 12.04.3 from a live-usb stick. Halfway through the installation, I get the error message: The 'grub-efi-amd64-signed' package failed to install into /target/. 

I read somewhere that I should use boot repair, here is the console output:

```
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra gawk glade2script libsigsegv2
Suggested packages:
  lvm2 mbr mdadm clean-ubiquity os-uninstaller
Recommended packages:
  pastebinit
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk glade2script libsigsegv2
0 upgraded, 6 newly installed, 0 to remove and 217 not upgraded.
Need to get 1,138 kB of archives.
After this operation, 4,278 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main glade2script all 3.2.2~ppa45~precise [42.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/main libsigsegv2 amd64 2.9-4ubuntu2 [14.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise/main gawk amd64 1:3.1.8+dfsg-0.1ubuntu1 [465 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main boot-sav all 3.199~ppa40~precise [427 kB]
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main boot-repair all 3.199~ppa40~precise [46.9 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main boot-sav-extra all 3.199~ppa40~precise [142 kB]
Fetched 1,138 kB in 12s (91.3 kB/s)                                            
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously unselected package libsigsegv2.
(Reading database ... 146259 files and directories currently installed.)
Unpacking libsigsegv2 (from .../libsigsegv2_2.9-4ubuntu2_amd64.deb) ...
Setting up libsigsegv2 (2.9-4ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package gawk.
(Reading database ... 146267 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.8+dfsg-0.1ubuntu1_amd64.deb) ...
Selecting previously unselected package glade2script.
Unpacking glade2script (from .../glade2script_3.2.2~ppa45~precise_all.deb) ...
Selecting previously unselected package boot-sav.
Unpacking boot-sav (from .../boot-sav_3.199~ppa40~precise_all.deb) ...
Selecting previously unselected package boot-repair.
Unpacking boot-repair (from .../boot-repair_3.199~ppa40~precise_all.deb) ...
Selecting previously unselected package boot-sav-extra.
Unpacking boot-sav-extra (from .../boot-sav-extra_3.199~ppa40~precise_all.deb) ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ 


```

Any help would be much appreciated.

---

### Post by grahammechanical on 2013-12-25
Hi,

Lets us not get sidetracked with issues installing Bootrepair on a live session. Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I do not say that this is the problem. I am not experienced in installing Ubuntu on windows 8 machines. But look at this

> [h=2]Creating an EFI partition[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]If you are manually partitioning your disk in the Ubuntu installer, you need to make sure you have an EFI partition set up.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]If your disk already contains an EFI partition (eg if your computer had Windows8 preinstalled), it can be used for Ubuntu too. Do not format it. It is strongly recommended to have only 1 EFI partition per disk.[FONT=inherit][/FONT][FONT=inherit][/FONT]
[*=left][FONT=inherit]An EFI partition can be created via a recent version of [GParted]("https://help.ubuntu.com/community/GParted") (the Gparted version included in the 12.04 disk is OK), and must have the following attributes:[FONT=inherit][/FONT][/FONT]

[LIST]
[*=left][FONT=inherit][FONT=inherit]Mount point:[/FONT] /boot/efi (remark: no need to set this mount point when using the manual partitioning, the Ubuntu installer will detect it automatically)[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit][FONT=inherit]Size:[/FONT] minimum 100Mib. 200MiB recommended.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit][FONT=inherit]Type:[/FONT] FAT32[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit][FONT=inherit]Other:[/FONT] needs a "boot" flag.[/FONT]
[/LIST]
[/LIST]


Regards.

---

### Post by roma24ster on 2013-12-25
Hi there,
Thanks for your reply, it does indeed have an EFI partition, see the screenshot below:
[http://i.imgur.com/Bs7R7zb.png](http://i.imgur.com/Bs7R7zb.png)

Do I set the I set the EFI partition to be /boot?

---

### Post by oldfred on 2013-12-26
The efi partition is not a /boot partition. Most desktops do not need a /boot. (Servers, LVM, RAID may need it.)

But the efi is more like the MBR. But MBR could only hold one boot system, where an efi has a folder for every system you install and from UEFI menu you can choose which system to boot. You just install grub to drive like with BIOS systems and it installs to efi partition.  This assumes you correctly installed in UEFI mode not installed in BIOS mode. And how you boot installer is how it installs.

The type of error you had is usually from opening Software Center or any other application like synaptic that sets a lock file on update process. Then update  from command line cannot run as it sees lock. Make sure all other update process are closed/finished.

---

### Post by roma24ster on 2013-12-26
I'm quite sure that all other update processes are finished. I tried again and clicked 'install ubuntu' instead of 'try ubuntu' so there was no chance of me starting another update process. The bios is in UEFI mode.Ia there anything else I can try? I would really like to install ubuntu.

---

### Post by oldfred on 2013-12-26
Are you trying to install or have you installed and having boot issues?
Be very careful on a reinstall. Many users have totally overwritten Windows on a reinstall and auto install options. You should only use something else once you have Linux partitions on the drive.

---

### Post by roma24ster on 2013-12-26
Well it seems ubuntu installed, or at least nearly finished installing, but grub didn't and therefore I cant boot into ubuntu. Every time i've been tried to install ubuntu I've set it up manually (ie specifiying the '/', '/home' and 'swap' partitions)

---

### Post by roma24ster on 2013-12-26
Good news, some how it worked fine with Ubuntu 13.10 (instead of 12.04.3). I had to set the boot device to be 'ubuntu' as the number 1 priority in the BIOS as well. Thanks

---

### Post by feng.yunyi on 2014-01-05
> **roma24ster said:**
> Good news, some how it worked fine with Ubuntu 13.10 (instead of 12.04.3). I had to set the boot device to be 'ubuntu' as the number 1 priority in the BIOS as well. Thanks

Hi I have an exactly same problem! How did you fix it? Could you please explain a little bit detail? I am a novice but I really need to go over this problem. The second time when I tried, the "half-installed" ubuntu was detected, so I have three choices: alongside ubuntu; erase ubuntu and something else. Did you choose something else and delete the partitions you set last time to release free space? Or you choose erase ubuntu?

Thanks a lot!

---

### Post by oldfred on 2014-01-05
You can reuse existing partitions with Something Else. Just choose same / as existing root. and if you have /home choose that also. If an older /home DO NOT tick the reformat box as then it would be erased. If swap exists it will auto find it.

If you have other installs like Windows, the auto install over Ubuntu may erase entire drive, so best to use Something Else. But you do have everything well backed up?

---

### Post by feng.yunyi on 2014-01-05
> **oldfred said:**
> You can reuse existing partitions with Something Else. Just choose same / as existing root. and if you have /home choose that also. If an older /home DO NOT tick the reformat box as then it would be erased. If swap exists it will auto find it.

If you have other installs like Windows, the auto install over Ubuntu may erase entire drive, so best to use Something Else. But you do have everything well backed up?


I see. Then I will choose something else coz I want to keep windows. But I don't really understand "reuse" that you mentioned. I chose my G:(/dev/sdb10) and click "delet" to make free space that I created 4 partition(/boot;/;/home and swap). So what I need to do is delete all these and make those partitions again and tick format box? Or just leave all those 4 old partitions there and click continue directly. The /home is shown having been used. / and /boot is unknown, swap is not used.

What does that sentence means: "I had to set the boot device to be 'ubuntu' as the number 1 priority in the BIOS as well."

I am sorry if my questions are stupid. Thanks!

---

### Post by oldfred on 2014-01-05
That is with UEFI. Grub does not make the ubuntu entry in UEFI first.
With BIOS whichever boot loader is in MBR is the default.

You can just reuse existing partitions. But you have to specify which is which or what mount point each partition is and its format. I do not think most desktops need the separate /boot partition, but often suggest a separate /home or data partition.
If you delete them, then you have to recreate them as well as tell mount point & format.

---

### Post by feng.yunyi on 2014-01-06
> **oldfred said:**
> That is with UEFI. Grub does not make the ubuntu entry in UEFI first.
With BIOS whichever boot loader is in MBR is the default.

You can just reuse existing partitions. But you have to specify which is which or what mount point each partition is and its format. I do not think most desktops need the separate /boot partition, but often suggest a separate /home or data partition.
If you delete them, then you have to recreate them as well as tell mount point & format.

Thank you so much. Finally I successfully installed 13.10! I strongly recommend using new version on new laptop rather than those version with more support.

---

