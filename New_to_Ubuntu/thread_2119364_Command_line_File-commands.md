---
title: "Command line File-commands"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by Karl10 on 2013-02-23
Hi geniuses!

I used to be so good with DOS and the Windows command line... I'm just not getting it with Linux... too old, probably (*ME, not Linux*).

I recently bought and installed an external, 1TB USB drive in preparation for 'nuking' my current setup and starting over clean, from empty hard drives.  The drive is running fine, no apparent problems, Nautilus seems to be happy with it, reads and writes with no issues.

I've been trying to use the "cp" command to do an incremental-backup type operation.  Basically, I'd like for "cp" to copy only those files that have been changed, or are completely new and don't exist in the destination folder(s) at all, so I don't have to sit there and babysit Nautilus when it sees things it doesn't know what to do with.  Reason for all this is that I copied the "home" directory (*the only one I'm interested in saving*) external USB drive, using Nautilus, but I've been continuing to use 10.10 to do other things, getting ready to pull the plug, and I'd like to ensure that any new or changed files anywhere within the "home" directory or it's sub-directories get copied over before i pull the trigger.

I'm not using a dedicated backup app because my current install (*10.10*) has become so squirrely that it won't install or even upgrade a LOT of things, this among them.  Given the level of weirdness of this install, I'm going "tabula rasa" and starting blank-disc clean. 

Problem is, when I try to use this command in Terminal, from the source directory (*home*):

     **cp -r -u -v / 1Tb Xtrnl Backup/Home Folder **

terminal returns the error:

     "**cp: target 'Folder' is not a directory**"

????

I tried using "1TbXtrnlBackup/HomeFolder", and terminal returns:

    "**[B]cp: missing destination file operand after '/HomeFolder**"  or  "cp: cannot create directory '1TbXtrnlBackup/HomeFolder' : No such file or directory[/B]"  

I should probably note here that when I type: 
"cd /",   then type "dir" or "ls", the external drive does not appear, even though Nautilus sees it just fine.

I haven't been able to find any examples of any similar problem anywhere, so here I be, hat in hand.

I'm especially puzzled by terminal's failure to display an existing drive that Nautilus does.  I think that's probably the root of my difficulties, but I'm at a complete loss as to where to go with it (*other than here, of course }:-)*  )

Any thoughts greatly appreciated; I'm really looking forward to catching up with everyone else, and having a stable, fully-working install again!

Karl

---

### Post by iponeverything on 2013-02-23
you should see the drive under /media/

also use double quotes for names that contain spaces i.e. "Home Folder"

---

### Post by DuckHook on 2013-02-23
Consider rsync, which is designed to do exactly what you want with aplomb.

Re: commands: You must escape all spaces, ergo (in your example):
```
cp -r -u -v /1Tb\ Xtrnl\ Backup/Home\ Folder
``` or perhaps the more human readable way with double quote marks:```
cp -r -u -v /"1Tb Xtrnl Backup"/"Home Folder"
```Best not to use spaces in Linux. I substitute with the underscore (_).

---

### Post by sudodus on 2013-02-23
+1 for double quoting, otherwise names with spaces are regarded as separate parameters. This is actually the same in MSDOS.

I use this mini-script for incremental backup with cp

```
#! /bin/bash

echo simple backup script using cp -auv SOURCE[directory]... DESTINATION_directory
echo cp -auv $*
echo press {ENTER} to continue or {CtrlC} to quit
read
cp -auv $*
```

But soon you will be ready for ***rsync***. The manual is very well written and contains several examples.
```
man rsync
```
Rsync can also be used for backup between computers via the network.

---

### Post by schragge on 2013-02-23
> **Karl10 said:**
> Reason for all this is that I copied the "home" directory (*the only one I'm interested in saving*) external USB drive, using Nautilus, but I've been continuing to use 10.10 to do other things, getting ready to pull the plug, and I'd like to ensure that any new or changed files anywhere within the "home" directory or it's sub-directories get copied over before i pull the trigger.To copy from your home directory to an external USB drive, the *cp* arguments should look something like
```

cp -auv ~ "/media/[color=blue]mountpoint_of_your_external_drive[/color]/${HOME##*/}"

```
where ~ and ${HOME} are just two fancy ways to specify your home directory.

You'll see what the [color=blue]mountpoint_of_your_external_drive[/color] is by issuing *ls /media*. It's usually either the *label* or, if the disk has none, the *device name* of your external hard drive. If your drive as I guess has an NTFS filesystem on it then ```
blkid -t TYPE=ntfs -o list
``` will show its device name, and, optionally, its label. The mount point is also shown there.

The first argument (~) is the source, the second is the destination of your copy operation.

Similar arguments can be used with *rsync*, too.

---

### Post by DuckHook on 2013-02-23
> **Karl10 said:**
> I used to be so good with DOS and the Windows command line... I'm just not getting it with Linux... too old, probably (ME, not Linux).

It's not you. It ***can't*** be you. Such self-flagellation is simply not permissible. We old geezers have to stick up for each other. I'm an old DOS warhorse like you (going back even further, actually), but comparing Linux to DOS is comparing a BMW to a tricycle. I've found that the following resources are great for new users.

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)

More advanced but absurdly useful is:

[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download)

...enjoy!

---

### Post by Karl10 on 2013-02-23
Thanks Everyone,

Chugging away as we 'speak'.  

Going to have to set aside a chunk of time each day to learn one new command.  Ain't gonna let it get the best of me!

---

