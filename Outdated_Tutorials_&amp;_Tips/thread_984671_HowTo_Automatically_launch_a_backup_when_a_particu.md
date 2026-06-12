---
title: "HowTo: Automatically launch a backup when a particular external drive is connected"
date: 2008-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by sarang on 2008-11-16
I was looking for a something that would automatically start backing up my computer (running Ubuntu 8.10 Intrepid Ibex at the time of writing) when a particular external hard-drive is connected to the computer. However, I could not find one so I wrote a script that would make this possible. First some background:

**  Desired behavior:**
A backup program should be launched when a particular external hard drive is connected to the computer. This program should preferably make incremental backups and store them as snapshots so that one can choose to restore to any of the available snapshots. To conserve hard-drive space, at most one backup should be performed everyday, regardless of how many times the external hard drive is connected. The program should distinguish between the hard-drive on which it regularly stores backups and other external hard-drives, and it should not write anything to drives that are not explicitly designated as backup drives. However, the program should not require the whole external drive to be used exclusively for backups. Also, the program should not interfere with the regular auto-mounting behavior of Ubuntu and should be as transparent to the user as possible, but should also be able to supply details if the user wants them. 

**Available Options:** 
No program that I know of meets all these requirements. However, good candidates that come close to the above requirements and can be modified to meet all the above requirements are:

1. rdiff-backup
2. rsnapshot (this is essentially rsync with snapshots, I think)
3. Simple Backup (sbackup)
4. Hacked setup of rsync and svn.

I chose Simple Backup (sbackup) partly because it was rated favorably by many people online, it was available in the Intrepid repositories and it seems that it is not a 'dead' project - if you report a bug, it will probably fixed in the future. Also, I think I prefer programs from the repositories because then they get automatically updated right away in case of a security flaw. However, the script that I wrote (that automatically calls sbackup when the correct external drive is connected) can easily be modified for use with other programs.

**Simple Backup Suite (sbackup)**:
What it can do:
It can do incremental backups and can save multiple snapshots. Also, one can specify which locations to back up and which not to via both a graphical front-end  and a textual config file that can have regular expressions etc. Backups can be performed manually and also automatically via cron jobs.  It can be configured to perform a full backup after a specified number of incremental backups. Also, backups are stored essentially as .tgz files and no 'binary blobs' are involved.
What it can't do:
 (This refers to version  0.10.5ubuntu2, latest in the Intrepid repository as of Nov 16, 2008 )

 Automatic backup after specific hard-drive is connected.

[B]The solution:
[/B]We add a udev rule that causes a script called backup-to-usbdrive  to be run when an external hard-drive is connected. Every partition (actually, volume) has a unique identifier, its UUID. We configure backup-to-usbdrive to check the UUID of the connected external hard-drive and we compare it with the known UUID of the volume that we use for storing backups. If the UUID of the external drive is different from the known backup UUID, we do nothing special and all actions that usually happen, like auto-mounting the external drive and creating an icon on the user's desktop etc. happen as configured by default. On the other hand, if the UUID is that of the backup volume, we wait for a while for auto-mounting etc. to happen, then mount the volume manually if necessary, then check the date of the last backup and if the last backup is more than a day old, we launch the backup program to do the backup. After that completes, we leave the system as it was before. That is, if we manually mounted the volume, we manually unmount it, but if it was mounted automatically by ubuntu, we leave it as is.

**Other features:  **
The script includes a provision for enabling audio alerts that let the user know if the backup was successful or not.

**Installation:**

[LIST]
[*]Install the backup program of your choice that you want to call automatically when the correct external drive is connected. I chose 'Simple Backup Suite' for this.
[*]Extract the attached backup-to-usbdrive.tar.gz to get the folder backup-to-usbdrive:
```

tar -zxvf backup-to-usbdrive.tar.gz
cd backup-to-usbdrive

```
[*]Find the UUID of the volume on which you want to store backups. One way of doing this is:
[/LIST]
[INDENT]Disconnect all usb drives connected to the computer, open a terminal and run:

```
ls /dev/sd*
```and note the output.

Now connect only the drive on which you want to store backups, wait for some time (say 1 minute) and re run the same command:

```
ls /dev/sd*
```and compare it to the previous output. You should have some more entries in the new output. In my case, I had [FONT=Courier New]/dev/sdb[/FONT] and [FONT=Courier New]/dev/sdb1[/FONT] as the extra entries.
The entry [FONT=Courier New]/dev/sdb1[/FONT] is of interest to us here. In general, the entry of interest will always have a number at the end. If  you see no such entry, your external drive may be unformatted. _The external drive needs to have a filesystem on it_. Make sure the external drive on which you want to store backups is formatted. It does not have to be empty, just has to have some filesystem created. I recommend ext3 filesystem with an ordered journal and no reserved blocks if you are creating a new one. Hint: see the manuals for programs [FONT=Courier New]parted[/FONT],[FONT=Courier New] gparted[/FONT] and [FONT=Courier New]mkfs.ext3[/FONT] if you want to know more. (the command [FONT=Courier New]man program_name[/FONT] generally brings up the _man_ual for [FONT=Courier New]program_name[/FONT].) If you have multiple partitions on the drive, you will see more entries of the form [FONT=Courier New]/dev/sdb2[/FONT], [FONT=Courier New]/dev/sdb3[/FONT] etc. and you need to take the one for the partition that you want to store backups on. I am assuming henceforth that the entry of interest is [FONT=Courier New]/dev/sdb1[/FONT].

Then run the following, replacing [FONT=Courier New]/dev/sdb1[/FONT] with the approprite entity found above:
[/INDENT][INDENT] ```
sudo vol_id -u /dev/sdb1
```This will give you the required uuid.
[/INDENT]
[LIST]
[*]Now open in a text editor of your choice the [FONT=Courier New]backup-to-usbdrive[/FONT] script from the similarly named folder that you extracted, and look for a line that looks like 

```
BKP_UUID="3470edcb-0df2-41f3-9b6e-e044e3a18790"
``` in the region where I define variables. This is right after the comments at the beginning of the script.

Change the line to

```
BKP_UUID="uuid_obtained_above"
```where uuid_obtained_above is the uuid that you found in the above step.
[*]_Applicable only if you want to use some other program instead of Simple Backup Suite (sbackup) to do the actual backup. Skip otherwise._
[/LIST]
[INDENT]In the [FONT=Courier New]backup-to-usbdrive[/FONT] script, change the lines 
```
BKP_COMMAND="/usr/sbin/sbackupd"
BKP_CMD_ARGS="--config=/etc/sbackup.conf"
``` to the ones appropriate for your program. ('your program' = the one that was installed in the very first step.)
[/INDENT]
[LIST]
[*]In the [FONT=Courier New]backup-to-usbdrive[/FONT] script, change the line 
```
BKP_MTPT="/media/myBook1"
``` so that the mount point is what you want. This way, the script will always make sure that the external drive is mounted to this location before starting the actual backup.
[*]_Optionally_, change the lines 

```
LOGGING_ENABLED=true
SOUNDS_ENABLED=true
```to disable logging or sounds. Just change true to false. Do not use quotation marks like "". However, I strongly suggest keeping both on, at least for the first few runs to make sure everything works fine for you.
[*]Create the directory [FONT=Courier New]/usr/local/share/sounds/backup-to-usbdrive/[/FONT] and all its required parent directories by:

```
sudo mkdir -p  /usr/local/share/sounds/backup-to-usbdrive
```
[*]Create a symbolic link to it as well:

```
sudo ln -s /usr/local/share/sounds/backup-to-usbdrive /usr/share/sounds/
```
[*]Copy contents of the '[FONT=Courier New]sounds[/FONT]' directory to the above directory:
```
sudo cp sounds/* /usr/local/share/sounds/backup-to-usbdrive/
```
[*]Copy the udev rule to your udev rules directory:
```
sudo cp 93-backup-to-usbdrive.rules /etc/udev/rules.d/
```
[*]Copy the _modified_ script to [FONT=Courier New]/usr/local/bin[/FONT]:

```
sudo cp backup-to-usbdrive /usr/local/bin/
``` It is critical that you have the script modified to suit your needs as explained in the steps above.
[*]Make it executable:
```
sudo chmod +x /usr/local/bin/backup-to-usbdrive
```
[*]**Edit Nov 27 2008: Add a logrotate rule:**
This is to prevent log files from becoming too large.
Extract the contents of the attached [FONT=Courier New]backup-to-usbdrive-logrotate-config.tar.gz[/FONT] fileand then copy the [FONT=Courier New]backup-to-usbdrive.logrotate.conf[/FONT] file to [FONT=Courier New]/etc/logrotate.d/[/FONT] and rename it to [FONT=Courier New]backup-to-usbdrive[/FONT]:
```

tar -zxvf backup-to-usbdrive-logrotate-config.tar.gz
cd backup-to-usbdrive-logrotate-config/
sudo cp backup-to-usbdrive.logrotate.conf /etc/logrotate.d/backup-to-usbdrive
```
[/LIST]
That's all, I think.

[B]Edit Nov 20 2008: Uninstallation:
[/B]
[LIST]
[*]Uninstallation is pretty straight-forward: remove the udev rule, logrotate config file, the bash script and the sounds directory and that should uninstall everything except the actual backup program (like sbackup) that you installed in the very first step of the installation process.
```

sudo rm -f /etc/udev/rules.d/93-backup-to-usbdrive.rules
sudo rm -f /etc/logrotate.d/backup-to-usbdrive
sudo rm -f /usr/local/bin/backup-to-usbdrive
sudo rm -rf /usr/local/shared/sounds/backup-to-usbdrive
sudo rm -f /usr/shared/sounds/backup-to-usbdrive

```
[*]To uninstall the actual backup program, if you installed it from the repositories, run ```
sudo apt-get remove --purge backup_program_name
``` where backup_program_name is the name of the program that you want to remove. Note that this will remove any custom configuration of the program as well. To keep configuration files, remove [FONT=Courier New]--purge[/FONT] from the above command.
[/LIST]

That should uninstall everything.
 

**Additional details about my configuration:**
Note that these are for reference only and should not be copied word-to-word. They are just guidelines.

```
sudo apt-get install sbackup
```installs Simple Backup Suite.

Then I edited my [FONT=Courier New]/etc/sbackup.conf[/FONT] so that it looked like the one in the [FONT=Courier New]sbackup.conf.tar.gz[/FONT] file that is attached. This config stores backups to the directory [FONT=Courier New]/media/myBook1/backups/raigad[/FONT]. Change that to suit your needs. Also, the external drive, mounted as [FONT=Courier New]/media/myBook1[/FONT] in my case, must have appropriate directories already created, viz. [FONT=Courier New]/media/myBook1/backups/raigad[/FONT] in my case.

**More hints:**

[LIST]
[*]Life becomes easier if we configure ubuntu to auto-mount our backup drive to one particular location, rather than to to some random mount-point like [FONT=Courier New]/media/disk1[/FONT] or [FONT=Courier New]/media/disk2[/FONT] based on how many external drives are connected, with no uniformity between successive mounts of the same drive. To do this, I made sure that the external drive was connected, then went to
[/LIST]
 [FONT=Fixedsys]ubuntu bar at top of the screen -> Places -> Computer[/FONT]

and right clicked on the icon for the external volume and selected [FONT=Fixedsys]Properties -> Volume -> Settings[/FONT]

and entered [FONT=Courier New]myBook1[/FONT] as the [FONT=Fixedsys]Mount Point[/FONT]. _Note that one should not_ enter the full path, like [FONT=Courier New]/media/myBook1[/FONT] here. _Only [FONT=Courier New]myBook1[/FONT] should be entered_. I chose the name 'myBook1' because the external drive I was using was a 'Western Digital My Book' brand external drive that I got as a gift. Any name without spaces or obnoxious special characters should be fine. However, I recommend using a slightly non-natural name so that the chance of ubuntu automatically mounting a different drive with the same name is minimized. Hence, I would recommend against choosing names like 'disk' or 'disk1' or 'My Book' etc.

And yes, if you encounter an error here, the only way that I know of correcting it is running [FONT=Courier New]gconf-editor[/FONT] and navigating to [FONT=Fixedsys] system -> storage -> volumes[/FONT] and then unsetting the offending key by clicking on the volume to get a map of keys - value pairs and then right-clicking on the key and saying [FONT=Fixedsys]unset key[/FONT].



This concludes this HowTo. Do not hesitate to suggest any improvements!

---

### Post by tp42 on 2008-12-24
Dear Sarang,
thanks a lot for this Xmas present. Your script is just that what I was looking for on my Ubuntu 8.10 system :-)
Just one hint:
In the README file deployed with the script 
"sudo mkdir -p  /usr/local/share/sounds/backup-to-usb-drive"
should be:
"sudo mkdir -p  /usr/local/share/sounds/backup-to-usbdrive"
because it is used that way in "sudo cp sounds/* /usr...." and in the script itself. The script would otherwise exit with "can not resolve dependencies"

And one question:
After mounting of my external FireWire disk, the first message I hear is "Oops, an error occurred". Directly after that, "backup starts" and then after a while "backup completed successfully, all done, no errors encountered". In the log file, it is just "main: EVERYTHING SUCCESSFUL." Though, do you have a hint where I could look for the "oops error encountered"?

Best regards, Thomas

---

### Post by tp42 on 2008-12-24
> **tp42 said:**
> 
And one question:
After mounting of my external FireWire disk, the first message I hear is "Oops, an error occurred". Directly after that, "backup starts" and then after a while "backup completed successfully, all done, no errors encountered". In the log file, it is just "main: EVERYTHING SUCCESSFUL." Though, do you have a hint where I could look for the "oops error encountered"?

Sorry Sarang, I think I was the reason for the error. For testing purposes, I deleted "datefile.txt". So ,now I found in the log file: "check_datestamp: Datefile /var/log/backup-to-usbdrive/backup-datefile.txt does not exist.". I think this is the reason for "Oops, an error occurred".
Sorry about that.
Best regards, Thomas

---

### Post by brs19301 on 2008-12-24
I must have something configured wrong.  When "files.tgz" gets to 4.0 GB the program exits stating "EVERYTHING SUCCESSFUL".  Ideas?
regards & Merry Christmas.

===============

---

### Post by sarang on 2008-12-25
> **tp42 said:**
> 
...
Just one hint:
In the README file deployed with the script 
"sudo mkdir -p  /usr/local/share/sounds/backup-to-usb-drive"
should be:
"sudo mkdir -p  /usr/local/share/sounds/backup-to-usbdrive"
because it is used that way in "sudo cp sounds/* /usr...." and in the script itself. The script would otherwise exit with "can not resolve dependencies"...


Thanks a lot for pointing this out - I have corrected the instructions and re-uploaded the file. Thanks again and Merry Christmas!

---

### Post by sarang on 2008-12-25
> **brs19301 said:**
> I must have something configured wrong.  When "files.tgz" gets to 4.0 GB the program exits stating "EVERYTHING SUCCESSFUL".  Ideas?
regards & Merry Christmas.

===============

I do not think it is your configuration. Is the filesystem on the drive on which you are storing files.tgz a FAT32 filesystem? Most external drives come formatted to FAT32, but it does not support files over 4GB. If this is indeed the problem in your case (I highly suspect so), your only choice would be to reformat the drive to a different filesystem. If you can afford to do so (note that this will permanently delete all data on it) I suggest formatting it to ext3 with no reserved blocks. To allow critical programs to operate at all times, ext3 by default reserves 5% of the space ('reserve blocks') so it is not usable under ordinary circumstances by a regular user. IMO this is not necessary _on an external drive_ and could be avoided as for today's large sized external drives, the 5% is a significant amount of space. (However _never_ get rid of the reserved blocks on your system partition.) Check the manual for mkfs.ext3 for more details.
 ```
man mkfs.ext3
```
I believe the [FONT="Courier New"]-m 0[/FONT] option specifies 0% reserved blocks.  

Note that if you do format your drive to ext3, windows will be unable to use it without additional (free) software. See [http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows") for details.

If you need more detailed instructions, please to not hesitate to ask before trying to format: a mistake there could make you lose data on your computer. Happy debugging and Merry Christmas!

---

