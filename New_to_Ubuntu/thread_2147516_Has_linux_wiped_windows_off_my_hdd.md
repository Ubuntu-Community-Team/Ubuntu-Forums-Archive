---
title: "Has linux wiped windows off my hdd"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by arranskye on 2013-05-22
**Hi**, I was using Linux Ubuntu on my desktop PC  HP Compaq CQ5226 2.6 dual  core 2GB ram 320HDD runnin WIn 7 home premium. Linux was running from  the DVD\RAM.  I decided to install Linux with a dual boot system,and  got as far as this, (see below)  when I remembered that there was a newer version so I  decided to cancel the installation and get the new version.
I had only opened the prep screen ( updates & 3rd party sofware) when the following screen came up.

"Do  you want the installer to try to unmount the partitions on these disks  before continuing.  If you leave them mounted, you will not be able to  create, delete, or resize partitions on these disks but you may be able  to install existings partitions there  Yes/No  I choose No as I did not  want Linux to touch these partitions. The next screen offered "Replace  windows 7 with Ubuntu." This was pre-selected, plus 3 other options.  I  did not take any of the options.  To respond:  "Quit : Back : Continue.   I choose quit to end the installation. 

I went through the correct  procedure to close Linux and remove the disk, but when I went to boot up  my pc I got the first bios page then just a black screen with a  blinking cursor on the top left. I then tried to access the repair  screens. ie last good configuration, safe mode etc.  No joy.  I inserted  my installation disk and did repair install, no good. I then used  command prompt to do Bootrec.exe.but no good. I then tried BCD but again  no good.

I got 3 different messages : The partition table does not  have a valid system partition.   The Boot selection failed because a  required device is inaccessible.  Sorry cant remember the exact words  but another message mentioned the bootpath.  Ran Linux again and the  windows HDD no longer shows in Ubuntu where as, before it was on the  Linux system and I could access my files.

Please can you tell me for sure if the HDD has been wiped and Win 7 has completely gone.  Is there a way of telling if the current OS system has been wiped from the HDD when I cant get into windows.   I am not concerned about losing win 7 only the recent files and photos on the system  Thanks

I find the questions regarding installing linux quite ambiguous especially the boot configurations. Its is really quite difficult when you are completely new to linux.

---

### Post by westie457 on 2013-05-22
Hi
Use the LiveCD/DVD for this.
Could you please show us the output of ```
sudo fdisk -l
```
The l is a lower-case L, not a 1.
The result of that command will decide the course of action that will be necessary.

---

### Post by arranskye on 2013-05-22
Thanks for your reply.. Sorry to be such a dumbo but where and how do I input that command.  Ie.  which file do I open and will there be a command line to use similar to DOS. thanks

---

### Post by brandontn on 2013-05-22
Use the application terminal when your in the live cd/dvd

---

### Post by westie457 on 2013-05-23
To open a terminal (in the Live Desktop or a normal installation the procedure is the same) click on the Dash-icon top-left of the screen and type terminal in the pop out and hit enter. Alternatively you could press Ctrl+Alt+T at the same time. Either way will work.

The command posted by me earlier should give a list of the partitions on your hard drive.

When you post the output could you put it in [code] tags please. To do this highlight the text in the terminal, right-click and select copy. In a new reply here paste the output then select again and click the # symbol. This will place the [code] brackets around the text preserving the formatting and make things easier for us to read.

Thank you.

---

### Post by arranskye on 2013-05-24
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8329

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   625141759   312320001    5  Extended
/dev/sda5          501760   625141759   312320000   8e  Linux LVM
ubuntu@ubuntu:~$ 



Usage: fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

Hi Westie,  Sorry I probably should have done this as an attachment. also sorry for the long delay.  I think I have followed your instructions correct, if not I will try again.  Thanks

---

### Post by lethall1 on 2013-05-25
> [COLOR=#000000]Device Boot Start End Blocks Id System[/COLOR]
[COLOR=#000000]/dev/sda1 * 2048 499711 248832 83 Linux[/COLOR]
[COLOR=#000000]/dev/sda2 501758 625141759 312320001 5 Extended[/COLOR]
[COLOR=#000000]/dev/sda5 501760 625141759 312320000 8e Linux LVM[/COLOR]


You have wiped your windows. And all your data. That happens T_T Make backup of important information.

---

### Post by arranskye on 2013-05-25
hi Westie Thanks, I thought that was the situation but much happier now it has been confirmed. I have ordered a new SSD so i was going to re-install anyway.  Backed up all my data immediately prior to trying to install Ubuntu so no problem there.  A big thank you for my first introduction to the terminal.  many things are much clearer now.

This is absolutely not a problem to me but i do think that a warning/alert with the option to stop/continue would be a good idea in any Linux distro.  there is a form available in puppy  ie. Install puppy alongside windows: yes/No

The installation obviously continued even after I had pressed Quit and confirmed this action.

People will be reluctant to install or continue to try linux distros when thing like this happen.  Us - - - -  minus  newbies still see things through windows eyes, stripping of these trapping while trying to learn the Linux system/terminology and language makes it quite easy to misinterupt or misunderstand the actions we are permitting.

Anyway thats twice I got it wrong. 1st time courrupted the MBR. and stopped windows booting. 2nd wiped windows so lets hope 3rd time lucky.
I have read a lot but you really only learn by doing.

I will search the forums for installation instructons. thanks again for everything.

---

### Post by lethall1 on 2013-05-25
> [COLOR=#000000]People will be reluctant to install or continue to try linux distros when thing like this happen[/COLOR]
People just need to pay more attention ))
> [COLOR=#000000]The installation obviously continued even after I had pressed Quit and confirmed this action.[/COLOR]
disk partition recreation takes about... 5 sec on my ssd. You pushed quit, and OS installation was aborted, but partition manager done his job

---

### Post by deadite66 on 2013-05-25
when ever i try a new distro i always try it in a virtual machine first to get an idea of the partitioner/installer.

---

### Post by westie457 on 2013-05-25
@arranskye
If you wish to attempt recovery of your previous partitions and OS take a look at this [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is in the repo's. Using the terminal

```
apt-get install testdisk
```

then ```
testdisk
```

Nothing is written to the hard drive until you agree to write the changes to the drive.

Full instructions are provided in the link.

You should get a full recovery provided that only the partitions changed and no other info was written to the hard drive.

Good luck

---

### Post by arranskye on 2013-05-28
hi thanks for your replies.   

Sorry but speaking from a real    "linux unknown " perspective and despite having read & re-read forums, websites & loads of info, when actually installing and clicking yes/no,   or selecting other choices.which **to the TOTAL beginner**   appear to be somewhat ambiguous it is very easy to get it wrong no matter how much attention one pays to the task.


[COLOR=#008000]disk partition recreation takes about... 5 sec on my ssd. You pushed  quit, and OS installation was aborted, but partition manager done his  job 				[/COLOR].

Thats exactly what i mean.  That easy.  That fast.    One can play with a linux live disc for years but it will not give them any experience of installing unless they actually install, complicated further by installing onto a disk with an existing OS.

My only previous experience was installing Puppy 5.28 and it gave a very clear choice "install along with windows"   yes/no 

When you have absolutely no understanding of mount/unmount/ grubs/ ext/ it is quite daunting.  Even in windows, installing, partitioning, MBR etc were not exactly everyday tasks.

trust me Lethall I try very hard and pay the utmost attention.  The above quote proved very helpful.  Thanks 

Deadite,  Hi  thanks for your suggestion but havent a clue how to creat a VM. although it seems to be a very good idea.
Perhaps you could point me in the right direction to get info and instructions.  Thanks

---

### Post by richierich1986 on 2013-05-28
The Ubuntu installer does clearly ask you if you want to install alongside Windows. Even better, it is set as default
if a Windows installation is detected. You only had to press enter. Since your system is obviously using LVM, as shown
from the terminal output you posted, you had to have selected secure install manually, which clearly says it wipes
the disk completely. I remember that it can be quite daunting at first, but Canonical have made it really quite easy
these days. An Ubuntu install is as simple, if not simpler, to do than a Windows install.

---

### Post by arranskye on 2013-05-28
Thanks Rich.

Will be installing on thursday but this time I will make a note of each action and if Im unsure I will ask questions before continuing.  Also I will not restore my data to win 7 or ubuntu until both os have been installed. Your post has given me a lot more confidence. Thank you.

This is not just to install win7 & Ubuntu but I also want to install several distros on my various pc's to fully learn & understand the process. I will keep you posted. Thanks again

---

### Post by arranskye on 2013-05-28
sorry I forgot to ask should I use the desktop install icon.??????????

---

### Post by arranskye on 2013-05-29
hi. input text in terminal as suggested:

got this;      ubuntu@ubuntu:~$ apt-get install testdisk
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ testdisk
The program 'testdisk' is currently not installed. You can install it by typing:
sudo apt-get install testdisk
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  testdisk
0 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
Need to get 500 kB of archives.
After this operation, 1,152 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/universe testdisk amd64 6.13-1ubuntu2 [500 kB]
Fetched 500 kB in 3s (139 kB/s)    
Selecting previously unselected package testdisk.
(Reading database ... 161743 files and directories currently installed.)
Unpacking testdisk (from .../testdisk_6.13-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up testdisk (6.13-1ubuntu2) ...
ubuntu@ubuntu:~$ 

Sorry I dont understand what it is telling me. Do I need to input another command to continue, or does this indicate existing files on HDD


[COLOR=#40e0d0].(Reading database ... 161743 files and directories currently installed.)[/COLOR]

Thanks

---

