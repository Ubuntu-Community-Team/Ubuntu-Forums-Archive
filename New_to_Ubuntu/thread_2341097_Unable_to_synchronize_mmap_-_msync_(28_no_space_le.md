---
title: "Unable to synchronize mmap - msync (28: no space left on device)"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by elvis6 on 2016-10-24
There is already a thread on this, and I attempted to use the suggestions in it, but I am concerned that I may have done something wrong.
Apparently my disk space was so full, that I could not even log on.
I went to the thread mentioned above, and I tried multiple suggestions, including ```
sudo apt-get clean
``` which was supposed to clear out my synaptic application packages, to make space. But that did not work. I went on to the next suggestion, to find any large files in my root directory  	```
sudo find / -type f -size +100000k
```
It then listed all the large files on my drive, which I recognized.

 

I am not literate in Terminal code, so I wasn't sure how to pick and choose which files to delete, to make space.
So, after this list came up, I was at a loss for what to do, so I exited, and then decided to re-start, and for the first time in about a hundred log-on attempts, I was able to log-in, and the system seems to be working fine. 

But I am concerned that one of my personal files was deleted without my permission or knowledge, in order to make space on the device for the graphics to allow me to sign in again. Otherwise, how else, am I suddenly able to log in and use the system with no problem ?
So, does the command above actually delete anything on its own ? Am I actually telling it to delete anything over 100000k, or just to list it ?
If it doesn't delete anything on its own, I'm curious what might have happened to make space on the drive to let me gain access again.

---

### Post by WedgeHG on 2016-10-24
No, that command does not delete anything on its own. Its purpose is to show you large files so that you may choose some to delete yourself in order to free up disk space.

I won't speculate as to why it is working now, but if your disk was completely full before your last reboot then you're probably still very close to full and will probably experience more problems soon. If you aren't sure what to delete, video files are a good choice. Look for files ending in .mkv, .avi, .mpeg and so on. The output of that ''find'' command you pasted will point out large files on your computer. Any file that size in /home is probably safe to delete so long as it is something that you don't want to keep.

You can use this command to see how much disk space you have:

```

df -h

```

You'll want to look for the line that has "Mounted on" as "/". Below is the output of that command on my computer. Note the line that starts with /dev/sda8 and shows that I have used 21% of my disk:

```

$ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       3.9G     0  3.9G   0% /dev
tmpfs                      787M  9.6M  777M   2% /run
/dev/sda8                  114G   23G   86G  21% /
tmpfs                      3.9G  944K  3.9G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2                  256M   57M  200M  22% /boot/efi
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      787M   76K  787M   1% /run/user/1000

```

---

### Post by elvis6 on 2016-10-26
> **WedgeHG said:**
> You can use this command to see how much disk space you have:


Thanks - is there any way to set it up, to give me a pop-up warning when I'm getting low on disc space, in case I forget to check ?

---

### Post by kingneutron on 2016-11-30
$ apt-cache search 'disk space' # reveals a few packages that may help:

k4dirstat - graphical disk usage display with cleanup facilities
localepurge - reclaim disk space by removing unneeded localizations
procmeter3 - graphical system status monitor
xdiskusage - Displays a graphic of your disk usage with du

--Honestly though, your best bet is to just open a terminal window and type ' df -h ' once a day or so, or just leave it running with something like 'watch' - this is what I use:

$ xterm -bg black -fg green -rightbar -geometry 90x29-0+0 \
 -e watch -n 61 df -T -h -x{tmpfs,usbfs,devtmpfs,debugfs} &

--(Note, my command syntax applies to Ubuntu 14.04.) This runs the 'watch' program with 'df' and updates it every 61 seconds.  

--Also see attachment, this is my script that I run every time I login - it requires some extra packages, such as sysstat, xvt and bwm-ng, but provides a birds-eye view of pretty much everything I need to keep track of (top CPU processes, network usage, disk usage, and disk I/O.)  I run it on its own virtual desktop.

--Long term, you may need to resize partitions to give yourself more room to work in. I usually give "/" root partition about 20GB for 64 bit installs, and at least 10GB for separate /home partition (in the old days; nowadays my main system has /home on a mirrored/RAID1 compressed ZFS filesystem, so I don't have to worry about it.)

--If you post results of ' df -h ' and ' du --max-depth=1 -h / ' I can try to help you further.

---

