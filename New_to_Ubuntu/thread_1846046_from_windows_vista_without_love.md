---
title: "from windows vista without love"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by R-otrebor on 2011-09-18
Hi, folks... Im currently moving, or trying to move, from that crappy windows vista to Ubuntu... Hope i can count on you guys to usher me in...
Ive bumped into the following problems:
1. on Ubuntu, i cannot see my files and file structure i've built on my C: drive, and i cannot open any of my files with ubuntu apps. Does it have to do with the file system?;
2. i am trying to let ubuntu update my system with the Update manager, but whenever i select all files and click on "update", nothing seems to happen. Now i don't know wether something is running or not.
3. i've had problems (although randomly) of my keyboard and right mouse button going totally dead, forcing me to shut down the computer and restarting it.

Could anybody help me on that?

many thanks in advance.

---

### Post by Lisiano on 2011-09-18
Welcome to the Linux World.
1) Linux has a different file hierarchy, / (Root) is similar to My computer in Windows, everything in / (/etc, /bin, /sbin, etc) is usually something from C:\Windows or C:\Program Files, /home is your C:\Documents and Settings (Or C:\Users as in Vista and 7).
If you want to start anything from the Windows world you need to install a program called Wine ```
sudo apt-get install wine
``` or use Synaptic or use the Ubuntu Software Center. Usually there are alternatives to the software you use in the Windows world inside the Linux world (MS Office is LibreOffice, Photoshop is GIMP) or even have a Linux version instead (Chrome, Opera, Firefox, Skype).

2) Update means "Update the list". You probably want to use "Install Updates". If it still doesn't work for you, try using Synaptic (Mark All Upgrades -> Apply) or even use the command line ```
sudo apt-get update
sudo apt-get upgrade
``` Some people might bicker at me for saying to use Apt-Get so you can also use ```
sudo aptitude update
``` but I think you first need to install Aptitude.

3) Do you see any patterns before they "Freeze" for example "Used my PC for 2hrs then they froze" or "I started Skype and they froze"?

---

### Post by Wim Sturkenboom on 2011-09-18
I don't think R-otrebor wants to run windows applications in Ubuntu. I guess he/she just wants to view movies or listen to music on the C drive (or maybe read a word document).

If so, forget about wine; it's not necessary. Your C drive should be somewhere in the places menu, e.g. as 120GB disk or as the label of the disk.

If it's not in the places menu, open a terminal and please post the output of sudo fdisk -l (that is lower case L)

```

wim@aa0:~$ **sudo fdisk -l**
[sudo] password for wim: 

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003255d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         918     7367680   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             918         981      509953    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             918         981      509952   82  Linux swap / Solaris
wim@aa0:~$ 

```
I'm not behind a dual boot system to show what you can expect.

> 
on Ubuntu, i cannot see my files and file structure i've built on my C: drive
Does the above not imply the below? Maybe you can elaborate a bit? Maybe it becomes clear after you have posted the requested output of the fdisk command.
> 
and i cannot open any of my files with ubuntu apps.

---

### Post by SirDrexl on 2011-09-18
If you were using the standard Windows folders for storing your files, you may need to look under

Users/YOUR_USER_NAME/My Documents

(which will contain My Music, My Pictures, etc.) on your Windows partition.  These are presented in a way that's more obvious on Windows, but that's where the files are actually located.

---

