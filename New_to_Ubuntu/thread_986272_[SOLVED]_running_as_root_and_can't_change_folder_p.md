---
title: "[SOLVED] running as root and can't change folder permissions"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by simtaalo on 2008-11-18
the external hard drive i use to store my torrents has suddenly thrown up errors when running in ktorrent, saying folder is read-only.

i've run nautilus as root to go in and change the permissions on the folder and had this error thrown up

```
 sorry, couldn't change the permissions of *** : Error setting permissions: Read-only file system
```

this was running fine before, permissions were fine before but this has just recently done this. how can i fix it?

---

### Post by Keith Hedger on 2008-11-18
Your HD has some sort of error on it so the system mounted it read only (like a cd) so u wont be able to change anything on it untill u correct the errors umount it and run fschk on it

---

### Post by simtaalo on 2008-11-18
> **Keith Hedger said:**
> Your HD has some sort of error on it so the system mounted it read only (like a cd) so u wont be able to change anything on it untill u correct the errors umount it and run fschk on it

could you give me the terminal commands? seems like it would be useful to learn for future use

---

### Post by handydan918 on 2008-11-18
> **Keith Hedger said:**
> Your HD has some sort of error on it so the system mounted it read only (like a cd) so u wont be able to change anything on it untill u correct the errors umount it and run fschk on it

That seems like a bit of a leap.


Perhaps the OP could show us his /etc/fstab?

---

### Post by simtaalo on 2008-11-18
/etc/fstab here 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3c5f65f2-35a5-46a8-a93d-2391e926c2bd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cdf22e15-54f2-48eb-a7da-ca00d3493d20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by simtaalo on 2008-11-18
i managed to change the settings but when using ktorrent again it somehow threw the error that one of the directories was read-only, anyone else had this error?

---

### Post by Elliander on 2008-11-18
Same thing just now happened to me. Just now actually. And to make matters worse, the torrent didn't download. What a totally useless program. I'd go so far as call it Malware because it locks all of my files. 

I can't install anything now. And my folders say:

"You are not the owners, so you can't change these permissions." and I don't really understand how to undo it.

---

### Post by Elliander on 2008-11-18
How exactly did you manage to undo it?

---

### Post by bodhi.zazen on 2008-11-18
> **Elliander said:**
> Same thing just now happened to me. Just now actually. And to make matters worse, the torrent didn't download. What a totally useless program. I'd go so far as call it Malware because it locks all of my files. 

I can't install anything now. And my folders say:

"You are not the owners, so you can't change these permissions." and I don't really understand how to undo it.

I really can not tell if you are having basic permissions issues or if you are having problems with your partition.

First, do you understand basic permissions ?

        [uhelp]community/FilePermissions[/uhelp]

Second, did you follow what Keith Hedger said ? if your partition has errors it will often be re-mounted read only.

So, to look at this problem we need to know what partition it is (/dev/??), where it is mounted, and the file system (vfat and ntfs are different from linux native file systems).

can you tell us the basic ownership and permissions of the directories and files ?

---

### Post by Elliander on 2008-11-18
I know enough about permissions to go into a folder and a file, and change permissions. I also know that before I tried using torrents I had permissions. Now entire folders say that I don't even own the files.

I think it's pretty obvious that the program in question changed permissions. And that it has nothing to do with corrupt partitions. Furthermore, if it was a problem with the partition, it stands to reason it wouldn't be so selective. I can still download and edit files to and on my desktop. Furthermore, I dual boot with windows xp and my windows folders on other partitions were ALSO changed. But do *NOT* have any problems running under windows xp. 

However, I don't really understand enough about the terminal or it's commands to know how to manually fix anything from there.

P.S. - Yes, I know, I did right-click the files in question, and clicked the check box to allow it to run as a program. The errors I get are that I don't have permission to write to the folders that the program needs to write to in order to install anything.

---

### Post by Elliander on 2008-11-18
hmm. Looks like my problem is worse than the original poster...

> elliander@elliander-ubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied


And here is what I get when I try to install a program: (permission of file allows it to read and write, and for the file to run as a program) 
> 

elliander@elliander-ubuntu:~$ /home/elliander/Desktop/Creatures3/creatures3.run
Verifying archive integrity... All good.
Uncompressing Creatures: Internet Edition..
Uncompressing Creatures: Internet Edition................................................................................
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Creature Labs Technical Support at [http://support.creaturelabs.com](http://support.creaturelabs.com)
/bin/rm: cannot remove `/tmp/selfgz9239/help/Chemical Names.txt': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/help/Sostanze chimiche.txt': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/help/Chemikalien.txt': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/help/Nombres qu\355micos.txt': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/help/Produits chimiques.txt': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/help/Chemische stoffen.txt': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/libSDL_mixer-1.2.so.0': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/imageconvert': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/libsmpeg-0.4.so.0': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/libSDLStretch.so': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/libstdc++-libc6.1-2.so.3': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/creatures3': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/plaympeg': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/langpick': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/creatures3intro': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/libSDL-1.2.so.0': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/lc2e-netbabel.so': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/lc2elib.so': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/bin/x86/lc2e': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/GPL': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/LGPL': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/README': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/SDL_mixer-1.2.0.tar.gz': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/setup-1.5.8.tar.gz': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/SDLStretch.h': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/smpeg-0.4.4.tar.gz': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/SDLStretch.cpp': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/src/SDL-1.2.0.tar.gz': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/postinstall.sh': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/Linux/x86/glibc-2.0/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/x86/glibc-2.1/setup.gtk': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/Linux/x86/glibc-2.1/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/x86/setup': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/x86/uninstall': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/Linux/x86/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/sparc64/glibc-2.1/setup.gtk': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/Linux/sparc64/glibc-2.1/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/sparc64/setup': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/sparc64/uninstall': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/ppc/glibc-2.1/setup.gtk': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/Linux/ppc/glibc-2.1/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/ppc/setup': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/ppc/uninstall': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/alpha/glibc-2.1/setup.gtk': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/Linux/alpha/glibc-2.1/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/alpha/setup': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/Linux/alpha/uninstall': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/FreeBSD/x86/glibc-2.1/setup.gtk': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/FreeBSD/x86/glibc-2.1/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/FreeBSD/x86/setup': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/bin/FreeBSD/x86/uninstall': Permission denied
/bin/rm: cannot remove directory `/tmp/selfgz9239/setup.data/bin/FreeBSD/x86/plugins': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/setup.glade': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/setup.xml': Permission denied
/bin/rm: cannot remove `/tmp/selfgz9239/setup.data/splash.xpm': Permission denied
elliander@elliander-ubuntu:~$ 


There is a whole lot of "permission denied"

And here is another program I tried to install: (where it says password, I assume it wanted my password, but it won't accept any input)

> 
elliander@elliander-ubuntu:~$ /home/elliander/Desktop/Creatures3/dockingstation.run
Verifying archive integrity... All good.
Uncompressing Creatures: Docking Station............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
./dstation-install: line 83: type: creatures3: not found

Docking Station InstallBlast
----------------------------

Installing off filesystem /tmp/selfgz9305/.

Current linux_x86_glibc21 build:
Latest linux_x86_glibc21 build: linux_x86_glibc21_64
Updating to latest version
You do not have write access to /usr/local/games

(You can install to your home directory by setting
INSTALL_DEST to a path before running this script.
e.g. INSTALL_DEST=~/DockingStation BIN_DEST=~/bin ./dstation-install)

Rerunning installation script as root
Password: 
su: Authentication failure
Failed to run "su" with --shell.  This could be because
you got the password wrong, or it could be because su
does not support the --shell option on your distribution.

Trying again without --shell.  If you are using a 
shell other than bash as your standard shell then 
you may have problems.  If so, either upgrade to 
a more recent version of "su" or change root's shell
to be bash.

Password: 


---

### Post by Elliander on 2008-11-19
This is interesting. I am still able to install programs from the Synaptic Package Manager. I just can't install anything I paid for. :confused:

---

### Post by simtaalo on 2008-11-19
> **bodhi.zazen said:**
> 
Second, did you follow what Keith Hedger said ? if your partition has errors it will often be re-mounted read only.


i think this is my problem, keith said something about running fschk, but having to unmount it first. i know how to unmount it through the gui but not through the terminal, and what would be the location of the drive when its not mounted anymore?

terminal commands would be ideal, i always want to get better at doing things on the terminal.

---

### Post by simtaalo on 2008-11-19
> **Elliander said:**
> This is interesting. I am still able to install programs from the Synaptic Package Manager. I just can't install anything I paid for. :confused:

what have you paid for?

if your not able to install things on the terminal have you made sure you run the command as the root user? 

sudo {enter command}

keith's advice does make the most sense. its not the program ktorrent, as when i download stuff to a different HD it has no problems at all.

---

### Post by Keith Hedger on 2008-11-19
> **simtaalo said:**
> i think this is my problem, keith said something about running fschk, but having to unmount it first. i know how to unmount it through the gui but not through the terminal, and what would be the location of the drive when its not mounted anymore?

terminal commands would be ideal, i always want to get better at doing things on the terminal.

use ```
sudo fdisk -l
``` find your device eg:/dev/sdb1
```
sudo umount /dev/sdb1
sudo fsck /dev/sdb1
```

obviously u need to replace /dev/sdb1 with the device number of your external disk.
PLEASE check the man pages BEFORE u use these commands!

---

### Post by simtaalo on 2008-11-19
thank you for the advice, i ran the commands, after reading man and finally got this output

```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb1: clean, 167/1835008 files, 2875980/7325632 blocks

```

thanks :)

EDIT: i just tried to mount the HD using the command

```
 sudo mount /dev/sdb1 
```

and i received this error
```
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
```

---

### Post by bodhi.zazen on 2008-11-19
You need to specify a mount point.

sudo mount /dev/sdxy /media/mount_point

See [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

