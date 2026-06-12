---
title: "Dual-boot: Recovery/Backup image?"
date: 2018-01-28
forum: New to Ubuntu
---

### Post by antttren on 2018-01-28
Hi, I apologize if this question has a well known answer but since this is the new to Ubuntu section I figured I'd give it a go. 

Say I have Ubuntu 16.04 running as a dual-boot (or as the only operating system on a computer), I've just downloaded all the packages and applications I'll ever use and all my important files are automatically being synced with Insync to Google Drive. This is the state of my system at the moment.

Is there a way to make a bootable USB such that the current state of the Ubuntu system can be saved to it, and in the event of some error causing the operating system to tweak irreparably I can simply boot off this USB, install Ubuntu once again and have all my settings, packages, and applications exactly as they were at the moment of the creating of this USB? 

That would be fantastic and I'd love to hear if this is possible, or if something similar can be done in Ubuntu.

---

### Post by cruzer001 on 2018-01-28
A partial answer to your question would be Synaptic Package Manager to save all loaded packages.

[https://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation](https://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation)
```

sudo apt install synaptic
```

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)

---

### Post by oldfred on 2018-01-28
I use rsync to backup /home and my /mnt/data partitions.
I have in the rsync script the dpkg export of installed applications.
I do edit a couple of files in /etc, but manually copy them into /home so backed up. /etc is not large and you can back up entire /etc, but if doing a new install, settings may not be exactly the same, so only use for reference if new install.

Some like an image backup, but that quickly gets obsolete.
 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 

      
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

