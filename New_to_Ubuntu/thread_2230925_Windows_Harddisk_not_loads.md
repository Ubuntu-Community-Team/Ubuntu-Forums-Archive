---
title: "Windows Harddisk not loads"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by blackpearljack on 2014-06-22
My laptop has dual boot with windows 8.1 and ubuntu 14.04 .I started my system and i started windows 8 from grub but it never loads it just shows me a black screen.But when i logged in with ubuntu then i choose c drive from home folder of ubuntu it shows the following message any idea on how to fix it.It is same case with other drives also.Please suggest me how to fix this

The message is as follows
Error mounting /dev/sda5 at /media/hack3r/Windows8_OS: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda5" "/media/hack3r/Windows8_OS"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by Bucky Ball on 2014-06-22
Know the problem. Win8 hibernates the hard drive so it never actually unmounts. Nasty trick, that. Therefore, can't remount from grub or in Ubuntu. The hard drive needs a clean shutdown.

I'm not sure how you fix this, but from what I've seen on my travels around here, you might try going to the BIOS and switching off all forms of hibernation; faststart; fastboot, or anything else Windows related, and try a reboot ...

About the only concrete info I can give you is where to start searching as the Win8 hibernation thing is the cause of your problems. There is a fix, I just don't know it, but there are others here who do. Hopefully one of them will drop by eventually or you can dig up the resolution online.

This is a fresh install, I presume? Also, did you install Ubuntu in UEFI mode? Have a look in the BIOS for that. If there is a problem there, Boot Repair may be able to help.

Awaiting a report back of your findings.

---

### Post by blackpearljack on 2014-06-22
Yes i installed in uefi mode mine i in my bios i could see very few features like secureboot,usb boot,Intel virtualisation only and i can't find fast start or fast boot option in bios settings.I'm using lenovo ideapad z510.Does removing battery make clean shutdown(without plugging the machine)

---

### Post by Mark Phelps on 2014-06-22
It's not as BIOS setting; it's a Windows 8 setting -- FastStartup.  You have to disable it in Windows 8.

---

### Post by blackpearljack on 2014-06-22
But how can i do it if windows doesnot even load after i choose it from grub menu

---

### Post by -Marco on 2014-06-22
Yes, please disable Secure Boot and the order of the boot, move the Windows Boot Manager to last place. Trust me, it worked for me! :)

---

### Post by blackpearljack on 2014-06-22
I did this but still no change

---

