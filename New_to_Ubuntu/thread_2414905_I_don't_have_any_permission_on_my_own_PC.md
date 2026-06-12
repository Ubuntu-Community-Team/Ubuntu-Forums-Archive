---
title: "I don't have any permission on my own PC"
date: 2019-03-17
forum: New to Ubuntu
---

### Post by vtrgames on 2019-03-17
Hello,

Recently I decided to trade my Windows 10 for the Ubuntu 18.04.2 LTS. Removed my extras HDDs 1 and 2, leaving only the main one on the PC, made the boot, installed Ubuntu and put my extra HDDs back in.

For some reason, all files on those extras HDDs are locked in read-only mode: I can access them, open them, etc., but I can't delete or modify them for not having authorization. Even though I'm the only user on the PC.

I've tried some tutorials about the terminal here and there to grant me authorization, but it either tells me "command not found", doesn't do anything or, again, says I have no authorization. How can I get control of my own machine back?

By the way, I'm not an expert user, in fact it's my first time using Ubuntu, so please be kind and explain for the noob here how things work.

Thanks for the assistance.

---

### Post by webaake on 2019-03-17
Take a look at this: [https://askubuntu.com/questions/657264/with-fstab-how-do-i-automatically-mount-an-ntfs-partition-with-full-permissions](https://askubuntu.com/questions/657264/with-fstab-how-do-i-automatically-mount-an-ntfs-partition-with-full-permissions)

I assume the HDD's you try to mount are NTFS.

---

### Post by Impavidus on 2019-03-17
You may be the only *human* user on your computer, but you're not the only user. Various system services rus as their own user and there's the root user for administrative tasks. You, as the only human user, can act as the root user, but you're not the root user. Having separate users for different tasks is what makes Linux such a secure system.

I assume that you already used those hard drives to store data on Windows. They're probably formatted as NTFS partitions. You should be able to mount a clean NTFS partition for read-write access by clicking it in the file manager. To make things easier on the long term, you can use /etc/fstab to mount them automatically at boot with the ownership and permissions you like.

That fact that you can't suggests something different is going on. The NTFS partitions may be mounted in read-only mode. In this mode, no user (not even root) can write to the NTFS partitions.

Windows 10 likes to use a trick to speed up the boot time, which involves not cleanly unmounting the filesystems. This may have left the filesystems on the hard drives in an unclean state. Ubuntu can mount an unclean NTFS partition in read-only mode (or at least attempt so), but not in read-write mode and cannot clean it up either. Which of course means that you shouldn't use NTFS partitions on a Linux-only computer.

I suggest you copy all contents from your hard drives to a backup drive, then format the drives using a native Linux filesystem, then copy the files back. Also read up on users, file ownership and permissions on Linux. This is central to security on Linux systems. The permissions system is quite simple and effective and understanding it will save you from a lot of frustration.

---

### Post by The Cog on 2019-03-17
Unless windows was fully shut down, it will have left the disks in an unsafe state that Linux won't write to. 
See post #4 in this thread (and th page that post links to): [https://ubuntuforums.org/showthread.php?t=2379710](https://ubuntuforums.org/showthread.php?t=2379710)

---

### Post by yancek on 2019-03-17
Ubuntu and all Linux systems were designed as multi-user systems so that an ordinary user does not usually have access to write/delete anything outside the /home/user directory.  To do that you can either use root privileges which entails using the sudo command or you can change ownership/permissions on the directories you want.  Ubuntu documentation on using sudo with Ubuntu in the link below.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

With Ubuntu, you should be able to write to windows ntfs/vfat filesystems if you have the proper software (ntfs-3g).

You indicated that you got a 'command not found' error but neglected to post the command(s) you used so no one will be able to help with that.

There are hundreds of Linux systems available and one of the big advantages of using Ubuntu is that it is very well documented and this documentation is available online.  The site below has official documentation on using Ubuntu, just get the appropriate link for the release you are using.

 [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by jdeca57 on 2019-03-17
As root you have complete control over your system, to put it in Windows term you're administrator. Standard in Linux you work as a user and that has limitations: you can't disrupt your system and viruses are less effective.
Now the problem of the ntfs drives with read only can only be solved in two ways (supposing there is no windows on the original system)

One: You have access to a Windows computer, then with a simple sata enclosure you can attach the drive to a usb port of the Windows computer consult the data, verify you can write on it, and properly eject it from the usb connection. That should provide you with a 'clean' drive and rw access from Ubuntu. A lot of work, but a solution.

Two: You really can't find a Windows computer or taking the disk out and putting it in an enclosure is cumbersome and you dont't want to do that then there exist usb external disks and you can make a backup on one disk you have to buy or that you have because you backup your data.
After the backup, you reformat the ntfs drive with a Linux file system and restore. Do that for both drives,

Actually the last recommendation is a copy from reply #3 and I agree that's simply the best long term solution.

---

### Post by vtrgames on 2019-03-18
Thanks for replying, everyone. I have a laptop with windows on it, so I'll do a backup and format my HDDs.

Making some more research, I realized I was being a bit dumb with the things i tried to do. Definitely Windows and Ubuntu are very different from each other.

Well, I'll go now to the games area here. I need to check if GeForce Experience can work and record things on Ubuntu. Otherwise, this system change will be for nothing. I'm trying to be a let's player after all.

---

