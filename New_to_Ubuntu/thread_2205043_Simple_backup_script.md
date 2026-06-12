---
title: "Simple backup script"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-02-11
My wife's computer runs 12.04 from a SSD. She keeps her data files on a hdd on the computer and periodically backs them up to a desktop USB drive which she plugs in to do the backup.

There are data files on the USB drive that do not exist on the hdd, and these need to be retained.

I would like to know a simple script (or program) that would allow her to plug in her USB drive, then click on an icon on her desktop (or something equally simple), and back up all the new and changed files since the last backup. Ideally, the switches (this probably isn't the right word) on the files will be set each backup so that she does not have to keep track of when she last backed up. Thanks.

---

### Post by ubudog on 2014-02-11
The tool 'rsync' would be ideal for this task.

Here's a one-liner that'll do it:
```
rsync -av /home/user/ /media/mountpoint/backup
```

This example would backup a user's home directory to a mounted drive.

Keep in mind that trailing slashes [do matter]("http://devblog.virtage.com/2013/01/to-trailing-slash-or-not-to-trailing-slash-to-rsync-path/") with rsync.

Hope this helps.

---

### Post by Odyssey1942 on 2014-02-11
Ubudog, Looks easy enough. Is there any way to turn that into a script that can be started with a desktop icon?

I am getting more comfortable with the terminal, but it would terrify her.

Thanks

---

### Post by ubudog on 2014-02-11
Sure, just create a file called, for example, "backup.desktop" and place it in the Desktop directory of your user's home directory.

An example .desktop file for this script would be something like:
```
[Desktop Entry]
Type=Application
Name=backup script
Exec=/location/to/script.sh
Name=Backup
```

Then just make the file executable:
```
chmod +x ~/Desktop/backup.desktop
```

Also, make sure that your script is executable as well.

---

### Post by Odyssey1942 on 2014-02-11
Ok, got some of that.

In the code that goes in the backup.desktop file, how does that code incorporate the rsync command line in your first reply?

I am guessing that the answer is in the line

> Exec=/location/to/script.sh but I am completely new to scripting and have no idea how these things work. 

Apologies, "Noob" here.

---

### Post by ubudog on 2014-02-11
Yep, it is defined in the Exec line.

In fact, you could just replace Exec with the rsync command.
```
Exec=rsync -av /home/user/ /media/mountpoint/backup
```

---

### Post by monkeybrain20122 on 2014-02-11
I use unison for exactly that purpose, it is in the repository. It has a gui, it is very easy to use. You set up a profile for the matching folders and every time when you plug in the external hard drive, just open the profile and it will sync the differences, then press 'go' to sync (default goes by the latest change. But you have options to override it, say, if you accidentally delete something by default it will delete the other copy as well, so you need to sync in the other direction.. the gui is very intuitive so there is no point to explain now)

```
sudo apt-get install unison-gtk
```

---

### Post by Odyssey1942 on 2014-02-11
MB, thanks. That can be my next project as time permits.

For now, want to keep it simple and get something working for her but getting a little over my head here. I am trying to figure out the "to" portion of the Exec line.

Gparted shows the USB drive to be /dev/sdg1 and an ntfs partition. Does this mean the USB drive is mounted at /dev/sdg1? The "View:Device information" shows the path to be /dev/sdg

Or maybe it is not mounted at all because while the drive shows up in Nautilus, when I click on it nothing happens. Very confused as to why it shows up, but doesn't open up.

---

### Post by ubudog on 2014-02-11
Usually the mountpoint of a flash drive will be in /media/username.

You will need to install the ntfs-3g package in order to be able to mount and see ntfs partitions.
```

sudo apt-get install ntfs-3g

```
Alternatively, you could format the drive to FAT32 (make sure you have backups of the data on the drive if you do this).

---

### Post by monkeybrain20122 on 2014-02-11
I have not used rsync but I suppose it is /dev/sdg1 because you want the partition.  

It seems that the command only does one way backup. Does it overwrite the old copy or does it just change files that have been modified? What if you accidentally delete something and want to restore it from the backup (i.e syncing the other way around)? I am sure rsync has options for all these stuffs, it is quite widely used, but I haven't read its manual..

P.S. I however have never used unison with ntfs. All my drives are in ext4. I don't use Windows and therefore have no reason to use its file system.

---

### Post by ubudog on 2014-02-11
> **monkeybrain20122 said:**
> I have not used rsync but I suppose it is /dev/sdg1 because you want the partition.  

It seems that the command only does one way backup. Does it overwrite the old copy or does it just change files that have been modified? What if you accidentally delete something and want to restore it from the backup (i.e syncing the other way around)? I am sure rsync has options for all these stuffs, it is quite widely used, but I haven't read its manual..

/dev/sdg1 is a special device file for the drive, not a mountpoint.

rsync has many options, and can be configured to do anything mentioned above.  :)

---

### Post by Odyssey1942 on 2014-02-11
Earlier I had witnessed my wife transferring files from the hdd to the USB drive (an Iomega portable), so I knew it should show up. So I drew on my Windoze training, and restarted the computer. Opened Nautilus again and clicked on the drive. Voila, there it was. 

So ntfs-3g was already installed somehow (Ubuntu Software Center confirms.)

OK, so I found the drive at /media/Iomega_HDD.

However this is a very good time to look into the question raised by MonkeyBrain. My wife has just become an Ubuntu user at my insistance because I just can't put up with Windows any longer and don't want to try to support her Windows computer with a dwindling Win knowledge. So this USB drive was created under Windows and may well need to be hooked up to the one remaining Windows computer sometime in future, so it retains the ntfs filessys.

As mentioned in the original post, there are files already on the USB drive that need to be retained. So whatever my first instance of rsync is, it must not overwrite everything on the USB drive. 

Ideally the first run should just copy anything not already on the USB drive and add to it in the same name folder that each file is being copied from, and ideally set the flags so the any future updates only copies new or changed files from the source.

As always, I dutifully have a dazed read of the man rsync pages (and am happy to report for the first time ever, some of it seems to be in English rather than Greek). But still over my head nonetheless.

So as I understand it the backup.desktop file should read:
```
[Desktop Entry]
Type=Application
Name=backup script
Exec=rsync -av /home/susie/desktop/susiefiles /media/Iomega_HDD
Name=Backup
```

1) totally clueless as to what the two (seemingly duplicate) "Name=" lines do. Are both needed?

2) do the qualifiers "-av" accomplish my objective with respect to the first instance mentioned above?  

3) 2) do the qualifiers "-av" accomplish my objective with respect to the subsequent instances mentioned above?

4) Finally, the folders containing the files being copied from already exist on the USB drive, as do 99.8% of the files on the source. Is the above going to put the "new" files from the source into the correct place on the target?

Thanks for your patience and assistance on all of this.

---

### Post by ubudog on 2014-02-11
> **Odyssey1942 said:**
> 
So as I understand it the backup.desktop file should read:
```
[Desktop Entry]
Type=Application
Name=backup script
Exec=rsync -av /home/susie/desktop/susiefiles /media/Iomega_HDD
Name=Backup
```

1) totally clueless as to what the two (seemingly duplicate) "Name=" lines do. Are both needed?

2) do the qualifiers "-av" accomplish my objective with respect to the first instance mentioned above?  

3) 2) do the qualifiers "-av" accomplish my objective with respect to the subsequent instances mentioned above?

4) Finally, the folders containing the files being copied from already exist on the USB drive, as do 99.8% of the files on the source. Is the above going to put the "new" files from the source into the correct place on the target?

Thanks for your patience and assistance on all of this.

1: I believe the first name could/should be replaced with "Comment".  This is the text that pops up when you hover over the icon.

2: The -a switch includes the following other switches:
```


    -r, --recursive recurse into directories

    -l, --links copy symlinks as symlinks

    -p, --perms preserve permissions

    -t, --times preserve modification times

    -g, --group preserve group

    -o, --owner preserve owner (super-user only)

    -D same as --devices --specials

    --devices preserve device files (super-user only)

    --specials preserve special files

```

3: rsync will not overwrite your drive.

4: Yes, however you must be careful with trailing slashes.  I'd suggest playing around with rsync locally before you get the backups going.

For instance,
```
rsync -av /home/user/directory/ /media/drive
```
will copy the **contents** of /home/user/directory/ into the root of /media/drive, and not into a new directory on /media/drive.
So, if you look in /media/drive, you will see all the files inside /home/user/directory.

However,
```
rsync -av /home/user/directory /media/drive
```
will copy the **directory** /home/user/directory into the root of /media/drive
So, if you look in /media/drive, you will see the directory that you copied, and inside you will see the files.

I hope this clears some things up; if you have any questions I'm here.

---

### Post by Jason_Gibson on 2014-02-11
```
#!/bin/bash

##### Begin Script #####

backup()
{
    if mountpoint -q $2 ; then
        rsync -au --delete $1 $2
    fi
}


while true
do
    backup /folder/to/backup /mount/point/of/bu/drive
    sleep 120
done

##### End Script #####

```

For this to work you would need to set up the fstab with a uuid of the backup drive with a specific mount location. The script runs every 2 minutes (120 seconds.) Checks if mounted, if mounted runs backup. If it isn't mounted it doesn't do anything except sit until it checks for mountpoint again in 2 minutes. Fully automated just set this to run at boot and leave it alone.

Note : Only use this if you want your external drive mirroring your working drive location. If you want multiple backups that is another matter. If you want it to only backup but never delete anything from the backup drive remove the --delete flag.

---

### Post by Odyssey1942 on 2014-02-12
Jason, This is exactly the sort of thing I was hoping for. With thanks to Ubudog, I was getting a bit muddled and quite unsure whether I was going to create grief.

Yes, I only want to backup (one-way) from the hdd to the one external USB drive, and as mentioned earlier want to take care not to erase any files or overwrite unchanged files on the USB.

What I am still a bit unsure of is whether the "backup" command below: 

(a) is correct as I have modified it [all her "source" data folders and files are within "SusieStuff"], 

(b) will add new or changed files from existing folder 1 under SusieStuff on the HDD to the existing folder under SusieStuff 1 on the USB, and from folder 2 under SusieStuff on the HDD to the existing folder 2 under SusieStuff on the USB, etc, [i.e., don't want to somehow create 2 folders of the same name on the USB, one old, one new], as well as 

(c) will create any folders not now existing on the USB that do now exist on the HDD (i.e. very recently created folders) and adding any files within to the new folder on the USB?

Another thing I am unclear on, since I would prefer not to overwrite any existing files on the USB, does removing "--delete" prevent this from happening, both first time and subsequent?

Also, I have again consulted the man rysnc pages about $1 and $2 but did not see anything. I removed the "--delete" but should I also remove $1 and $2 in that same line as well (i.e., I don't understand their function)?

Also note that I have changed the frequency to 10 mins.

Here is the code that I plan to put into backup.susiestuff

> #!/bin/bash

##### Begin Script #####

backup()
{
    if mountpoint -q $2 ; then
        rsync -au $1 $2
    fi
}


while true
do
    backup /home/susie/desktop/SusieStuff /media/Iomega_HDD
    sleep 600
done

##### End Script #####

For clarification, it is as close to a certainy as I can control, that there will be no files on the USB that are newer than, or have later modification dates than the files on the HDD. So it is entirely a one-way operation. In the man pages, it says about the qualifer "u":

> This forces rsync to skip any files which exist on the destination and have a modified time that is newer than the source file.

Since this should never happen, is "u" a qualifier I need?

Finally, if the qualifier is -av instead of -au, where will the verbose output show up? Will she need to already have a terminal window open, or will rsync open one to display progress?

Thanks.

---

### Post by monkeybrain20122 on 2014-02-12
Why don't you just give unison a try? Takes you a minute to figure out how to use it. If it doesn't suit your need just sudo apt-get remove unision-gtk. It is really easy.

---

### Post by Dennis N on 2014-02-12
There is also a **graphical version of rsync** called **grsync** in the Ubuntu Software Center. Just browse to the folder to be backed up and then browse to the destination, set your options by checking boxes and go. There is also an button for a trial run.

---

### Post by Odyssey1942 on 2014-02-12
MB, I had already installed Unison and had a quick look, but it was not obvious to me how to get started. Didn't spend much time as I will get back to it later. I did look at a YouTube video of a "how to install", but it confirms that it looks like a new project.

I also installed grsync, but again the setup looks like a learning curve.

So I am just going to continue with rysnc as a script as I feel I am very close to implementation. If anyone can respond to my last post (long, but not complicated, apologies), which if carefully read is pretty narrow on a point by point basis, I think I will be ready to set it up.

---

### Post by monkeybrain20122 on 2014-02-12
> **Odyssey1942 said:**
> MB, I had already installed Unison and had a quick look, but it was not obvious to me how to get started. Didn't spend much time as I will get back to it later. I did look at a YouTube video of a "how to install", but it confirms that it looks like a new project.


It is not a new project. In fact it has stopped active development but since the developers use it themselves there will be updates if there are major bugs.

To use it is very easy. First open the interface, click add to create a new profile, then enter the folders to be sync and that's it. If you sync with an external device then of course it has to be mounted first. To use it just mount the external device, start unison, choose profile from the list  of profiles you created and click "open", when it finishes its calculation, click "go" and that's it. As I said the default is to sync according to the most recent modifications, but you can override it if you wish  (use the buttons "left to right" and "right to left"). See the screenshots, the second one should be the last, I added it later and the order messed up. (you need to install unison-gtk)

---

### Post by Odyssey1942 on 2014-02-12
MB, my apology as I meant it was a new project for me to learn it. Maybe simple, maybe not. For example, I do not know what a profile is and have no idea which of the boxes I should check or not and will need to google and read so as to make good choices, etc. 

As much a beginner as I am, my wife is way back from me If I asked her to explain what an O/S is, or what a terminal is, she would not even know what I am talking about. So this needs to be either a one click process, or better a totally automated one, such as the script that Jason kindly provided. From what I understood of what you wrote, it does not seem to be an automated process (e.g., "then of course it has to be mounted first.")

I really do plan to spend some time on both Unison and grsync, but for now, I want to get her files backed up as efficiently and expediently as possible, starting as soon as possible. So for now, finishing the script is my priority. Thanks again for your good suggestion, which I will indeed follow up on, and soon.

---

### Post by monkeybrain20122 on 2014-02-12
Ok, suppose you want to sync several different folders, e.g Music folder on your hard drive to a folder named Music-backup on external drive A,  Videos to Videos-backup on external drive B etc. A profile is just a name to keep track of which is which, so you create a profile fore each, say the profile "music" for syncing your Music folder to the backup in external drive A, and a profile "videos" for syncing the Videos folder to the external drive B. You can name them anything, it is just a way to keep track of different syncing paths, so to speak.

But your wife doesn't have to worry about this because presumably you set it up for her. Once it is set up all she needs to do would be 1) connect the external device 2) start unison 3) choose the profile (say music) and click "open", 4) wait for the calculation to complete and then 5) press "Go"

I find it a lot easier than messing around with obscure rysnc commands and scripts.

---

### Post by Dennis N on 2014-02-12
You are backing up to an Iomega USB drive? Is it formatted FAT32? Many external HDD come formatted that way when purchased. If so you need to add an extra rsync option.

---

### Post by Odyssey1942 on 2014-02-12
"File System Support" in gparted shows check marks across the FAT32 line, so I am unsure if this provides a complete answer to your question as ntfs is also checked. Is there a terminal command to determine whether FAT32 or what it is?

Since you did not supply the required next step, I have again paged through the 3663 lines of the man page, then searched backwards for FAT32, but do not see a mention. Google finds indicate that it could be a file size issue or a time stamp issue. (Maybe there are others?) I am unsure that I should be concerned about the time stamp. What is the issue that needs an attribute, and to help move this along, could I trouble you to disclose the required attribute? Thanks.

---

### Post by monkeybrain20122 on 2014-02-12
> **Odyssey1942 said:**
> "File System Support" in gparted shows check marks across the FAT32 line, so I am unsure if this provides a complete answer to your question as ntfs is also checked. Is there a terminal command to determine whether FAT32 or what it is?
.

The command is 

```
sudo blkid
```

---

### Post by Odyssey1942 on 2014-02-12
Thanks, MB. It shows to be ntfs.

Dennis, does this make the issue that you alluded to go away? Thanks.

---

### Post by Dennis N on 2014-02-12
Yes, there is a terminal command:

```
[FONT=Courier New]sudo parted -l[/FONT]

```
That's a lower case letter l (as in life) on the end.

Here is how a FAT 32 Flash Drive appears (you also get results for your internal hard drive, but I omitted those here)

```

Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdb: 4008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4008MB  4004MB  primary  fat32        lba
```

---

### Post by Dennis N on 2014-02-12
> **Odyssey1942 said:**
> Thanks, MB. It shows to be ntfs.

Dennis, does this make the issue that you alluded to go away? Thanks.

My article says the problem is with FAT file systems and says nothing about NTFS, so let's assume it will not be a problem.

---

### Post by Odyssey1942 on 2014-02-12
gparted -l confirms ntfs, so I trust I am good to go.

Hope to get replies to my questions in post #15. Thanks.

---

### Post by monkeybrain20122 on 2014-02-12
If your wife is just going to access the backup drive with her Ubuntu system then why format it to a MircoSoft file system (ntfs)? A lot of things will be simplified if you format it to a native Linux file system such as ext4 since you are going to use Linux backup tools.

---

### Post by Dennis N on 2014-02-12
I looked at your questions:

Questions:

a) yes
b) yes
c) yes 

--delete will remove a file on the destination if it does not exist on the source.

remove it if you don't want this behavior.

as to the u, I would leave it in. I use it.

I use the options -rtui with rsync.

In your backup line:

> backup /home/susie/desktop/SusieStuff /media/Iomega_HDD

are you sure desktop is not Desktop? It usually is capitalized. 

Newer versions of Ubuntu would use **/media/user/Iomega_HDD** Check this.

---

### Post by Dennis N on 2014-02-12
Adding option n will give you a simulation. Remove it when you are sure it works ok.
Adding option i will list all changes made.
-naui

As the saying goes, "the proof is in the pudding"

---

### Post by Odyssey1942 on 2014-02-13
MB, I am not against reformatting, but since there is a chance that some of those files might be wanted on our Windows 7 computer that we keep for scanning, itunes (Susie's iPod), and a few other things that I haven't figured out how to do in Linux, and so far haven't found a specific issue with leaving it as ntfs, as well as possible use on daughter's Mac when visiting her, thought to let sleeping dogs lie. What concerns do you have in terms of possible problems? I can probably be easily converted on this.

Dennis, All that very helpful.

You are correct, it is Desktop.

Will set up a simulation tonight when I return and will report back.

Many thanks.

---

### Post by monkeybrain20122 on 2014-02-13
> **Odyssey1942 said:**
> MB, I am not against reformatting, but since there is a chance that some of those files might be wanted on our Windows 7 computer that we keep for scanning, itunes (Susie's iPod), and a few other things that I haven't figured out how to do in Linux, and so far haven't found a specific issue with leaving it as ntfs, as well as possible use on daughter's Mac when visiting her, thought to let sleeping dogs lie. What concerns do you have in terms of possible problems? I can probably be easily converted on this.
.

If you need to interface with Windows then by all means. Since you didn't mention it in the first post I assume it is just strictly for backing up files from Ubuntu, in that case it makes no sense to use ntfs.

---

### Post by rewyllys on 2014-02-13
Odyssey, I suggest that you take a look at LuckyBackup, which is in the Ubuntu repository.  

LB is an easy-to-use GUI for rsync, with the additional advantage that it also incorporates Cron, so that once you have defined the task(s) that you want performed by your backup, you can easily set up a schedule for performing the backup.  And you can define a number of different backups, for different purposes, on different schedules.

I've used LB for at least 3 years now, and it has performed flawlessly.  I've set my primary backups to run daily at 01:00, a time when I'm almost always asleep, i.e., not using my computer.  

Rsync is very reliable, and LuckyBackup provides a convenient way to employ it.

---

### Post by Odyssey1942 on 2014-02-13
Will definitely add that to my list of alternatives. Have you had any experience with grsync or Unison, and if so, how does Lucky compare? Clearly the scheduling aspect is attractive.

Had planned to implement the rysnc tonight but the missus has decided to "sort out" all her folders (early Spring Clean), and I am going on the road probably before she completes, so this will need to be finished up when I return, assuming that she had completed her reorganization. Will report whenever that might be. 

Thanks for all the help to date.

P.S. for rewyllys, I may try  LuckyBackup on my own computer once I can sort out my earlier post (  "Where did my network drive go?"  ) and locate the NAS drive.

---

### Post by rewyllys on 2014-02-14
> **Odyssey1942 said:**
> . . . . Have you had any experience with grsync or Unison, and if so, how does Lucky compare? . . . . 
Sorry, but I haven't looked carefully at either grsync or Unison.

---

