---
title: "unable to open SSD drive, seen but getting error about mounting"
date: 2024-06-02
forum: New to Ubuntu
---

### Post by dfoster1980 on 2024-06-02
HI! 

I can't see the files in my SSD drive, I can see the SSD on my homepage, but when I click on it to view the files, I get this error

**"Failed to mount SSD drive. Error mounting, wrong fs type, bad option, bad superblock, missing codepage or helper program, or other error."**

I have 2 SSD drives and they both get this message, all my older non-SSD drives all work properly.  When I booted using a Windows CD it could see the SSD and the files within. 

I have looked a lot of posts but the only one with a similar problem says to wipe the drive and create a new filesystem. I don't want to erase it, I'd like to use the files. 

Thanks

---

### Post by oldfred on 2024-06-02
If NTFS and you use with Windows then it can just be Windows set the hibernation flag with either hibernation or Fast startup.
The Linux NTFS driver will not or should not mount hibernated NTFS as when hibernation restored by Windows any work done by Linux is lost.
You may be able to manually force mount as read only (ro) instead of rw.
Or turn off fast startup in Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Force mount, read only (ro), change example with sda3 to your correct NTFS partition:
sudo parted -l
sudo mkdir /media/windows
sudo mount -t ntfs -o ro /dev/sda3 /media/windows

---

### Post by dfoster1980 on 2024-06-02
The force mounting worked!  Thank you!

---

