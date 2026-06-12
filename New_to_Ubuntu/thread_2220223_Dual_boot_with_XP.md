---
title: "Dual boot with XP"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by neoverse2 on 2014-04-27
Hi,
This will be my first time installing Ubuntu, I have WinXP currently installed. Not so long ago I installed a new HDD and I made several partitions, the 1st is C: for windoz, the 2nd is 15gb, and I specifically made it that size because I wanted to install Ubuntu there but never got around to it. Not I am ready to try it but I've hit a couple of snags.

I used UUI and put Ubuntu on a flash drive. The 1st attempt was with the 64bit ver, the DL site said anything over 2gb it was recommended. It hung on what looked like an initialization screen in a section that was titled "Trace Call:". Now I am trying the 32bit version and I'd like to know a few things before I continue with the installation.

1. Which format is best? Ext4? The 2nd partition is currently NTFS
2. What are "mount points"?
3. If I select the 2nd partition to install Ubuntu, what mount point should I use?

thanks

---

### Post by El Tito on 2014-04-27
I would go for ext4, here you can find a comparison chart [http://en.community.dell.com/techcenter/high-performance-computing/w/wiki/2290.aspx](http://en.community.dell.com/techcenter/high-performance-computing/w/wiki/2290.aspx)

Here is a definition of mount points: [http://www.linfo.org/mount_point.html](http://www.linfo.org/mount_point.html)   and a definition of filesystem: [http://www.linfo.org/filesystem.html](http://www.linfo.org/filesystem.html)
In the links above it is explained correctly. Here a briefer explanation [http://askubuntu.com/questions/20680/what-does-it-mean-to-mount-something](http://askubuntu.com/questions/20680/what-does-it-mean-to-mount-something)

Normally you need at least 3 partitions; one for root (/), one for home (/home) and one for swap. If you have enough RAM, some people say it is not neccesary
to create a swap partition (above 4GB). So, if you have windows installed on sda1 (the 'a' stands for your primary hard disk, and the numbers for the partition; 
if you insert a usb or have more hard disks, you will see sdb, sdc ...), I would make 3 additional partitions, say 5GB for root (/), 2GB for swap and the remainder for your home directory (/home).
 Here is a guide you can follow to install ubuntu [http://howtoubuntu.org/how-to-install-ubuntu-14-04-trusty-tahr#install](http://howtoubuntu.org/how-to-install-ubuntu-14-04-trusty-tahr#install)  

Be careful with the master boot redord (MBR), and not to install over or delete the windows filesystem.

---

### Post by whitesmith on 2014-04-27
You might want to check out the stuff in my sig line. Good luck with Linux and welcome to the forum!

---

### Post by suprleg on 2014-04-27
Good reads, thanks for that.

---

### Post by stalkingwolf on 2014-04-27
a seperate /Home partition is not a requirement. but is suggested by many.  I make a periodic copy of my home folder with all its hidden files to an external drive.

---

### Post by LastDino on 2014-04-27
Well, having different Home benefits when you install fresh Linux when you're in trouble with older one, your settings with software on older Linux are preserved plus your valuable data too.  But it's by no means a must deed. It is up to you if you are careful, it wont ever bother you.

---

### Post by Impavidus on 2014-04-27
A separate /home partition can be useful, but if your total install is small (say, less than 50GB) or if you plan to store all your data on a shared partition with Windows, it's better not to make a /home partition. You will encounter the situation where one partition is full and the other has relatively a lot of space left. The partition you use for installing the system can best be ext4 and has to be mounted at /.

---

### Post by neoverse2 on 2014-04-29
Well I finally got Ubuntu installed, so I thought.

When I try to boot to Ubuntu i get this error:      "[    9.954563] systemd-udevd[310]: Error calling EVIOCSKECODE: Invalid argument"

After the error the screen changes to what looks like a load screen, a redish color background and "UBUNTU" in bold white letters and some progress dots. Once the last dot is shaded white the screen goes blank and nothing else happens.

Here are the steps I followed for the install.
I made 3 partitions, 5gb for "/" (<assuming that is root), 3Gb for "swap" and 26.95Gb for home.

Also, I an willing to start from scratch so here is how my drive is setup at the moment,
300GB total
>(partitions are in the correct order from beginning of the drive to the end)
C: 15.25Gb - (windowz xp) the only apps in the program files folder are some that don't allow custom install.
: 5.50GB - ext4 root (/)
: 3.03Gb - ext4 swap
: 26.95GB - ext4 /home
E: 15.25 - (Only apps and tools here)
D: 35.52 - (mostly games here)
V: 100.50Gb - [videos]
X: 25.50GB - [system]- upgrades, patches, drivers, etc
Y: 10.25GB - [Recovery] - planned use is a custom recovery partition
Z: 60.31GB - [storage] - app updates, utilities, wares, etc..

In case you need to know any of the specs on the machine I'm installing Ubuntu on:
MB -  MSI_7309v1.3(K9N6PGM2-V) rom v9.1, AMIbios v2.6
CPU - AMD Athlon 64 X2 4200+
Memory 2.75Gb (suppose to be 3Gb but the on board graphics share some of it.
(I plan to add a PCIe card but don't know which one would be best for this board yet.)

---

### Post by Impavidus on 2014-04-29
5.5GB root partition is too small. The base system just fits in, without operating headroom. When you want to install something it will be full soon. If you only have 35GB total disk space available for Ubuntu, don't make a separate home partition.

---

### Post by monkeybrain20122 on 2014-04-29
XP is a dead OS,  get rid of it and give Ubuntu the whole drive (L/xubuntu probably runs better on old xp machines) This XP necrophilia has to stop. :)

---

### Post by BBQdave on 2014-04-29
> **monkeybrain20122 said:**
> XP is a dead OS,  get rid of it and give Ubuntu the whole drive...

+1

Depending on your hardware, Ubuntu Unity 12.04LTS may be a good choice. You can run tighter on system resources with Xubuntu and Lubuntu, but once you open Firefox web browser or LibreOffice... you'll feel the pull on your system, regardless of what DE you are using :)

---

### Post by LastDino on 2014-04-30
I would rather have you copy those ''video'' files on external and get some space from there for your ''root''. It sounds nice to get rid of XP but do that after you get used Ubuntu not before.

---

### Post by neoverse2 on 2014-05-01
> **Impavidus said:**
> 5.5GB root partition is too small. The base  system just fits in, without operating headroom. When you want to  install something it will be full soon. If you only have 35GB total disk  space available for Ubuntu, don't make a separate home  partition.

Guess I followed the wrong suggestion making the partitions. Also, can I not just use NTFS for the time being until I get the new drive? If so ca n I use available space on on like my games partition or the apps partition to install apps for Ubuntu? I don't really like keeping everything on 1 partition in case of corruption.

 I don't know anything about the Ubuntu file structure, and from what you guys have commented on since my last post may I assume the "root" partition for Ubuntu is similar to the root dir(C:\) in windoz, the swap partition is self explanatory and I have no idea what the /home partition is for.
 Any help with this info would be much appreciated for my quest.


Thanks to all of you for taking the time to respond to this thread.

---

### Post by LastDino on 2014-05-01
Yes, ''/'' or Root is basically ''c:'' drive or the drive where windows is installed.

I didn't see anyone suggesting you 5.5GB for root (?), it should be in between 20-24 GB. I'm yet to meet a person who has used all of it, this is more than sufficient if you're going to make different ''/Home''. 

You should read some things about partitioning in order to get better handle. You can use NTFS for storage purpose on Linux but you must format drive (at least partitions which you're going install Linux on) to ''ext4'' in order to install Linux on it. i.e; You need to at least make ''/'' and ''/home'' partitions to be ''ext4''.

Swap is also needed and it should be equvalant to your RAM. You can get away by not making ''/home'' but in that case ''home directory'' will be stored in your ''/''. And that can be bit problematic if you ever need to have a re-install due to crash as you will probably lose everything on ''/'' including ''home'' unless you take backups of ''home directory''.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[https://help.ubuntu.com/12.04/installation-guide/powerpc/apcs03.html](https://help.ubuntu.com/12.04/installation-guide/powerpc/apcs03.html)

---

### Post by Impavidus on 2014-05-01
/home is the directory containing the home directories of all users. The home directories of the users are /home/user1, /home/user2 etc. This /home directory is often on a separate partition. Windows has a separate directory tree for each partition, called C:\, D:\, E:\ etc. Linux attaches (mounts) the file systems of all partitions on directories from other partitions, with one acting as the root, giving one big tree.

Both the system itself and the home directories of the users have to be on a Linux partition, most commonly ext4. For data storage on dual boot systems with Windows you can also use NTFS. So in your case I would not use a separate /home partition. /home partitions have advantages, but they also have some disadvantages which you'll notice especially on smaller installs. Instead you can permanently mount one of your NTFS data partitions. Then create directories for storage on the NTFS data partitions and create symbolic links to them from inside your home directory. In that case only the user config files will be stored on the root partition, all documents on the NTFS partition. I have one computer with a 40GB root partition and no separate /home partition. It has been used reliably for more than seven years now, including 3 release upgrades. I have another computer with a larger drive and separate partitions for root, /home, /usr/local, a second Ubuntu install and swap.

And whether you have a separate /home partition or not, you should always make backups of your vital files. Not necessarily all your files. I make backups of source code, photos and hard-to-find documentation, not of any compiled files that can be recompiled, saved games and things like that.

A swap partition is not strictly necessary, but usually recommended. The size depends on your ram (and any planned ram upgrades), whether you want to hibernate and the available disk space.

Sorry that we keep disagreeing on the use of a separe /home. It must be confusing to you.

---

### Post by neoverse2 on 2014-05-01
> **Goten0007 said:**
> Yes, ''/'' or Root is basically ''c:'' drive or the drive where windows is installed.

I didn't see anyone suggesting you 5.5GB for root (?),
I was in the first response to this thread, the guy said 5gb for root, 2 for swap and the rest for /home

Thanks for the links

> **Impavidus said:**
> Sorry that we keep disagreeing on the use of a separate /home. It must be confusing to you.
It's all good.



Thanks for al lthe help guys, will repartition the space and reinstall this weekend.

---

