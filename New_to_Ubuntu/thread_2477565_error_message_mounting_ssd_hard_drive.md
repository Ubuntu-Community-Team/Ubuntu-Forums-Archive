---
title: "error message mounting ssd hard drive"
date: 2022-07-29
forum: New to Ubuntu
---

### Post by annachino9 on 2022-07-29
Hi everyone!

I am trying to save data from an ssd hard drive through my old Dell Inspirion Laptop on which I have Lubuntu as the os. I can see my hard drive but there's an error message. it reads:  
 "error mounting: mount exited with exit code 14: windows is  hibernated, refused to mount. Failed to mount dev/sdb3: operation not  permitted. please resume and shutdown windows properly or mount the  volume read-only with the ro mount option or mount the volume read-write  with the "remove_hiberfile" mount option. For example on the command  line: mount -t nfts-3g -o remove_hiberfile/dev/sdb3/media/E......"

  
 I used Linux a few years ago and remember nothing about it really. So I am hoping you can tell me how to get to my data, I would be eternally grateful! What do I do now?

Thank you very much in advance!! 
Anna

---

### Post by TheFu on 2022-07-29
Seems that Windows was the last to access that partition and didn't correctly close the file system.  There's nothing that Linux can do, until that is fixed.  You'll need a Windows machine.  Then disable "fast startup" and "hibernation" from inside Windows.

Once those things are addressed, Windows should properly close the file system on shutdown and Linux will be able to access the file system - assuming it is NTFS.

---

### Post by annachino9 on 2022-07-29
Thank you for your reply. The external had drive is nfts. I have absolutely no idea how to "disable "fast startup" and "hibernation" from inside Windows." Would it be best if I googled it (since I'm in a Linux forum)? Or do you happen to know what to do?

---

### Post by oldfred on 2022-07-29
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)


You can force mount in read only mode. Normal read/write mode not allowed to prevent damage to a hibernated file system.
External drive, use safe eject or try manual mount read only with recover
[https://superuser.com/questions/1231582/hdd-with-windows-boot-locked-because-of-hibernation-flag](https://superuser.com/questions/1231582/hdd-with-windows-boot-locked-because-of-hibernation-flag)

Unless dual booting with Windows, do not use Windows formats like NTFS. You can only repair or defrag from Windows.

---

### Post by TheFu on 2022-07-29
> **annachino9 said:**
>  Or do you happen to know what to do?

I see oldfred answered.  He's one of the dual-boot people around here.

I haven't dual booted in over a decade after being burned by MSFT.  I've never had any Windows system that used fast startup or hibernation.  In short, I have no first hand knowledge of the issue you have.

+1 for using native Linux file systems unless the storage device will be physically connected to some other OS.  Network access from Linux system storage doesn't need NTFS. Linux can talk network storage protocols that other OSes understand.

---

### Post by Impavidus on 2022-07-29
If this is for saving files from the SSD of a failed Windows computer or something like that, try to mount it read-only.```
mkdir mountpoint
sudo mount -t ntfs -o ro,umask=222 /dev/sdb3  mountpoint
```(I think I got that right, but I never really mount ntfs filesystems.)
And to unmount it later:```
sudo umount /dev/sdb3
```(Yes, that's umount, not unmount.)

---

### Post by TheFu on 2022-07-29
I think the masks in the mount options need to be:
fmask=0002,dmask=0002


For NTFS, I use these options:
```
nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```
A few are for performance. Some are for security and the uid/gid/dmask/fmask are so my userid can have ownership, while everyone else can read.  The timeout is because my only NTFS device is a USB drive, so it isn't always there or powered on.

---

### Post by yancek on 2022-07-30
The link below is to the microsoft site and explains how to disable hibernation and to enable it again.  You can also do it by going to the power settings in windows.l

 [https://docs.microsoft.com/en-us/troubleshoot/windows-client/deployment/disable-and-re-enable-hibernation](https://docs.microsoft.com/en-us/troubleshoot/windows-client/deployment/disable-and-re-enable-hibernation)

---

### Post by ActionParsnip on 2022-07-30
You may want to chkdsk the file system in Windows too. Make sure it is complete and consistent.

---

