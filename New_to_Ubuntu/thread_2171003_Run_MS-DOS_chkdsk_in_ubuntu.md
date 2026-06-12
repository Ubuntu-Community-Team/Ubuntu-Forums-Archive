---
title: "Run MS-DOS chkdsk in ubuntu"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by Hankbonk on 2013-08-28
Can I run the chkdsk command (DOS) in ubuntu ?  And how ?

---

### Post by Bashing-om on 2013-08-28
Hankbonk; Hi !

Short answer, no. As the files system formats are different.
'buntu file system check is "fsck" ->File System Check" that relies on the utility e2fsck for the ext? family of formats.

What do you need to check so we can give better advise.

[INDENT][INDENT][INDENT]just try'n to help
[/INDENT][/INDENT][/INDENT]

---

### Post by lisati on 2013-08-28
Depending on what you're wanting to do, I'd recommend looking into one of the equivalents available for Ubuntu. If you're wanting to check your Ubuntu partition, one of the safer options for a beginner is to open up a terminal, and type the following:
```

sudo touch /forcefsck

```
What this will do is tell your system to run a **F**ile **S**ystem **C**hec**K** the next time you boot.

Some information of file system troubleshooting can be found here: [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

### Post by SeijiSensei on 2013-08-28
If your asking about how to run chkdsk against a DOS drive like a USB stick from Ubuntu, you can use fsck with the "vfat" option.  Plug the drive into the machine.  If you only have one disk in the computer, the stick will probably be assigned to /dev/sdb.  The first (and probably only) partition on the device will then be /dev/sdb1.  If you open a Terminal and run the command "sudo tail -f /var/log/syslog" then plug in the drive, you'll see what device it is assigned to.

To run a filesystem check, run the command

```
sudo fsck -t vfat /dev/sdb1
```

However if you have something formatted with NTFS, I'd use Windows chkdsk to examine that.

---

### Post by Hankbonk on 2013-08-28
I have a Windows XP that has gone totally corrupt, and that doesn't run the needed chkdsk at reboot .  I have an ubuntu 9.04 jaunty version on disk .  In a 'Running Linux' book there's somthing mentioned as "dosemu" to emulate a MS-DOS interface, but it's a very complicated explanation .  I simply need to run the chkdsk /f DOS command, but I don't know how !!!

---

### Post by SeijiSensei on 2013-08-28
The chkdsk command for DOS won't be able to check an NTFS partition like that used by Windows XP.  You might try installing **testdisk** from the repositories and giving that a try.

---

### Post by VMC on 2013-08-28
Kubuntu has their own partition editor that I use on my Windows NTFS, and to my surprise it analyzed, reported and wanted fix the errors.  I canceled the reply and was going to find out what exactly what it was doing. I haven't since used it. Thanks for the topic, I'll test that out again.

---

### Post by Mark Phelps on 2013-08-29
The Minitool Partition Wizard boot CD, whose ISO can be downloaded for free, is a Windows utility disk that can run CHKDSK without having to boot into Windows.

You should try that if you can't get into Windows to run CHKDSK.

And sorry, there is no Linux equivalent of CHKDSK for NTFS.

---

### Post by Hankbonk on 2013-10-07
Dear SeijiSensei,

I'm really a beginner in Ubuntu Linux .  Could you specify step by step how to install that **testdisk** ?

---

### Post by Hankbonk on 2013-10-07
Dear Mark Phelps,

 I found that 'Minitool Partition Wizard' .  Is this a Windows or a Linux tool ?

---

### Post by oldfred on 2013-10-07
@hankbonk
Better to start your own thread with your issues.

These are Windows tools.
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

Testdisk is primarily a Linux tool which may overlap some functions with the above Windows tools
From Ubuntu terminal you can directly install from repository. Or Testdisk is on many Linux repairCDs.
```

sudo apt-get install testdisk
```
      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by newb85 on 2013-10-07
> **Hankbonk said:**
> Dear SeijiSensei,

I'm really a beginner in Ubuntu Linux .  Could you specify step by step how to install that **testdisk** ?

First of all, you're probably best off *not* using a release that has reached it's End-of-Life, like Jaunty.  (It would be possible to use Jaunty, but that would require somewhat involved steps to change to software sources, and it would leave you with a version of testdisk that hasn't been updated since at least as far back as October 2010.)

I would suggest you download 12.04, as it will be supported through April 2017.  If you're just looking to use it for computer administration or things like testdisk, it will be a faster download (and run a little faster on your system) if you go with Lubuntu instead.

Once you've booted from the 12.04 install media (CD/DVD/USB) and connected to the internet, open a terminal emulator window.  In Ubuntu, Ctrl+Alt+T will accomplish this.  In Lubuntu, I believe it's Applications>Accessories>Terminal.  Running the commands should install testdisk from the Ubuntu repositories.
```
sudo apt-get update
sudo apt-get install -y testdisk
```

Once it's installed, it looks like testdisk is run from the terminal, as well.  I have no experience using it, but it looks like there's a detailed tutorial here.  [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)  Notice it says you need to have root privileges, so you'll need to prepend testdisk commands with sudo.

---

### Post by newb85 on 2013-10-07
> **oldfred said:**
> @hankbonk
Better to start your own thread with your issues.


Hmm...I'm pretty sure hankbonk *did* start this thread for these issues...

---

### Post by oldfred on 2013-10-07
oldfred has really lost it. :)

---

### Post by Hankbonk on 2013-10-07
Dear Bashing-om,

When I run the chkdsk in Windows in a dos prompt, it states that it will perform a chkdsk with the next (re-)boot, but due to tha fact the file system is RAW, it doesn't do that .  And I get a lot of errors when I reboot Windows XP : "File /.../x.y is unreadable and corrupted" !

---

### Post by Hankbonk on 2013-10-07
Dear newb85,

I have allready installed and ran testdisk : It doesn't give errors on all HDD's I have !

---

### Post by Hankbonk on 2013-10-07
Dear Bashing-om,

   I allways have errors when I boot up Windows XP : " File /..../.../x.y is corrupted and unreadable".  I have tried many times to run the chkdsk utility from a DOS-prompt, but normally that chkdsk should then run with the next boot in Windows, but it doesn't, specifying "Chkdsk can nit run on RAW file system", you see ?

---

### Post by Hankbonk on 2013-10-07
Dear lisati,

I've tried it, it does run a file check on a ubuntu boot, but doesn't that only check the Linux part of the PC ?  I think so !

---

### Post by oldfred on 2013-10-07
RAW means it sees the partition as unformatted. NTFS has info in the PBR  or partition boot sector that has what boot loader to use and start & size of partition.
If really a NTFS partition that lost its partition info or you overwrote with grub2's boot loader you can use testdisk to restore the backup. If backup is also bad, testdisk can create a default NTFS PBR. It creates a XP type which is different than Vista/7/8 type, but if XP type seen then you can run chkdsk from the newer version and it will update the PBR.

This was if grub overwrote PBR, but works or any issue as long as backup is good.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
Note in above, if backup not valid, then use the [Rebuild BS] which creates a new PBR or partition boot sector. 

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by Hankbonk on 2013-11-06
Thanks oldfred, seems I got a lot of work to do .  Sorry for my late reply, I was concerned in other matters .

---

