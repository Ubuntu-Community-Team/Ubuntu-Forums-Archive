---
title: "Help!! Uninstalled python 3*"
date: 2019-01-23
forum: New to Ubuntu
---

### Post by patrick1610 on 2019-01-23
Hi, 

I wanted to install Tautulli on my Ubuntu system. In the info page it said to make sure Python 2.7 is installed, but 3.* not. 
I googled how to uninstall python 3 and the command was something with python3*. 
After I ran this, firefox, terminal, settings, Plex and many other apps disapeared and I'm in a lot of stress!
What to do now? 

I see Plex is still running (accessible through the iOS app), but the icon is disappeared..

Now that the screen has locked I only authentication errors..

Can I save my setup without starting all over?

Regards, 

Patrick

---

### Post by oldfred on 2019-01-23
Did you not see when you uninstalled python3 that it essentially uninstalled the entire desktop.
Ubuntu uses python3 by default now.

It used to be if you uninstalled python, you just had to reinstall as everything was broken including Internet access.
If you can get to terminal try reinstalling the entire desktop.

#Make sure everything else is updated:
       sudo apt update
sudo apt upgrade 
#Install desktop:
sudo apt install        ubuntu-desktop 

If you cannot run sudo, then you have to use live installer and chroot into your system and run the update commands.
If UEFI you also have to mount ESP. Otherwise older instructions also ok.
      
  chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2, you should not need to reinstall grub, but run the other repair commands posted above.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by monkeybrain20122 on 2019-01-23
I think you misunderstood the instruction. It seems to  mean the software uses python2 rather than python3 so make sure that is installed instead of 3 to run this software. That  just means your software does not use python3, it doesn't mean you can't have python3 and python2 coexisting in your system.

It would be very weird indeed if software x says install me then you can't have software y (which is not a version  of x) The dev of software x shouldn't have the power to tell you what *other* software you can or cannot install in your system.

In Ubuntu both python 2 and 3 have to be installed. if you type python that means python2, to use python3 you have to explicitly type python3.

---

### Post by patrick1610 on 2019-01-24
I indeed think I misunderstood that part.. It was so screwed up that I was not able to fix it.. 
Thanks for the support, but I didn't manage to save my install! I have now installed Ubuntu clean and set it up again! 

I also use the built-in backup app now to save my setup. (or are there better alternatives for a backup solution?)

---

### Post by oldfred on 2019-01-24
There are many ways to backup.
Some like images, most of us use some sort of script like rsync, or rdiff.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 
    
       Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)

---

