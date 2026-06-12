---
title: "Unable to create data directory /----: error creating directory: No space on device"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by gnl.weirdness on 2014-03-23
First off, stoked to have linux on one of my machines finally, not sure why it took me so long to get around to it.   Second, well I am new, thus posting in the beginners section. The issue I am having, which seems to be causing multiple issues, is that it seems my home directory /home/studinas has no space left on it. I installed Ubuntu to a 32gb SSD via MSATA on my mainboard. The install was a breeze, but I fear I did something wrong.  I have also set up 4 3.5 sata drives as an LVM to all be read as one large volume (this works fine, but it doesn't like to load when I reboot, but that is a seperate issue).  What seems to be the problem is that my home directory is lacking space, but I know for a fact (least I think I do) that ubuntu and the few other aps i've installed are NOT taking up 32gb of space. I am not sure how to check on this to be perfectly honest.  I ran  
du -h --max-depth=1 | sort -hr  
and got this as output:  
```
118M    . 
76M    ./.cache 
26M    ./.config 
13M    ./.mozilla 
2.0M    ./.local 
392K    ./.gstreamer-0.10 
208K    ./.gconf 
80K    ./.thumbnails 
68K    ./.gnome2 
40K    ./.speech-dispatcher 
40K    ./.pulse 
36K    ./.pki 
16K    ./.compiz-1 
12K    ./.mission-control 
12K    ./.dbus 
4.0K    ./Videos 
4.0K    ./Templates 
4.0K    ./Public 
4.0K    ./Pictures 
4.0K    ./Music 
4.0K    ./Downloads 
4.0K    ./Documents 
4.0K    ./Desktop 
0    ./.gvfs  
```
I am not really sure where to go next, but if I am reading this right, and have even used the proper command, it seems that my home dir only has 118m allocated to it...  Huge thanks ahead of time for anyone who can help, the application that was throwing the error was shotwell when I tried to install it, but it was also affecting torrents via transmission (which I removed and opter for Deluge which seems to not have the storage issues of trans.  Anyway thanks a million to anyone who can point me in the right direction. Absolutely loving linux thus far.

---

### Post by gnl.weirdness on 2014-03-23
wow apologies on the post formatting... no idea why it didn't creat paragraphs, is that not built in?

---

### Post by The Cog on 2014-03-23
Don't know what went wrong with the formatting. That's not normal. I took the liberty of cleaning up a bit.

Can you post the output of **df -h** please.

---

### Post by gnl.weirdness on 2014-03-23
certainly, here you go  
```
Filesystem                Size  Used Avail Use% Mounted on 
/dev/sdd2                  12G   11G     0 100% / 
udev                      7.7G  4.0K  7.7G   1% /dev 
tmpfs                     3.1G  964K  3.1G   1% /run 
none                      5.0M     0  5.0M   0% /run/lock 
none                      7.7G  164K  7.7G   1% /run/shm 
/dev/sdd1                 487M  2.1M  484M   1% /boot/efi 
/dev/mapper/nexus-volume  7.2T   56G  6.8T   1% /mnt/nexus 
/dev/sdf1                  31G  7.6G   23G  25% /media/EOS_DIGITAL
```

---

### Post by The Cog on 2014-03-23
/dev/sdd2 is full. Where on earth has 12G gone? 
Start with 
```
sudo du -xh --max-depth 1 /
```
and work down the tree. e.g. if /var is the biggie:
```
sudo du -xh --max-depth 1 /var
```

Edit:
Original post said "/sudo ...". The slash should not have been there.

---

### Post by gnl.weirdness on 2014-03-23
I will give that a shot and post my findings when i get back home.

---

### Post by monkeybrain20122 on 2014-03-23
Maybe you have forgotten stuffs that you have thought deleted but have been moved to trash instead, or maybe /tmp (some torrent clients store incompleted downloads there by default, which should clear up on reboot)

---

### Post by drmrgd on 2014-03-24
Just to add to The Cog's excellent advice, I also like to add a sort to the du command in order to see the bigfiles at the top (in fact, I usually make an alias called 'bigfiles' with this command):

```

du -hsx * | sort -rh | head -10

```

That will give you a list of the top 10 largest files in the directory from which you run the command.

---

### Post by gnl.weirdness on 2014-03-25
so this is quite embarrassing, using the suggested code from Cog, but it's saying no such file or directory. I imagine I skipped a step, I tried using CD but I believe dev/ssd2 is not a directory?

Any thoughts, I cannot actually do anything on the system now other than use terminal. Can't even get firefox to stay open, so i believe this to be a mem issue I just botched when setting everything up.

Thanks a trillion for any quick response.

---

### Post by gnl.weirdness on 2014-03-25
So I was able to figure out some of it, but still not sure how to explore that 12gb on dev/ssd2 as it's not showing. I looked into var and found that cache has 399 and lib has 285, tmp only has 4k...

So the var folder does not really sound like it id the trouble area as roughly 700mbs should hardly be enough to cause these issues. 

Anyone with some thoughts on how to get into the dev/ssd2 area? Also what should i be looking for and can I delete the things in the var/cache?

---

### Post by Impavidus on 2014-03-25
For some reason there are leading slashes on The Cog's commands. They have to be removed: **sudo du -xh ...**.

---

### Post by gnl.weirdness on 2014-03-25
I figured that much out hah. I am just not sure what to do next... I got the dev/sdd2 to show but it just lists:

```
 0          /dev/sdd2

```

I feel like there is some really simple fix to all of this, least I hope so would be nice to be able to use the system finally haha.

---

### Post by slooksterpsv on 2014-03-25
What was the output of:
```

du -hsx * | sort -rh | head -10

```
when run on / ?

---

### Post by gnl.weirdness on 2014-03-25
```
 error reading '/': Is a directory 
```

apologies for slow responses, I have to type all of this out by hand vs copy/paste as I can't open internet browsers on the linux rig (imagine due to the memory issues)

---

### Post by slooksterpsv on 2014-03-25
I apologize for how I worded that, if you change directory to / and then run the command what does it output:
```

cd /
du -hsx * | sort -rh | head -10

```

Output on mine:
```

32G	home
5.1G	usr
1.3G	var
699M	opt
451M	lib
66M	boot
23M	etc
11M	sbin
9.7M	bin
3.5M	lib32

```

---

### Post by gnl.weirdness on 2014-03-25
ahh that makes more sense haha:

```

du: cannot access `home/studionas/.gvfs': Permission denied
du: cannot access `proc/30359/task/30359/fd/4': No such file or directory
du: cannot access `proc/30359/task/30359/fdinfo/4': No such file or directory
du: cannot access `proc/30359/fd/4': No such file or directory
du: cannot access `proc/30359/fdinfo/4': No such file or directory
2.1G    usr
691M    var
458M    lib
173M    opt
103M    home
70M    boot
13M    etc
9.4M    sbin
8.9M    bin
960K    run

```

so still not sure where the heck all the extra space is.

---

### Post by slooksterpsv on 2014-03-25
This is a wild shot, but it was an issue I had before with Ubuntu - go to your home directory via:

```

cd

```

Nothing after cd just type in cd and press enter:

```

ls -alh

```

How big does it say .xsession-errors or .xsession-errors.old is?

---

### Post by gnl.weirdness on 2014-03-25
9k and 68k respectively :: (

---

### Post by gnl.weirdness on 2014-03-25
this would all be so much easier if chrome and ff actually opened/stayed open lol.

---

### Post by slooksterpsv on 2014-03-25
Dang; ok well this one is quite a bit longer, I apologize, but it should list the large offending file (if there is one):
```

sudo find /[a-o]* /[q-z]* -type f -size +1G | xargs ls -lh

```
So this will do the following:
Search through all the directories in / except for proc (proc will give u errors); it will search for files that are larger than 1GB, it will list the file. It's quite the command, but helpful.

---

### Post by gnl.weirdness on 2014-03-25
so all it found was some media files (movies) which I have in mtn/nexus/movies... All of those files are on a completely separate volume I made out of 4 2TB drives.

It showed nothing found anywhere else, but it did say

```
find home/studionas/.gvhs: permission denied
```

Then with everything else it found it just said 

```
 ls: cannot access lh (no such file or directory)
ls: cannot access "everything else": no such file or directory

```

That seems like a completely separate issue from the memory space on my 32gb ssd that runs the OS, but maybe not. I thought I had a half a grasp on this, but I am def treading in deeper water now as I have no idea why this is happening haha.

---

### Post by slooksterpsv on 2014-03-25
[https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows](https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows)

I'm wondering if its a disk caching issue, seems like a common problem. I'm not sure how to specifically fix it, but there's a link which may provide useful information. Read through and see what you can make of it.

---

### Post by gnl.weirdness on 2014-03-25
will do, if anyone else has any further insight it would be great. will respond again after playing around.

---

### Post by gnl.weirdness on 2014-03-25
So looking at this a bit more, it seems my home directory is 100% used, which we seemed to have already established. However I cannot find out how this is possible, I have gone through every folder under it and none have anywhere near the mysterious missing gbs of space...

How could that possibly be? I read through that article btw and it didn't seem to really apply to this unless I missed something,

---

### Post by slooksterpsv on 2014-03-25
If it is in the home directory, lets run this:
```

cd
du -h -d1 | sort -h

```
 That can tell us the directory, but if it doesn't show anything large, it's probably in the home directory itself like I have a 15GB file in my /home/shawn - the command I told you to run doesn't show that, but I just know it's there.

---

### Post by gnl.weirdness on 2014-03-25
I have done that a few times now, shows nothing larger than 65M. Total of 105M. I have also looked at the disk in diskutil, it shows 511mb FAT, 13gb ext4 (/dev/ssd2), and 17gb Swap (/dev/ssd3).

I feel like for some reason ubuntu is thinking there is more on the system than there is... Or something. I have read a ton of others issues similar to mine, but no one method/solution is getting me anywhere. It's really just a lot of the same as what you and others have suggested I do in this thread.

Hopefully we can get to the bottom of it and I can update all these unsolved threads with some insightful info. Just seems like such a trivial thing, but refuses to show itself lol.

---

### Post by gnl.weirdness on 2014-03-25
er so going through my / folder in the GUI, it looks like my proc folder has 49,000+ items in it at a whooping 140.7TB... WHAT 

So I am pretty sure that might be the culprit? It just has thousands of folders in it with numbers, how could it even register at 140.7TB lol. I am pretty sure this is the cause, but will wait for someone with some more info/knowledge to respond.

---

### Post by gnl.weirdness on 2014-03-25
*edit* looks to just be a virtual file and doesn't actually use up that space, just says what a 64bit system can allocate. FML 

kcore file is the specific one that is 140.7tbs... or so it thinks, I so hope this is the issue, any thoughts?

---

### Post by slooksterpsv on 2014-03-25
What does:

ls -alh ~

Show?

---

### Post by gnl.weirdness on 2014-03-25
```

total 144K
drwxr-xr-x 25 studionas studionas 4.0K Mar 25 17:40 .
drwxr-xr-x  3 root      root      4.0K Mar 22 14:11 ..
-rw-------  1 studionas studionas    0 Mar 23 18:29 2zvekl
-rw-------  1 studionas studionas    0 Mar 23 18:55 60uKGp
-rw-------  1 studionas studionas  770 Mar 23 15:17 .bash_history
-rw-r--r--  1 studionas studionas  220 Mar 22 14:11 .bash_logout
-rw-r--r--  1 studionas studionas 3.5K Mar 22 14:11 .bashrc
drwx------ 18 studionas studionas 4.0K Mar 25 17:22 .cache
drwxrwxr-x  3 studionas studionas 4.0K Mar 22 15:17 .compiz-1
drwx------ 13 studionas studionas 4.0K Mar 25 17:21 .config
drwx------  3 studionas studionas 4.0K Mar 22 14:17 .dbus
drwxr-xr-x  2 studionas studionas 4.0K Mar 22 14:17 Desktop
-rw-r--r--  1 studionas studionas   25 Mar 23 15:51 .dmrc


















drwxr-xr-x  2 studionas studionas 4.0K Mar 22 14:17 Documents
drwxr-xr-x  2 studionas studionas 4.0K Mar 23 14:32 Downloads
-rw-r--r--  1 studionas studionas 8.3K Mar 22 14:11 examples.desktop
-rw-------  1 studionas studionas    0 Mar 23 19:03 f3QPUU
drwx------  4 studionas studionas 4.0K Mar 23 15:51 .gconf
-rw-r-----  1 studionas studionas    0 Mar 22 15:28 .gksu.lock
drwx------  4 studionas studionas 4.0K Mar 22 14:17 .gnome2
drwxrwxr-x  2 studionas studionas 4.0K Mar 23 19:14 .gstreamer-0.10
-rw-rw-r--  1 studionas studionas  157 Mar 23 15:51 .gtk-bookmarks
dr-x------  2 studionas studionas    0 Mar 23 15:51 .gvfs
-rw-------  1 studionas studionas  990 Mar 23 15:51 .ICEauthority
drwxr-xr-x  3 studionas studionas 4.0K Mar 22 14:17 .local
drwx------  3 studionas studionas 4.0K Mar 22 14:18 .mission-control
drwx------  4 studionas studionas 4.0K Mar 22 14:18 .mozilla
drwxr-xr-x  2 studionas studionas 4.0K Mar 22 14:17 Music
-rw-------  1 studionas studionas    0 Mar 23 18:29 osh4QS
drwxr-xr-x  2 studionas studionas 4.0K Mar 22 14:17 Pictures
drwx------  3 studionas studionas 4.0K Mar 22 14:23 .pki
-rw-r--r--  1 studionas studionas  675 Mar 22 14:11 .profile
drwxr-xr-x  2 studionas studionas 4.0K Mar 22 14:17 Public
drwx------  2 studionas studionas 4.0K Mar 23 15:51 .pulse
-rw-------  1 studionas studionas  256 Mar 22 14:17 .pulse-cookie
-rw-------  1 studionas studionas    0 Mar 23 19:03 r5h8KW
drwx------  4 studionas studionas 4.0K Mar 23 15:54 .speech-dispatcher
drwxr-xr-x  2 studionas studionas 4.0K Mar 22 14:17 Templates
drwx------  4 studionas studionas 4.0K Mar 23 02:04 .thumbnails
-rw-------  1 studionas studionas    0 Mar 23 18:55 vdixLL
drwxr-xr-x  2 studionas studionas 4.0K Mar 22 14:17 Videos
-rw-------  1 studionas studionas   54 Mar 23 15:51 .Xauthority

```

---

### Post by gnl.weirdness on 2014-03-25
Also maybe worth mentioning. I had transmission installed for a night, but I didn't like it. I removed it completely, but I am wondering if maybe there isn't still some set of large files/temp files sitting somewhere on the drive that I cannot locate? I doubt it, but figure it's worth asking. I use Deluge now.

---

### Post by gnl.weirdness on 2014-03-25
or is it possible that I set up my root and home dir improperly? how could I check that?

---

### Post by slooksterpsv on 2014-03-25
I'm at a loss at the moment without directly interfacing with your system. Its either gotta be a caching issue (but where you said home had most of the data maybe not), or there's a large file in your home folder. Is there anything you absolutely need in your home folder such as: documents, images, videos, downloads, configuration, etc. etc. etc.

We could try deleting the content of your users home directory and see if that fixes it. It's the last thing I can figure where we don't know where that space is being taken up at.

Wait... how about this...
Open your home folder in.. nautilus? thunar???? forgot which version you were running - in the filemanager, right-click on each folder and go to properties, it'll tell you the size, find the folder with the most GB in it; if none of them, it's a hidden one, which we can just remove all of the hidden folders (which will delete your configuration of your apps and caches and what not) and see if that helps. Trying to do this where if we mis-type a command we won't completely wreck havoc on the system.

Try the GUI way first

---

### Post by steeldriver on 2014-03-25
I'm of much the same mind as slooksterpsv - if it's some kind of weird msata caching I would not know where to begin diagnosing

However just in case it's a simple 'big file hiding somewhere' situation, this command should be pretty comprehensive:

```

sudo find / -xdev \( -path /proc -o -path /run -o -path /sys \) -prune -o -size +100M -type f -exec du -h {} + | sort -hr | head -20

```

The -xdev should stop it descending into your LVM and/or .gvfs remote filesystem, so it shouldn't take *too* long to search the rest

---

### Post by gnl.weirdness on 2014-03-26
So I should be able to tick this to solved shortly. It turns out the issue was with my main storage volume I created NOT auto mounting at boot, and thus the OS drive took over for any software I had running at startup (torrent).

I wasn't seeing this because it created the same folders as the mounted storage volume. So there was a second (mirror) directory if you will that was on the drive but NOT showing when I had the main storage volume mounted.

Unmounted it, and I am removing the alt directory the os created. Will update this when I am able to reboot and have the storage volume mount properly.

---

### Post by steeldriver on 2014-03-26
Ah yes that makes sense... the LVM getting mounted over the top of the (full) /mnt/xxx directory

---

### Post by oldfred on 2014-03-26
Not sure I can add much.

But have you checked trash? And root trash does not show normally or can be difficult to houseclean.

I did this to delete some files in / with nautilus:
       1261  df -h
 1263  gksudo nautilus
 1268  sudo chown -R fred /root/.local/share/Trash/
 1274  sudo rm -rf /root/.local/share/Trash/
 1275  df -h
 1276  history

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)



Separately:
Why is / only 12GB on a 32GB SSD. My 64GB SSD has two root partitions so I can have two different installs and each is about 28GB. And I use about 11GB in main working install, so a 12GB / is not large and would require regular housecleaning.

Also if using LVM, you do have to have good backups. If any drive fails then all data on all drives is lost.

---

### Post by slooksterpsv on 2014-03-26
oldfred brings up a good point; Ubuntu alone takes 7GB so you'd only have 5 gb left. Other various take anywhere from 4-6GB

---

### Post by gnl.weirdness on 2014-03-26
yep, issue officially resolved. If anyone has a similar issue, feel free to PM me.

---

