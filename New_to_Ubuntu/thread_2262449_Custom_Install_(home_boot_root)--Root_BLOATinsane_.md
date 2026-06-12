---
title: "Custom Install (/home /boot /root)--Root BLOATinsane size (~5GB-now 35GB) Thus &quot;FULL&quot;"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2015-01-24
Hey,
Thanks for reading. 

I have no clue what is going on. This am....Somehow (??) My Root Partition Bloated from ~5GB to "Full" (35GB). 
The only thing I was doing immediately prior to this was installing additional "Apt" commands (Apt-Utils,etc.) 

Thus I'm stuck with "FULL" drive being reported. (aka-can't run ap-get, dkpg, etc.) 
(see full output below)---but just one of few errors( clip)

```

dpkg: error processing archive /var/cache/apt/archives/libqtgui4_4%3a4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb (--unpack):  cannot copy extracted data for './usr/lib/i386-linux-gnu/libQtGui.so.4.8.6' to '/usr/lib/i386-linux-gnu/libQtGui.so.4.8.6.dpkg-new': failed to write (No space left on device) No apport report written because the error message indicates a disk full error                                                                               dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am completely stuck....any help appreciated!!
Even tred to do a Grsync--normal once-ish week---it won't let me (I'm of coruse Backing to a 2nd  Drive)---but it fails out with an "out of space" error.


```

The only thing I see that is "glaringly off" (to me)--is I looked up what a Generic (mine) LInux Architecture shoudl be
----that "RUN" Directory/follder--I never created. AND I'm convinced that's not nearly accurate reporting of the size of the Entire Folder. 

A right click properties shows 569 items, totalling 54.9 kB. 

However "something" inside of the root tree is breaking my system as I can't run dpgk,      apt-get autoremove....etc. (because it says "out of space") (and or error (1)

```


I included a shot of my partition structure (ignore the drive names) . Trying to expand ROOT---For some other reason, the "empty" partition abobve the root partition (when I activate it,etc.) it won't let me expand the root folder. 

Is there a way to "rebuild" the directories???


*************************************

I checked the boards, prior to poslt, couldn't find much help.   
DId notice a consistent theme, saw Helpers asking for the output of 

dkpg --configure -a  
apt-get -f install 
cat /etc/apt/sources.list

thus --have included those. 


```

root@Dooley:~# sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
 libqt4-declarative:i386 depends on libqtgui4 (= 4:4.8.5+git192-g085f851+dfsg-2ubuntu4); however:
  Package libqtgui4:i386 is not installed.

dpkg: error processing package libqt4-declarative:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libphonon4:i386:
 libphonon4:i386 depends on libqtgui4 (>= 4:4.8.1); however:
  Package libqtgui4:i386 is not installed.

dpkg: error processing package libphonon4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-help:i386:
 libqt4-help:i386 depends on libqtgui4 (= 4:4.8.5+git192-g085f851+dfsg-2ubuntu4); however:
  Package libqtgui4:i386 is not installed.

dpkg: error processing package libqt4-help:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdbusmenu-qt2:i386:
 libdbusmenu-qt2:i386 depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4:i386 is not installed.

dpkg: error processing package libdbusmenu-qt2:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-declarative:i386
 libphonon4:i386
 libqt4-help:i386
 libdbusmenu-qt2:i386

```


```

root@Dooley:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-python1.54.0 libboost-system1.54.0 libmikmod2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqtgui4
Suggested packages:
  qt4-qtconfig
The following NEW packages will be installed:
  libqtgui4
0 upgraded, 1 newly installed, 0 to remove and 241 not upgraded.
4 not fully installed or removed.
Need to get 0 B/4,185 kB of archives.
After this operation, 13.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 135190 files and directories currently installed.)
Preparing to unpack .../libqtgui4_4%3a4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb ...
Unpacking libqtgui4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
dpkg: error processing archive /var/cache/apt/archives/libqtgui4_4%3a4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb (--unpack):
 cannot copy extracted data for './usr/lib/i386-linux-gnu/libQtGui.so.4.8.6' to '/usr/lib/i386-linux-gnu/libQtGui.so.4.8.6.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
E: Sub-process /usr/bin/dpkg returned an error code (1)

```




```

root@Dooley:~# cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140723)]/ trusty main multiverse restricted universe
# deb cdrom:[Xubuntu 14.10 _Utopic Unicorn_ - Release i386 (20141022.1)]/ trusty main multiverse restricted universe
# deb cdrom:[Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140723)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu utopic partner
# deb-src http://archive.canonical.com/ubuntu utopic partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
root@Dooley:~# 

```

---

### Post by whereismymindat2 on 2015-01-24
PS--
1st Pic--to Show "Size of"---what is being reported for the RUN Directory
2nd-Pic the GParted (about as full bloat as you can get). 
3rd pic is intened to show "RUN" (sitting in the Root DIR)--then, Inside "RUN" Directory---all those files (why I think it's misreporting it's size). (side by side--aka--"Root" ---left----"Run" DIR (and subs)---on the Right 

It's blurry on my end, thus the explain THANK YOU!

---

### Post by oldfred on 2015-01-24
I forgot to mount my /mnt/backup once and it just copied to / and filled my root.
So what is filling root?

Post this:
       # check sizes of 
Partition sizes
df -Th | sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

---

### Post by whereismymindat2 on 2015-01-25
HI [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711")  Thanks for the help!! Think you are on to something ....it showed several errorts. 

THANK YOU1--hope these help. 

 ********************
Output each below
Post this:
       # check sizes of 
Partition sizes
df -Th | sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null
 ********************


********************
df -Th | sort
********************

```

_____________________________________________________
root@Dooley:~# df -Th | sort
/dev/sda1      ext4      523G   91G  408G  19% /home
/dev/sda3      ext4       21G  338M   19G   2% /tmp
/dev/sda4      ext4       35G   35G     0 100% /
/dev/sda5      ext4       24G   77M   23G   1% /boot
/dev/sda6      ext4       26G  319M   24G   2% /var
/dev/sdd1      vfat       15G   14G  1.3G  92% /media/bender/MULTIBOOT1
Filesystem     Type      Size  Used Avail Use% Mounted on
none           tmpfs     100M   24K  100M   1% /run/user
none           tmpfs     1.5G   76K  1.5G   1% /run/shm
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     302M  1.2M  301M   1% /run
udev           devtmpfs  1.5G  8.0K  1.5G   1% /dev
root@Dooley:~# 

```
______________________________________

Just a reminder, that "RUN" directory I never created myself (or did any command to do so. that "I" know of). 



 ********************
Inodes
(I wasn't clear if this was a stand alone request or not-thus inclunded) *Grin*
********************



```

_____________________________________________________
root@Dooley:~# Inodes
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 27, in <module>
    from CommandNotFound.util import crash_guard
  File "/usr/lib/python3/dist-packages/CommandNotFound/__init__.py", line 3, in <module>
    from CommandNotFound.CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 7, in <module>
    import dbm.gnu as gdbm
  File "<frozen importlib._bootstrap>", line 2214, in _find_and_load
  File "<frozen importlib._bootstrap>", line 2203, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1200, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1129, in _exec
  File "<frozen importlib._bootstrap>", line 1444, in exec_module
  File "<frozen importlib._bootstrap>", line 1547, in get_code
  File "<frozen importlib._bootstrap>", line 656, in _compile_bytecode
EOFError: marshal data too short
root@Dooley:~# 

```


 ********************
df -i
********************


```

_____________________________________________________
root@Dooley:~# df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda4       2305632 294138  2011494   13% /
none             217566      2   217564    1% /sys/fs/cgroup
udev             212779    562   212217    1% /dev
tmpfs            217566    576   216990    1% /run
none             217566      5   217561    1% /run/lock
none             217566      4   217562    1% /run/shm
none             217566     21   217545    1% /run/user
/dev/sda3       1343488     92  1343396    1% /tmp
/dev/sda1      34791424  97608 34693816    1% /home
/dev/sda5       1602496    301  1602195    1% /boot
/dev/sda6       1695744   8169  1687575    1% /var
/dev/sdd1             0      0        0     - /media/bender/MULTIBOOT1
root@Dooley:~# 

```




 ********************
sudo du -hc --max-depth=1
********************




```

_____________________________________________________
root@Dooley:/home# du -hc --max-depth=1
91G    ./bender
16K    ./mythtv
16K    ./lost+found
91G    .
91G    total
root@Dooley:/home# 

```




 ********************
du -hx --max-depth=1 / 2> /dev/null
********************


```

_____________________________________________________
root@Dooley:/home# du -hx --max-depth=1 / 2> /dev/null
4.0K    /cdrom
235M    /lib
4.0K    /mnt
2.7G    /usr
14M    /etc
16K    /lost+found
31M    /root
4.0K    /srv
13M    /sbin
9.3M    /bin
830M    /opt
31G    /media
35G    /
root@Dooley:/home# 

```

********************
.eom
********************

---

### Post by oldfred on 2015-01-25
Should have suggested to run du commands on / as that is the one that is full, not /home, sorry.

       cd / 
sudo du -hc --max-depth=1

 sudo du -hx --max-depth=1 / 2> /dev/null

---

### Post by Impavidus on 2015-01-25
There is 31GB in /media, but this is on the root partition. It seems you (or some automatic process) tried writing stuff to a file system that was supposedly mounted there, but wasn't. Dig into /media to find the files and move them to where they were supposed to go.

---

### Post by whereismymindat2 on 2015-01-26
@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711")   (as per your request)


 *******************************
cd / 
sudo du -hc --max-depth=1

 sudo du -hx --max-depth=1 / 2> /dev/null                 
*******************************



```

*******************************
root@Dooley:~# sudo du -hc --max-depth=1
*******************************
________________________________________
4.0K    ./.gnome2_private
256K    ./.synaptic
4.0K    ./.gvfs
28M    ./bluefish-2.2.6
8.0K    ./.gnome2
28K    ./.dbus
392K    ./.rpmdb
760K    ./.cache
4.0K    ./.gconf
96K    ./.config
16K    ./.aptitude
36K    ./.local
31M    .
31M    total
root@Dooley:~# 
_____________________________________________________
 
```


*******************************
root@Dooley:~# du -hx --max-depth=1 / 2> /dev/null du -hx --max-depth=1 / 2> /dev/null 
*******************************
 ```

_______________________________________
4.0K    /cdrom
235M    /lib
4.0K    /mnt
2.8G    /usr
4.0K    /boot
14M    /etc
16K    /lost+found
31M    /root
4.0K    /srv
13M    /sbin
9.3M    /bin
772M    /opt
31G    /media
35G    /
root@Dooley:~#
_____________________________________________________
 
```

---

### Post by whereismymindat2 on 2015-01-26
@[**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")  I think you are correct. 
I checked Media folder---looks like a copy of my external drive files. (backup)?????

Will mv (actually "move" the files (not leave behind a dupe?) 

I'll try that. 

T

---

### Post by whereismymindat2 on 2015-01-26
@[**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721") 

I'm trying to move that----but (far as I know)--nothing is writing to that drive "SATURN" (it's an Internal Drive)--but one I only used for Backups/Saving stuff,etc. (no os,etc. on it). 

I tried to Unmount;/Mount---hoping to stop a process (if was working)---it didn't help. 

Any suggestions?

root@Dooley:/# mv -f -v  /media/bender/SATURN1/ -t /media/bender/SATURN/
mv: cannot move &#8216;/media/bender/SATURN1/&#8217; to &#8216;/media/bender/SATURN/SATURN1&#8217;: Device or resource busy
root@Dooley:/#

---

### Post by whereismymindat2 on 2015-01-26
OK, mystery deepens. @[**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721") I think you are correct. The Bloat is coming from Media. However what's happened is. 

My (2nd Internal HDD---1TB)----is called "SATURN"

It appears that "SATURN" was mirrored somehow (I'm guessing it failed when it reasched 35GB as was size of disk. 

BUT---If you see the screen shot. "SATURN" the Physical Drive (is still named SATURN....BUT IN THE MEDIA FOLDER IS SATURN1

No big deal, however before I messed with "SATURN" ("folder"--inside media)---I want to make sure what's inside the folder. 

BUT, I can't get in (even with Root Privledges). Any advice on how to make that Media Folder Readable/Viewable? (see screen shot). 

FYI-now makes sense why the drive was "Busy"--trying to copy it onto itself. (even though was SATURN1 and SATURN--thought were Different. (the drive with the Jacked up name--UUID---was a drive I created on the fly to see if I could move the SATURN1 FOLDER--I thought was "bad"---but I figured it all out--when it kept running and running and filled up 145GB of the "Foo" drive.....before I bailed. Figured it out. 


SO, I guess next need a way to gain permission to look inside that locked folder to make sure it's one I can delete or move.

---

### Post by Impavidus on 2015-01-26
Now you have me confused.

The important thing right now is that you don't mount the 1TB drive on top of the offending directory in /media. As I understand it, you usually mount that 1TB drive by clicking it in the file manager. Then it creates the directory /media/bender/SATURN and mounts the partition (entire drive) there. At some point something went wrong and the drive was unmounted without deleting that directory. In an attempt to write a backup, the backup, being almost identical to the contents of the existing backup drive, was written to /media/bender/SATURN, the usual location of the backup drive. When mounting the backup drive again, the system sees you already have a /media/bender/SATURN and creates a /media/bender/SATURN1 instead as a mount point.

If /media/bender/SATURN (the directory on the root partition, not the 1TB drive that was supposed to be mounted there) only contains data present on the 1TB drive, it will be safe to delete it all. Make sure you properly delete it, not send it to the trash can. But best to be really sure first. Furthermore, if you can't get in to view the contents, chances are you can't get in to to delete stuff either. Maybe there is some file system damage. Run```
touch /forcefsck
```and reboot. This will force a file system check during reboot. Then check the directory /lost+found, where recovered bits and pieces may be stored.

---

### Post by oldfred on 2015-01-26
Also confused.
Part of why I do not mount anything in /media myself, so only automounts of external devices are in /media.

Post this:
cat /etc/fstab
cd /media
ls -l

---

### Post by whereismymindat2 on 2015-01-26
Hey Guys, thanks for your help. I just simply reinstalled. (wanted to avoicd as Invariable I have to "rebuild" broken Packages...but price I pay for messing it up. ya know?

---

### Post by whereismymindat2 on 2015-01-29
Hello (former helpers)@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711")  and @[**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")  (and anyone else that can help).
-----I reopened this---- as The exact same issue has cropped up AGAIN!
I have no clue what is going on. This time, the only "novel" thing I've done since boot. (novel in quotes because not really novel).

But, I use Grsync to backup /bender (course /bender is the user--not the root). 
Should I forcefully add "SATURN" to "exclude" (even though it's not part of my backup set?)--located under /(root)/media/SATURN
"SATURN" (drive) is a 2nd (independent/stand alone Internal HDD (no OS,ETC)---only used for backups, file storage,etc.
*********************************************
I THINK I found the issue. It's 4:34am (got up early, enough sleep I guess)---but *THE ONLY* thing I've done "today" (where I can only assume 95% suspect is to perform a Grsync backup.

If you notice in the screen shot, you'll see the name it's mapping to is "SATURN2"---of course is Incorrect.

"SATURN"--is the 2nd HHD Backup Drive (and shows that name both in the "tree" and "mounted" on my desktop.

I don't know the correct term, but it's almost like a "Phantom"/"Ghost"/"Mirror"---

*********************************************
Thus, if the command to exclude "SATURN2" ("SATURN",etc.) is a potential solution, is this the correct command switches (and correct place to put into Grsync?)--see screen shot--to NOT backup (even though far as I know--mnt is not under the "tree" of /bender but IS under the tree of /root of course.
```

___________________________________
rsync --exclude 'SATURN'/ /media/bender/SATURN2/backup_bender/

OR?

rsync --/media/bender/'SATURN'/ /media/bender/SATURN2/backup_bender/
_______________________________________

```

and "exclude before run"?

```

/media/bender/ (IS the "USER"/"Production Drive")

/media/bender/"SATURN2"/backup_bender/ (IS the Independent-Internal HDD---NO OS/2nd Drive used only for Backups on CPU).

```

****************************

Then, most Important, how can I get everything renamed (safely back to "SATURN")--as of course it won't let me do a "mv"--as it's the same drive.
rid of the dupe SATURN1 and SATURN2 (as of typing this, SATURN2 thinks "it's" the drive...incorrect, just "SATURN" (course naturally the OS creating the 2----to avoid the name "clash".


THANK YOU GUYS *VERY* much for the help!!

---

### Post by whereismymindat2 on 2015-01-29
PS--as "evidence"----I ran both 
df -i
df -Th | sort

```

*************************************************
root@Dooley:~# df -i
_________________________________
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda4       2305632  193621  2112011    9% /
none             217559       2   217557    1% /sys/fs/cgroup
udev             212726     624   212102    1% /dev
tmpfs            217559     711   216848    1% /run
none             217559       4   217555    1% /run/lock
none             217559       5   217554    1% /run/shm
none             217559      22   217537    1% /run/user
/dev/sda5       1602496     306  1602190    1% /boot
/dev/sda7       3055616      13  3055603    1% /srv
/dev/sda9      12115968    4570 12111398    1% /opt
/dev/sda3        732960      21   732939    1% /tmp
/dev/sda8       3194880  254474  2940406    8% /usr
/dev/sda10       609600      44   609556    1% /usr/local
/dev/sda6       1695744   11862  1683882    1% /var
/dev/sda1      34791424  102105 34689319    1% /home
/dev/sdf1             0       0        0     - /media/bender/RANTHONY
/dev/sdb1      61054976  460214 60594762    1% /media/bender/SATURN2
/dev/sdc1       3023112 3022023     1089  100% /media/bender/LaCie
*************************************************

```


```

*************************************************
root@Dooley:~# df -Th | sort
____________________________________________
/dev/sda10     ext4      9.1G   22M  8.6G   1% /usr/local
/dev/sda1      ext4      523G   97G  403G  20% /home
/dev/sda3      ext4       11G   28M   11G   1% /tmp
[COLOR=#ff0000]/dev/sda4      ext4       35G   33G  182M 100% /[/COLOR]
/dev/sda5      ext4       24G  105M   23G   1% /boot
/dev/sda6      ext4       26G  1.2G   23G   5% /var
/dev/sda7      ext4       46G   52M   44G   1% /srv
/dev/sda8      ext4       48G  4.6G   41G  11% /usr
/dev/sda9      ext4      182G  460M  173G   1% /opt
/dev/sdb1      ext4      917G  384G  487G  45% /media/bender/SATURN2
/dev/sdc1      fuseblk   1.9T  1.9T  265K 100% /media/bender/LaCie
/dev/sdf1      vfat       31G   30G  478M  99% /media/bender/RANTHONY
Filesystem     Type      Size  Used Avail Use% Mounted on
none           tmpfs     100M   28K  100M   1% /run/user
none           tmpfs     1.5G   80K  1.5G   1% /run/shm
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     302M  1.5M  301M   1% /run
udev           devtmpfs  1.5G  4.0K  1.5G   1% /dev
root@Dooley:~# 
*************************************************

```

  (*I think*), there sits our "suspect"   [COLOR=#ff0000]/dev/sda4      ext4       35G   33G  182M 100% /[/COLOR]

fyi-yes, if you notice---I created all the sub folders for in install (on the recent wipe)---as I *thought*---might help avoide this issue. Guess was wrong. 

R.

---

### Post by oldfred on 2015-01-29
Not sure how you are doing it.
I also use rsync, so I know a bit more what is going on. 
I do create a mount point /mnt/backup and then in my rsync script mount my backup partition to /mnt/backup. I know at least once I has similar issue where I forgot to mount or correctly mount my backup and it just put a new backup folder in / and it took me a while to find it.

I started with this simple backup file and then over time have modified it for my use.
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first 

Then I found these threads and added more files to exclude in a separate file.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

Some recent discussion.       
 Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)

---

