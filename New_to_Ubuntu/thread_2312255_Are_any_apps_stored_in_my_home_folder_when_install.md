---
title: "Are any apps stored in my home folder when installed?"
date: 2016-02-03
forum: New to Ubuntu
---

### Post by sbtypo3 on 2016-02-03
Related to my [last question]("http://ubuntuforums.org/showthread.php?t=2311611"), I just made a new partition on my SSD and want to move my steam games there as they seem to have been installed in my home folder (hdd).

But could there be anything else there??? Gimp? Inkscape? Are all apps installed via the software center in the / root drive somewhere? What about apps that I installed via the software centre with a deb file that I downloaded? Are they in my home folder too?

Thanks for your help!

---

### Post by mcduck on 2016-02-03
Anything coming from the package management is installed for all users of the computer, so their files will end in various system directories. It makes no difference if you use the software center, Synaptic, apt-get or directly install a .deb package (in the end all of the systems install .deb packages anyway, it's all part of the same system).

Steam is a bit different because it works outside of the package management system, and only installs the games for the user running Steam. Since the users won't have write access to anything than their own home directories, that's where Steam will create it's apps directory by default. You can select different locations in Steam's settings if you want to, as long as you have the suitable permissions for that location Steam will then give you the option to pick which location to use when you download a game. (Pretty nice for individual user, but of course if you have multiple users on a computer, and they all want to play the same game, it'll actually end being installed multiple times, and waste a lot of space because of that...)

edit: All applications you *use* will then create their user-specific configuration files and things like that inside your home directory, as they belong to you only, not the system or any other user on the computer.

---

### Post by sbtypo3 on 2016-02-03
About: "All applications you *use* will then create their user-specific  configuration files and things like that inside your home directory, as  they belong to you only, not the system or any other user on the  computer."

About once a month I copy all my files on to an external Harddisc

I have just been copying all the folders I see in my home folder. Should I also be copying the hidden .files too? If yes, which ones or just all of them? Some of the require quite a lot of space but I think this is mainly steam which I plan on moving anyway.

---

### Post by Vladlenin5000 on 2016-02-03
Those hidden folders are the ones containing the "user-specific configuration files and thing like that". Some programs also create regular (visible) folders in your userspace, mostly for their own outputs, but configuration / user profiles are usually stored hidden. So, yes, if you need configs/profiles backed up then you should also backup all the relevant hidden folders.

---

### Post by oldfred on 2016-02-03
Firefox & Thunderbird profiles are some of the larger hidden folders in /home.
I have moved them to a /mnt/data partition or a NTFS partition when still booting XP years ago.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by mcduck on 2016-02-03
If you want to keep your program settings, browser bookmarks & history and that kind of stuff, then yes, making backups of the hidden files & directories is a good idea.

Most of them should be just some simple text files and practically take no space at all, the only bigger ones would usually be things like your Steam folder, and maybe web browser's cache (both of which you can leave out anyway if you want). Also leave the ~/.gvfs alone, that's used by Gnome for mounting removable drives and things like that so there's no need to copy it, and trying to do so would just give you an error anyway...

---

