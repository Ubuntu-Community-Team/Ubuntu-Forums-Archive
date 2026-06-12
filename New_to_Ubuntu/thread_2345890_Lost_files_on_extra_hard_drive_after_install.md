---
title: "Lost files on extra hard drive after install"
date: 2016-12-08
forum: New to Ubuntu
---

### Post by coreygallant on 2016-12-08
Hi I am new to Linux and have installed and really enjoyed the new open source operating system. 

However I am having a problem.  I am running the Ubuntu os on a raid0 between two of my ssd hard drives and everything is running great.   I had an extra hard drive that I used for storage that i set up while using windows.   It is an ntfs file system.   When I mount the disk in Ubuntu it says there are no folders to show and it appears empty.   However if I go to properties is says that 650 out of 750 gb are still being used.  So I was just wondering how I can access or even see these files since they are obviously still there. 

Thanks a ton.   I can't afford to lose this storage disk or any of the things on it.

---

### Post by yancek on 2016-12-09
How did you try to access/mount the partition?  With a command from a terminal, clicking an icon?
Was the disk last used on a windows computer?  If so, which version?  Dynamic disk?

---

### Post by coreygallant on 2016-12-09
I tried to access the disc just by double-clicking to mount it in Ubuntu and when it opens after it mounts it says no folders to show.. the extra hard drive was created using disk Manager in Windows 7 64 bit and was last used with Windows 7 64 bit.. Yes I believe it is a dynamic disk

When I first made the hard drive on windows 7. I used disk manager and formatted it ntfs.   Then I used the "create new simple volume" option

Bump

Someone please help me

---

### Post by oldos2er on 2016-12-10
Have you seen [https://help.ubuntu.com/community/Mount%20Windows%20Raid%200%20Volumes%20Howto](https://help.ubuntu.com/community/Mount%20Windows%20Raid%200%20Volumes%20Howto) ?
I've no idea if or how this works with dynamic disks.

Also see [http://askubuntu.com/questions/567432/how-do-i-properly-access-windows-software-raid-0](http://askubuntu.com/questions/567432/how-do-i-properly-access-windows-software-raid-0)
I've no personal experience with this; hopefully someone who does will post soon.

---

### Post by coreygallant on 2016-12-10
Ok I checked it out..  The problem is that the hard drive that I'm trying to access is not part of the raid.  I have 2 hard drives in raid0 with the ubuntu os installed working fine.  I also have two other hard drives that arent in the raid that are working fine as well.  Then there is one more hard drive that is also not in the raid but for some reason I cant open it the way i can with all the other hard disks..

If i double click the disk it mounts it then brings me to a window thats says "folder is empty" but if i right click and hit properties it shows that all the space is still being take up by my files.  I just dont understand why I cant see them or open them..

The only thing I can really see that is different about this drive from all the others is that if i go into the "Disks" application and click down through all the extra hard drives (that arent in the raid) the one that isnt functioning says "Partition Type HPFS/NTFS (Bootable)" and all the other ones that work just say "Partition Type HPFS/NTFS"

Someone please help me out here.  I really want to use linux.. but if it means parting with all my work files and my family's movies and stuff I just can't and I'll have to return to windows..

---

### Post by thatsmyboy on 2016-12-10
Hi Corey, Welcome to Ubuntu Forums! You posted into the NEW HERE forum, so your specific question might not be quickly attended to by specialists. Also, we're all volunteers here so a little patience goes a long way :P Have you tried to mount from the command line before??

p.s. it probably doesn't mean parting with all your files

---

### Post by oldfred on 2016-12-10
If this is NTFS, that is Windows.
Did you have the drive mounted with Windows 8 or later? If so it may still be hibernated.
Windows 8 or later uses a fast start up setting that is always on hibernation. So if hibernated you may not be able to mount it read/write with Linux.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You can see if you can manually mount read only. Change example with sda3 to your drive, partition.

 Force mount, read only:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows 

If it also needs chkdsk, that can only be done from Windows. And then the Linux NTFS driver will not mount it at all.

---

