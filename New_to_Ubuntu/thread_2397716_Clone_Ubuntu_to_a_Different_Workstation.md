---
title: "Clone Ubuntu to a Different Workstation"
date: 2018-08-02
forum: New to Ubuntu
---

### Post by giobaxx on 2018-08-02
Hello 

We had a request to clone an Ubuntu Workstation to Laptop. I Windows is almost impossible to make a clone to a Workstation make it run in a different model. From what i have understood linux it does not have this issue correct?

Apart this, we proposed to reinstall a fresh ubuntu to a Laptop because we don't have disk so big as he has in his WS to be cloned , but the guy told us that his workstation has same strange configuration, he had installed lots of packages/librabries with dependencies that needs week before reconfigure correctly. So it's possible to get the whole list of packages and dependencies installed from and old Workstation  to be copied and reinstalled to a fresh one?

---

### Post by TheFu on 2018-08-02
Ask for the installation documentation for each of the "strange configuration" items.  Without that you can't promise anything.  The person who did it should create that documentation.

Backup and restore.
Fix the boot and fstab.

Or
clone the disk. This requires that the target be the same size or larger than the source disk- unless you use **fsarchiver** and manually deal with the partitioning. fsarchiver can backup whole partitions and if the actual data on them is smaller, it can restore to other, smaller, partitions on a different disk.

Or 
Backup user data (almost always in /home/ )
Use **aptik** to backup lists of packages, repos, themes and restore those onto a freshly installed version on the laptop.

Or
There are 50 other ways.   User settings are kept inside each user's HOME.   **apt-mark** or **dpkg --get-selections** can be used. Copy the list of packages to the new system and use that to script adding them all back there.  **dpkg --set-selections** is one way. It can read the output from --get-selections, but it gets ALL the installed packages, not just those manually installed.  That's where **apt-mark** can be better.

It takes me about 45 minutes to move between systems. When I'm done, it **is** the same system. Same programs. Same settings. How I do it depends on why I'm moving.  If I can pull the HDD and physically move it, that is the easiest.  If I only have my daily backups, then I follow the restore process.  If I have time, I'll use sfdisk to clone the partition tables (if MBR) or parted (if GPT) exporting in "machine readable" text, then use that to recreate the same layout on the new disk.  Next, I'd use rsync, fsarchiver or ddrescue (which I prefer over dd) to get the bits from system A to system B. fsarchiver and dd-based tools don't need the file system created manually first, but rsync does.  **mkfs** is the command for that.  It can seem overwhelming at first, but if you think through the steps, it all makes perfect sense.
* make partition table, fill with values/sizes/types that are needed
* make file systems as needed
* copy bits into file systems.
* correct/fix any changes due to fstab differences.  Partitions usually get different UUIDs which are used for mounting.
If LVM is used, there are 3 more layers between the partition creation and file system creation to add much more flexibility.  With LVM, lots of amazing things are possible, but it needs to be put in either before installation or during OS installation. The ability to resize actively used file systems while running it pretty great.  Having perfect backups while databases are very active is another nice thing that LVM snapshots allow.

Sometimes there are problems do to poor package dependency management.  Installing .deb files manually, outside APT, is a common problem.  Also, if anyone manually installed software outside any package management, that will be lost unless manual steps are taken.  Only the person/people who did those installs will know where they were placed.  If all software was installed using apt-get/synaptic/aptitude or one of the other package managers only using reputable repositories.

There are at least 50 different threads in these forums for more data on this.

The good news is that if the files appear to be in the correct places on the system, then that is all that matters. The details about how that happens behind the directory layout doesn't matter. You can swap out file system types, use LVs (logical volumes), use NFS, as long as the files and directories "appear" in the correct place.

If you are switching from legacy boot to EFI boot,  things get more complicated.

The clone disk method is the most bonehead.
The aptik method is pretty easy, but will miss things if the system has manual modifications outside the "expected" locations.  There are standards for where things should be located, but non-professionals might not know that and put things in odd, unexpected places.

---

### Post by sudodus on 2018-08-02
1. Cloning works if and only if the target drive is at least as big as the source drive, not one single byte smaller.

Such 'proper' cloning can be done in a convenient way with [Clonezilla](http://clonezilla.org)


2. If the target drive is smaller, there are workarounds. You can shrink the partitions so that the tail ends of all partitions are within the size of the target drive. Then you can clone and if there is a GUID partition table repair the backup partition table at the end of the target drive.

You can clone 'manually' with a dangerous **dd** command line. So **check and double-check**, that everything is correct before pressing the Enter key. It is easy to get it wrong, and that might destroy your family pictures or other valuable data. It is best to make sure that all connected drives have backups, that are not connected. **No partitions** on the source drive and target drive should be **mounted**.

```

sudo dd if=/dev/sdx of=/dev/sdy bs=4096
sync

```

where x is the drive letter of the source drive and y is the drive letter of the target drive.


3. Another method is to copy the source system to the target drive at the file level, to create partitions and for example use rsync for the copying,

```

sudo rsync source/ target

```

You must also match the content of the **/etc/fstab** file with the **UUID**s in the target system, and you must install the **grub bootloader**. It works (I have done it more than once), but can be somewhat tricky to get everything right.

---

### Post by HermanAB on 2018-08-02
The official way to clone an installation to different hardware is to use Preseed:
[https://wiki.debian.org/DebianInstaller/Preseed](https://wiki.debian.org/DebianInstaller/Preseed)

If done right, you can install thousands of dissimilar machines in no time.

---

### Post by monkeybrain20122 on 2018-08-02
Use [fsarchiver]("http://www.fsarchiver.org/quickstart/"), it is fast and clean  (file system copying basically) and can do live cloning (without stopping your computer) by using the -a -A options in savefs (command: sudo savefs -a -A ....)It is in the repo. I have cp OS from one machine to the other this way many times. If you are cloning the whole system (without having to exclude directories) there is an even easier to use [gui]("https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver"). The things to look out for are graphic driver and grub. If your original system uses a proprietary graphic driver different from one you would be using in the targeted machine, uninstall it and revert to the open driver before you clone (then reinstall afterwards in the original system) You may need to reinstall grub restoring to the targeted machine if say target uses uefi while source machine uses bios, this can be done easily with a ubuntu live usb.

I wouldn't use dd.

---

### Post by TheFu on 2018-08-02
```
$ savefs
savefs: command not found
```
Could it be the option to fsarchiver?

When I've  read the manpages for fsarchiver, it doesn't quiesce the file system, so to get a clean backup, without crossing our fingers (which doesn't actually work) to avoid file corruption, we'd need to boot from alternate media or use LVM snapshots or have any partition to be backed up, mounted read-only.

From the project website [http://www.fsarchiver.org/live-backup/](http://www.fsarchiver.org/live-backup/)
> Backup with no snapshot
If your partition are not LVM Logical-Volumes, you can&#8217;t make a snapshot. If the partition are not used, it&#8217;s recommended to remount it as read-only,
...
When a filesystem is writeable during the backup, it means changes can be done in files during that time, and there may be inconsistencies in the data. For instance, if you are backing up a web server which is running both Apache and Mysql, the Mysql database refers to files that can be uploaded in the Apache directory from the website. In that case the backup could contains a reference in the database but not the referred file because these files have been backed up already. So you have to know whether or not your system may have such inconsistencies.

Be afraid is you attempt to backup a read-write mounted, active, file systems.  PLEASE. Data corruption is just a matter of time.

fsarchiver is a great tool, but isn't doesn't have any magic.

---

### Post by HermanAB on 2018-08-05
A simple copy f the disk will only work IIF the other machine is EXACTLY the same.  You cannot clone a desktop to a laptop or a Dell to a HP etc.  

To do what you want, you need to create a package list and use Preseed (the Debian equivalent of Red Hat Kickstart).

---

### Post by oldrocker99 on 2018-08-05
I personally use grsync, which works beautifully for me.

Of course, this being Linux, you have a choice.

Freedom!

---

### Post by monkeybrain20122 on 2018-08-05
> **HermanAB said:**
> A simple copy f the disk will only work IIF the other machine is EXACTLY the same.  You cannot clone a desktop to a laptop or a Dell to a HP etc.  

To do what you want, you need to create a package list and use Preseed (the Debian equivalent of Red Hat Kickstart).

Not true. I have moved my system  between laptops of different manufactures many,  many times and I use fsarchiver which copies. I have no desktop, but have booted  cloned laptop systems off a few  desktops at work with different manufacturers with no issue (clone to an external hd) Only thing that doesn't work is Mac (but I haven't tried very hard)

---

### Post by TheFu on 2018-08-05
> **monkeybrain20122 said:**
> Not true. I have moved my system  between laptops of different manufactures many,  many times and I use fsarchiver which copies. I have no desktop, but have booted  cloned laptop systems off a few  desktops at work with different manufacturers with no issue (clone to an external hd) Only thing that doesn't work is Mac (but I haven't tried very hard)

I've moved many systems between different ones over the years. Just had to remove any incompatible proprietary video drivers before the move.

I suspect UEFI might make this a little harder, since some vendors still don't follow the UEFI boot standards, but those can be fixed (with more effort than most new-to-linux people would like). Probably wouldn't be to hard for any of the people replying here.

I prefer to do a fresh install, then restore data, settings, and package lists to be installed from backups myself. Lists of packages can be made from **dpkg --get-selections** or **apt-mark**, easy-peasy. 
In the last 2 weeks, in these forums, someone posted that they pulled an SSD from a Windows system that had an Ubuntu dual boot setup and put it into a MAC then booted fine. Not sure I believe the poster, but maybe it did work?  IDK.

---

### Post by HermanAB on 2018-08-05
Yes, of course a straight copy works - except for all the things that require different device drivers... 

However, if you want the device driver problem sorted also, then you have to use preseed/kickstart, which will do so automagically.

Here is how:
[https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html](https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html)
[https://www.aeronetworks.ca/2014/06/replicating-fedora-machines-using.html](https://www.aeronetworks.ca/2014/06/replicating-fedora-machines-using.html)

---

### Post by TheFu on 2018-08-06
You'll never know if you don't try.  Hope for the best, but be prepared for the worst.  HermanAB has lots of experience and probably has been burned.  The rest of us where it worked, might simply have been lucky.

In my experience, it is only the difficult devices which cause problems, so if you stick with normal, expected devices that are automatically recognized, those problems go away.  At boot inside the new system, the different HW is recognized and configured automatically, for common devices.

Things that have worked without issues:
* Almost all onboard storage controllers
* Intel NICs (PRO/1000 line)
* Intel iGPUs (built into Corei3/5/7 and Pentium/Celerion CPUs)
* "normal" audio chips on motherboards (intel versions)
* JBOD use from popular RAID cards (not the HW-RAID setup). I've been using SW-RAID since the early 2000s and it "just works"
* normal USB mice with legacy USB support enabled.

I suppose of you have an odd mix of touchpads or gaming things with unusual drivers, those would need help.  Same for wifi? I don't use wifi at home with computers, ever.

---

