---
title: "Advice on partitions for dual booting"
date: 2017-01-22
forum: New to Ubuntu
---

### Post by mjpin1 on 2017-01-22
I am very new to using ubuntu and was seeking some advice to help get me going. I am planning on dual booting ubuntu and windows and was wondering how much space I should give both windows and ubuntu and how I should do it.  My system is running with a 1TB HDD. Any help would be greatly appreciated.

---

### Post by oldfred on 2017-01-22
I find partitioning to be very personal. It depends a lot on what you are using system for.

I only have one system with Windows and did not plan even on using Windows. It came with Windows 8 and I shrank it to 50GB on a 1TB drive to install Ubuntu. But to watch some DRM's videos only Windows worked. But to upgrade to Windows 10 I had to expand to 100GB. And I only use it for videos. And have two Ubuntu installs, one LTS and the other newest just to try it out. I do have a shared NTFS partition, but Windows updates turn on fast start up or hibernation and that locks up all the NTFS partitions as the Linux driver will not mount read/write hibernated partitions.

I typically install Ubuntu in 25GB / (root) partition, use about 2 or 3GB for swap at end of drive so out of the way. But then I have very large data partition(s).
When I had XP I started using a shared NTFS partition for all data I might want in both systems including Firefox profile, Thunderbird profile, & all photos. Then I had same email, bookmarks and photos in both systems.
I stopped using XP years ago, but then converted shared data partition to Linux format as I typically have more than one Ubuntu install. I like to try next version or see difference with another flavor. But with data partition I can have same data in all installs.

I also typically put / on SSD, but have data on HDD. But also have another install just in case on all data partitions.

I find even my own optimal partitioning plan is not the best a few years later. But by then I add a new drive as I do not trust drives for extended periods, even if warrantee is 5 years.

Is system UEFI or BIOS? Is then Windows installed in UEFI or BIOS boot mode?
You want Ubuntu in same boot mode as Windows.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by scriber on 2017-01-22
Thanks for that very helpful post oldfred, wish I had seen that before I installed Ubuntu earlier.
 I guess I'm going to redo the whole setup soon as I currently have a multiple partition setup ( 7 Primaries ) on the main HD and after reading your post I see can improve things.

---

### Post by oldfred on 2017-01-22
Just be sure to have good backups, as reconfiguring system can have issues. And a good backup means issues do not matter.

---

