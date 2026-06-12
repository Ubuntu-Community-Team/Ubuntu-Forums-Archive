---
title: "Make An ISO Of Current Configuration"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by iancvt552 on 2014-08-06
Hi,
A couple of weeks into life with Ubuntu and know at some point I'm going to make a hash of things. So please can someone let me know how to create an ISO of my 14.04 build as it stands and then burn it onto a DVD.
Learnt a lot already but still keen to go further. Thanks

---

### Post by ian-weisser on 2014-08-06
Several unsupported tools exists to do that, but it seems a complex solution to your described problem.

Would regular backups accomplish the same goal? Ubuntu has a backup/restore utility built in....

---

### Post by iancvt552 on 2014-08-06
If it means I don't have to go back to day 1 yes it would probably do the job. Thanks

---

### Post by sudodus on 2014-08-06
Yes, that is the idea with backup :-)

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Creating an iso file usually means that you make your own linux 'distro' or 're-spin', so that it can be installed in other computers with your tweaks.

---

### Post by iancvt552 on 2014-08-06
Great link thank you

---

### Post by yancek on 2014-08-06
The best software for that was remastersys which worked up to version 12.04.  It is no longer being developed as it was a one man show and he got little support/help but lots of demands.  If you have a newer version of Ubuntu, it probably won't work.  Using remastersys, you could create an iso of an installed system from that same system and put it on a flash drive or CD/DVD.  You could do this using grubmkrescue from another Ubuntu install with your original system mounted but that would entail manually creating a boot (grub.cfg) file.

The only system I am aware of that has something like remastersys is PCLinuxOS, enter a single command from the installed system and it creates the iso.

---

### Post by oldfred on 2014-08-06
discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

With Windows it can be difficult to reinstall and may take a full day.
But with Ubuntu you can reinstall very quickly.
So my backup is not to use space for system when I already have the Ubuntu ISO and just backup my data, and any configuration changes I may have made.

With Linux user data and most application data is in your /home. So backup /home. If you are running a server you then may have applications in / (root) and that is different. 
And if you manually edit system wide configurations like grub menu, video or Internet configuration you may want to back those up also.

I prefer to use a script using rsync, but there also is a gui version grsync.

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

I started with this simple script and then over time added a few things:

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

### Post by tea for one on 2014-08-06
> **yancek said:**
> 
The only system I am aware of that has something like remastersys is PCLinuxOS, enter a single command from the installed system and it creates the iso.

It is a pity that Remastersys is no longer being maintained, however there is an alternative for consideration:-

Systemback

More info via this website [http://www.unixmen.com/systemback-restore-linux-system-previous-state/](http://www.unixmen.com/systemback-restore-linux-system-previous-state/)

Developer's launchpad [https://launchpad.net/systemback](https://launchpad.net/systemback)

I have tried it and it seems to work OK although I have not _extensively_ tested the re-installed ISO yet.......

---

