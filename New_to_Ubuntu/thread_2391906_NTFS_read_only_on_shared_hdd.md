---
title: "NTFS read only on shared hdd"
date: 2018-05-14
forum: New to Ubuntu
---

### Post by kashei on 2018-05-14
i have a dual boot machine 
one ssd is windows and the other ssd is kubuntu and i installed a 3 hdd to share between them
my main OS is linux and windows is just basically for VR and couple of programs that only work on windows 
so when i installed a 3 hdd, i  formatted in ubuntu, ntfs file system because both OS's can read them 
at the beginning i had no issue with ubuntu read and wright on 3hdd, but now i don't have permission  says read only 
i need to copy and del files on it but it won't let me 
i tried 
"[FONT=monospace][COLOR=#000000]sudo ntfsfix /dev/sdb1"
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]" sudo chown $USER -R /media"
"[/COLOR][/FONT][FONT=monospace][COLOR=#000000]sudo apt-get install ntfs-config    [/COLOR][/FONT][FONT=monospace][COLOR=#000000]sudo mkdir -p /etc/hal/fdi/policy  "

running kubuntu 18.04
guys please help 
thank you
[/COLOR]
[/FONT][FONT=monospace]
[/FONT]

---

### Post by oldfred on 2018-05-14
Windows fast start up is really hibernation & it keeps all NTFS partitions hibernated. And Windows with updates will turn it back on, so check if it is on again.
Also ntfsfix does very little, primarily it turns on the chkdsk flag, so Windows will run chkdsk. Better to just run chkdsk from Windows is that is the issue. And once chkdsk flag is on, again the Linux NTFS driver will not mount it.

Grub only boots working Windows, so if boot partition is hibernated or needs chkdsk you have to directly boot Windows from UEFI or boot using Windows repair disk.

Hal errors with Windows almost never were related to hal, but other issues.

Windows partitions do not support Linux type ownership and permissions. 
So you cannot use chown nor chmod to change settings. Windows formats are only mounted with defaults either with fstab or the automount defaults which will work if the NTFS partition is not otherwise locked (hibernation or needing chkdsk).

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by kashei on 2018-05-14
Thanks Oldfred!!!!
so simple and yet so frustrating
worked like a charmed

---

