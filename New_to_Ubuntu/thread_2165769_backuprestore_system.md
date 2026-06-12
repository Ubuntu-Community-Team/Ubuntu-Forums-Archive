---
title: "backup/restore system"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by amigoface on 2013-08-06
hi
i am using ubuntu 13.04 and i am seriously considering to migrate too :)
now !, is there any way to backup/restore mechanism for the system configuration

what i want is to backup all my system config/drivers... etc , (not the data),
so if something goes wrong (bad drivers installation, bad updates, ... etc), i can restore my config

i had this issue two times, my desktop completly gone after some drivers installation ,I managed to recover my system after searching on the internet with my windows partition, 
but the second one did'nt, i had finally formated and installed the system again :(

thanks for your help and good day

---

### Post by Vladlenin5000 on 2013-08-06
I usually create a full system backup with Clonezilla.

---

### Post by ibjsb4 on 2013-08-06
Cloning your system with [clonezilla ]("http://clonezilla.org/")works well, just remember that you cannot mount the clone while using the original as they have the same [uuid]("http://en.wikipedia.org/wiki/Uuid") ([also]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uuid&sa=Search&cof=FORID:9")) and will confuse your system.

Another way to save most of your configurations is to create a [separate home partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=separate+home+partition&sa=Search&cof=FORID:9").

You can also create a [backup of all installed apps]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup+installed+packages&sa=Search&cof=FORID:9") (packages).  My preferred way of doing this is with [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") and creating a [markings list]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=markings+list+synaptic+package+manager&sa=Search&cof=FORID:9").

And last, [a general reference]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=system+backup&sa=Search&cof=FORID:9").

And welcome to the forums :)

---

### Post by oldfred on 2013-08-06
I use rsync to backup /home, parts of /etc that I manually edit and anything else I manually do inside /. But the vast majority of what you need is in /home. The list of installed applications also makes reinstall easy.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Some like full image, others like regular updates as full images get old quickly. Some use a combination.

      
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)


 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

      
 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

      
 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

