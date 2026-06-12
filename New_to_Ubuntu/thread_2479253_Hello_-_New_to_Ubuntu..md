---
title: "Hello - New to Ubuntu."
date: 2022-09-19
forum: New to Ubuntu
---

### Post by mag3lxub on 2022-09-19
Afternoon all!  I am new to the Ubuntu Forums, but I've had extensive experience with building my own desktops, servers, etc. I run a small LAN at home with one Windows Server 2003 tower as a "primary domain controller."  I use it for Active Directory, DCHP an DNS servers.  I also have my other Windows client stations.  In addition, I currently run  a set of NAS devices (all RAID1 and housed in Western Digital "My Cloud EX2 Ultra" housings. my primary desktop is Windows7 64 bit "Ultimate" with Bitlocker Encryption enabled as well as a TPM installed on the motherboard.  

Obviously, both the server an my primary desktop are well beyond EOL, so it's time to build new ones.  Thus, I have made the decision to go with Ubuntu desktop and server, respectively (22.04.1 LTS).  I've done as much of the YouTube Homework that I can. I have my Flash drives created with both .iso's.  I just have to build/assemble the new hardware, before I start installing Ubuntu.

I have made peace with the decision to let the install process find the drivers needed for my hardware (ASUS Motherbaord with Intel corei9 processor, etc. etc. etc and an NVidia GTX 1050 graphics card). Assuming that all works, then it would be time to start configuring.  I have some specific questions and I hope someone out here has some experience with this.  Questions as follows:

1) File Hierarchy System (FHS) - I understand that I can partition different portions of the FHS onto different volumes/partitions (eg. have /home on a separate volume/partition) and that I can install certain apps on that /home volume. However, most apps would install on /usr/bin on the main partition.  For almost all my Windows machines, I built them with 2 physical hard drives. One was partitiond in to a 75%/25% split as C:\ and D:\ respectively, and the other was one whole partition as E:\ for files and data.  C:\ would be for all Windows OS, files and info, and D:\ would be for any apps I would install where I was allowed to choose the install directory (many times I was not as the install process forced the install onto C:\:mad: ).  Can I do something similar with Ubuntu's FHS? Or is everything pretty much restricted to be under the root directory on that partition?

2) Network Storage - As stated, my Windows LAN supports  several NAS houses which are accessible via IP addresses.  I've inquired with Western Digital (the maker of the units) who advise that they have not tested them in any Linux/Ubuntu environment. They have tested them only on Windows and MAC Os environments. The NAS units are the [Western Digital My Cloud EX2 Ultra]("https://www.westerndigital.com/products/network-attached-storage/wd-my-cloud-expert-series-ex2-ultra#WDBVBZ0000NCH-NESN") variety. Has anyone had any experience getting Ubuntu to recognize these units? Hopefully, they'll be accessible via TCP/IP.  

3) Migration to Ubuntu Server (from Windows Server 2003) - What's your best recommendation for DHCP and DNS servers? I will try to use SAMBA4 for Active Directory, but I need to do all three on the server itself. Any issues with that?
I may also want to add a print server and email server as well, but we'll see. 

Anyway, thanks to all, and I look forward to a good collaboration!


Regards,
Arnold.
mag3lxub

---

### Post by grahammechanical on 2022-09-19
Welcome to Ubuntu and Ubuntu forums

> I have made peace with the decision to let the install process find the drivers needed for my hardware

Ubuntu is a Linux distribution and things are done differently in Linux than in Microsoft's Windows operating system. The developers of the Linux kernel also provide Linux firmware (hardware drivers). This firmware software package is a few hundred megabytes in size. Its size gets bigger as the developers work to produce Linux drivers for the latest hardware. The Ubuntu installer will give you a Try Ubuntu option where you can test Ubuntu to see if all the drivers are there. If we change hardware such a video adapter we usually find that Ubuntu will continue working.

When we choose the Install Ubuntu option we can select Erase disc and install Ubuntu or Something else. The Erase disc and Install Ubuntu option will create two partitions. A small partition to put the boot loader files in. And a large partition to put Ubuntu in.

The Something Else option will allow us to create all the partitions ourselves. An EFI System Partition (ESP) for boot loader files. A Root partition ( / ) for the operating system. A /home partition for the user data and files.

After installation some of us create a large partition for user data and then edit a system file (fstab) so that the data partition is mounted (made accessible) when the system boots. We do this because we may need to reinstall the OS and then we do not loose our data. Otherwise we use the File Manager to open that partition and that makes the partition accessible until we shutdown and reboot.

When we install applications all application files are placed in various folders in the root ( / ) folder. Which may be on a partition if we have chosen to do things that way. User configuration files for that application will be placed in folders in the user's home folder. Which may be on a /Home partition if we have chosen to do things that way. This is different to how things are done in Windows.

Linux/Ubuntu can be a single user OS or a multi-user OS. Each user will have his/hers own /home folder with their own configuration files.

Regards

---

### Post by Holger_Gehrke on 2022-09-19
Regarding question 1: in theory yes, in practice no. Programs on Ubuntu are installed from packages which either get pulled apart and installed in fixed directories (.deb packages) or put as is in fixed places and then mounted as file system images (snap and flatpack). Since a lot of the directories contain stuff that is needed to bring the system up (specifically systemd - once that is running it can mount the rest of the file systems - but systemd is itself made up of many parts which are all over /usr, /var/ and /etc), it's quite difficult to split the various directories to different file systems, since those would have to be mounted very early in the boot process. The only program packages you can put wherever you want are AppImages.

Regarding question 2: If you look in the manual for your NAS on pages 84 ff, you'll see it uses SMB or CIFS for Windows. Since in another place there's instruction for connecting to the NAS from Windows XP, I'd say it uses some older variant of those protocols, shouldn't be a problem to use that on Ubuntu. It also offers NFS, which might be a better protocol as far as Linux is concerned. There also seems to be an SSH server on that NAS, but I can't tell whether that allows SFTP and/or scp access to your shares ...

Question 3 is a bit outside of my expertise, but I'm sure there are server packages in the repositories for all of that ... A quick 'apt search dhcp' gives dnsmasq (small; DNS-Proxy, DHCP and TFTP all in one) and isc-dhcp-server (enterprise class) as options, there are a lot of others ...

Holger

---

### Post by oldfred on 2022-09-19
Warning - steep learning curve ahead.

Another user asked about where apps are installed. good answer here.
[https://ubuntuforums.org/showthread.php?t=2479254](https://ubuntuforums.org/showthread.php?t=2479254)

New system will also be UEFI (even if it says BIOS somewhere) as Microsoft has required vendors to install in UEFI boot mode from gpt partitioned drives since 2012 and release of Windows 8. So all newer hardware is UEFI and you should use gpt even though Ubuntu will let you use the very old MBR partitioning. I think it allows MBR, just so you do not erase other partitions, if a very old drive that is MBR already.

If using nVidia, you need proprietary driver. Ubuntu now has made that very easy, if you make the correct selections during install. 
You need to boot in safe boot mode & choose to install proprietary drivers. 
Ubuntu has permission from nVidia to offer the latest drivers.

Many that use servers, suggest LVM which is Logical volumes over standard partitions. The volumes are in one very large partition. 
I do not know LVM, so can only offer a few links. Search for other posts by TheFu.
[https://ubuntuforums.org/showthread.php?t=2433281](https://ubuntuforums.org/showthread.php?t=2433281)

For general UEFI info see link in my signature, but more for desktops than servers. 
If terms not understood scroll to bottom and see Acronyms with short description & link to more info.

---

### Post by mag3lxub on 2022-09-19
Thanks all!  This is a very good start to my journey.  It's not that critical that I can't separate installs of System files/data etc. vs. Apps. I was only trying to minimize the time it takes to backup the volumes.  But the fact that I can have the /home system on a separate drive/partition is very good.  

I'm sure I'll be back with other questions.  For now, I'll be busy building the hardware and getting the initial software installed.  

Thanks again!  Any other comments greatly appreciated! ;)

---

### Post by oldfred on 2022-09-19
I typically suggest new users use default install.
But that goes way back and is just / (root) and now ESP. With drives much larger and some not installing for dual boot, you can end up with a too large / (root) partition. I used to suggest 25 GB, but now Ubuntu is using snaps and they take a lot of room. May be best to start with 40 or 50GB if you are allowing snaps.

I immediately uninstall all snaps.
I do not use LVM, but have some idea of sizes I need & after a few years get a new drive & can redo sizes then.
I do not use separate /home, but do have all data in separate /mnt/data. Many suggest not using /mnt, but just mount in / or /home. I then link data back into /home. Shows partitions & sizes. I use Kubuntu which is a bit smaller but still has many features. And now all partitions seem to get mounted to /media where before I had to click on them before they were mounted.

```
[FONT=monospace]
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblkt [/COLOR]
MODEL                      NAME        FSTYPE   SIZE FSUSED LABEL     PARTLABEL            MOUNTPOINT            UUID 
Samsung SSD 840 PRO Series sda                119.2G                                                              
                           &#9500;&#9472;sda1      vfat   499.7M                  efi                                        F626-A4D4 
                           &#9500;&#9472;sda2                 2M                                                              
                           &#9500;&#9472;sda3      ext4      86G  21.8G data_sata data_sata            /media/fred/data_sata d40287b2-a529-483c-aa25-99841429f78e 
                           &#9492;&#9472;sda7      ext4    30.9G   9.2G jammy_a   jammy_a              /media/fred/jammy_a   111c16c5-1cc0-4648-b406-5cd7b38a20ba 
SSD 850 EVO                sdb                232.9G                                                              
                           &#9500;&#9472;sdb1      vfat     510M        M2_ESP    EFI System Partition                       D966-440A 
                           &#9500;&#9472;sdb2      vfat     5.9G   3.5G           FAT                  /media/fred/4738-7B8C 4738-7B8C 
                           &#9500;&#9472;sdb3      ext4    35.2G   9.3G jammy-ssd                      /media/fred/jammy-ssd c710e825-ff33-4df7-9749-61c926e85398 
                           &#9492;&#9472;sdb5      ext4   127.4G 108.9G m2_data   m2_data              /media/fred/m2_data   0c374965-53c6-437c-a2ad-f0508486f9d5 
Samsung SSD 980 PRO 1TB    nvme0n1            931.5G                                                              
                           &#9500;&#9472;nvme0n1p1 vfat     550M  37.2M ESP_NVME  EFI System Partition /boot/efi             138A-44FF 
                           &#9500;&#9472;nvme0n1p2 swap     4.1G                                       [SWAP]                393cd3f4-c4d8-42df-bae3-4690f542ee0b 
                           &#9500;&#9472;nvme0n1p3 ext4      40G  14.3G jammy     jammy                /                     3c01cc90-636c-4a7e-aa12-fe610d95d5f3 
                           &#9500;&#9472;nvme0n1p4 ext4      40G    24K future    future               /media/fred/future    a76d4960-69de-42ab-a8e9-88dc93d07c3e 
                           &#9500;&#9472;nvme0n1p5 ext4   205.1G  37.6G data_nvme data_nvme            /mnt/data             012965c6-d942-4efb-8e1d-5dcc54911f3a 
                           &#9492;&#9472;nvme0n1p6 ext4   205.1G  79.5G photos    photos               /mnt/photos           cf40f922-78bb-4f82-93be-9c3720132a0d


[/FONT]
[/FONT]
```

---

### Post by mag3lxub on 2022-09-20
> **oldfred said:**
> I typically suggest new users use default install.
But that goes way back and is just / (root) and now ESP. With drives much larger and some not installing for dual boot, you can end up with a too large / (root) partition. I used to suggest 25 GB, but now Ubuntu is using snaps and they take a lot of room. May be best to start with 40 or 50GB if you are allowing snaps.

I immediately uninstall all snaps.
I do not use LVM, but have some idea of sizes I need & after a few years get a new drive & can redo sizes then.
I do not use separate /home, but do have all data in separate /mnt/data. Many suggest not using /mnt, but just mount in / or /home. I then link data back into /home. Shows partitions & sizes. I use Kubuntu which is a bit smaller but still has many features. And now all partitions seem to get mounted to /media where before I had to click on them before they were mounted.

```
[FONT=monospace]
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblkt [/COLOR]
MODEL                      NAME        FSTYPE   SIZE FSUSED LABEL     PARTLABEL            MOUNTPOINT            UUID 
Samsung SSD 840 PRO Series sda                119.2G                                                              
                           &#9500;&#9472;sda1      vfat   499.7M                  efi                                        F626-A4D4 
                           &#9500;&#9472;sda2                 2M                                                              
                           &#9500;&#9472;sda3      ext4      86G  21.8G data_sata data_sata            /media/fred/data_sata d40287b2-a529-483c-aa25-99841429f78e 
                           &#9492;&#9472;sda7      ext4    30.9G   9.2G jammy_a   jammy_a              /media/fred/jammy_a   111c16c5-1cc0-4648-b406-5cd7b38a20ba 
SSD 850 EVO                sdb                232.9G                                                              
                           &#9500;&#9472;sdb1      vfat     510M        M2_ESP    EFI System Partition                       D966-440A 
                           &#9500;&#9472;sdb2      vfat     5.9G   3.5G           FAT                  /media/fred/4738-7B8C 4738-7B8C 
                           &#9500;&#9472;sdb3      ext4    35.2G   9.3G jammy-ssd                      /media/fred/jammy-ssd c710e825-ff33-4df7-9749-61c926e85398 
                           &#9492;&#9472;sdb5      ext4   127.4G 108.9G m2_data   m2_data              /media/fred/m2_data   0c374965-53c6-437c-a2ad-f0508486f9d5 
Samsung SSD 980 PRO 1TB    nvme0n1            931.5G                                                              
                           &#9500;&#9472;nvme0n1p1 vfat     550M  37.2M ESP_NVME  EFI System Partition /boot/efi             138A-44FF 
                           &#9500;&#9472;nvme0n1p2 swap     4.1G                                       [SWAP]                393cd3f4-c4d8-42df-bae3-4690f542ee0b 
                           &#9500;&#9472;nvme0n1p3 ext4      40G  14.3G jammy     jammy                /                     3c01cc90-636c-4a7e-aa12-fe610d95d5f3 
                           &#9500;&#9472;nvme0n1p4 ext4      40G    24K future    future               /media/fred/future    a76d4960-69de-42ab-a8e9-88dc93d07c3e 
                           &#9500;&#9472;nvme0n1p5 ext4   205.1G  37.6G data_nvme data_nvme            /mnt/data             012965c6-d942-4efb-8e1d-5dcc54911f3a 
                           &#9492;&#9472;nvme0n1p6 ext4   205.1G  79.5G photos    photos               /mnt/photos           cf40f922-78bb-4f82-93be-9c3720132a0d


[/FONT]
[/FONT]
```


Thanks much.  My physical drives tend to be much larger than the above (4TB and 6TB internal SATAs) so I'll be partitioning accordingly.  I understand that Ubuntu 22.04 has gone past the 2TB limitation. The primary root partition will be on the 4TB drive partitioned as 3TB/1TB (3TB for / and the system).  /home will be on the 6TB volume.

I'll keep everyone posted. Thanks again!

---

### Post by oldfred on 2022-09-20
It not Ubuntu per se, but partitioning to allow larger partitions.
MBR(msdos) was designed in the early 1980's when KB was standard, MB large and GB unheard of. So they set the max at 2TB.
Of course now 2TB in not a large drive.
The came up with gpt which you can use on smaller drives, but have to use on larger drive.
With gpt you have to have an ESP - efi system partition to boot in UEFI mode. I always put an ESP on every drive, and often have another install of minimal or test install of Ubuntu with some repair utilities added, but not my full install.

I have used gpt with all new or totally reformatted drives since 2010 and back then with BIOS.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by SeijiSensei on 2022-09-20
> **oldfred said:**
> If using nVidia, you need proprietary driver. Ubuntu now has made that very easy, if you make the correct selections during install. 
You'll see a page of options during installation that includes a check box to install any required proprietary drivers you need. The driver for my NVIDIA card was installed this way.

> You need to boot in safe boot mode & choose to install proprietary drivers. 
Ubuntu has permission from nVidia to offer the latest drivers.

I've never needed to use safe mode to install the NVIDIA driver. I go to System Settings > Driver Manager and let the application detect my hardware. After the driver is added to the set of kernel modules, I need only reboot to get the correct driver.

---

### Post by mag3lxub on 2023-02-18
Hello all!  Long time, no type!   I know I've been away for a while, but I made some progress over the past couple of days.  I was building the hardware (two mid towers)  and having trouble getting the first to work. It just wouldn't POST. I couldn't understand why and I had never had this difficulty with some other builds of mine.    

As usual, it was the RAM.  Apparently, I had not pushed it in far enough to where both sides "click."   Now the box is up and running, and so is Ubuntu 22.04 server.  Just the raw install, right now.No SNAP apps or anything.  I did invoke LVM and I did encrypt it. And, Glory be, all of the hardware (including the graphics card) seem to work well with Ubuntu.  No issues. I have yet to check the Blu-Ray player but will, shortly.   

My next step is to figure out what I want on the "server"  and the order in which I should install them.  I know I want the following:

1)  /home directory mounted on my 2nd physical drive (not the one where /root is installed).   [COLOR=#0000ff]**{Completed 02/18}**[/COLOR]
2)  DCHP Server;
3)  DNS Server;
4)  Active Directory equivalent (Zentyal or the like).     [COLOR=#0000ff]**{Will use Zentyal Development Addition 7.0 for all of the above.  **[/COLOR][COLOR=#ff0000]**Update:  I guess I can't use Zentyal for Ubuntu 22.04. Only available for 20.04 I guess I'll have to wait for Zentyal 8.0 or try something different.**[/COLOR][COLOR=#0000ff]**}**[/COLOR]
5)  Maybe a desktop skin (I won't be running it "Headless").  [COLOR=#0000ff]**{Completed - Instaled LXDE}**[/COLOR]
6) Integrate Original Network attached storage devices **[COLOR=#0000ff]{Completed - They just popped up as if they were always there. I can copy back and forth to them}[/COLOR]**
7) Install other Apps **[COLOR=#0000ff]{Installed Firefox Snap, VLC Media Player Snap, - Looking to Install others as needed for the server}[/COLOR]**
8) Install drivers for my Blu-Ray Disc recorder/player and get it up and running.
9) Install Backup software for the local file systems (more than likely, rsync or Cloudberry but we'll see).

I don't necessarily need a bunch of other apps on the server, but it's nice to know they work under Ubuntu or have Ubuntu native versions.  

Will keep you posted.  

Regards,
Arnold.

---

### Post by MAFoElffen on 2023-02-19
Me, for server and infrastructure, my methodologies have changed greatly since Windows  Server 2003 through 2012R2... And how I applied doing those kinds of things in Linux. One thing was where I had to decide whether I wanted all my services on separate machines, or all on one server.

I now do a hybrid solution, where I use KVM as a Virtual machine Host system, then use VM Servers for services. With VM's I can spin up a machine, add a service, make snapshots along the way in case I need to revert something, or clone machines to add redundant services.

For DHCP, it is isc-dhcp-server ([https://help.ubuntu.com/community/isc-dhcp-server?_ga=2.55939373.781514896.1676841615-339163398.1632768351](https://help.ubuntu.com/community/isc-dhcp-server?_ga=2.55939373.781514896.1676841615-339163398.1632768351)). For DNS, it is bind9 ([https://ubuntu.com/server/docs/service-domain-name-service-dns](https://ubuntu.com/server/docs/service-domain-name-service-dns)).

As for data organization, in that respect, for shared data, I create a data folder off from root (not stored in home) and set permissions/access to groups, not to specific users. Then I set users as members of groups... It (basically) works the same as with Win Server...

Any folder from the root folder can be a mount physically located somewhere else... Remember that. You can have things in different partitions and disks, and make it appear as a single structure. Having things segregated and organized is a good thing, especially for backups and snapshots. You can do snapshots with LVM Logical Volumes, if you leave room for those snapshots. learn about LVM2 and it's capabilities, and how to use it. You can do more with BTRFS and ZFS. (Me? I used to use LVM2, now back to using ZFS...) Just remember that snaphots are not a replacement for a good backup strategy.
```

mafoelffen@Mikes-B460M:~$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              265M  1.49G       96K  /boot
bpool/BOOT                                         264M  1.49G       96K  none
bpool/BOOT/ubuntu_2cwpns                           264M  1.49G      264M  /boot
datapool                                           630G  2.90T       96K  none
datapool/DATA                                      630G  2.90T      630G  /data
rpool                                             11.3G   880G       96K  /
rpool/ROOT                                        6.71G   880G       96K  none
rpool/ROOT/ubuntu_2cwpns                          6.71G   880G     4.28G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   880G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   880G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   880G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      2.43G   880G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   880G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  2.34G   880G     2.20G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   880G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    168K   880G      168K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              97.3M   880G     97.3M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             40.0M   880G     40.0M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                  90.7M   880G     90.7M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   880G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.43M   880G     1.43M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   880G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   880G       96K  /var/www
rpool/USERDATA                                    4.61G   880G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.61G   880G     4.61G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.75M   880G     1.75M  /root

```
As a strategy and methodology, I never allocate all my storage. That way I can add more, where I need it, when I need it, in slices.

You can do shared printers and other peripherals with Samba or Cups...

Welcome to your journey...

---

### Post by mag3lxub on 2023-03-12
Here's another update.  After some gyrations in re: getting my hardware to work, properly, both my Ubuntu Boxes are built. On one I have Ubuntu Server 22.04 installed. I intend to make that my domain controller, so I will wait until Zentyal 8.0 is released (I understand in May, 2023) and use that for the domain controller software. 

I also have installed Ubuntu desktop 22.04 (Jammy Jellyish) on the other box. I am quite lucky in that several of my earlier concerns were resolved quickly.

[LIST=1]
[*]The video card works perfectly and I can use dual monitors for it.  I have a strong 1920x1080 resolution. 
[*]I can see my NAS boxes without difficulty. 
[*]I found an excellent screensaver. 
[/LIST]

So, now begins the transfer of software (or replacement of it) with Linux/Ubuntu based versions. I'll do this on the desktop while I'm waiting for Zentyal 8.0 to be released.  But, already, I face some challenges Including:

1)  No "Windows Sidebar Gadgets" equivalent.  There was a package called "Screenlets" but it is no longer available. Apparently, it was for 14.xx versions or less.  I wasn't able to follow instructions to get it installed. So now I have to look for equivalents. What do y'all do for gadgets?

2)  Bottles - I have it installed,  but now I have to sit down with some documentation and figure out how to configure it for the Windows programs I absolutely need over on Ubuntu (i.e. for which I can't find a Linux based equivalent).

3) Firefox - I guess I went with the SNAP version of it and it's not working right. I can't import my bookmarks .html file from Windows.   It just doesn't work.  I believe I recall hearing that most people dump the SNAP version and re-install it standalone.  I may have to look into that if I still can't get to import my bookmarks. It works fine, otherwise, and even my extensions installed just fine.   

So that's where we're at now.  Any thoughts  on the current list of issues would be greatly appreciated.  

Regards.

---

### Post by MAFoElffen on 2023-03-13
Windows Sidebar Gadgets-- In Linux, I've uses Conky for years, which run from conky scripts and overlays the whatever you want to display on the desktop. This used to be completely manual editing of the scripts and previously I wouldn't have recommended it to a new Linux User...

But now there is a GUI editor to add pre-written widgets on the screen, called "Conky Manager". Here is a description: [https://ubuntuhandbook.org/index.php/2020/07/install-conky-manager-ubuntu-20-04-lts/](https://ubuntuhandbook.org/index.php/2020/07/install-conky-manager-ubuntu-20-04-lts/)

---

### Post by Holger_Gehrke on 2023-03-13
'Bottles' is - as far as I can tell - just another graphical frontend for WINE. You're probably better of using one that's better known. 'playonlinux' is probably the best known of these. It is in the repositories and can be installed using the 'Software' application (or snap-store or whatever else it's called today ...). Don't be put off by the Software app saying it is proprietary. Somebody obviously missed the link to the source code on github in the documentation on the programs homepage ...

I'm also using the Firefox snap and if I open the bookmark manager (ctrl-shift-o) there's a button at the top of the window marked 'Importieren und Sichern' ('Import and Save' would be my translation). If I click on that, I get a menu which offers to import from html as its third option.

Holger

---

### Post by mag3lxub on 2023-03-19
> **MAFoElffen said:**
> Windows Sidebar Gadgets-- In Linux, I've uses Conky for years, which run from conky scripts and overlays the whatever you want to display on the desktop. This used to be completely manual editing of the scripts and previously I wouldn't have recommended it to a new Linux User...

But now there is a GUI editor to add pre-written widgets on the screen, called "Conky Manager". Here is a description: [https://ubuntuhandbook.org/index.php/2020/07/install-conky-manager-ubuntu-20-04-lts/](https://ubuntuhandbook.org/index.php/2020/07/install-conky-manager-ubuntu-20-04-lts/)

Just out of curiosity, was "Conky"  named after the Pee-Wee Herman reference (i.e. In the "Pee-Wee's Playhouse" TV show, there was animated  robot like object that had a voice. When you turned it on, it would fire up and eventually exclaim, "Conky 2000 - Ready to Assist you PeeWee")!  And it would normally do things like output to Pee-Wee the "Secret word, etc. "

[https://www.youtube.com/watch?v=_zOLV0QlcGg](https://www.youtube.com/watch?v=_zOLV0QlcGg)


:D

I'll definitely look at that ubuntuhandbook.  Thanks!

---

### Post by mag3lxub on 2023-03-19
> **Holger_Gehrke said:**
> 'Bottles' is - as far as I can tell - just another graphical frontend for WINE. You're probably better of using one that's better known. 'playonlinux' is probably the best known of these. It is in the repositories and can be installed using the 'Software' application (or snap-store or whatever else it's called today ...). Don't be put off by the Software app saying it is proprietary. Somebody obviously missed the link to the source code on github in the documentation on the programs homepage ...

I'm also using the Firefox snap and if I open the bookmark manager (ctrl-shift-o) there's a button at the top of the window marked 'Importieren und Sichern' ('Import and Save' would be my translation). If I click on that, I get a menu which offers to import from html as its third option.

Holger

I'll check it out.  I got Bottles to work for a couple of my Windows apps but there are some that have specific requirements and you can't know what they are unless you run/install the Windows .msi file via the Bottles terminal to see what errors you are getting.  In my current case (my email client), probably easier just to pick a Ubuntu based client that does all the functions my current client does.  I currently use Forte Agent 7.2 for email. One of things I like about it is that you can have multiple email accounts and filter the emails onto multiple different folders. I have yet to find an Ubuntu client that does that. I'm currently evaluating KMail.  We'll see.

I have that same Import from HTML file option as well, but when I select the import file, it doesn't work. I may consider uninstalling the Firefox snap and installing it natively from the Mozilla Website and see if that works.

---

### Post by MAFoElffen on 2023-03-20
[quote=mag3lxub]One of things I like about it is that you can have multiple email accounts and filter the emails onto multiple different folders. I have yet to find an Ubuntu client that does that. I'm currently evaluating KMail. We'll see.[/quote]
I use "Evolution" email client, mostly because I use encrypted mail, and it does that out of the box. I have multiple accounts and can set up custom folders and filters... Has calendaring, etc.

It has been my go-to email client for years. It is maintained by Gnome now, but originally can from Novell.

---

### Post by mag3lxub on 2023-03-20
> **MAFoElffen said:**
> I use "Evolution" email client, mostly because I use encrypted mail, and it does that out of the box. I have multiple accounts and can set up custom folders and filters... Has calendaring, etc.

It has been my go-to email client for years. It is maintained by Gnome now, but originally can from Novell.

Well, believe it or not, I have my Forte Agent installed! And it works!   What I used was a WINE like software called "Crossover Linux"  by CodeWeavers.   Once I switched the bottle it created to WIN7-32, it worked great!  Of course, now I have to pay $74.00 for the licensed version of it, but....

Next thing I have to do is get my data folders copied over from my original Agent install on my Windows box to the Ubuntu box and get this new version to recognize it.   We shall see.    

If this works, I'll see if I can get Windows Sidebar gadgets to work.  Probably not, but....

---

### Post by mag3lxub on 2023-04-15
Aother Update.  Both my Ubuntu client and server box remain stable.  I await the release of Zentyal 8.0 (hopefully in another month) so I can apply it to my Ubuntu Server box.It's now a matter of finding equivalent Ubuntu apps that match or come close to my main Windows apps.  I'm thinking it not all that productive to attempt to install Windows apps with WINE or Bottles because, even if they do install, there are often problems getting them to work. And, since there isn't a lot of good documentation on WINE (and thus Bottles), I may as well devote those efforts towards finding native Ubuntu Apps.  

Two things are generally outstanding at this point.  I'm noticing that in the native Ununtu 22.04 (Jammy Jellyfish) that there is some latency when it comes to mouse movement and pointing/clicking. If I  scroll towards a window and/or the buttons I can click (close / X button or back button) sometimes it doesn't respond. I have to re-scroll back onto the button in the hope that it accepts the click. I have similar issues with scroll bars in windows. Hard to click and drag.  Am I doing something wrong?  I'm running 22.04 on a WINTEL machine (Core i7 with 32 gigs of RAM).  I don't think it's CPU speed or power.  I dunno... maybe I'm trying to move/click/drag too fast.  Just not sure.

Second, Is there an app which re-organizes the list of applications that pops up (i.e. when you press the apps button on the lower left)?  I see, for example,. there is one group of "utility" icons.  How do I create more groups and put individual icons in those groups?

---

### Post by TheFu on 2023-04-15
> **mag3lxub said:**
>  I may as well devote those efforts towards finding native Ubuntu Apps.  

Very true. On your machine, you can always load up a Windows virtual machine to run office/productivity applications. I do that for financial and tax software.  For everything else, I've finally found native Linux applications that meet my needs. I had to be a little flexible and for a few applications, never found a 1-for-1 exact replacement.  Of course, if you've been using F/LOSS programs on Windows, then almost all of them will have a native Linux port and the switch over is trivial even for great grandmas who do millions of things better than they handle computers (usually).

> **mag3lxub said:**
>  Two things are generally outstanding at this point.  I'm noticing that in the native Ununtu 22.04 (Jammy Jellyfish) that there is some latency when it comes to mouse movement and pointing/clicking. If I  scroll towards a window and/or the buttons I can click (close / X button or back button) sometimes it doesn't respond. I have to re-scroll back onto the button in the hope that it accepts the click. I have similar issues with scroll bars in windows. Hard to click and drag.  Am I doing something wrong?  I'm running 22.04 on a WINTEL machine (Core i7 with 32 gigs of RAM).  I don't think it's CPU speed or power.  I dunno... maybe I'm trying to move/click/drag too fast.  Just not sure.
I'm inclined to think it is a hardware problem.  Try a different mouse.  They don't last forever.  Also, avoid wireless. Stick with wired, PS2, mice.  I have a few issues with new USB keyboards and mice on my systems.  The vendors all got too fancy.  But good, standard, ps2 port, keyboards and mice work flawlessly.

> **mag3lxub said:**
> Second, Is there an app which re-organizes the list of applications that pops up (i.e. when you press the apps button on the lower left)?  I see, for example,. there is one group of "utility" icons.  How do I create more groups and put individual icons in those groups?
GUI question?  Ewwww.  IDK.  There are lots and lots of different GUIs. Some are more customizable than others.  I'm running nearly the same GUI I used in 1995 on a UNIX workstation today.  It hasn't needed any major updates since 2005-ish, so each release when {insert crazy desktop distro team name} does something with the GUI that I don't care for, I really don't care.  I'll see it for 10 minutes, before swapping in my WM with my customizations that are over 25 yrs old now, and I can get back to being productive.

Anyway, when asking for GUI help, it is best to put all the system information right there. For example:
```
$ inxi -bz
System:    Kernel: **5.15.0-69-generic** x86_64 bits: 64 Desktop: **FVWM 2.6.7** Distro: **Ubuntu 20.04.6 LTS** (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 5003 date: 02/03/2023 
CPU:       6-Core: AMD Ryzen 5 5600G with Radeon Graphics type: MT MCP speed: 4244 MHz min/max: 1400/4200 MHz 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] driver: **amdgpu** v: kernel 
           Display: **server: X.Org 1.20.8 driver: amdgpu** **resolution: 1920x1200~77Hz** 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 

```
that little command provides all the needed info so people can help. inxi is very handy and does much more.

---

### Post by mag3lxub on 2023-04-22
> **TheFu said:**
> Very true. On your machine, you can always load up a Windows virtual machine to run office/productivity applications. I do that for financial and tax software.  For everything else, I've finally found native Linux applications that meet my needs. I had to be a little flexible and for a few applications, never found a 1-for-1 exact replacement.  Of course, if you've been using F/LOSS programs on Windows, then almost all of them will have a native Linux port and the switch over is trivial even for great grandmas who do millions of things better than they handle computers (usually).

I may have to do that for some things, but I really want to try and get WINE/Bottles to work.  I wish there was a good Text/Reference book on it. Know of any?


> **TheFu said:**
> I'm inclined to think it is a hardware problem.  Try a different mouse.  They don't last forever.  Also, avoid wireless. Stick with wired, PS2, mice.  I have a few issues with new USB keyboards and mice on my systems.  The vendors all got too fancy.  But good, standard, ps2 port, keyboards and mice work flawlessly.

It's a brand new wired USB mouse.     I'll try a PS2, though.   I have a port for it on the motherboard.  I didn't think a USB mouse would be an issue as I use them on all my Windows Laptops and desktop.    


> **TheFu said:**
> GUI question?  Ewwww.  IDK.  There are lots and lots of different GUIs. Some are more customizable than others.  I'm running nearly the same GUI I used in 1995 on a UNIX workstation today.  It hasn't needed any major updates since 2005-ish, so each release when {insert crazy desktop distro team name} does something with the GUI that I don't care for, I really don't care.  I'll see it for 10 minutes, before swapping in my WM with my customizations that are over 25 yrs old now, and I can get back to being productive.

Anyway, when asking for GUI help, it is best to put all the system information right there. For example:
```
$ inxi -bz
System:    Kernel: **5.15.0-69-generic** x86_64 bits: 64 Desktop: **FVWM 2.6.7** Distro: **Ubuntu 20.04.6 LTS** (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 5003 date: 02/03/2023 
CPU:       6-Core: AMD Ryzen 5 5600G with Radeon Graphics type: MT MCP speed: 4244 MHz min/max: 1400/4200 MHz 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] driver: **amdgpu** v: kernel 
           Display: **server: X.Org 1.20.8 driver: amdgpu** **resolution: 1920x1200~77Hz** 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 

```
that little command provides all the needed info so people can help. inxi is very handy and does much more.

```
My inxi -bz

[B][COLOR=#0000cd]System:
  Kernel: 5.19.0-40-generic x86_64 bits: 64 Desktop: GNOME 42.5
    Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: ASUS product: N/A v: N/A serial: <superuser required>
  Mobo: ASUSTeK model: PRIME Z590-P v: Rev 1.xx
    serial: <superuser required> UEFI: American Megatrends v: 0811
    date: 04/06/2021
CPU:
  Info: 8-core Intel Core i7-10700K [MT MCP] speed (MHz): avg: 3050
    min/max: 800/5100
Graphics:
  Device-1: NVIDIA GP107 [GeForce GTX 1050 Ti] driver: nvidia v: 525.105.17
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia resolution:
    1: 1920x1080~60Hz 2: 1920x1080~60Hz
  OpenGL: renderer: NVIDIA GeForce GTX 1050 Ti/PCIe/SSE2
    v: 4.6.0 NVIDIA 525.105.17
Network:
  Device-1: Realtek RTL8125 2.5GbE driver: r8169
Drives:
  Local Storage: total: 10.92 TiB used: 40.63 GiB (0.4%)
Info:
  Processes: 331 Uptime: 6m Memory: 31.2 GiB used: 2.73 GiB (8.8%)
  Shell: Bash inxi: 3.3.13
[/COLOR][/B]
```

---

### Post by TheFu on 2023-04-22
> **mag3lxub said:**
> I may have to do that for some things, but I really want to try and get WINE/Bottles to work.  I wish there was a good Text/Reference book on it. Know of any?
The manpages?  Any book or website that isn't the project team's or specific to an ubuntu release are out of date or just wrong. Manpages have the information for the exact version of the programs you have installed on your system. That should always be the first place you look for information.
There's also the WineHQ website. They have an appdb where people that get a specific version of a program can report the steps they took to make it happen.  I posted my steps for a few programs about 10-12 yrs ago.  Then the programs were modified with new releases that included some types of Windows 3rd party tools that were never going to be supported by WINE. After trying to get the most important Windows-only software working again, that had been working for 3 yrs under WINE (mostly), I gave up, created a Windows VM and installed the software inside it.  Not only did it work, but the 20% of non-working parts in WINE worked perfect under the VM.  That VM has migrated across 3 physical machines, no reinstall done.  I can't say that for anything setup with WINE that I've ever gotten working.

> **mag3lxub said:**
> It's a brand new wired USB mouse.     I'll try a PS2, though.   I have a port for it on the motherboard.  I didn't think a USB mouse would be an issue as I use them on all my Windows Laptops and desktop.    
I have Logitech keyboard and mouse that I had to return because they didn't work. I contacted support and Logitech (aka Logi) said they don't test nor support Linux.  If you stay on Linux, you'll get used to hearing that and learn to be suspicious if nobody is using a device on Linux.  Even if the box for the hardware says "SUPPORTS LINUX" in huge letters, that doesn't mean they support the kernel you have.  I've been burned a few times by that.  Assuming it won't work, until you hunt down proof that it is supported AND supported in the kernel-shipped drivers.  Buying hardware that requires extra drivers will always be a problem. I did it for a decade, then finally decided to stop that and just get the most standard hardware that was well supported by the built-in, shipped, Linux kernels.  Sure, I spend $20 more for a quality motherboard to get better NICs (or avoid crappy hardware), but when the install "just works", that $20 pays for itself every time there's a new install.  

> **mag3lxub said:**
> My inxi -bz

```
System:
  Kernel: 5.19.0-40-generic x86_64 bits: 64 Desktop: GNOME 42.5
    Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: ASUS product: N/A v: N/A serial: <superuser required>
  Mobo: ASUSTeK model: PRIME Z590-P v: Rev 1.xx
    serial: <superuser required> UEFI: American Megatrends v: 0811
    date: 04/06/2021
CPU:
  Info: 8-core Intel Core i7-10700K [MT MCP] speed (MHz): avg: 3050
    min/max: 800/5100
Graphics:
  Device-1: NVIDIA GP107 [GeForce GTX 1050 Ti] driver: nvidia v: 525.105.17
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia resolution:
    1: 1920x1080~60Hz 2: 1920x1080~60Hz
  OpenGL: renderer: NVIDIA GeForce GTX 1050 Ti/PCIe/SSE2
    v: 4.6.0 NVIDIA 525.105.17
Network:
  Device-1: Realtek RTL8125 2.5GbE driver: r8169
Drives:
  Local Storage: total: 10.92 TiB used: 40.63 GiB (0.4%)
Info:
  Processes: 331 Uptime: 6m Memory: 31.2 GiB used: 2.73 GiB (8.8%)
  Shell: Bash inxi: 3.3.13

```

I fixed the post - if you post anything to these forums that is terminal output, which needs to be default (avoid images), then please, please, please, use forum code-tags.  There are lots of commands that look great in a terminal but the forum software messes them up.  Also, don't change from the default font or use huge blocks of color.  A few words that are bold or colors are fine, provided they ARE important to highlight.  Remember that people reading these posts are using different devices, different browsers, different fonts, different screen resolutions than you. The defaults mean they've already setup everything for easy viewing, if that was necessary.

That's a respectable system and you can run anything you like on it.  I'd definitely put Windows into a virtual machine and forget about WINE completely, but I suppose everyone needs to learn that for themselves.  Only the most popular software will maintain WINE support for multiple years.  It doesn't take much for a Windows programmer/company to break a program so that it can never run under WINE.  For all the time you waste on WINE, you could have been productive running a small Windows VM for months.

Uptime 6 minutes?  That seems really short. Here's the uptime for 3 physical systems here:
```
$ uptime
 21:54:12 up 7 days, 12:46,  5 users,
$ uptime
 21:54:41 up 7 days, 12:41,  1 user,
$ uptime
 21:54:33 up 5 days, 15:38,  3 users,
```

So, a week ago, I rebooted all my systems - must have gotten a new kernel during patching.  The one that made it only 5 days was due to some USB storage used for backups that got disconnected improperly. Everything I tried to get it working without a reboot failed - and I tried.  USB storage connections are susceptible to vibrations which make them lose and eventually fail. I certainly didn't unplug the devices, but they were reporting as disconnected, starting around 4am that day. Nobody was awake then, so it was a vibration-caused issue or USB controller inside the devices.  Another USB storage device didn't disconnect.

---

### Post by stevermann on 2023-04-28
> **oldfred said:**
> 
I immediately uninstall all snaps.


Why, and how?

---

### Post by TheFu on 2023-04-28
> **stevermann said:**
> Why, and how?

There are lots of threads here discussing snaps for why or why not.  Do some reading.
Most of those threads will explain how to remove all snaps and the snap subsystem as well.  

There are compromises with and without snaps.  There is good and bad on each side.

---

### Post by BBQdave on 2023-04-28
> **stevermann said:**
> Why, and how?

As stated by TheFu much discussion about the pros and cons of snaps and the snap-store.

I'm trying it out and would offer that it's a nice experience. Snaps: Firefox, LibreOffice suite, Darktable, GIMP. The snaps applications are up to date, and in the case of Darktable, a huge difference between the snap Darktable and older Darktable version in .deb repos.

My computer has a SSD of 64GB, small storage compared to current standards. Along with snaps applications, I also installed Google Chrome and use it's suite of applications. With all of the applications, and system, and personal data - I am using 18GB of my SSD.

I like Ubuntu 22.04LTS. I like the up to date snaps applications. I appreciate the function and pleasant flow of Ubuntu, and consider 18GB reasonable usage of my SSD :)

---

### Post by oldfred on 2023-04-28
Some of the threads discussing snaps.
I see some cases like new system where you want old version or older install where you may not the very latest version where snap may make sense.
But for me updating every two years to latest LTS and its versions is all I need. Some like Firefox are updated regularly whether the snap or if you use the ppa, and pps also updates Thunderbird.

remove old snaps script
[https://ubuntuforums.org/showthread.php?t=2470573&p=14073812#post14073812](https://ubuntuforums.org/showthread.php?t=2470573&p=14073812#post14073812)
[https://askubuntu.com/questions/1386455/can-i-remove-the-older-revision-package-of-duplicated-snap-packages](https://askubuntu.com/questions/1386455/can-i-remove-the-older-revision-package-of-duplicated-snap-packages)

boot time cut in half by removing snap, they since have improved boot somewhat
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

You also have to reset priorities as shown or it will reinstall the Firefox snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by mag3lxub on 2023-07-09
Time for an update.

See my other thread on "[Staying with 22.04 or reverting to 20.04]("https://ubuntuforums.org/showthread.php?t=2484219")"   I've decided to revert to Ubuntu Server 20.04, but it hasn't been easy.

Otherwise, things are moving along. I am getting closer to being able to retire my Windows 7 desktop.  just a few more apps to replace. And good that I'm getting close, as I was advised by Mozilla that Firefox for Windows 7  is no longer being updated with features but only security updates.  They want me to update to Windows 10-11.  Not gonna happen! 

I've pretty much deferred any use of Bottles or WINE and will prioritize searching for equivalent apps in Linux.  I will also keep my old Win7 desktop alive, but it won't be my "production" machine.  

I'll keep you posted.

---

