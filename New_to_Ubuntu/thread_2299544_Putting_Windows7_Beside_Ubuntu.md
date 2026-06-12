---
title: "Putting Windows7 Beside Ubuntu?"
date: 2015-10-19
forum: New to Ubuntu
---

### Post by tomsubt on 2015-10-19
Hello Everyone,  A friend gave me a gift of windows 7 and I already have Ubuntu(1310, i believe) on the desktop pc.
Two Questions, first, how can i place it side by side with ubuntu?

Second Question, if i had to temporarily wipe out ubuntu try windows 7 can i do that if they dont fit side by side? I dont want to lose my ubuntu, i just want to try out windows 7.  Thank You Very Much

---

### Post by TheFu on 2015-10-19
13.10 support ended in 2014. So you need to back up your data and install a new version of Ubuntu- 14.04 LTS is probably best since it has support until 2019. All other Ubuntu releases only get 9 months support. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) has a table to help everyone plan their OS upgrades.

So... 
1) backup the data
2) install win7 - don't  let it use the entire disk- 60G is about the minimal for Win7 (I know this from personal experience)
3) install Ubuntu 14.04 into the free space.

If the system drive is over 5 yrs old on this machine, this would be a good time to replace it. Then you can use the old drive as a "backup" and don't have to risk any data.  Windows needs to be installed first. It likes to assume it owns the entire disk.

If you need more specific help, more system information would be very helpful. I wrote a script for this exact  purpose:
[http://blog.jdpfu.com/sysinfo](http://blog.jdpfu.com/sysinfo) explains.  Get the script: [http://blog.jdpfu.com/files/quick-sys-info.sh](http://blog.jdpfu.com/files/quick-sys-info.sh) Just updated it to post the data to a pastbin-clone automatically. If you won't want to do that, comment the line at the bottom of the script.

Anyway, hope this all helps.

---

### Post by oldfred on 2015-10-19
Newer UEFI or older BIOS?
Post this:
        sudo parted /dev/sda unit s print

If BIOS/MBR, Window will overwrite boot loader in MBR, so you must have live installer to fix it. And depending on partitions, Windows often "forgets" to write the Linux partition, so you need a backup just of the partition table structure.

 MBR(msdos) only, Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


Your 13.10 is obsolete, you need to upgrade or reinstall.
Either way good backups are vital. And even if upgrading you need a current version live installer in case you need to make repairs.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by tomsubt on 2015-10-19
I keep getting Drivers Not Found, arent the drivers on the windows 7 disk? Thanks

---

### Post by TheFu on 2015-10-19
> **tomsubt said:**
> I keep getting Drivers Not Found, arent the drivers on the windows 7 disk? Thanks

Sorry. Installing windows is far outside my skillset.
It is impossible to include every possible driver on a DVD. As long as the system isn't doing RAID or have some really strange GPU, can't imagine there would be an issue.

Really need the info from that script to help more.

---

### Post by Quarkrad on 2015-10-19
Re your win7 install - you need to identify the make and model of your motherboard and go to the manufacturers site (of the motherboard) and download the win7 drivers for your specific motherboard.   Install win7 and then install the downloaded drivers (these are drivers for things like, chipset, LAN connection, audio, video, etc).  Once these drivers are installed you can update win7.  With a windows fresh install you have to download the drivers for your motherboard and manually install them - you do not have to do this for ubuntu/linux.  The drivers are part of the install process.

---

### Post by Geoffrey_Arndt on 2015-10-19
Tomsubt:   the odds are very high, that if you try to install Windows 7 on a PC that already has any version of Linux on it (like Ubuntu) . . . it will totally hose (destroy) Ubuntu and all your data with it.

Consumer versions of windows especially are not friendly to other OS's being on the same hard drive (or even a secondary drive in some conditions).   

I would say, to try WIndows, just get a "Live Windows 7 DVD" . . . . . excepting that as far as I know, any Live version of Windows (except rescue utilities disk) *doesn't really exist* (MS doesn't "even" like the concept of Live OS's).

---

### Post by Quarkrad on 2015-10-20
I agree with Geoffrey above - generally if I completely rebuild I install windows first (on the whole HD) and then install ubuntu/partition the HD.  However, having said that, the last time (a week ago!) I completely rebuilt I partitioned the HD first, installed ubuntu (14.04) and then installed win7. If you are confident with windows and ubuntu install processes and hd partitioning you can install ubuntu first but installing windows first is the safest.

---

