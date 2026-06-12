---
title: "ExFat vs NTFS"
date: 2022-05-17
forum: New to Ubuntu
---

### Post by jenniferx2x on 2022-05-17
Hey, I have windows and ubuntu. I can't very often save files from ubuntu on windows data ntfs partition because I hibernate windows and use fast boot there. Today was thinking what would happen if I convert one NTFS partition to exFat? Will I be able to always access it regardless of windows state? (I am talking about data partition, not the one on which windows is installed)

---

### Post by sudodus on 2022-05-17
You are right, it is a good idea to use a separate data partition. Then writing to it from either Ubuntu or Windows will not damage the system partitions of 'the other' operating system.

But it is very important to turn off Fast Startup in Windows. Otherwise Windows is closed without flushing the buffers and there might be 'dirty data' alias not completely written files, so that the other operating system will see a corrupt file system, and for that reason Linux refuses to write into it.

When Fast Startup is turned off, you can use whatever file system you want, provided that it can be read and written by both Ubuntu and Windows.

- The advantage of FAT32 is that it is small and fast, but there is a file size limit of 4 GiB.

- The advantage of NTFS is that it is well polished and debugged and there is a journal, that help keeping it healthy, even when there are some problems with writing. There is no file size limit.

- The advantage of exFAT is that it is modern (replacing FAT32 except for booting) and well suited for slow media. I think there is no journaling and this reduces wear of cheap media (e.g. USB pendrives), and there is no file size limit.

[hr][/hr]
I would suggest NTFS except for USB pendrives and memory cards. SSDs and HDDs can stand the extra write operations of the journaling.

I would suggest exFAT for USB pendrives and memory cards or if you want access to and from MacOS too.

---

### Post by yancek on 2022-05-17
I rarely use windows or exfat so I'm wondering if windows will hibernate other windows filesysems other than ntfs.  Have you verified this.  From the link below, it appears 3rd party software is needed to format exfat on an internal drive.  Have you investigated this?

[https://www.diskpart.com/articles/diskpart-format-exfat-1984.html](https://www.diskpart.com/articles/diskpart-format-exfat-1984.html)

If you dual boot with Linux, you will find doing that much simpler if you do not hbernate but that is your choice.

---

### Post by C.S.Cameron on 2022-05-18
I believe Ubuntu 20.04 needed an add on to see exFAT.
22.04 seems able to see exFAT right off the shelf.

---

### Post by seminiva on 2022-05-19
And what prevents you from formatting through the GUI in Windows? Why use third-party software or cmd ?

---

### Post by yancek on 2022-05-19
>  And what prevents you from formatting through the GUI in Windows? Why use third-party software or cmd ? 				

The link I posted in post 3 above indicates that it is possible to do from windows but the default windows softwware won't work on an external drive.  It would seem the OP is referring to an internal drive but can't be sure so that may not be a problem.

I think the question is does windows hibernate windows filesystem other than ntfs.  i did a brief online search but didn't come up with anything.

---

### Post by kurt18947 on 2022-05-19
Yes, having fast startup in Windows enabled is known to cause problems when trying to read an NTFS partition with Linux. It's possible to turn off fast startup in Windows. The problem is that a Windows update can re-enable fast startup without the user's knowledge. It's  possible I believe to prevent the unclean file system issues caused by fast startup by holding the shift key when shutting down Windows. The problem with that is remembering to hold the shift key each time. I wonder if there's a registry entry to disable the hybrid hibernation file(s) permanently but I don't use Windows enough to worry about it.

Edit: I was curious so did a quick search. There seems to be a Registry edit to permanently disable fast startup.```
 Either add the following to a .reg file:
  Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Power]
;TO UNBLOCK, SWITCH 0 TO 1 IN THE FOLLOWING:

"HiberbootEnabled"=dword:0
  or make a batch file (.BAT) with:
  reg add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /v HiberbootEnabled /t REG_DWORD /d "0" /f
ECHO The operation completed successfully.
  and drop it in a startup script/folder/task.
     

```
[https://superuser.com/questions/1146892/how-to-disable-fast-startup-permanently](https://superuser.com/questions/1146892/how-to-disable-fast-startup-permanently)

---

### Post by TheFu on 2022-05-19
I always choose a journaled file system over a non-journaled file system, except for cheaper flash media where write counts matter for lifetime.
Journaling is an amazing thing.  People forget how bad corruption was with non-journaled file systems. Data loss happened a bunch back then.  And if there were any issues, the fsck times could be days, not seconds for non-journaled storage.

NTFS is journaled.  exFAT is not.  

That's the answer, if a native Linux journaled file system cannot be used.  Of course, if the flash storage will only be used by Linux systems, then use f2fs. It is non-journaled to reduce write counts, but also supports native POSIX owner, group, permissions, ACLs ...

---

### Post by kurt18947 on 2022-05-27
> **C.S.Cameron said:**
> I believe Ubuntu 20.04 needed an add on to see exFAT.
22.04 seems able to see exFAT right off the shelf.

Yes Microsoft was willing to reveal enough about exFAT's internals that exFAT is now supported by recent kernels. I don't know at what kernel version exFAT became natively supported, obviously after 5.4 or whatever is used in Ubuntu 20.04.

---

### Post by green-eyed on 2022-05-27
I personally use fat32 on systems I move between Windows and Linux. But in a linux environment i try to stay 100% ZFS if possible.

---

