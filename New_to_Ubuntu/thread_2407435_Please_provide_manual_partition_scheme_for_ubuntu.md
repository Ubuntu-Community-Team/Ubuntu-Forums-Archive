---
title: "Please provide manual partition scheme for ubuntu"
date: 2018-12-04
forum: New to Ubuntu
---

### Post by ramrajesh on 2018-12-04
Dear all,

I am new to Ubuntu .Please provide manual partition for installing Ubuntu in HP Laptop.

I am an advanced user where i can run number of virtual machines in vmware or virtual box.


My Hardware details listed below:

Model : HP AB-522TX
HDD : 1 TB
Ram : 16 GB
Graphics : 4 GB Nvidia

---

### Post by oldfred on 2018-12-04
There is no one right partitioning scheme. Every user is unique and had different needs.
Even my own optional partitioning plan from several years ago is now obsolete and changed (somewhat).

Ubuntu's default install is just / (root) as ext4. If UEFI then first partition will be an ESP - efi system partition as FAT32 with boot flag/esp flag. Ubuntu now uses a swap file, so older instructions on creating swap partition are obsolete. But a swap  partition will still be used if you have one.

Many like a separate /home to separate data from system. I do multiple installs on one drive, so do not want changes in /home to change main working install, but do want all my data, so I have separate data partition(s). Some what separate partitions for video or music, separate from the defaults in /home. But too many partitions can mean data fills one partitions, when you have lots of room in another partition.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Or use gdisk which is in repository, now standard in newer installs: 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[*]You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
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
Older /boot & swap not now required.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by oldrocker99 on 2018-12-04
What he said. By all means, create a separate /home partition. If you ever have to reinstall, you'll be glad you did.

---

### Post by MoebusNet on 2018-12-06
>  I am new to Ubuntu .Please provide manual partition for installing Ubuntu in HP Laptop  I believe Gparted is still available on tne installation media. You can run the Live DVD/USB and choose the 'Try Ubuntu' option then use Gparted from the menu to partition your dismounted drive before installation or if you prefer you can use the manual partition option during installation.

---

### Post by oldrocker99 on 2018-12-06
I have always made 2 partitions; a 64GB partition for /, which is plenty, and the rest for /home. It makes reinstallation, should worst come to worst, or you just want to try another distro, simple. In the installation window, choose "Something Else." The partitions you made using Gparted are then shown in a dialog. Mount the 64GB partition as /. Then, mount the other partition as /home. Format each partition as ext4, click on "Continue," and the installation will proceed. When it's finished, it will ask if you want to restart, or keep using the booted system. Restart, and you'll have a complete system. 

I advise backing up /home, if there is anything there, and reinstallation.

---

### Post by Topsiho on 2018-12-09
+1 for all these answers. Nothing I can add to them, except this:

I would go for the answer oldrocker99 gives, as it, so far (for me), has been sufficient and very easy to understand.

But.

But when you get into problems, the answer oldfred gives is very complete, and covers GPT and MBR kinds of installs.
If something goes haywire, you'll probably find your answer in his post.

Topsiho

---

