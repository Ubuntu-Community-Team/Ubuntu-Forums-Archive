---
title: "convert linux files to windows 11 files"
date: 2023-04-18
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2023-04-18
Some years ago I set up an Ubuntu-Mate computer for my wife, hoping to provide her with as much native protection from scammers, etc as possible. She has been happily using it, but for a good reason (employer related) I continued to use Windows (now 11).

It is time to replace her aging computer and she wants to convert back to Windows before I kick the bucket (hopefully not any time soon). Lots of good reasons for her to do so, including that my recollection of linux has faded in my aging (80 year old) brain. Of course we must transfer her entire linux personal files to the new computer.

I remember enough about linux to expect that file permissions will be a problem unless the transfer is done properly. However, I never understood file permissions and have no idea how to prepare them for permanent use on her new windows computer, which we have not bought yet.

Keeping in mind that I am still very much a noobie, how might I go about transferring her linux files to the new computer. Step by step please and if possible avoiding the command line as I remember very little about how to use it. If the command line is required, it will definitely need to be line by line.

Your kindness in assisting with this will be greatly appreciated.

---

### Post by Holger_Gehrke on 2023-04-18
Permissions are not going to be a problem, just put the files on a USB flash drive formatted with FAT32 (that file system can't store permissions and Linux therefore doesn't even try to set any) on the Ubuntu system and copy them to the Windows machine.

A potential trouble point is her email archive. Depending on what program she uses on Ubuntu this could be trivial (if using a program that also exists on windows like for example Thunderbird) or quite difficult ...

Holger

---

### Post by Odyssey1942 on 2023-04-18
Holger, thanks for your most welcome information.

She uses gmail so it sounds from yours that this will also not be an issue?

---

### Post by BBQdave on 2023-04-18
> **Holger_Gehrke said:**
> Permissions are not going to be a problem, just put the files on a USB flash drive formatted with FAT32...

+1 and exactly how I make files accessible to my family on Windows.

I would further offer, that backing up to FAT32 makes life simple. If another family member needs access to my data, plug in the USB hard drive and data readily available.

The use of Gmail and the available suite of applications with Chrome and Gdrive, makes data access and sharing simple too.

Note: the data I share is non-sensitive.

---

### Post by yancek on 2023-04-19
>  my aging (80 year old) brain

Nice to see someone actually older than I am (barely).  There are countless sites explaining Linux permissions online such as the one at the link below if you care to read it.  A bit pointless I guess if you are going back to windows.

 [https://www.linuxfoundation.org/blog/blog/classic-sysadmin-understanding-linux-file-permissions](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-understanding-linux-file-permissions)

Linux permissions are meaningless on a windows system as they are not understood.  I'd agree the method suggested above will probably be simplest.

---

### Post by Odyssey1942 on 2023-04-19
Thanks for these.

My wife keeps a couple of USB backup drives, both of which are NTFS. 

With respect to continuing future use of these USB drives as backups:

should I copy the contents from the backup drives to her linux computer now, reformat the USB drives as FAT, then copy the files back, 

or can I just copy the files onto the new Win 11 computer, reformat the USB's and copy the files back, 

or can Win 11 read and write to NTFS therefore nothing needed to be done? 

And what is safest way to do whatever might need doing? TIA

---

### Post by Holger_Gehrke on 2023-04-19
> **Odyssey1942 said:**
> 
or can Win 11 read and write to NTFS therefore nothing needed to be done? 


Exactly. NTFS is the native file system of all versions of Windows NT since  Version 3.1 in 1993. If Windows 11 - which is the newest iteration of  the Windows NT line - could not just work with it it would have been  major news ...

So yes, Windows 11 should read and write NTFS just  fine - actually it can even repair NTFS file systems which have logical  errors, something which Linux based Operating Systems can't do - and  you should not need to do anything to those backup drives.

Holger

---

### Post by MAFoElffen on 2023-04-19
I do multi-boot... Meaning computers that boot optionally to Linux, Unix, Windows, MAC OSX, etc.

I use NTFS as the common filesystem for shared data between OS'es. Nothing needs to be done for Windows to use it.

---

### Post by TheFu on 2023-04-19
Unless you have specific hardware devices like an old camera or really old phone, there's no reason to use FAT32 in 2023. ExFAT has replaced it and is a much better file system for Windows use on flash media - like USB flash "thumb drives" and SDHC storage cards.

FAT32 and ExFAT shouldn't be used on normal SSDs or spinning HDDs.  NTFS is the better choice for a number of reasons, if you are limited to MS-Windows.  NTFS is a journaled file system, which is much safer than non-journaled file systems like ExFAT/FAT32/FAT16.

For flash media like SDHC/microSD or "thumb" drives that will only be used on Linux, f2fs is my choice rather than exFAT.  f2fs supports all the POSIX standards, which include Unix permissions and ACLs.  f2fs isn't available by default, but installing **f2fs-tools** fixes that.  f2fs tests show it to be fast. It compares well to ext4.  Performance tests with comparisons are available online, if you are interested.

---

### Post by Odyssey1942 on 2023-04-20
All great news! Thanks for the helpful guidance.

---

### Post by mIk3_08 on 2023-04-21
> **Odyssey1942 said:**
> All great news! Thanks for the helpful guidance.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

