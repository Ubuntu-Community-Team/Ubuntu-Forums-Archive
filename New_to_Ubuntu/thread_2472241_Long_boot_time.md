---
title: "Long boot time"
date: 2022-02-21
forum: New to Ubuntu
---

### Post by ejr32123 on 2022-02-21
Hello, I have two questions. I don't have much experience with ubuntu or linux. The problem I am having is extremely long boot times, over 2 minutes. I have grub version 2.04 is that the right version for ubuntu 20.04.4? The reason I ask is because I had ubuntu on my PC from a few years back. I never removed grub, I just switched to use windows boot manager instead. I just reinstalled ubuntu tonight and it now I am having slow boot times. I read some where that running systemd-analyze can help debug problems. Can anyone help me figure what's going on? Thanks!

edit: I tried installing ubuntu on my old laptop and it has the same version of grub, so I can confirm it is the right version
edit 2: It stopped booting slowly. maybe it was just installing new updates or something since it was a new install. either way it is working now.

[https://ubuntuforums.org/attachment.php?attachmentid=290085&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290085&stc=1)

---

### Post by mIk3_08 on 2022-02-22
> **ejr32123 said:**
> Hello, I have two questions. I don't have much experience with ubuntu or linux. The problem I am having is extremely long boot times, over 2 minutes. I have grub version 2.04 is that the right version for ubuntu 20.04.4? The reason I ask is because I had ubuntu on my PC from a few years back. I never removed grub, I just switched to use windows boot manager instead. I just reinstalled ubuntu tonight and it now I am having slow boot times. I read some where that running systemd-analyze can help debug problems. Can anyone help me figure what's going on? Thanks!

edit: I tried installing ubuntu on my old laptop and it has the same version of grub, so I can confirm it is the right version
edit 2: It stopped booting slowly. maybe it was just installing new updates or something since it was a new install. either way it is working now.

[https://ubuntuforums.org/attachment.php?attachmentid=290085&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290085&stc=1)

How about the results of 
```
systemd-analyze blame
``` 
Just post the results here in thread wrap with code.
Good Luck and Cheers

---

### Post by ActionParsnip on 2022-02-22
If you reboot then run:
```

dmesg -T > /tmp/myBoot.txt; gedit /tmp/myBoot.txt

```
You can look for big gaps in time and identify issues

---

### Post by oldfred on 2022-02-22
Please do not post screen shots of terminal output.
Just copy & paste, if longer use code tags.
Easy to add code tags with Forum's advanced editor and # icon.

Did you create new swap file or have some other mount in fstab that is now not valid. It then has to time out before failing.
Check UUIDs in fstab match all UUIDs in partitions.
lsblk -f 
cat /etc/fstab
and swap in this if swap partition reformatted (may not exist, also which is ok):
 cat /etc/initramfs-tools/conf.d/resume

Some things to review:
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

