---
title: "mount.ntfs and samba high cpu usage."
date: 2014-12-05
forum: New to Ubuntu
---

### Post by rapid3642 on 2014-12-05
Hi i am running a ESXI 5.5 u2 OS with a Ubuntu 14.04 LTS virtual machine server. I recently bought 2 5TB external USB 3.0 hard drives, I shared them both with samba (one is the main nas and the second drive is to backup the main one). Now when these drives came shipped to me they were formatted in NTFS, I would like to keep them in this format however when copying a file over to the share drive the CPU usage goes to 100%! mount.ntfs is taking around 60-70%, and the smbd process is taking around 30-40% and my transfer speed suffers from this, i am only getting about 20MBs write, when i should be getting 60-70MBs write. Now here are a list of things i tried:

[LIST=1]
[*]Tried mounting NTFS with defaults in my fstab.
[*]Installed ntfs-3g and tried mounting the drive with ntfs-3g and with defualts.
[/LIST]

So i was thinking that maybe since this is a VM that i may be hitting limitations with the ESXI OS. So i reformatted one of the drives to EXT4 and then instantly got 60-70MBs write lol. also my processor usage went down but the smbd service was still high, it was taking up 60-70% of the CPU usage. I was no longer capping out but still high usage. after the transfer was complete then the CPU usage went down to normal idle around 6%. Thanks in advanced for anyone being able to help out.

---

### Post by rapid3642 on 2014-12-08
I tried unmounting the drive and formatting it and using the mount command in command line i let the OS mount the drive using defualts, i didnt specify defualts when mounting it. so i still had the same issue, so it doesnt seem like its a mounting issue.

---

