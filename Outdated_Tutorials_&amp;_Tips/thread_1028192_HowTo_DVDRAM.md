---
title: "HowTo DVDRAM"
date: 2009-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by BigJules on 2009-01-02
[Tested on Gutsy, Hardy and Intrepid]

The cinderella of Ubuntu must be dvd-ram. It is quite unique, a dvd that the system treats transparently like any other file system, complete with read, write and rewrite, permissions and all the rest without the need of an iso file or other. Therefore it can be used directly with Nautilus, drag & drop, rename and so on. Its ready to use now - any dvd writer bought in the last few years has probably got dvd-ram read/write capability built-in already, 

Dvd-ram has had a bad press, which in the main has been caused by a desperate lack of documentation, leading to urban myths about its reliability and place in the Linux world, only some of which is deserved. This HowTo is written by a user, not a geek, and tries to show that in fact it can be damn useful.

Apart from acting like a giant floppy, one real utility lies in the combination of dvd-ram and rsync - I have a row of disks behind my monitor. Each one has on it a complete 3.5 GB snapshot of my entire data set, taken at succeeding intervals. This means I have (a) a local off-line, precise backup in standard file format (b) generations of backups going back in time, so the file that got deleted back then can be easily retrieved from somewhere. And the miracle is that the operation seldom takes more than a few minutes!

**This HowTo** is in two parts: setup and its use in such a backup. 

***Setup.***
This need only be done once. It will provide a reliable disk that Ubuntu will see as a seamless extension of its file structure, usually at /media/cdrom0. 

**You will need:** a dvd-ram rewriter. If you don't have one, a fast SATA model all in one DVD +/-, ROM/RAM are now selling for about $30-40. The three I've had over the years all do a good job. Media: non-cartridge type (Type 3). These now come in much faster speeds, up to 12x, but these are hard to find and expensive. A 3x can write at about 1GB in 15-20 mins and costs around a dollar only, good value for a long-life re-writable. You will want them in individual jewel-cases for stacking in a row, taking them in sequence and replacing at the other end.
[B]
Preparation:[/B] the only file system you should consider is udf. This has the property that writes are evenly distributed across the surface, unlike ext3 and others which need to constantly consult inode tables and things and cause uneven wear in one place. Dvd-ram is easily the most robust and long-wearing of all the removeable disk media and as it handles defect management at hardware level does not benefit from journalling. There is no post-write software verifications, and the session does not require finalization. 

Acquire udftools from Synaptic. Of it, you'll only need mkudffs (see below) which is as well, documentation is dire. This writes a udf file system on the dvd-ram disk, the actual file handling subsequently has been native to Ubuntu since at least Dapper but is not in user space. Because of the lack of man pages its highly recommended that the magic spell under must be followed exactly, mess with the options later.

Getting permissions right is very essential. The principle is that the user should do the writing/rewriting, for if root did so, a r/o file is created which can't be updated by an rsync running under user. If it does run, it has the bizarre effect of altering the directory entry for that file to nulls which causes baffled users to mutter darkly about certain udf versions causing directory corruption or their particular model dvd rewriter being poor. A problem thereby arises in that mkudffs must be run as root. The fix for this is simple of course: ask root to hand over the disk to user afterwards, hence the business with chown and chmod at the end of the script. 

**The meat**
The line to use in /etc/fstab is vanilla cdrom (with the addition of 'dirsync' which tells the dvd-ram to update directory entries on the fly) and is usable with a DVD-ROM in the same device 
```
/dev/scd0 /media/cdrom0 udf,iso9660 rw,noauto,dirsync,utf8 0 0
```
This script below is run as root when the DVDRAM is detected. Its heart is mkudffs: media-type is self-explanatory, udfrev sets the udf version to current (2.01) while utf8 is standard for Linux. The magic number after the device sets the desired capacity to the full 4.7GB The dvdram is then mounted and root creates a top-level holding directory, then turns the whole thing over to the user.

```
echo Setting up DVDRAM. . .
umount -l /media/cdrom0
mkudffs --media-type=dvdram --udfrev=0x0201 --utf8 /dev/scd0 2456789

echo Mounting...
mount -t udf /dev/scd0 /media/cdrom0
echo Setting up a top level directory...
chmod -R a+rwx /media/cdrom0
mkdir /media/cdrom0/MyData
chown -R _user_ /media/cdrom0/MyData
chmod -R a+rwx /media/cdrom0
echo Finished everything, now unmounting...
umount -l /media/cdrom0
echo Unmounted.
eject /media/cdrom0
```

This will take less than a minute each. Batch through your disks and they're ready for action, either for Nautilus drag and drop or script-driven backups.

**Part the second**
This deals with creating a super-quick 4.7GB backup.

Rsync is a truly wonderful creation, able to synchronise a destination to a source such that they will then be reliably complete clones. It does this by comparing the two and updating only those files that have been modified on source, even on request deleting files on destination that no longer exist on source. It has a blindingly quick algorithm and has an infinity of options for operating over LAN, secure shell and so forth. Here, actual backup times for dvd-ram will vary with the number of files needing updating, but I seldom go over 5 minutes for a full morning's work. As with most removable media, there will be a delay while the write cache is flushed when unmounting, varying with work that was done.

**The script: **
The magic is in the rsync line, the rest is a nice touch, datestamping on the root of the disk its latest update time for easy identification.
Options on rsync are: -a = recurse directories and preserve attributes; --delete = remove destination files that no longer exist on source (works only on directories, not file arguments); --temp-dir = make the temporary directory on hard disk, else by default it will use the dvd-ram itself, doubling times; source; destination. It is run as user from home.

The datestamp routine first removes evidence on the hdd /home/_user_ of notice of your last update, as well on the dvd-ram. Makes a formatted string, load it with the current time/date and creates a .BAK file in /home/_user_ before setting the permissions and copying it to the dvd-ram root. It then unmounts the dvd-ram and ejects it. 

```
echo Starting...
rsync -a --delete --temp-dir=/home/_user_/Temp/rsyncing /home/_user_ /media/cdrom0/MyData

# Visibly datestamp this dvd-ram disk
rm *.BAK
rm --no-preserve-root /media/cdrom0/*.BAK
DATER=$(date +%H%M-%a%d%b)
date > DVD=$DATER.BAK
chown _user_ DVD=$DATER.BAK
chmod a+rwx DVD=$DATER.BAK
cp -a --force DVD=$DATER.BAK /media/cdrom0

# Unmount, flushing write cache
umount -l /media/cdrom0
echo Unmounted...
eject /media/cdrom0
```

There are other options in rsync, such as file excludes (e.g. .mozilla cache) and so on which make a peruse of the well-written man pages a worth while exercise. Running this as a cron job is not advantageous for this type of backup. I usually throw in a disk when the spirit moves, meaning when I start to get nervous about the data and at least twice or three times a day. An old-fashioned burning of a dvd-rom takes care of laying down an archive when my cycle of disks has gone through and we start again. Dvd-ram can be read from nearly all modern dvd devices even if not write-capable, so can be used to restore on another machine.

---

### Post by antiplex on 2011-01-31
can't believe this post is already 2 years old and did not get much attention as it seems.

it just served me well as a quick lookup since i forgot which package has to be installed (udftools).

i got to admit that udf has its downsides in terms of user-friendliness but i would not want to miss it especially for my backup needs. 

since kernel versions 2.6.30 and behind udf became pretty easy to use without any hassles and even udf-version 2.5 and 2.6 (used for blueray) should be readable (i fear not writable, but this is not really needed for dvd-ram, 2.01 is fine and should be the best choice for formatting dvd-ram discs). 

one thing i miss though is a way to get some information about the udf-format of a certain disc, mainly the udf-version in which the disc is formatted as.

```
$ dvd+rw-mediainfo /dev/sr0
``` gives some information about the disc inserted but i can't figure out the magic number you mention but i guess the defaults should do as well, right?

i stumbled across various hints to a (sadly) non-gnu tool developed by philips called 'UDF Verification Software' which should be available after a registration/login [here]("http://www.ip.philips.com/") at [this resource]("http://www.ip.philips.com/partners/registered/par_udf_index.html") but this might be outdated and i did not feel the urge to register there.

anyhow, i wonder what might be the difference among the parameters --lvid , --vid and --vsid . of course, one is the logical volume identifier, the other the volume identifier and the last the volume set identifier but which should be used for what?

any ideas?

you mention some myths about its reliability but as far as i can say, i never had any unreadable dvd-rams yet but for most of them i don't do a lot of writes and handle them properly.
lets see what i say about this in 10 years from now...

regards, anti

---

### Post by warfie on 2011-04-05
Hi,

What do I do with "The Code" in "The Meat"?

Cheers

---

### Post by BigJules on 2011-04-16
Sorry for the delay - haven't checked this post for yonks...

The meat:
The first is a line to include in /etc/fstab
The second is a bash script. 

If you're unfamiliar with these, open a plain text editor to make a new file "FormatDVDRAM.sh", make a 1st line:
#!/bin/bash
(tells it what to expect)
then copy in the code, replacing the "_user_" with your user name. The "MyData" can be anything as well. Write and exit.

Now you have a script. To use it, put in a blank (or used) DVDram disk, and:
# bash FormatDVDRAM.sh

That's it. Your disk will now be useable to its full 4.7GB

Note that this will delete data already on it, and will format to UDF 2.01. You don't need to worry about the --lvid and other stuff any more.

I've used DVDrams since Dapper, 3x a day. Rarely they get in a twist, a file corrupt or something. I just re-format as above and they're just fine. Truly excellent value for off-line backup

---

