---
title: "[lubuntu] No wubildr?"
date: 2014-09-13
forum: New to Ubuntu
---

### Post by Pkmns on 2014-09-13
Hello everybody.
Total newbie here, installing Lubuntu for the first time in his life. 
Basically, what I wanted to do was bring my EEEPC 900 back to life. I had installed Win7 on it some time ago and it worked decently, albeit quite slow - and most of the HDD was occupied by the OS itself. Since I had stopped using it because of these problems, I looked on the Internet for the best OS for EEE and found out about Lubuntu.
I used Unetbootin on another PC to make a bootable thumbdrive with Lubuntu Live 14_04, then booted the PC with the thumbdrive plugged in. Since nothing happened, I installed the helper and rebooted. Now, each time I choose to boot Lubuntu, I get a DOS screen with the message:
"Try (hd0, 0): NTFS5: No wubildr."
I googled the problem and from what I gather, I should just wait for it to boot - I did but nothing happened.
Any ideas on why this happens and how to solve it?

 Thanks in advance :)

---

### Post by yancek on 2014-09-13
Before booting the flash drive you created with Ubuntu, you need to change the boot priority in the BIOS pointing to the flash drive which should be plugged in before you boot.

Not sure what helper you are referring to.  You refer to getting the message below when trying to boot Lubuntu.  Did you manage to get it installed or are you talking about booting the flash drive.  The message below refers to wubi which is a program to install Ubuntu as a program inside a windows operating system.  Do you still have windows 7?  Wubi is actually not supported any longer but you may get it to work if you have windows 7.

> Try (hd0, 0): NTFS5: No wubildr."

---

### Post by Pkmns on 2014-09-14
I have already checked the boot priority, I'm sorry I didn't specify that.
I just realized that the .exe I used to install yesterday is Wubi. I opened it and clicked Demo and Full Installation. Since rebooting didn't work, I picked "Help me to boot from CD". It installed Lubuntu (Again, sorry, I thought it simply installed a helper or something) and now each time I boot the PC I can choose between Win and Lubuntu (with Lubuntu getting stuck at that screen). 

Maybe I should try a non-Live distro? I'm okay with directly formatting the computer, I meant to do that after trying out Lubuntu, anyway.

---

### Post by lisati on 2014-09-14
You don't normally need to touch Wubi: most of the official downloadable installation CD/DVD images provide a "try Ubuntu without installing" option once burnt to disk or written to USB drive.

---

### Post by hakuna_matata on 2014-09-14
> **Pkmns said:**
> 
```
Try (hd0, 0): NTFS5: No wubildr.
```

This message is OK, if file wubildr is not on first partition of the first HDD/SSD.

But if it works, this line should not be the last line e.g.:
```

Try (hd0,0): NTFS5: no wubildr found
Try (hd0,1): NTFS5: no wubildr found
Try (hd1,0): NTFS5:

```
If a partition is not a DOS/Windows partition (e.g. a Linux partition with ext4), it terminates the search.

Maybe you have two installations. An install on real partitions and an install with Wubi.

If you can boot from a (L)ubuntu CD please open a terminal and type
```
sudo fdisk -l
```
and copy the result to your next post.

---

### Post by Pkmns on 2014-09-15
> **hakuna_matata said:**
> This message is OK, if file wubildr is not on first partition of the first HDD/SSD.

But if it works, this line should not be the last line e.g.:
```

Try (hd0,0): NTFS5: no wubildr found
Try (hd0,1): NTFS5: no wubildr found
Try (hd1,0): NTFS5:

```
If a partition is not a DOS/Windows partition (e.g. a Linux partition with ext4), it terminates the search.

Maybe you have two installations. An install on real partitions and an install with Wubi.

If you can boot from a (L)ubuntu CD please open a terminal and type
```
sudo fdisk -l
```
and copy the result to your next post.

There might be two installations, albeit both with Wubi, since the first time I installed it stopped halfway through as there was not enough free space on the HDD, so I uninstalled Lubuntu from the control panel, freed some space and then installed again. Maybe something's "left"?
The hard disk is not partitioned and there is no way to boot Lubuntu, it gets stuck on that screen.
Could formatting Win7 and then installing Lubuntu again help?

---

### Post by verymadpip on 2014-09-15
I was under the impression that wubi was defunct & consequently pretty much dead in the water.
I could be wrong.  It's not like that's never happened before.
I await for more knowledgeable persons to respond.

---

### Post by yancek on 2014-09-15
It's still available and shourl/could work on versions of windows before windows 8 according to the wubi site:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by craig10x on 2014-09-15
I thought Wubi was dropped from all versions  as of 13.04, wasn't it?

---

### Post by Pkmns on 2014-09-16
Soooo... What should I do? Could installing a clean Win7 do any good?

---

### Post by hakuna_matata on 2014-09-16
> **Pkmns said:**
> Soooo... What should I do? Could installing a clean Win7 do any good?
IMHO you have two possibilities:

) you analyze and repair current installation(s)
) you backup important data (if exists), discard all and install a clean Lubuntu
Hint: I installed Lubuntu with an external USB DVD drive on my Eee.

edit: If somebody should help you, in both cases [BootInfo]("https://help.ubuntu.com/community/Boot-Info") would be helpful

---

