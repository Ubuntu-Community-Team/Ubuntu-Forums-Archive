---
title: "Full system restore using Tar backup file"
date: 2018-04-19
forum: New to Ubuntu
---

### Post by trish.h on 2018-04-19
Hey!

I've been working on setting up automated backups using anacron and tar and have got all of the backing up working. Now the next part is being able to restore my system from the backup, and so I followed the steps in the same guide that I used to get the backup working: 

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Because I don't really have anything important on my system yet, I basically stored my backup on my HDD, which is only running as storage, booted on a live USB and wiped my system SSD clean. Next, I partitioned and formatted one single ext4 partition, extracted my tar backup on to it. In my former mind, I was thinking that I was done and that my system would just boot from there. Of it did not, and as I understand it, it is because my GRUB does not exist OR is not configured properly. Would love to find out which one of those are true. So next, I actually read the "restore" part of the guide linked above, and after wiping the system drive again, making an ext4 partition and extracting the tar backup again, I followed these specified steps from the guide: 
sudo -s
for f in dev dev/pts proc ; do mount --bind /$f /media/whatever/$f ; done
chroot /media/whatever
dpkg-reconfigure grub-pc

Once again, it did not work out as I intended, and instead of "You will get a menu asking you what drive(s) grub should be installed  on.  Choose whatever drive(s) the computer will be booting from.", I got an error saying that the package grub-pc did not exist, or something along those lines. I could find out what exactly was the entire error message if it's needed.

Either way, I really want to understand what GRUB is and how I can manually install and configure it to my liking. I've searching for information on it, but all I've found so far has been either outdated or just doesn't seem to apply to my installation for some reason. For example, one article I read stated that there should be a menu.lst in /boot, and I do not have one there.

I'm fairly sure my installation should boot using UEFI, as I have had CSM disabled in motherboard settings during and after Ubuntu installation. 

I'm sorry if this post just looks like a mess and that I have no idea what I'm doing, but if there is something I clearly have misunderstood, I would be grateful for any links offering explanations.

---

### Post by TheFu on 2018-04-19
Hi and welcome to the forums!

Good work on doing backups and setting up a process.

IMHO ... 

**Tar is a terrible backup tool.** Pretty much **anything** would be better.  tar was created when 50MB (not GB) was huge storage. Using tar for anything over 500MB of data is crazy.  Tar is like ZIP. Would you try to make a complete system backup using zip?

duplicity or rdiff-backup or back-in-time would all be better backup tools, IMHO. Backup tools should do these things:
* fast to complete (1-5 minutes per system per day)
* automatic
* versioned (30 - 120 days of daily backups
* retain ownership, groups and permissions
* efficient (storage and network use)
* encrypted (transfer and storage)
* verified
* never use network storage for backups (avoid crypto-malware)

Image-like backups (partimage/dd/tar/rsync) all lack the versioning.

Basically, a backup tool should let you restore a backup from last night or last week or last month with minimal issues.

Onto your questions about grub.

While you can boot off flash media, setup a chroot and do a **grub-install** and **update-grub** to get it placed, that is a wee bit of hassle. It doesn't easily handle encrypted partitions, so more complex, manual steps are necessary.  The setup for grub in a legacy BIOS system is different from the setup for UEFI.  For UEFI, there is a FAT32 partition where a grubx64.ef boot file has to be located.  Different systems will handle the /boot/efi/EFI/ and below directories differently.  My chromebook required that I manually move the files to a different location because the BIOS for it only looks 1 place, which is different from other systems.  Some HP computers are picky too and require manual intervention to successfully boot with EFI.

Not that anyone cares, but I do backups a little differently for a few reasons. 
* I do *not* backup the core OS.
* I do backup data, lists of installed packages, system and personal settings.
* My restore process begins by performing a fresh install of the OS with minimal setup (usually just an ssh-server)
* Next I restore /etc/, /home/, and any server data (DBs, websites, nextcloud, wallabag, zimbra, etc).
* Last I take a list of installed packages created just prior to making daily backups, and install those.  They see the prior settings, accept those settings. They see the prior data and accept it. The restored system isn't 100% bit-for-bit identical, but the data and settings are.  It also saves about 4GB of backup data per machine.

My restore process takes about 30-45 minutes.  15 minutes to install the fresh server/desktop, and 15-30 minutes to restore most data.  This skips the grub-install stuff.  It also handles complexities that aren't addressed with encrypted partitions using LVM.

Media files are something I backup separately. Because they are so huge, versioning isn't practical. But having at least 1 other copy is worth my time and cost. I didn't always think that way, then I ran the numbers about effort to recreate it and decided that $150 for a 4-8TB backup disk was worth it.

I use rdiff-backup.  My main desktop has 20G of storage connected. 
```
$ df
Filesystem          Size  Used Avail Use% Mounted on
/dev/vda1            20G   16G  3.0G  84% /
```

Here's a summary report about the different versions that it has:```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Apr 15 01:15:07 2018         6.49 GB           6.49 GB   (current mirror)
Sat Apr 14 01:15:06 2018         19.6 MB           6.51 GB
Fri Apr 13 01:15:06 2018         19.3 MB           6.53 GB
Thu Apr 12 01:15:06 2018         23.4 MB           6.55 GB
Wed Apr 11 01:15:05 2018         9.24 MB           6.56 GB
Tue Apr 10 01:15:06 2018         21.7 MB           6.58 GB
...
Mon Mar 26 01:15:06 2018         2.25 MB           6.88 GB
Sun Mar 25 01:15:06 2018         8.01 MB           6.89 GB
Sat Mar 24 01:15:05 2018         55.0 MB           6.94 GB
```
So, that's 30 days of daily, versioned backups.  The current amount of storage that I backup for the system is 6.5G. The total size for 30 days of versioned backups is 6.94G - 500MB more storage for 30 more days of versioned backups?  I call that a no-brainer.  Last night the backup took ... 
```
ElapsedTime 306.49 (5 minutes 6.49 seconds)
```

My nextcloud/wallabag server, has 6.69G of data in the backup and 90 days of daily backups because it sits on the internet and is much higher risk. Total storage used is 7.25G.  BARGAIN!  Last night the backup took 
```
ElapsedTime 205.86 (3 minutes 25.86 seconds)
```

There are 20 other systems here with similar backup information - which might clarify also why NOT backing up the core OS saves lots of storage and time.
My tool of choice, rdiff-backup, certainly isn't perfect.

Why bother with encryption?  Because HDDs fail and if warranty service of the HDD is needed, I really don't want to worry about the returned disk having sensitive data on it.

Anyway, hope this is helpful. The exact way that you do backups isn't nearly as important as the big ideas around  doing them, versioning, and automatic processes. There are lots of great backup tools, so don't take my short list as me trying to slight some of the other tools.  

Hopefully, others will chime in.

---

### Post by Quarkrad on 2018-04-20
Sorry to hijack this thread but I have a couple of questions on rdiff-backup I cannot find an answer to.  Without going into detail, I only need 1 or 2 versioned copies - how do you limit the number of versions created (what is the addition to the script)?   Last question - I have managed to link rdiff-backup with systemd so my backup happens when I shut down.  This is working OK using the command **rdiff-backup /home/dad/.mozilla /media/dad/backup/rdiff** - what I would like to do is amend the script so that I backup .thunderbird as well as .mozilla. Any help appreciated.

---

### Post by wildmanne39 on 2018-04-20
Hello Quarkrad, please start your own thread so you and the OP of this thread can get the help you both need.

Thanks

---

### Post by trish.h on 2018-04-20
Thanks a lot for the input!

I guess I like Tar because it's a simple concept that I understand, but as you say, maybe it isn't the most amazing way to back up. I'll look into some other tools. I also really like your point about not saving the entire system. Installing Ubuntu, as you say, only takes about 15 minutes, so just doing that and then restoring your personal files later seems great! The only trouble for me is I don't yet understand how packages are installed and configured completely, so I worry about there being conflicts and stuff, and about backing up only part of a program's files: Say for example a program that for some reason stores it's files partially in /etc and partially in some other directory. If I don't back up the whole system, I'm afraid I'll miss one of the directories, and the program just wont work properly after the restoration. That's sort of why I originally wanted to back up everything on the system, so that I could just restore everything, and then the whole system would be just like it was before a drive failure or whatever. 

Either way, thanks again, I'll check out some more backup tools!

---

### Post by TheFu on 2018-04-20
If you are a typical desktop end-user, something like **Aptik** might be all you need for backups if moving to new storage. There should be a PPA. I've never used it. I don't think it does versioning, so it is useless to me. Plus it is designed for single-user backups, so maintaining permissions really isn't handled in the way I'd want.

There is no need to backup these places, if you will reinstall the OS.
* /bin
* /usr
* /lib*
* /boot
* /proc
* /sys
* /dev
* /run

You do need to backup these places:
* /home
* /etc
* /usr/local/*
* parts of /var/ ... if you have websites, DBMS, virtual machines there.

If you run a web server or DBMS, then you'll know where those data files are located. The locations are listed in config files under /etc/.

All personal settings for each userid are stored in their HOME directories. That location is spelled out in the password entry, which is usually in /etc/passwd file, but might be stored in an LDAP directory server. If you didn't setup LDAP, it isn't used.

To get a list of manually installed packages, check out apt-mark.   APT manages dependencies, unless you manually install .deb files outside using a package manager. If you manually install source-code tools, those should be placed into /usr/local/ .. which is why that area needs to be backed up.

If you mount extra storage, you'll know where that is (hopefully never under /mnt/ or /media/ ) and can backup those locations as needed too.  While you can use storage anyway you like, following the normal standards really is helpful. Lots of very smart people came before us. ;)

Nothing can replace fully testing the backups and restore procedures.  It took me about 3-5 attempts to get everything needed.
For what things are stored where,  there is a standard which all Linux distros should follow. I'm positive the major distros do.  Google "Linux File System Hierarchy" for that standard.  Usually there is a table with a summary, which is all I've ever needed.

Hopefully, that clarifies things.

And don't feel bad about backing up everything.  If I'm moving disks, I will do it that way too.  I haven't used tar in over a decade, perhaps 2, except when I needed to transfer entire structures (with permissions/owners/groups) on non-Linux formatted storage, like fat32.

---

### Post by trish.h on 2018-04-20
That does clarify a lot! 

Thanks a ton!

---

