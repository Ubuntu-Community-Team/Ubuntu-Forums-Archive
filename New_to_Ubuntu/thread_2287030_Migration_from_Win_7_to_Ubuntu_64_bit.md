---
title: "Migration from Win 7 to Ubuntu 64 bit"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by incurablegeek on 2015-07-16
I just returned from India where I am working on an IT project. With everything being done on Linux, I must make the leap - no more splashing around in the kiddie pool.

What I need to do: Migrate from Win 7 Ultimate 64 bit to Ubuntu Desktop 14/04.2.

Question: What do I do with files on my many hard drives that are in NTFS?

Note: All my computers have SSD's with the OS and Programs installed on the SSD - and the files on Western Digital Greens.

Do I need to move these files in NTFS to another computer with Win 7 and then bring them back into Linux formatted hard drives? Ugh! Hours and hours of work. Or can I convert from NTFS within Ubuntu without losing these files?

All my business is contained in these files and I cannot afford to lose them to an Oops.

Suggestions, anyone?

---

### Post by Bucky Ball on 2015-07-16
Doesn't matter what filesystem the files are stored on. It is about the files. Just drag and drop them from an NTFS filesystem partition to an EXT* filesystem partition. Not an issue.

Basically, install Ubuntu and that's it. Leave the WD Greens just as they are. Plug them in and there they are with your files on them. You may need to install ntfs-3g, but that is about it. If you want them on an EXT filesystem partition, just drag 'em over. That easy.

The issue is with Windows reading EXT partitions, not the other way around. Linux is quite comfortable with NTFS (and FAT) so don't panic. Carry on and post a new thread if you hit any brick walls or have any other questions.

Again, NTFS has nothing to do with the files themselves. A .doc file is always going to be a .doc file, doesn't matter where you store it. Having it on EXT or NTFS or FAT doesn't change it into anything but a .doc file. No effect on that.

Good luck. :)

---

### Post by howefield on 2015-07-16
> **incurablegeek said:**
> Question: What do I do with files on my many hard drives that are in NTFS?

You do with them exactly as you would in Windows. Ubuntu will read the files stored on an NTFS just fine with the caveat that you have an application capable of opening them.

> All my business is contained in these files and I cannot afford to lose them to an Oops.

That speaks more to your backup strategy than your choice of operating system ;)

---

### Post by dino99 on 2015-07-16
Ubuntu can read NTFS partitions via the ntfs-3g driver (installed by default)
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

---

### Post by Bucky Ball on 2015-07-16
> **dino99 said:**
> Ubuntu can read NTFS partitions via the ntfs-3g driver (installed by default)
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

And there you go. It appears you don't need to install ntfs-3g as I suggested you might. It is there by default.

So just plug in the WD greens once you're installed (if external, if internal already done, obviously) and carry on as you normally would.

---

### Post by toxx on 2015-07-16
Just in case everyone else is misunderstanding this query: if you mean to format your entire Win7 hard drive and install Linux instead, but keep the documents and files that you currently have on your windows install, You will have to backup the files you want to keep to the cloud or an external drive, then move them back after the install.

I have done this many times while re purposing old computers. It could be tedious to search for all the files you want to keep from your windows install, but certainly doesn't take *hours. *If you kept all your personal files in your user folder, you can just zip that up..

---

### Post by oldfred on 2015-07-16
Also are you keeping Windows & dual booting?

If not you need to consider converting data over time and must make a Windows repairCD or flash drive. Ubuntu automatically runs fsck on every 40 or 60 reboots on its ext4 partition. And you need to run chkdsk periodically or if issues with the NTFS partitions. And you cannot run chkdsk or make some other repairs from Linux. So only Windows repair console can run chkdsk.

       Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Geoffrey_Arndt on 2015-07-16
Just a couple of suggestions to build on the good advice already provided by forum members:   If not already installed, install  Windows 7zip - - top compression app & includes encrypt/decrypt option (AES256).   Then, if not already using, consider a Cloud provider like "Dropbox" that has excellent support for most Linux distros (especially those using Nautilus or a variation of that venerable file manager).

Then, compress your files (by folder) and encrypt those folders or files needed.   Drag those files into your local PC dropbox folder, and you're done with everything.   Once you have Ubuntu and Dropbox installed, all those files will be available in Nautilus and online.

Additionally, if you need extra Windows to Ubuntu connectivity, you can use Samba and other tools.

---

### Post by incurablegeek on 2015-07-16
Thank you so very much for all of your helpful responses. 

Although my mind is benumbed by jetlag, I am fighting to get moving quickly. Please allow me some time to digest all that you have sent me and then I hope to get back to you with more, hopefully relevant, questions.

OK, here is my quandary.

1) I have 5 computers, 1 of which will be my start-computer for Ubuntu. I also have a pfSense box for firewall.

2) Because I develop educational programs with various iterations of files stored, I have necessarily butted up against the long file-name restrictions of NTFS, such that if I simply move them, file names truncate to the point of being unrecognizable. Winzipping them would incur the same problem. Total: 65 TB of files to be moved.

My solution pending suggestions/objections from you more knowledgeable folks:

_Set up 1 computer as Ubuntu._ Note: all of my work must be done in Linux for my partners in India. Then prune the necessary files and import them one-by-one into the Ubuntu computer, with Linux formatted partitions. For temporary backup, I plan to have 2 X 3 TB WD HDD's in RAID 1. That computer will be an AMD 8-core, 16 GB RAM, but only 2 X 3 TB HDD's (in RAID 1 for backup) - with no cloud backup and no backup on the storage server which is currently on Win 7.

In short, I think all _this migration must be incremental_ lest I lose all my work - which is also backed up in the cloud with CrashPlan for which I have a migration policy to follow from CrashPlan. Unfortunately CrashPlan is on a computer which must remain on Win 7 due to all the GB's of critical files stored there and backed up by CrashPlan. My associate in India suggested I make a total jump with [http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

One heckuva ghastly problem. Am I on the right track?

---

### Post by oldfred on 2015-07-20
I am not knowledgeable on networking but use NFS to copy data from Desktop to laptop when I travel.

But I have seen that RAID should not be considered backup.
       [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I currently use rsync, but copy most critical data to DVDs and/or flash drives. But am reviewing converting to rdiff.
      
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[URL="http://www.kirya.net/articles/backups-using-rdiff-backup/"]http://www.kirya.net/articles/backups-using-rdiff-backup/
[/URL]
 [http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

[URL="http://www.kirya.net/articles/backups-using-rdiff-backup/"]
[/URL]

    [URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]
[/URL]

---

