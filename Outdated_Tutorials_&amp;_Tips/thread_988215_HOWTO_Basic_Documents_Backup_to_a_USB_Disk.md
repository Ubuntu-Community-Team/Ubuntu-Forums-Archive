---
title: "HOWTO: Basic Documents Backup to a USB Disk"
date: 2008-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Junkieman on 2008-11-20
[SIZE="4"]**Greetings!**[/SIZE]

Today I will show you how to set up a system for backing up your personal documents onto a USB disk. This is not a complete system backup, it is intended for your personal documents. I use this method for backing up my photos onto a USB device, and it's always a good idea to keep your backups separate from your PC! 

Because this method synchronizes two directories, you can also use this setup for your day-to-day use to make sure the files on your PC and USB disk are always the same. Once set up, running the backup is practically quick and painless.

[COLOR="Navy"]Newbie Note[/COLOR]: We're going to be using the terminal for setting up our backup system. You can open a terminal window by using the main menu Applications -> Accessories -> Terminal. Most of the commands require super user access, and will prompt you to enter your password.

[COLOR="Navy"]Terminal Hint[/COLOR]: in most cases you can use the TAB key to auto-complete user and directory names.

[COLOR="Navy"]Tutorial Hint[/COLOR]: Commands that you should enter are shown in code boxes, and their resulting output is shown as gray text in this tutorial. Let's get to it!

[SIZE="4"]**Preparation**[/SIZE]

Decide on what you want to backup, as I mentioned I use this to backup my photos. Do a rough estimation how much space your files will take and get a USB disk that will satisfy your space requirements, with space to spare of course. I'm using a 8GB USB disk for this tutorial.

[SIZE="4"]**Format the Disk**[/SIZE]

We will now format the USB disk. I will use the ext2 file system for our backup disk. You can format it as FAT32 if you have a really good reason, and if you're not sure what the differences are, just stick with the tutorial :)
If you know how to do this you can skip to the next section, and you can also use gparted for this if you know how. I'm going to explain how to do this using the console.

**[COLOR="Red"][WARNING][/COLOR]** Formatting a device will erase all files on that device. Please double check the commands that you enter. I won't be responsible if you format the wrong device. I will also assume the USB disk comes with one partition, as they normally do. If you have any doubts there is much help on the net on how to do this. [Google is your friend](http://www.google.com/search?q=how+to+format+a+usb+disk+as+ext2).

If at any stage you get a "Permission Denied" message after running a command, enter "sudo -s", enter your password if prompted, and retry the command that failed. I found that the *echo* command gives this problem in Xubuntu, even if running with sudo.

Connect your USB disk, and let's get some info about it. Open a terminal window and enter:

```

**sudo fdisk -l**

[COLOR="#808080"]
Disk /dev/sdc: _8011_ MB, 8011120640 bytes
16 heads, 32 sectors/track, 30560 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
_/dev/sdc1_               1       30560     7823344    c  W95 FAT32 (LBA)
[/COLOR]

```

My USB disk is a 8Gb disk and it is listed as /dev/sdc1, note that down - whenever you enter a command, use your /dev/ assignment as listed in your output. We must un mount the disk before we format:

```

**sudo umount /dev/sdc1**

```

Now we format. Please remember my device is /dev/sdc1, replace this with your device name as you noted down in the previous step:

```

**sudo mkfs.ext2 /dev/sdc1**

[COLOR="#808080"]mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
489600 inodes, 1955836 blocks
97791 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2004877312
60 block groups
32768 blocks per group, 32768 fragments per group
8160 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done[/COLOR]

```

We also want to give the USB disk a useful name, which will be used as it's default mount point, let's call it "backupdisk":

```

**sudo e2label /dev/sdc1 "backupdisk"**

```

Unplug the USB disk, and plug it back in to your PC. It should show up as a removable disk called "backupdisk", and the mount point should be "/media/backupdisk", verify this by listing the /media directory contents:

```

**ls /media**

[COLOR="#808080"]_backupdisk_ cdrom cdrom0 floppy[/COLOR]

```

Next we create a backup directory in the root of the USB disk, all our backed up files are going to be stored in this directory:

```

**sudo mkdir /media/backupdisk/backups**

```

We have to create the directory as root (sudo) and then change the directory owner, because only root has write permission on the device at the moment.
In this example my user name is wes, replace "wes" with your user name:

```

**sudo chown wes\: /media/backupdisk/backups/**

```

This will allow us to run the backup as the current user. Nifty.

[SIZE="4"]**The Script**[/SIZE]

We're going to create an executable file in the root of the USB disk, and when run/executed it will synchronize your files onto the USB disk. We will be using the rsync command, this is a powerful little command used to synchronize directories. Before we create the file, let's look at the command that will do the actual backup (colour coded for readability):

**rsync** --recursive --times --delete --progress [COLOR="Green"]/home/wes/photos/[/COLOR] [COLOR="DarkRed"]/media/backupdisk/backups/[/COLOR]

Just to be thorough, here is a breakdown of the command parameters:

*rsync*: the command to synchronize files
*recursive*: backup all files, even those in sub directories
*times*: preserve modification times on the backup target
*delete*: delete extraneous files from the destination directory
*progress*: show progress during transfer
*/home/wes/photos/*: the directory on my PC I want to backup, [COLOR="Blue"]replace this with the path on your PC you want to backup[/COLOR]
*/media/backupdisk/backups/*: the backup destination, which is the backups directory on our USB disk

Note: The trailing slash in the source path [COLOR="Green"]/home/wes/photos/ [/COLOR]means "copy the contents of /photos/". If you omit the slash, the backup will create a photos directory on the backup device, including the directory contents. In our example the contents of /photos/ are copied directly into our destination path, [COLOR="DarkRed"]/media/backupdisk/backups/[/COLOR]

*Terminal Hint: You can copy the code below and use Shift+Insert to paste it into the terminal. Just remember you must change the source path to point to your documents before running the command.*

Enter this command to create the script file, replacing "[COLOR="Green"]/home/wes/photos/[/COLOR]" with the path of your files you want to backup:

```

**sudo echo "rsync --recursive --times --delete --progress /home/wes/photos/ /media/backupdisk/backups/" > /media/backupdisk/sync.sh**

```

Let's take ownership of this file we just created, that way we can easily edit later if need be. Remember to replace "wes" with your own user name:

```

**sudo chown wes\: /media/backupdisk/sync.sh**

```

And finally, we must make this file executable by the user so that it can run as a script:

```

**sudo chmod u+x /media/backupdisk/sync.sh**

```

If everything went as expected you should have a file called **sync.sh** in your USB disk's root, with a directory called **backups**. You can now close the terminal window, we are done with it. You can also eject the USB disk since we are done here.

[SIZE="4"]**Conclusion**[/SIZE]

That's it, your backup system is ready for action. Let's give it a run to test if it works, plug the USB disk in you PC and run/execute the file named **sync.sh** found on the USB disk. This can be done through your window manager by double-clicking on the file. If you are prompted to *Open* or *Run in Terminal* choose the second option. You will see a terminal window while rsync synchronizes your files, the window will close when the backup is complete. You now have a duplicate of your files on the USB disk! Remember to eject/unmount the USB disk before you remove it from your PC.

Thanks for reading!

[SIZE="4"]**Considerations for the Technically Minded**[/SIZE]

There is a reason I use the ext2 file system, apart from being native to our favourite OS. 

FAT32 only stores file timestamps with a 2-second resolution, this means that two files would be seen as different even if their contents match! rsync has a clever delta-transfer so it will only copy changed data, but the documentation recommends matching files to exact times. If you insist on using FAT32 on your USB device, include the --modify-window option with a value of 2 in the rsync command. For more info on this option see the [rsync man page](http://www.samba.org/ftp/rsync/rsync.html).

Here is our example rsync command with the --modify-window option:

```
rsync --recursive --times --delete --progress --modify-window=2 /home/wes/photos/ /media/backupdisk/backups/
```

---

### Post by thunderbirdje on 2008-12-02
Nice tutorial! Great work! With al the warnings and extra information for newbies! :p

Just one question:

I would like to backup my USB disk (which I use at work) to my personal documents. It would be nice if backup is made automatically when I plug in the USB disk at home. (if a lose my disk or it get corrupt, I still have a backup at home).

Problem is: I do have to use fat32 (otherwise it isn't readable @ work). But then I can't use e2label.

What I did try: I synchronized 2 folders (with [Conduit]("http://www.conduit-project.org")), but the problem is that my USB disk isn't always mounted under the same path: example: sometimes **/media/disk** or if another disk or MMC card or something else is plugged in) it will be **/media/disk-1**. Because the USB drive isn't ext2, I can't use e2label to identify uniquely my USB drive. Is there another way around?

---

### Post by Junkieman on 2008-12-03
> **thunderbirdje said:**
> Nice tutorial! Great work! With al the warnings and extra information for newbies! :p
I can't use e2label to identify uniquely my USB drive. Is there another way around?

Thankyou! funnily enough i realized i could have made it even easier :p but i hope we can make it useful by solving your problem.

my guess is that the mount point changes if the volume doesnt have a label, and yes there is a way to label a FAT32 volume on a Windows machine, try this...

on your work pc (i assume its a Windows OS) open a command prompt while you have your USB disk connected and enter this command

*replace h: with your USB disk drive letter*

```
label h:
```

check to see if this label picks up on your *nix pc, good luck!

---

### Post by mdebusk on 2008-12-04
> **Junkieman said:**
> plug the USB disk in you PC and run/execute the file named **sync.sh** found on the USB disk. This can be done through your window manager by double-clicking on the file.

If you name the script **[FONT="Courier New"]autorun.sh[/FONT]** instead, gnome will prompt you to run it when you plug in the drive.

---

### Post by Junkieman on 2008-12-04
> **mdebusk said:**
> If you name the script **[FONT="Courier New"]autorun.sh[/FONT]** instead, gnome will prompt you to run it when you plug in the drive.

Thanks for the tip, I didn't know that, despite it's obviousness :p

---

### Post by mdebusk on 2008-12-04
> **Junkieman said:**
> Thanks for the tip, I didn't know that, despite it's obviousness :p

The downside is it won't show the terminal window. If you want to know when it's done, you'll have to add a zenity popup or a sound to the script.

---

### Post by IMOC on 2008-12-04
Thanks for an excellent tip!

Is it possible to extend this further and and make the data on the USB disk encrypted?

---

### Post by mdebusk on 2008-12-04
> **IMOC said:**
> Is it possible to extend this further and and make the data on the USB disk encrypted?

[Truecrypt]("http://www.truecrypt.org/") will let you encrypt an entire partition.

---

### Post by Junkieman on 2008-12-08
> **IMOC said:**
> Thanks for an excellent tip!

Is it possible to extend this further and and make the data on the USB disk encrypted?

i did think about this initially, but that was beyond the scope of what i needed at the time. but as mdebusk suggests, you could use Truecrypt :)

---

### Post by mdebusk on 2008-12-10
> **thunderbirdje said:**
> Problem is: I do have to use fat32 (otherwise it isn't readable @ work). But then I can't use e2label.

Install mtools from the repos and use mlabel.

---

### Post by mdebusk on 2008-12-10
> **Junkieman said:**
> Considerations for the Technically Minded

When I worked my way through this howto, I found that my home directory backup took up just over half of my new eight-gig flash drive. With all that room, I decided I wanted to back up my netbook to the same drive in the same way.

I named the directories on the backup disk to match the hostnames on my PC and my netbook. So instead of "/media/backupdisk/backups" like in your example, I have "/media/Backups/desktop/" and "/media/Backups/eee900/".

The script I composed follows. It uses the "hostname" and "whoami" commands to set appropriate variables to the directories I want to back up. As in your example, the script is on the flash drive, but it works with either computer.

```
#!/bin/sh

# Make sure the 'hostname' command returns the value you want!
# RTFM "man hostname"
FLDR="/media/Backups/$(hostname)/"

# This is the user's home directory.
HM="/home/$(whoami)/"

# I want the backup to go to a directory that already
# exists, and if the directory doesn't exist, the
# script should return an error message.
if [ -d $FLDR ];
then
    rsync --recursive --times --delete --progress $HM $FLDR
else
    echo "This drive is not set up to sync with $(hostname)."
fi
```

If I were more industrious (and better versed in bash scripting), I'd set up the following instead of the error message:

```

**Ugly Pseudocode Follows:**
If the directory doesn't exist
    get the free space on the backup drive $FREESPACE
    get the size of the home directory $HOMESIZE
    subtract $HOMESIZE from $FREESPACE
    subtract an additional amount, maybe half a gig
    if there's enough room
        ask, "Want to back up to this disk?"
        if yes
            create the directory on the flash drive
            set the appropriate permissions
            run the backup
        if no
            drop the matter
    if there isn't enough room
        tell the user it won't fit
        drop the matter
```

As it is, though, I prefer to set it up by hand.

---

### Post by thunderbirdje on 2008-12-12
Still have to try the label function on a non Ubuntu PC @ work (busy time now before Winter vacation).

But thanks for sharing the script! It's inspiring me! :-)

---

