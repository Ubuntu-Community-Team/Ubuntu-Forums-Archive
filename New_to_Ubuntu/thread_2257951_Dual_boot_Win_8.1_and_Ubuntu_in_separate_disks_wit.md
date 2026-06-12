---
title: "Dual boot Win 8.1 and Ubuntu in separate disks with shared storage unit"
date: 2014-12-23
forum: New to Ubuntu
---

### Post by julio.c.aguilar.z on 2014-12-23
Hi all,

I've been working with Xubuntu in my new job for about 4 months and I love it. I want to install ubuntu in my new laptop, which came with Windows 8.1. I am a gamer and want to keep windows mainly for that, and ubuntu for development xD

What I have:
- 256GB SSD where windows is installed
- 1TB HDD

What I want:
- Option 1:
  + 256GB SSD for win 8.1
  + 256GB HDD Partition for ubuntu
  + 750GB HDD storage for both OSs 
- Option 2:
  + 128GB SDD for win 8.1
  + 128GB SDD for ubuntu
  + 1TB HDD  storage for both OSs

The first option is what I originally wanted. I thought of separate disks for each OS like a logical "object-oriented" approach (I wish I had a third small SDD to have both OSs on separate SDDs and 1TB storage for both). I also read that this way saves a lot of headaches with the boot-loaders or when upgrading/changing OSs, please correct me here ^^.

However, I also read it has its advantages to install both OSs in one disk (Option 2) but not sure what these are xD. Can someone enlightened me, please?

I found [this info]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs") on how to install windows and ubuntu on separate disks, but it doesn't explain how to allow both OSs to access the same HDD. Now, I know the HDD has to be formatted as NFTS. But is it the whole disk or just the partition I want for storage (250GB [COLOR=#000000]ext4 for ubuntu, and 750GB NFTS for storage[/COLOR])?

I also found that there are some issues with dual boot with windows 8. But don't really know how to get the workaround. 

Can someone please guide me with this? Links regarding each issue will be enough. If you'd like to provide more detailed explanations, even better XDDD

Best regards,
Julio

---

### Post by oldfred on 2014-12-23
Is Windows 8 is pre-installed, or did you do it yourself? Or really is it in UEFI boot mode or old BIOS boot mode.

If Windows is UEFI, you want Ubuntu installed in UEFI boot mode. And both drives configured with gpt partitions. I also like an efi partition at beginning of data drive. That would be if later you want to test the new version of Ubuntu and do not want to risk corrupting current working install. I actually have several Ubuntu's on my data drive as experiments.

I suggest Ubuntu only have 25GB for / (root) on SSD and configure it so all data is on hard drive. I keep /home where data normally is inside / (root) and on SSD for speed. But like the common data folders like Documents, Video, Music etc and a few I create like Projects to folders in a Data partition on data drive. When still using Windows I had both a NTFS data partition for any data I might want in both systems, but a Linux formatted partition for Linux only data. I now only have the Linux partition for all data.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

    
       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)
       
 Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

     
    
 [http://askubuntu.com/questions/524943/dual-boot-with-ssd-and-hdd-storage](http://askubuntu.com/questions/524943/dual-boot-with-ssd-and-hdd-storage)

---

### Post by julio.c.aguilar.z on 2014-12-23
Hi Oldfred, 

thanks for replying. It is a pre-installed windows 8.1 with UEFI. I will read those links and try to understand them ^^ I'll ask, if I don't. 

Regarding your suggestions, you would install ubuntu in the SSD inside a 25GB partition with only the /root folder and make links to the /home and /data folders, which are in the HDD. Right? Why? Is the only reason the speed?

The partitions on the HDD can have different formats? like NTFS for a shared partition, and ext4 for linux only data?

Best regards,
Julio

---

### Post by yancek on 2014-12-23
> Regarding your suggestions, you would install ubuntu in the SSD inside a  25GB partition with only the /root folder and make links to the /home  and /data folders, which are in the HDD. Right? Why? Is the only reason  the speed?

I don't think that is what he means but I'm sure he will post back.  When referring to '/', that means the root of the filesystem where all the system files are and not the root directory which you refer to as a folder.  There is a root directory which is for the root user and is very different from '/', root of the filesystem.  One advantage of having the /home on a separate drive or partition is it is easier to reinstall and save all your personal data you have there.  You can also just create a separate data partition and keep personal data/info separate even on a different drive.

---

### Post by oldfred on 2014-12-23
Since you have two drives you have to use the Something Else install option and choose what to install where.
The / (root) partition is where the entire system is normally installs. Several default folders like /home can be installed into different partitions and years ago and some servers still do that. But most desktops are better with just root & swap. And if a larger drive then /, swap and /home or data or perhaps both. 

My / is 25GB, and I currently use about 11GB of the 25GB. And 2GB of the 11GB is my /home. And my /home is only that large as I installed .wine for Windows version of Picasa. The internal user settings without data are tiny much less than 1GB. But normally data is stored in /home unless you specify other locations for data which I do.

I want / & /home (user settings portion) on SSD for speed. Data which is not as regularly read then can be on slower rotating hard drive. I even move some hidden folders like Filefox & Thunderbird profiles that normally are in /home into data partitions on some of my installs. Anything that is just data can be moved.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        24G   11G   13G  47% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G   12K  3.9G   1% /dev
tmpfs           793M  1.5M  792M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   80K  3.9G   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sdb5        28G  1.4G   25G   6% /mnt/backup
/dev/sdb4       385G   70G  296G  20% /mnt/data
/dev/sdc1       384M  242M  142M  64% /media/fred/NEWEFI_32
/dev/sda1       500M  5.6M  494M   2% /boot/efi

```

The other /run with none mounts are temporary files created by the system. And sdc1 is a flash drive.

---

