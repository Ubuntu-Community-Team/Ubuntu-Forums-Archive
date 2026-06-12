---
title: "NTFS mount error"
date: 2024-08-17
forum: New to Ubuntu
---

### Post by hackury on 2024-08-17
Hello, how are you people? I have a problem when I want to mount a disk HDD, I get this error "new vol:wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper programe, or the order error" no I know what to do, I tried everything, I already used ntfsfix and it didn't work, I just installed Ubuntu an hour ago I was using Windows and this disk is unit two of my PC I need to recover it, someone with a good heart can help me, thank you for paying attention to my message I wish you the best in life

---

### Post by oldfred on 2024-08-17
If asking for help, you need to post in your own thread in one of the help sub-forums.
Moved to New to Ubuntu forum.

Issue most often is from Windows and it has used Fast Startup which sets hibernation flag, or you have turned on hibernation.
May also be Windows turned on bitlocker.
Check settings in Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)

---

### Post by Morbius1 on 2024-08-18
What a mess this has turned out to be ................

If you are mounting this ntfs partition through the file manager it will use the ntfs3 "driver" and the chances are good you will get your exact error.

If you mount it manually or in fstab and use the ntfs or ntfs-3g type it will mount with the old ntfs-3g "driver".

ntfs3 is messed up: Here is one of many observations scattered across the internet: [Does the Linux NTFS3 Driver Corrupt Directories?]("https://www.heiko-sieger.info/does-the-linux-ntfs3-driver-corrupt-directories/")

As per the link above if you prevent ntfs3 from loading the file manger will use ntfs-3g
```
echo 'blacklist ntfs3' | sudo tee /etc/modprobe.d/disable-ntfs3.conf
```

Easily reversible by deleting the disable-ntfs3.conf file.

---

### Post by ActionParsnip on 2024-08-19
I'd plug the drive into a Windows system and run a fill chkdsk to make sure the file system is correct and complete.

---

### Post by nicolasdentremont on 2024-08-19
I had that error while using the wife's external HDD and couldn't find any Linux based solution. I plugged it into her laptop and Windows detected an error right away and corrected it. That's what convinced me to get my own external HDD formatted with a Linux filesystem.

---

### Post by Morbius1 on 2024-08-20
The problem with using a Windows machine to fix this is that it is not a permanent fix as file corruption will occur again at some point: [https://ubuntu-mate.community/t/ntfs3-kernelmodule-corrupted-a-ntfs-disk-again-im-reverting-to-fuseblk-ntfs-3g/27188](https://ubuntu-mate.community/t/ntfs3-kernelmodule-corrupted-a-ntfs-disk-again-im-reverting-to-fuseblk-ntfs-3g/27188)

I still recommend blacklisting the ntfs3 "driver" so that the old ntfs-3g driver is in charge until this is fixed or ntfs-3g is removed.

---

### Post by emmatf on 2024-08-22
Error you're encountering suggests that there might be an issue with the filesystem on the partition /dev/sdb2. This can happen for several reasons, such as a corrupted filesystem, an unsupported filesystem type, or a misconfiguration in the mount command. Want NTFS files get back you try "BLR data recovery tool" hope this is help you a quite answer. This software have some amazing features like repair your corrupted files.

---

