---
title: "New to Lubuntu, question about docx and increasing size of things"
date: 2020-07-07
forum: New to Ubuntu
---

### Post by hrafnagudh on 2020-07-07
Hello all!
First of all, I am glad I finally got to have a Lubuntu partition on my pc. My intention is to primarly use it for university work and other important stuff. 
I am slowly learning new things (I installed it yesterday so I am a true beginner), but I have a pair of questions, the answer of which I struggle to find on the internet

1 about LibreOffice: I updated a curriculum vitae, the original file was docx, and Libreoffice saved it as a ODS or something. Is there a way to save it as a docx? Problem is not for me, just for those times I will have to send something to my university teacher, and I want to avoid compatibility issues with his corrections or something similar. Also, I use mendeley, I noticed it has a "Export MS Word Compatible", but when I use it, I get an archive, not a wordfile. 
Finally about LibreOffice, I got stuck for a moment with the pdf export problem, I found a solution that, I think, downgraded Libreoffice (it was a sudo purge libreoffice thing), is it possible? The save windows for example was very different after the purge. 

2 things are a little too small. Nothing terrible but expecially when clicking small icons, or write in small spaces is sometimes difficult. For some reason, firefox address bar is a little bigger and just fine. There are lots of settings to tweak in, where do I find those about the display?

3 I can't wait to learn how to personalize everything, where should I start? :D

Thank you for the future help, sorry if my post is not in the right place or if it is redundant

---

### Post by CelticWarrior on 2020-07-07
Welcome.

You can save in any format you want including the original docx, just pay attention to the saving dialog.
Keep the original format which is supported by Libreoffice and you won't need any export feature.
Export to PDF also works fine. What was the problem exactly?

Additional note: Although Libreoffice has had support for DOCX for years and it mostly works, many have argued that WPS support for that Microsoft format is better. WPS is free software that you can install now from the software store or with the deb file they provide at [http://linux.wps.com/#](http://linux.wps.com/#)

---

### Post by GhX6GZMB on 2020-07-07
Yes, welcome.

1: Concerning .docx: what CelticWarrior said. With exporting .pdfs there have been issues and a bug report exists. Mine works fine, though. With Mendeley I can't help.

2: Desktop icon size can be changed in Preferences -> LXQt Settings -> Desktop. Icon size in the Panel (the bottom line on your screen) is done by right-click on the Panel, select Configure Panel.

3: Perhaps build your desktop and panel? It's a simple drag 'n drop from the Applications Menu (click the bottom left corner icon). Then right-click on the desktop icon and tick "Trust this executable".
 I attach a shot of my own desktop (wallpaper is 18.10, but OS is 20.04 LTS. Another customization :) )

---

### Post by hrafnagudh on 2020-07-07
Thanks for the answers :)
The pdf problem, as I understood reading around, is a compatibility problem between Lubuntu  20.04 and the version of Libreoffice that is already installed.
I found the docx, silly question, sorry...now I'm trying to find software store, and learn how to install programs :-s
For example: I have two programs at the moment, Mendeley and Starsector. Mendeley I just copy the executable (a python script) on the desktop and it works. Starsector has a .sh file, I understood how to use the terminal to start it (cd to folder, then sudo sh), but do I have every time to do that or there is a way to create a shortcut?

---

### Post by GhX6GZMB on 2020-07-07
The "software store" is the Muon package manager. That's the place to start

---

### Post by TheFu on 2020-07-07
Probably shouldn't run any end-user programs with sudo. There are often repercussions that are unintentional.  sudo is for administrative needs and generally shouldn't be used for any gui programs.

Unix systems have something called a symbolic link.  This has been available for 40+ yrs.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) covers most power-user needs.

---

### Post by monkeybrain20122 on 2020-07-07
> **CelticWarrior said:**
> 

Additional note: Although Libreoffice has had support for DOCX for years and it mostly works, many have argued that WPS support for that Microsoft format is better. WPS is free software that you can install now from the software store or with the deb file they provide at [http://linux.wps.com/#](http://linux.wps.com/#)

WPS is an adware I would recommend against it (I checked it out om Windows VM and deepin Linux). It is "free" as in a shareware, but certainly not  open source. "free" can mean different things on different forums, on a Linux forum I would assume it means open source. I have never had problems with pretty standard .docx files using LO. Unless there are some unusual formatting I don't think there is a problem. Moreover I have sent around ods at work and at school, no one ever complained. MSO is supposed to be able to open them now, why perpetuate MS's locked down format if don't have to? WPS doesn't support ODS so it helps to spread MS formats even without being MSO, this is a deal breaker for me.

---

### Post by Impavidus on 2020-07-08
> **hrafnagudh said:**
> Is there a way to save it as a docx? Problem is not for me, just for those times I will have to send something to my university teacher, and I want to avoid compatibility issues with his corrections or something similar. Also, I use mendeley, I noticed it has a "Export MS Word Compatible", but when I use it, I get an archive, not a wordfile. 
Finally about LibreOffice, I got stuck for a moment with the pdf export problem, I found a solution that, I think, downgraded Libreoffice (it was a sudo purge libreoffice thing), is it possible? The save windows for example was very different after the purge. 

Exporting to docx is supported, but it's recommended to save it for yourself in a native file format. I don't think I ever encountered any university teacher who wanted MS office format (or any other office format). It's all plain text (and pdf, if no further editing is required). Science journals want their submissions in LaTeX, so that's what everybody uses. But maybe that's only the case at science faculties.

> **hrafnagudh said:**
> now I'm trying to find software store, and learn how to install programs :-s
For example: I have two programs at the moment, Mendeley and Starsector. Mendeley I just copy the executable (a python script) on the desktop and it works. Starsector has a .sh file, I understood how to use the terminal to start it (cd to folder, then sudo sh), but do I have every time to do that or there is a way to create a shortcut?The software store, or synaptic, or apt, can install software packaged for Ubuntu and all its flavours. This typically comes from the official Ubuntu repositories, but if you wish you can add third party repositories. Try to avoid that, as it may destabilise your system.

Your two programs appear to be unpackaged software. It can be properly installed, but there are no hard rules for how to do that. You must put the executable file in a directory that's in your PATH (but I suggest you don't put it in /bin, /sbin, /usr/bin or /usr/sbin, which are reserved for packaged software), make it executable and put any other files belonging to that software in a place where the executable can find it. That allows you to run the software from terminal. If you wish, you can create a .desktop file, so you can make a nice launcher that works from a menu and has an icon.

Software that's not for system admin shouldn't be run with sudo. If it doesn't work without, I guess running it once with sudo changed ownership of some files, making it necessary to run it with sudo always. Check for root-owned files in all directories used by that software and change ownership back to you. Everything in your home directory (/home/username) should be owned by you.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hrafnagudh on 2020-07-08
Ok, I understood. sudo is an admin thing. 
I found the Muon package, there is a lot of stuff!:eek: 
Well, I will read the book TheFu linked, to lean new stuff.
Meanwhile, thanks all for the answers and the patience. It looks a little...overwhelming at first, but in a very positive way :D

edit, last thing that puzzles me, sorry. On some websites, under the linux installer section for a program, there are two ways, generic linux and ubuntu. Lubuntu is still Ubuntu, even if it is using another environment?
Similarly, in the Muon package  manager, categories are like desktop GNOME, desktop Gnustep, desktop Xfce. Is all of that Lubuntu compatible? Sorry if it is the dumbest question you ever read....

---

### Post by TheFu on 2020-07-08
None of your questions are dumb.  And don't worry, you will ask some in the future. We all do both when we start out **and** 20 yrs later.

iOS, OSX, Android are all Unix-like as well and follow the same file and directory permissions model, so learning that is not a waste of your time. The sooner you get that knowledge, the quicker you will end the frustration for not understanding when and how and why sudo is needed, when root is useful and when to swap to a different account - say to run a web server or email server or 50,000 other needs.  File and directory permissions are the front-line of all Unix system security, including for Lubuntu.  A slight mistake can trash your total system security, so be very careful using sudo with chown or chmod.

Unix is overwhelming and there is a steep learning curve. It is like learning a new language.  Some ideas are similar, but different. Other ideas are completely different, though they sound similar.  If you are coming from Windows, about 80% of what you think is similar is not.  Unix/Linux has a completely different philosophy around the OS and programs than Windows.  Unix systems can't tell if the command you've entered is stupid or genius, so they are allowed.  We all hope that our stupid commands are harmless, but that isn't always the situation.  These forums have people looking to correct their stupid mistakes, usually where they've destroyed data, almost daily.

So, please learn this next thing ASAP and follow though to solve it.  There are "restore points" for Linux and Unix systems. They are not automatic and we just use a different name - we call them **system backups**.  If you have anything on your system that cannot be lost, back it up.  It is best to **have daily, automatic, versioned, backups.**  The more critical an item is, the more likely you will lose it the night before you need it. We see this all the time.  At a minimum, setup daily, automatic, versioned, backups for your HOME directory.  This can be accomplished a few ways, depending on your desires.  Over time, you can expand that to include other stuff to make restoring a complete system easier.

Simple script for versioned backups of all HOME directories to $TARGET storage:

```
#!/bin/bash
SOURCE="/home"    # What to be backed up
TARGET=/mnt/Backups/$HOSTNAME  # Where to write the versioned backups
HOWMANY="90D"   # Retain backup versions for 90 days. Change to less or more, as needed

# May want to mount storage at this point in the script

# Ensure the target location exists. Best if this has a different HDD mounted to /mnt/Backups/
#   Do not use NTFS or FAT32 or vFAT or exFAT storage.  Use native, linux, storage like ext4, xfs, f2fs 
#    which supports full Linux permissions.
/bin/mkdir  -p "$TARGET"

# Do the verioned backup
/usr/bin/rdiff-backup     --exclude-special-files       "$SOURCE" "$TARGET"

# Remove the old backups 
/usr/bin/rdiff-backup    --force   --remove-older-than  "$HOWMANY" "$TARGET"

# May want to umount storage here

```

Pretty freakin' easy, right?

[LIST=1]
[*]I'd create this file as /root/bin/backup-home.sh, then 
[*]chmod 700 /root/bin/backup-home.sh it and 
[*]setup root's crontab to run it daily, perhaps a noon (when at lunch or midnight or 6am).  
[/LIST]

The first run will take as much time to run as a copy/rsync.  All runs after that should take 1-7 minutes, but depends on the changed data in the source.  It is best NOT to keep media (video/music) in the HOME directory, since large files will stay around in the backups for $HOWMANY days.
You might want to have specific directories in an --exclude list.  Things like browser caches, temporary files, stuff like that.  The script needs to run as root to maintain permissions, ACLs, for different userids.
To keep the script simple, I didn't show multiple directories in the backup SOURCE. It would be smart to include /root/, /etc/, and /home/ is a slightly more basic backup list.

I should mention, I didn't test this script, but think it should run fine to backup all normal user's stuff in /home/.  rdiff-backup can have the source be a remote system or the target can be remote. Prefer to use "pull" over "push" backups whenever possible. This will mitigate hacked client systems with malware from causing corrupted backups.

---

### Post by Impavidus on 2020-07-08
> **hrafnagudh said:**
> 
edit, last thing that puzzles me, sorry. On some websites, under the linux installer section for a program, there are two ways, generic linux and ubuntu. Lubuntu is still Ubuntu, even if it is using another environment?An installer for Ubuntu typically means that they offer a .deb file that integrates nicely with the official Ubuntu repositories. Lubuntu uses the official Ubuntu repositories, so that should work. It may even work on other distros that use .debs.
> Similarly, in the Muon package  manager, categories are like desktop GNOME, desktop Gnustep, desktop Xfce. Is all of that Lubuntu compatible? Sorry if it is the dumbest question you ever read....Most of it is compatible with Lubuntu. Maybe even all. But it may result duplicate applications and libraries, so it may not be very efficient use of your hard drive and memory. If some package is truly incompatible with Lubuntu, the package manager will tell you it has to remove lubuntu-desktop or something like that to satisfy dependencies.

---

### Post by hrafnagudh on 2020-07-08
Well....let's say I will learn how to do the backup code thing. :cry:
About  muon, I'm struggling finding anything online about it, my biggest  question is, how do I choose where to install the stuff (I have a  partition made for programs and staff, the partition for lubuntu is not  very big, and I wish to use it just for the os to avoid complications)?  There is a link to muon manual but redirects me to a page that says muon  doesn't exist...

---

### Post by Dennis N on 2020-07-08
> **hrafnagudh said:**
> Well....let's say I will learn how to do the backup code thing. :cry:
About  muon, I'm struggling finding anything online about it, my biggest  question is, how do I choose where to install the stuff (I have a  partition made for programs and staff, the partition for lubuntu is not  very big, and I wish to use it just for the os to avoid complications)?  There is a link to muon manual but redirects me to a page that says muon  doesn't exist...

The application packages (called .deb packages) you get through muon contain information on where to put the various files in the package. It's all automatic. You don't get to choose where to install.

---

### Post by Impavidus on 2020-07-08
How big is your not-very-big Lubuntu partition? If it's at least 20GB, that should be enough for OS plus applications. A separate partition for applications complicates matters, so don't. Anyway, there isn't a clear distinction between OS, tools and applications.

If you've got an application that needs a huge load of data, there are ways to move that data to a separate partition.

---

### Post by GhX6GZMB on 2020-07-08
> **Dennis N said:**
> The application packages (called .deb packages) you get through muon contain information on where to put the various files in the package. It's all automatic. You don't get to choose where to install.

^^^ This.

DON'T fiddle with where programs and associated files are located, leave this up to Muon, sudo apt-get install and your PPAs. Otherwise you'll have to do a complete reinstall very soon (ask me how I know, I was in your position about a year ago...).

The only thing you can do is think about how your $HOME directory structure should be set up, everything else is predefined and automatic.

> **Impavidus said:**
> How big is your not-very-big Lubuntu partition? If it's at least 20GB, that should be enough for OS plus applications

That's also what I thought until I started playing with CAD programs. I had to increase my / partition to 30 GB. But that's more of an exception, I guess.

Concerning backups: you actually need two:
One for backing up all your system setups and configurations.
A second one for backing up your stuff in your /home directory structure.

Why two? Well if you combine them because you've done some "optimizing" of your system that failed (this will happen a lot until you've used Linux for 30+ years) and do a restore, your /home directory will also be overwritten, including your latest documents.

For the system backup I recommend Timeshift (available in Muon). It's a GUI backup system based on rsync, which means it makes incremental backups (only changes are backed up). With Timeshift you can always do a rollback to a previous system state, which gives peace-of-mind when experimenting. By default it excludes /home and /root from backups, which is as it should be.

For document backups for /home and /root look around. there are plenty of programs available.


Last, here's a nice link to understand the Linux directory structure:
[https://www.thegeekstuff.com/2010/09/linux-file-system-structure/](https://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

---

### Post by hrafnagudh on 2020-07-09
It is 130 gb, but I'm thinking about the risk of installing too much of everything in the future...
Well, guys, thanks all for the help. I will start with Timeshift for the backup, and then look for the others :)
Have a nice day all!

---

### Post by Impavidus on 2020-07-09
Many laptop/desktop users (like me) only backup their home directory (skipping things like cache and compiled stuff). I haven't customised my system a lot, so if it breaks and I can't fix it (never really happened to me, but I'm the type who learns by reading, not by falling), I just reinstall. As you never log in as root, /root (=root's home directory) is mostly empty.

---

### Post by TheFu on 2020-07-09
> **hrafnagudh said:**
> It is 130 gb, but I'm thinking about the risk of installing too much of everything in the future...
Well, guys, thanks all for the help. I will start with Timeshift for the backup, and then look for the others :)
Have a nice day all!

130GB!!!

The OS should easily fit in 25G.

HOME directories can be an size needed, but I think of that as only stuff I created, that isn't media files, so it is hard imagine that to be larger than 25G.  Then the "big stuff" gets placed elsewhere, not on any desktop system, but on network storage that appears to be local storage ... but isn't.

For a desktop, I'll usually setup storage in this way:
```
$ dft  # df -hT with uninteresting loop/etc removed
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/sda2                       ext2  721M  185M  500M  27% /boot
/dev/sda1                       vfat  511M  3.7M  508M   1% /boot/efi
/dev/mapper/ubuntu--vg-root     ext4   25G   12G   12G  52% / 
/dev/mapper/ubuntu--vg-home--lv ext4   74G   21G   51G  29% /home 
/dev/mapper/ubuntu--vg-stuff    ext4   99G  367M   93G   1% /stuff
```

Don't worry too much about the left column. I use LVM as a volume manager. Think of those as extremely flexible partitions. For now, that's close enough for the root, home and stuff logical volumes.  /boot and /boot/efi are just standard partitions.

[LIST]
[*]/boot  700+MB for kernels
[*]/boot/efi   500MB or much less for EFI boot stuff (FAT32)
[*]/     25GB to hold the OS, applications, system settings
[*]/home   25Gx{number of users} Whatever is needed, but usually 20G is enough for each userid.
[*]/stuff    Storage not created by a human. Think areas for game data, media, and other large files.
[*]swap    4.1G on every desktop system. I have many reasons, but mainly because less swap on a desktop without 16G+ of RAM will lead to crashes and unexplained lockups. That's been my experience.
[/LIST]

Where things are places isn't really all that important, because we can easily move it around or if using LVM, add more storage to existing mounts, or just create a symbolic link from where we want the files to appear ---> where the files actually are.

For example, say I keep a 4th copy of some Music in /stuff/Music and want to access it from /home/thefu/Music.  That's trivial.  
**ln -s /stuff/Music ~/** is the command.  Best of all, my backup tool knows to save the symlink, but not follow it, so I don't get a 5th copy of Music in the backups.  MS-Windows tried to do something like this with "Libraries", but those were only dotNET-GUI capable. The NTFS file system didn't have those capabilities so anyone not using the GUI didn't have "Libraries" which merged locations.  I understand that MSFT fix that a few years ago in NTFS by adding the idea of symbolic links.  Unix has had them and used them widely for 40+ yrs.

I won't pretend that my list of storage above is THE only way to do it.  There are times when I need to make /var/ a separate mount to hold a DBMS or virtual machines, so I'll create storage for that and mount it where it is needed.  Storage needs to be flexible.

Why bother with all this?  It makes backups cleaner.  Backing up the OS is different from backing up user files.  Some files don't need to be backed up, so I keep those in places that are different too. Nobody needs 50 exact copies of the same files in their backups, but we do want 50 versions that can be easily restored if the files change slightly over time.

---

### Post by hrafnagudh on 2020-07-10
> **TheFu said:**
> 130GB!!!

The OS should easily fit in 25G.


I know but I wanted to be sure :P
I almost understood the soft-hard links thing, and learning how to stop worrying and to love the terminal commands

---

### Post by TheFu on 2020-07-10
> **hrafnagudh said:**
> I know but I wanted to be sure :P
I almost understood the soft-hard links thing, and learning how to stop worrying and to love the terminal commands

[https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link)  I haven't used a hard-link in about a year.  I use symlinks weekly - aka soft-links or symbolic links.  But often, there are other methods to make accessing directories and files quick like the **cdpath** or shell **aliases**.

As for CLI commands (actually, don't need a terminal to run them), we use them here since 
[LIST]
[*]Lots of different GUIs are available, each slightly different
[*]No need to post 20 huge images to explain something 1 copy/paste CLI command will do
[*]CLI commands work on "Servers", which don't have any GUI.
[*]CLI commands work over network connections like ssh, which usually doesn't have any GUI.
[*]CLI commands seldom change, whereas the GUIs seem to completely change every 3 yrs for no good reason. I'm using the same CLI commands today for end-user stuff that I used in 1993. Master the CLI and you'll find a GUI bloated and slow for about 98% of what you need.
[*]CLI stuff is always available. A GUI may not be.
[*]Usually, a GUI provides only 20% of the capabilities compared to the CLI interface.
[*]It is much harder to automate any GUI than every CLI command.  I can schedule a program to do work for me, daily, and have that work waiting for my review 1000x easier than using a GUI.
[/LIST]

Once you learn some tricks of your chosen shell, probably bash, you'll discover that you don't really type much at all. Bash has command completion, so I only need type 2-3 characters + {tab} to have what I want filled in, correctly. Only valid directories, valid filenames, and valid options are possible ... no more typos.  Basically, almost every command has a built-in little helper to ensure I cannot ask for the wrong answers.  Of course, on very minimal systems, tab-completion isn't enabled, so I make the same mistakes that a beginner would there ... until I load the tab-completion package (if I can).

These will get you started:
[LIST]
[*][https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)
[*][http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
[/LIST]

---

### Post by hrafnagudh on 2020-07-13
Thank you :)

---

### Post by cmcanulty on 2020-07-13
In libre office open any of the programs like writer and you can set the preferred way to save any file. So go to tools-options-load- save-general-then in the drop down box choose text document and below that always save as. Then the same for spreadsheets or any libre office type. All can be done from writer no need to open each type of office document. I still make mine save as .doc because anyone can open that from anywhere. ODF is also pretty universal but most people don't know what that is and they freak out if they see that type of document.

---

### Post by hrafnagudh on 2020-08-07
My only problem with ODF was exactly that people complains sometimes about it not being the classical docx. And I was a little prejudiced too, since some years ago I tried Libreoffice and had big compatibility problems, expecially in the format. 
But now I had no problem, I also solved my Mendeley issues with the docx I am keeping working on

---

### Post by kurt18947 on 2020-08-07
> **cmcanulty said:**
> In libre office open any of the programs like writer and you can set the preferred way to save any file. So go to tools-options-load- save-general-then in the drop down box choose text document and below that always save as. Then the same for spreadsheets or any libre office type. All can be done from writer no need to open each type of office document.** I still make mine save as .doc because anyone can open that from anywhere.** ODF is also pretty universal but most people don't know what that is and they freak out if they see that type of document.

This used to be the recommended method for creating MSOffice editable files in Libre Office. LibreOffice would read .docx files correctly, it wouldn't always create .docx files correctly. DocX is not a static file format, there are versions being created - I think a new version was released recently. .doc seems to be a static file format, it is not longer being "improved" by Microsoft so is not a moving target to emulate. If a document doesn't need to be editable, .pdf is my preferred file format. I've never had any complaints about it.

Another thing you could try to improve MSOffice compatibility would be to install MS Core fonts. That package includes fonts like Arial and Times New Roman. Older but MSOffice users should have them on their machines so one less incompatibility.

---

### Post by cmcanulty on 2020-08-07
Also in libre office you can go to tools-options-load save-general and set it to automatically save it to any odf or any microsoft format. You can set all the apps from any of the libre office parts

---

### Post by TheFu on 2020-08-08
Microsoft Word has supported ODF for some time, BTW.  Best to avoid proprietary data file formats. Stick with open standards, so any program of a similar type can use the data.

---

