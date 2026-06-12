---
title: "Thoughts on using WD My Passport 2.5&quot; as backup device on two different OS computers"
date: 2020-06-24
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2020-06-24
My wife has been using two Toshiba portable USB drives to back up her Ubuntu Mate 18.04 desktop and a win10 computer that she also uses. One is a 2T, the other is a 1T. She just added a 5T WD My Passport 2.5" portable and plans to use the 2T as a 2nd backup in case the new 5T goes toes up, and the 1T as a 2nd backup to back up the Windows computer.

First, the WD comes with two pre-installed packages:
1) Install Discovery for Mac.dmg
2) Install Discovery for Windows
but with not a word of explanation as to what they are for. Google reveals that they are disk management (encryption, and ?) and backup.

In googling for info on the programs, I found a lot of frustration that WD not only doesn't support Linux of any flavor, they seem to actively disavow any knowledge or, or interest in, using their drives with Linux. What's that about? Makes me wonder about WD as a hardware company. Anyway since one of hers is a Win10, would you recommend using the Discovery for Windows or is that likely to create problems with her linux desktop?

The drive mounts fine (best of my ability to tell) on the Ubuntu Mate desktop. She doesn't plan to encrypt it, so I am seeking guidance as to whether we should have any hesitation about using it with the linux machine? It is a NTFS which may or may not be ideal FS for either of these computers, so any recommendations on this also gratefully received.

AFAIK, it it mounts by itself, and files seem to copy to and from just fine, so seems OK to use, but doubtless there are members with some experience who might have guidance for the purposes above? Thanks in advance

---

### Post by TheFu on 2020-06-24
Non-SAS 2.5 inch drives are slow.  Avoid for system backups.  Stick with 3.5 inch drives that have external power for backups.

Only use encryption that is known to work with the OS you run.  For Windows, that means bitlocker or veracrypt.  For Linux, LUKS dm-crypt.  No way would i use software from WD. Just delete the files to get that space back.

Backup software needs to be automatic, daily, versioned and preferably "pull" by a server, not pushed and not directly connected.  "Pulled" means the malware infected clients can't harm the backups.

imho

---

### Post by Odyssey1942 on 2020-06-28
Thanks for yours. My comments between yours.

> **TheFu said:**
> Non-SAS 2.5 inch drives are slow.  Avoid for system backups.  Stick with 3.5 inch drives that have external power for backups.
 
O: Doubtless true, but we have this 2.5" drive for simple copy and paste backups which my wife is comfortable with. Not the most efficient backups but she doesn't want to know.....

Only use encryption that is known to work with the OS you run.  For Windows, that means bitlocker or veracrypt.  For Linux, LUKS dm-crypt.  No way would i use software from WD. Just delete the files to get that space back.

O: I am definitely persuaded as to your guidance on this.

Backup software needs to be automatic, daily, versioned and preferably "pull" by a server, not pushed and not directly connected.  "Pulled" means the malware infected clients can't harm the backups.

O: You just went over my head on this, but I will do a bit of research. The ideal system for me would be one that works as you advise and only updates files that have changed. If you have a URL or two in point that are not too technical, I would be much obliged. Thanks again.

imho

---

### Post by mastablasta on 2020-06-29
> **TheFu said:**
> Non-SAS 2.5 inch drives are slow.  Avoid for system backups.  Stick with 3.5 inch drives that have external power for backups.


that is very true. these 2.5 drives sometimes they last quite a while, sometimes they just stop working with no warning. we had a debate and i found out i wasn't alone in this experience. even when you are not using them if you need external drive (sometimes you do), use the one with added external PSU (large "WD Books" or "Samsungs" were good)

i still use 2.5." drives as secondary or temporary backup. the rest of backups are done on servers hat use more expensive, slower but more resilient drives (in RAID 1).

---

### Post by ActionParsnip on 2020-06-29
Bearing in mind that NTFS won't hold Linux ACLs so you'd need to make an archive you can extract from if you want to backup Linux files. If these are casual files (Images, videos, music ect) then back them up to NTFS but you may need to chown them to your user if you restore data.

---

