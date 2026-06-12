---
title: "Goes straight to Windows on Boot"
date: 2017-12-24
forum: New to Ubuntu
---

### Post by huggard on 2017-12-24
Howdy,

I installed Ubuntu on my laptop a while back, but whenever I boot my computer it goes straight to Windows.

I've tried using the Graphical Boot-Repair Tool, which did not fix the problem but gave me this link: [http://paste.ubuntu.com/26243799/](http://paste.ubuntu.com/26243799/)

Thanks.

---

### Post by RobGoss on 2017-12-24
So I'm assuming you was hoping for a dual system with Windows and Ubuntu correct?

Was your system dual booting at all or it just goes straight to Windows

---

### Post by oldfred on 2017-12-24
This is saying you still have Windows fast start up or hibernation on.

>  Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume 



 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

But HP is not dual boot friendly. You usually cannot boot the Ubuntu entry, except manually every time you reboot, but have to use a hard drive entry or fallback type entry.

 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

