---
title: "Install Maybe not Correct - Separate /home"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-06-16
For the first time I installed ubuntu (14.04) with separate **/root** and **/home** partitions.  I originally set the **/root** partition as 20GB but after a short while I had a message saying I had no disc space left for root.  I increased the partition size to 30GB and now, today, I am told I have no disk space left for root (my HD is 1TB).  According to GParted I have my 30GB root partition with only 16MB free space and my **/home** partition, 267GB with 240GB free space (I have another storage partition on the HD as well as a swap partition).  Nautilus only shows a flat file system so it is difficult to see what folders are in what partition.  My understanding is that having a separate **root/system** partition makes it easier to upgrade and that the partition itself is small.  Appreciate any help in finding out what my problem is.  (I have looked the properties of each folder in root and none of them appear large.  However, if I group them all and right click on properties I get quickly to 556.8MB and then the small calculating circle just circles and circles).

---

### Post by rahul4557 on 2014-06-16
can you post a screenshot of gparted?

---

### Post by westie457 on 2014-06-16
what is the output of```
df -h
df -i
```

---

### Post by Impavidus on 2014-06-16
There is no /root partition (or at least, there shouldn't). There is the / partition, also known as the root partition. /root is a directory that has to be on the / partition. It's the root user's home directory and it must be available when you boot into recovery mode and no partitions other than / are mounted. And I must say your /root is rather big. Mine is 208kB. What is .mozilla doing there? Never use web browsers as root.

Have a look here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
Use the **du** command as explained in that link to find which directory uses all your disk space. And show us the output from westie457's commands.

---

### Post by Quarkrad on 2014-06-16
dad@dadubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        30G   30G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.8G  8.0K  1.8G   1% /dev
tmpfs           369M  1.1M  368M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G  416K  1.8G   1% /run/shm
none            100M   68K  100M   1% /run/user
overflow        1.0M   12K 1012K   2% /tmp
/dev/sdb1       932G  834G   98G  90% /media/backup
/dev/sda7       533G  487G   46G  92% /media/store
/dev/sda6       264G   25G  226G  10% /home
dad@dadubuntu:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda5        1957888 431824   1526064   23% /
none              471296      2    471294    1% /sys/fs/cgroup
udev              468604    578    468026    1% /dev
tmpfs             471296    572    470724    1% /run
none              471296      3    471293    1% /run/lock
none              471296      6    471290    1% /run/shm
none              471296     32    471264    1% /run/user
overflow          471296     14    471282    1% /tmp
/dev/sdb1      102993548 288862 102704686    1% /media/backup
/dev/sda7       48285904  16416  48269488    1% /media/store
/dev/sda6       17547264 113553  17433711    1% /home

---

### Post by LastDino on 2014-06-16
Are you storing any large files in ''/''? 

Since when did you start to see this behavior? What was the amount of disk-space consumed when you installed the Ubuntu?

---

### Post by mastablasta on 2014-06-16
try kdirstat program or disk usage analyzer to see what is taking space.

do you maybe have deleted files (recycle bin) on / ? and you deleted large files and bin is not empty?

---

### Post by Quarkrad on 2014-06-16
I've just run baobab as sudo and the result is bab1 attached.  bab2 shows the details under the 31.2GB partition dadubuntu - the two big culprits are **/usr** and **/media**. bab3 shows in detail usr and bab 3a and 3b shows what is under media.  I'm a little confused about media because I believe my data partition called **/media/store** is /dev/sda7 as per gaparted so why is there a **/media** under **/** as per bab3?   Also confusing (me) is why, under** / (sda5**), is there dad with similar (but much smaller) visible and hidden folders as per my **/home/dad (sda6)** that is on a separate partition?  Again, on the right of bab3a, there is virtualbox - but I have (I thought) configured virtualbox to be on **media/store** (that is all the separate guests).

---

### Post by mastablasta on 2014-06-16
are they encrypted?

it seems 10 GB is taken on root.

---

### Post by Quarkrad on 2014-06-16
Nothing is encrypted.

---

### Post by Quarkrad on 2014-06-16
I followed the instructions on this forum and the install during the 14.04 (clean) installation.  To be honest - I am still unsure of the size of the separate / partition when using this method of install (separate /home) - as I had a 1TB HD I thought 20GB would be OK for 14.04 and future releases.  (My system is fairly clean re ubunt tweak and bleechbit).

---

### Post by steeldriver on 2014-06-16
You have 2 separate partitions mounted in media i.e. /media/store and /media/backup, however anything else that is **in /media but is not underneath one of those directories** (e.g. /media/dad) is taking up space on /

---

### Post by Quarkrad on 2014-06-16
Sorry - perhaps I should have mentioned earlier.   I have two HDs - the first is my 'pc' that was shown in my gparted picture.  On this disc (1) I have a partition for winxp, one for **/**, one for **/home**, one for storage (**media/store**) and another for swap.  On the other HD I have just one big partition called backup (that is presented as **media/backup**) that I use to backup **/home** from disk 1 and **media/store** from disk 1.

---

### Post by Quarkrad on 2014-06-16
I have no idea where **media/dad** has come from(?) - it does contain though a lot a files/folders (but not all) that is in** /home**.  **media/dad** is 2.6GB but **/home**(the real dad) is 25GB.  Would it safe just to delete **media/dad** via gksudo nautilus?

---

### Post by oldfred on 2014-06-16
I have forgotten to mount my backup partition and backups go into my / (root). Perhaps your backup went into /media/dad which then is not in your backup?
I would make sure it all is data you have elsewhere and then delete.

I use 25GB for / (root) and find I have 11GB used of the 25GB with lots of applications installed.

---

### Post by Quarkrad on 2014-06-16
OK, I've deleted media/dad and nothing has really changed.  To be honest I'm getting a little confused - Impavidus asked why .mozilla is under root and I can understand that because I believe I've configured this setup to have separate / and /home partitions. Indeed, .mozilla is in my /home directory but as 'everything' is shown under 'root' I'm not sure how to answer the question.  Nautilus shows everything - it would be nice if I could 'see' things on a partition basis.  bab1 shows dadubuntu as 31GB and I can see on gparted that this is a specific partition (and this is the one flagging up as my disk has no space on it).  When you open up dadubuntu you get bab2 that shows / as 9.5GB - I'm confused at the moment, because I do not understand (sorry), how the 31GB becomes 9.5GB, where and what is the other 21.5GB?

---

### Post by oldfred on 2014-06-16
Did you empty trash? 
And emptying trash in / can be difficult as Impavidus said you never launch applications as the root user or with sudo or gksudo.

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

---

### Post by Quarkrad on 2014-06-17
I've just completed all the actions on the above links - as well as running bleechbit (I run bleechbit regularly as stated previously) - I have saved 3.16GB. Gparted now report that** /** is 26.64GB.  This seems very large to me - from what I've read** /** is small'ish when using a separate partition for** /home**; but perhaps not.  I've only got 11% spare capacity on my **/** partition - what size should the** /** partition be for a 14.04 system?

---

### Post by mastablasta on 2014-06-17
well that's mighty strange indeed.

/ is not big unless you install some large programs. but Linux stuff is usually quite small.

for example i have assigned 8 GB in virtualbox for the whole system. and there is about 1 GB free after adding LAMP server and some other stuff i was trying out and testing. ok since then i deleted and reinstalled from minimal iso (to learn and to install what i need) and again 8 GB was more than enough.

as an alternative to separate home partition it might be better to just create separate data partition. /home is like my documents (if you know Windows). and then on reinstall all oyu need to do is backup home to data partition and then restore it once reinstall is completed. that's how Linux Mint does it actually. i did it as well once.

one thing that brings plenty to /home is any windows programs in wine. but that should be on home not on root i believe.

---

### Post by steeldriver on 2014-06-17
Can we see

```

sudo du -xsh --exclude={/dev,/proc,/run,/sys} /

df -h /

```

Comparing these will tell us if there is stuff 'hiding' under any of your other mount points. The first one will take some time.

---

### Post by Quarkrad on 2014-06-17
I haven't install wine as such because I do not run any windoze programs but I have installed Google Earth and Teamviewer which I think do install wine to run.
[B]
dad@dadubuntu:~$ sudo du -xsh --exclude={/dev,/proc,/run,/sys} /
[sudo] password for dad: 
5.8G	/
dad@dadubuntu:~$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        30G   26G  1.7G  94% /
dad@dadubuntu:~$ [/B]

---

### Post by steeldriver on 2014-06-17
So I think the most likely explanation is that you wrote a bunch of files to /media/backup, /media/store, or possibly /home either before you created separate partitions for them, or at some point when they weren't mounted for some reason. That space now counts as 'used' as far as the disk is concerned, but doesn't appear anywhere in your running filesystem because the subsequent mounts are hiding it.

You will need to unmount those partitions and have a look - for /media/backup and /media/store you can probably do that from the running system - if you need to dig underneath /home you will only be able to do that either from recovery mode or from a live CD/USB

---

### Post by grahammechanical on 2014-06-17
We can easily confuse partitions and folders. For example, / can be a partition of a definite size that can become full. But / is also a directory/folder in the /partition and certain commands will show / the folder to be 100% used but that folder and others can expand until most space in the /partition is used and then we get warning messages.

When I run those two commands on my system the first command shows the same amount of disk space used as the second command. But on your system the first command shows 5.8G used with the second command showing 26G used. I come to the conclusion that you have stuff on sda5 that is not being counted by the first command. Either that or there are symbolic links to data on other partitions and the second command is adding in that data.

Based on the Gparted screen shot I would say the sda5 is full.

Regards.

---

### Post by Quarkrad on 2014-06-17
Historically - I was running 12.04 and running out of disk space because I have lot family video files (these were, and are, in **media/store**).  So,  I bought 2 x 1TB hard drives and decided to do a clean install (I had to anyway with new disks) of 14.04.  I also decided, for the first time, to have a separate **/home** to make future upgrades easier (used ubuntu since 8.04).  I installed HD1 and partitioned it with partitions shown in gparted2 below - installed windoze xp (for itunes and some video editing s/w I use) and then followed the prompts during the 14.04 install to put** /** on sda5 and **/home** on sda6.  I then connect my old HD2 that I used for backup and copied my old **media/store** to sda7 and my backed up Documents, Desktop, Downloads, etc to my new empty folders in sda6.  I then installed some of the old s/w I used to use via the software centre on my new 14.04 machine and where applicable things like .mozilla and the .thunderbird profiles from my old backup disk (HD2) to the hidden folders in sda6.  At this point I had a pc almost like my old, took out my old backup HD and installed the new 1T, HD2, backup drive.  Configured it and using gdmin-rsync backed up my new 14.04 machine/HD1 to this new 1T backup drive (sdb1).  It was difficult to judge the size of **/**, from what I read having a separate **/home** it would be fairly small but having a 1T HD I went for 20GB to be future proof.  Hence my surprise when I was told that I was running out of disk space and had to increase **/ **from 20GB to 30GB.  But now I being told **/** (30GB) is running out of space!  bab10 shows my current state and bab11 is **/** expanded  (this is where the full 30GB partition is gparted becomes 6.2GB).  I am interested where there is a media entry under **/** - although it is only 12.3KB (my guess is these are something like symbolic links).  If you right click on it and choose open folder you get bab12.  At the end of the day, what ever is reading what, my / partition is filling up - I was hoping not to have to increase/decrease partitions once they were set up (at least at this rate).

---

### Post by oldfred on 2014-06-17
My / (root) is 11GB and 2GB of that is /home. All data except .wine is in other data folders. Of the 2GB in /home over 75% of that is the .wine folder, so my / is about 9GB with lots of apps installed.

This will show what you have in /root.
       to also see hidden in /root folder
sudo -s
du -sh /root/.[A-z]* /root/*
    
 Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

Some other commands to check sizes:

 #check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by Quarkrad on 2014-06-18
```
dad@dadubuntu:~$ sudo -s
sudo password for dad: 
**root@dadubuntu:~# du -sh /root/.[A-z]* /root/***
4.0K	/root/.bash_history
4.0K	/root/.bashrc
2.1M	/root/.cache
148K	/root/.config
12K	/root/.dbus
4.0K	/root/.fstab.log
8.0K	/root/.gadmin-rsync
4.0K	/root/.gconf
524K	/root/.gimp-2.8
8.0K	/root/.gnome2
4.0K	/root/.gnome2_private
668K	/root/.gstreamer-0.10
4.0K	/root/.gvfs
256K	/root/.kde
1.4M	/root/.local
28K	/root/.macromedia
12M	/root/.mozilla
4.0K	/root/.ntfs-config.conf
4.0K	/root/.profile
48K	/root/.synaptic
20K	/root/.thumbnails
4.0K	/root/Desktop
428K	/root/output.txt
root@dadubuntu:~# sudo du -hx --max-depth=1 / 2> /dev/null
12M	/sbin
651M	/lib
18M	/root
109M	/boot
2.4M	/tmp
12K	/media
4.0K	/cdrom
4.0K	/windows
16K	/lost+found
4.2G	/usr
12M	/bin
452K	/.rpmdb
661M	/var
253M	/opt
3.5M	/lib32
36M	/etc
4.0K	/mnt
4.0K	/srv
4.0K	/lib64
5.9G	/
```
```

**root@dadubuntu:~# sudo du -h --max-depth=1 / | grep '[0-9]G\>' # folders larger than 1GB**
du: cannot access ‘/run/user/1000/gvfs’: Permission denied
23G	/home
4.2G	/usr
du: cannot access ‘/proc/6526/task/6526/fd/3’: No such file or directory
du: cannot access ‘/proc/6526/task/6526/fdinfo/3’: No such file or directory
du: cannot access ‘/proc/6526/fd/3’: No such file or directory
du: cannot access ‘/proc/6526/fdinfo/3’: No such file or directory
```
```
**root@dadubuntu:~# sudo find / -name '*' -size +1G # files larger than 1GB**
find: ‘/run/user/1000/gvfs’: Permission denied
/home/dad/france ride/capture001.avi
/media/backup/dad/france ride/capture001.avi
/media/backup/olddad/france ride/capture001.avi
/media/backup/oldstore/Eddy Merckx/Eddy Merckx - La Course en Tete/Eddy Merckx - La Course en Tete.divx.avi
/media/backup/oldstore/Eddy Merckx/Eddy Merckx - La Course en Tete_The Greatest Show on Earth/Eddy Merckx - La Course en Tete.divx.avi
/media/backup/oldstore/French Ride DVD/canopusfiles/movie.m2v
/media/backup/oldstore/French Ride DVD/capture.avi
/media/backup/oldstore/Home Video/1112/1112can.m2v
/media/backup/oldstore/Home Video/1112/1112can.wav
/media/backup/oldstore/Home Video/12 elements/12can.m2v
/media/backup/oldstore/Home Video/12 elements/12can.wav
/media/backup/oldstore/Home Video/1314/1314can.m2v
/media/backup/oldstore/Home Video/1314/1314can.wav
/media/backup/oldstore/Home Video/1516/1516can.m2v
/media/backup/oldstore/Home Video/1516/1516can.wav
/media/backup/oldstore/Home Video/1718/1718can.m2v
/media/backup/oldstore/Home Video/1718/1718can.wav
/media/backup/oldstore/Home Video/1920/1920.m2v
/media/backup/oldstore/Home Video/1920/1920.wav
/media/backup/oldstore/Home Video/2122/2122.m2v
/media/backup/oldstore/Home Video/2122/2122.wav
/media/backup/oldstore/Home Video/2324/2324.m2v
/media/backup/oldstore/Home Video/2324/2324.wav
/media/backup/oldstore/Home Video/25.avi
/media/backup/oldstore/Home Video/2526/2526.m2v
/media/backup/oldstore/Home Video/2526/2526.wav
/media/backup/oldstore/Home Video/26.avi
/media/backup/oldstore/Home Video/27.avi
/media/backup/oldstore/Home Video/2728/2728.m2v
/media/backup/oldstore/Home Video/2728/2728.wav
/media/backup/oldstore/Home Video/2930/2930.m2v
/media/backup/oldstore/Home Video/2930/2930.wav
/media/backup/oldstore/Home Video/3132/3132.m2v
/media/backup/oldstore/Home Video/3132/3132.wav
/media/backup/oldstore/Home Video/3334/33.avi
/media/backup/oldstore/Home Video/3334/3334.avi
/media/backup/oldstore/Home Video/3334/34.avi
/media/backup/oldstore/Home Video/34 elements/3.avi
/media/backup/oldstore/Home Video/3536/35.avi
/media/backup/oldstore/Home Video/3536/36a.avi
/media/backup/oldstore/Home Video/78/78can.m2v
/media/backup/oldstore/Home Video/78/78can.wav
/media/backup/oldstore/Home Video/910/910can.m2v
/media/backup/oldstore/Home Video/910/910can.wav
/media/backup/oldstore/Ian/DVD 5/30.m2p
/media/backup/store/Eddy Merckx/Eddy Merckx - La Course en Tete/Eddy Merckx - La Course en Tete.divx.avi
/media/backup/store/Eddy Merckx/Eddy Merckx - La Course en Tete_The Greatest Show on Earth/Eddy Merckx - La Course en Tete.divx.avi
/media/backup/store/French Ride DVD/canopusfiles/movie.m2v
/media/backup/store/French Ride DVD/capture.avi
/media/backup/store/Home Video/1112/1112can.m2v
/media/backup/store/Home Video/1112/1112can.wav
/media/backup/store/Home Video/12 elements/12can.m2v
/media/backup/store/Home Video/12 elements/12can.wav
/media/backup/store/Home Video/1314/1314can.m2v
/media/backup/store/Home Video/1314/1314can.wav
/media/backup/store/Home Video/1516/1516can.m2v
/media/backup/store/Home Video/1516/1516can.wav
/media/backup/store/Home Video/1718/1718can.m2v
/media/backup/store/Home Video/1718/1718can.wav
/media/backup/store/Home Video/1920/1920.m2v
/media/backup/store/Home Video/1920/1920.wav
/media/backup/store/Home Video/2122/2122.m2v
/media/backup/store/Home Video/2122/2122.wav
/media/backup/store/Home Video/2324/2324.m2v
/media/backup/store/Home Video/2324/2324.wav
/media/backup/store/Home Video/25.avi
/media/backup/store/Home Video/2526/2526.m2v
/media/backup/store/Home Video/2526/2526.wav
/media/backup/store/Home Video/26.avi
/media/backup/store/Home Video/27.avi
/media/backup/store/Home Video/2728/2728.m2v
/media/backup/store/Home Video/2728/2728.wav
/media/backup/store/Home Video/2930/2930.m2v
/media/backup/store/Home Video/2930/2930.wav
/media/backup/store/Home Video/3132/3132.m2v
/media/backup/store/Home Video/3132/3132.wav
/media/backup/store/Home Video/3334/33.avi
/media/backup/store/Home Video/3334/3334.avi
/media/backup/store/Home Video/3334/34.avi
/media/backup/store/Home Video/34 elements/3.avi
/media/backup/store/Home Video/3536/35.avi
/media/backup/store/Home Video/3536/36a.avi
/media/backup/store/Home Video/78/78can.m2v
/media/backup/store/Home Video/78/78can.wav
/media/backup/store/Home Video/910/910can.m2v
/media/backup/store/Home Video/910/910can.wav
/media/backup/store/Ian/DVD 5/30.m2p
/media/backup/store/virtualbox/Android ICS/Android ICS.vdi
/media/backup/store/virtualbox/kubuntu 12.04/kubuntu 12.04.vdi
/media/backup/store/virtualbox/lubuntu 12.04 1/lubuntu 12.04 1.vdi
/media/backup/store/virtualbox/lubuntu 12.04 Jenny/lubuntu 12.04 1 Clone.vdi
/media/backup/store/virtualbox/newmachine/newmachine.vdi
/media/backup/store/virtualbox/nlite/nlite.vdi
/media/backup/store/virtualbox/Ubuntu 12.04 base/Ubuntu 12.04 base.vdi
/media/backup/store/virtualbox/Ubuntu 12.04 Clone (mimi)/Ubuntu 12.04 base Clone.vdi
/media/backup/store/virtualbox/Ubuntu 12.04 Jenny/Ubuntu 12.04 Jenny.vdi
/media/backup/store/virtualbox/ubuntu gnome/ubuntu gnome.vdi
/media/backup/store/virtualbox/win7/win7.vdi
/media/backup/store/virtualbox/Win7 base Clone/Win7 base Clone.vdi
/media/backup/store/virtualbox/win7 Clone/win7 Clone.vdi
/media/backup/store/virtualbox/win7 Clone 2/win7 Clone 2.vdi
/media/backup/store/virtualbox/win7 SkyGo/win7 Clone test.vdi
/media/backup/store/virtualbox/WinXP Clone/WinXP base Clone-disk1.vdi
/media/backup/store/virtualbox/Xubuntu base/Xubuntu.vdi
/media/backup/store/virtualbox/Xubuntu Clone/Xubuntu Clone.vdi
/media/store/Eddy Merckx/Eddy Merckx - La Course en Tete/Eddy Merckx - La Course en Tete.divx.avi
/media/store/Eddy Merckx/Eddy Merckx - La Course en Tete_The Greatest Show on Earth/Eddy Merckx - La Course en Tete.divx.avi
/media/store/French Ride DVD/canopusfiles/movie.m2v
/media/store/French Ride DVD/capture.avi
/media/store/Home Video/1112/1112can.m2v
/media/store/Home Video/1112/1112can.wav
/media/store/Home Video/12 elements/12can.m2v
/media/store/Home Video/12 elements/12can.wav
/media/store/Home Video/1314/1314can.m2v
/media/store/Home Video/1314/1314can.wav
/media/store/Home Video/1516/1516can.m2v
/media/store/Home Video/1516/1516can.wav
/media/store/Home Video/1718/1718can.m2v
/media/store/Home Video/1718/1718can.wav
/media/store/Home Video/1920/1920.m2v
/media/store/Home Video/1920/1920.wav
/media/store/Home Video/2122/2122.m2v
/media/store/Home Video/2122/2122.wav
/media/store/Home Video/2324/2324.m2v
/media/store/Home Video/2324/2324.wav
/media/store/Home Video/25.avi
/media/store/Home Video/2526/2526.m2v
/media/store/Home Video/2526/2526.wav
/media/store/Home Video/26.avi
/media/store/Home Video/27.avi
/media/store/Home Video/2728/2728.m2v
/media/store/Home Video/2728/2728.wav
/media/store/Home Video/2930/2930.m2v
/media/store/Home Video/2930/2930.wav
/media/store/Home Video/3132/3132.m2v
/media/store/Home Video/3132/3132.wav
/media/store/Home Video/3334/33.avi
/media/store/Home Video/3334/3334.avi
/media/store/Home Video/3334/34.avi
/media/store/Home Video/34 elements/3.avi
/media/store/Home Video/3536/35.avi
/media/store/Home Video/3536/36a.avi
/media/store/Home Video/78/78can.m2v
/media/store/Home Video/78/78can.wav
/media/store/Home Video/910/910can.m2v
/media/store/Home Video/910/910can.wav
/media/store/Ian/DVD 5/30.m2p
/media/store/virtualbox/Android ICS/Android ICS.vdi
/media/store/virtualbox/kubuntu 12.04/kubuntu 12.04.vdi
/media/store/virtualbox/lubuntu 12.04 1/lubuntu 12.04 1.vdi
/media/store/virtualbox/lubuntu 12.04 Jenny/lubuntu 12.04 1 Clone.vdi
/media/store/virtualbox/newmachine/newmachine.vdi
/media/store/virtualbox/nlite/nlite.vdi
/media/store/virtualbox/Ubuntu 12.04 base/Ubuntu 12.04 base.vdi
/media/store/virtualbox/Ubuntu 12.04 Clone (mimi)/Ubuntu 12.04 base Clone.vdi
/media/store/virtualbox/Ubuntu 12.04 Jenny/Ubuntu 12.04 Jenny.vdi
/media/store/virtualbox/ubuntu gnome/ubuntu gnome.vdi
/media/store/virtualbox/win7/win7.vdi
/media/store/virtualbox/Win7 base Clone/Win7 base Clone.vdi
/media/store/virtualbox/win7 Clone/win7 Clone.vdi
/media/store/virtualbox/win7 Clone 2/win7 Clone 2.vdi
/media/store/virtualbox/win7 SkyGo/win7 Clone test.vdi
/media/store/virtualbox/WinXP Clone/WinXP base Clone-disk1.vdi
/media/store/virtualbox/Xubuntu base/Xubuntu.vdi
/media/store/virtualbox/Xubuntu Clone/Xubuntu Clone.vdi
/proc/kcore
find: ‘/proc/11203/task/11203/fd/5’: No such file or directory
find: ‘/proc/11203/task/11203/fdinfo/5’: No such file or directory
find: ‘/proc/11203/fd/5’: No such file or directory
find: ‘/proc/11203/fdinfo/5’: No such file or directory
**root@dadubuntu:~# find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h**
4.0K	./aptdaemon-8erw4q
4.0K	./.gnome2_private
4.0K	./.googleearth
4.0K	./.gvfs
4.0K	./Public
4.0K	./Templates
8.0K	./.cups
8.0K	./.hplip
8.0K	./.mplayer
8.0K	./.sane
12K	./.dbus
16K	./.adobe
16K	./.dropbox-master
16K	./.dvdcss
16K	./.gnome2
20K	./Videos
24K	./Map Overlays
28K	./lizgraham
28K	./.unison
36K	./.filezilla
36K	./.macromedia
36K	./.pki
68K	./.winff
316K	./.arista
540K	./.kde
592K	./.gimp-2.8
656K	./.compiz
668K	./.gstreamer-0.10
820K	./.gconf
1.9M	./.dropbox
3.2M	./.thumbnails
8.0M	./.teamviewer
20M	./.config
25M	./.local
60M	./.mozilla
63M	./bin
63M	./house
83M	./.cache
83M	./Pictures
90M	./Music
102M	./Audio
128M	./Dropbox
232M	./.VirtualBox
1.7G	./.thunderbird
2.1G	./france ride
2.2G	./.aMule
2.9G	./Desktop
3.1G	./Documents
9.6G	./Downloads
**root@dadubuntu:~#dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n**
26	libjpeg8
26	libjpeg8-dev
26	libjpeg-dev
28	linux-generic
28	linux-headers-generic
28	linux-image-generic
28	ubuntu-restricted-addons
29	libjson0
29	libperl5.18
30	activity-log-manager-control-center
30	ubuntu-restricted-extras
31	libcolumbus1-common
31	module-init-tools
31	phonon-backend-gstreamer1.0
34	g++
34	zeitgeist
35	checkbox-ng-service
37	build-essential
39	app-install-data-partner
39	gsettings-ubuntu-schemas
40	iproute
40	libpthread-stubs0-dev
40	libxshmfence1
40	ubuntu-settings
41	gcc
41	libxshmfence1
41	python-gobject
42	libnatpmp1
43	fonts-thai-tlwg
43	libufe-xidgetter0
43	plainbox-secure-policy
44	libaudit-common
44	libsecret-common
44	ppa-purge
44	ruby
45	checkbox-ng
45	gir1.2-gtkclutter-1.0
45	python-dev
46	deja-dup-backend-gvfs
46	gir1.2-gdesktopenums-3.0
46	libao-common
46	libxau6
46	libxdamage1
46	libxdamage1
46	libxres1
46	ubuntu-keyring
47	grub-gfxpayload-lists
47	libaccount-plugin-generic-oauth
47	libharfbuzz-icu0
47	libmythes-1.2-0
47	libpwquality-common
47	libxcomposite1
47	unity-gtk-module-common
48	libtext-levenshtein-perl
48	libwhoopsie0
48	policykit-desktop-privileges
48	ubuntu-extras-keyring
49	gir1.2-messagingmenu-1.0
49	libestr0
49	libopenal-data
49	libva-egl1
49	libva-tpi1
49	libxinerama1
49	python-imaging
50	gir1.2-appindicator3-0.1
50	gir1.2-clutter-gst-2.0
50	libxau6
50	libxcb-dri3-0
50	libxcb-present0
50	tsconf
51	gkbd-capplet
51	libaccount-plugin-google
51	libenca-dev
51	libkeyutils1
51	libxcb-dri3-0
51	libxcb-present0
51	libxcb-shm0
51	qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
51	tcl
51	tk
52	command-not-found
52	glib-networking-common
52	libpython3-stdlib
52	libunity-scopes-json-def-desktop
52	libxshmfence-dev
52	overlay-scrollbar
52	wireless-regdb
53	liblwp-protocol-https-perl
53	libmnl0
53	libva-drm1
53	unity-scopes-runner
54	gir1.2-notify-0.7
54	libcap-ng0
54	libxcb-keysyms1
54	unity-scopes-master-default
55	account-plugin-windows-live
55	libcrypt-passwdmd5-perl
55	libfile-listing-perl
56	laptop-detect
56	libattr1
56	libck-connector0
56	libgdk-pixbuf2.0-common
56	libhttp-date-perl
56	liblog-message-simple-perl
56	libsemanage-common
56	libxcb-shape0
56	libxv1
56	phonon
57	libcap2
57	liblockfile1
57	libmtp-runtime
57	libsonic0
57	libva-wayland1
57	libxcb-render-util0
57	libxfixes3
57	python-lockfile
57	vbetool
57	xserver-xorg-video-glamoregl
58	libatomic1
58	libencode-locale-perl
58	libio-string-perl
58	libjbig-dev
58	libpython-stdlib
58	liburl-dispatcher1
58	libxxf86vm1
58	libxxf86vm1
58	lsb-security
58	smistrip
59	libasyncns0
59	libpwquality1
59	libxss1
59	libxxf86dga1
60	gir1.2-freedesktop
60	libcanberra-gtk0
60	libcanberra-gtk3-0
60	libdotconf0
60	libnet-smtp-ssl-perl
60	libnfnetlink0
60	libtag1c2a
60	libxcb-dri2-0
60	mscompress
60	rfkill
60	tk8.6
60	ubuntu-desktop
60	ubuntu-minimal
60	ubuntu-standard
60	xul-ext-webaccounts
61	libsigsegv2
61	libusbmuxd2
61	libva-glx1
61	libxcb-dri2-0
61	libxdamage-dev
61	python-commandnotfound
61	python-dirspec
61	session-migration
61	x11proto-dri2-dev
62	gtk3-engines-unico
62	libwebpmux1
62	libxfixes3
62	python3-commandnotfound
62	python-netifaces
62	python-ntdb
62	python-six
63	account-plugin-twitter
63	friends-facebook
63	libdaemon0
63	libxtst6
63	powermgmt-base
63	python3-six
63	python-dbus-dev
64	account-plugin-flickr
64	folks-common
64	gir1.2-coglpango-1.0
64	gir1.2-secret-1
64	libfile-basedir-perl
64	libnepomukcleaner4
64	libnet-domain-tld-perl
64	libutempter0
64	libwmf0.2-7-gtk
64	libxtst6
64	oneconf-common
64	tcl8.6
64	webaccounts-extension-common
64	xserver-xorg-input-all
64	xserver-xorg-video-all
65	account-plugin-facebook
65	gir1.2-dbusmenu-glib-0.4
65	gir1.2-gdkpixbuf-2.0
65	libexttextcat-2.0-0
65	libffi6
65	libijs-0.35
65	libnih-dbus1
65	libnspr4-0d
65	libproxy1-plugin-networkmanager
65	libqmobipocket1
65	libqtassistantclient4
65	libva-x11-1
65	libxcb-image0
65	libxcb-sync1
65	libxcb-sync1
65	libxmuu1
65	oneconf
66	account-plugin-google
66	glib-networking-services
66	libclone-perl
66	libfontenc1
66	lsb-invalid-mta
66	netbase
66	plymouth-label
66	python-gi-cairo
67	friendly-recovery
67	libcolamd2.8.0
67	libsys-hostname-long-perl
67	libwayland-cursor0
67	python3-gi-cairo
67	ttf-dejavu-core
68	friends-twitter
68	gnomine
68	libgphoto2-l10n
68	liboauth0
68	libpam-cap
68	libtext-wrapi18n-perl
68	libunityvoice1
68	python-pam
68	unity-gtk2-module
68	unity-gtk3-module
68	x11proto-damage-dev
69	faac
69	gir1.2-gudev-1.0
69	hostname
69	libgrip0
69	libnl-genl-3-200
69	libnotify-bin
69	libpam-ck-connector
69	libsignon-plugins-common1
69	libxkbcommon-x11-0
70	libffi6
70	libgsettings-qt1
70	libhttp-daemon-perl
70	libio-html-perl
70	libnih-dbus1
70	libnm-gtk-common
70	libpaper-utils
70	libpython-dev
70	libxdmcp6
70	rpm2cpio
71	hardening-includes
71	libdlrestrictions1
71	libio-socket-inet6-perl
71	liblockfile-bin
71	libxcb-xfixes0
71	libxdmcp6
71	python3-gdbm
72	libasprintf0c2
72	libcanberra-pulse
72	libdigest-hmac-perl
72	libhttp-negotiate-perl
72	libntrack-qt4-1
72	libsub-name-perl
72	libwacom2
72	ubuntu-artwork
73	libavc1394-0
73	libesd0
73	libopenobex1
73	libsub-identify-perl
73	libusb-0.1-4
73	libuuid-perl
73	libwildmidi-config
73	libxcb-icccm4
73	libxvmc1
73	libyajl2
73	odbcinst
73	telepathy-logger
74	libnss3-1d
74	librpmsign1
74	libxcb-util0
74	python3-louis
74	x11proto-fixes-dev
75	apport-symptoms
75	libasprintf-dev
75	libtext-charwidth-perl
75	libwhoopsie-preferences0
75	ntrack-module-libnl-0
75	ttaenc
75	unity-scope-calculator
75	unity-scope-manpages
75	unity-scope-texdoc
76	enchant
76	init-system-helpers
76	libacl1
76	libhtml-tagset-perl
76	libogg0
76	libsystemd-daemon0
76	libwww-robotrules-perl
76	ubuntu-sso-client
76	unity-scope-firefoxbookmarks
76	unity-scope-openclipart
76	unity-scope-tomboy
77	libgupnp-igd-1.0-4
77	libidl-common
77	libpciaccess0
77	printer-driver-sag-gdi
77	python3-defer
77	python-defer
77	unity-scope-devhelp
77	unity-scope-virtualbox
77	unity-scope-yelp
78	iputils-arping
78	libamd2.3.1
78	libgusb2
78	libjte1
78	libmtdev1
78	libterm-ui-perl
78	libvorbisfile3
78	libxp6
78	libxrender1
78	lockfile-progs
78	python-debtagshw
78	python-gdbm
78	python-tdb
78	unity-scope-chromiumbookmarks
78	unity-scope-colourlovers
78	unity-scope-gourmet
78	unity-scope-zotero
78	whoopsie-preferences
79	esound-common
79	geoclue-ubuntu-geoip
79	libatk-adaptor
79	libcamd2.3.1
79	libccolamd2.8.0
79	libemail-valid-perl
79	libfile-desktopentry-perl
79	libxcursor1
79	libxrender1
79	python3-markupsafe
80	diffstat
80	kubuntu-debug-installer
80	libalgorithm-merge-perl
80	libcanberra-gtk-module
80	libgnomecanvas2-common
80	libgnome-keyring-common
80	libminiupnpc8
80	libpciaccess0
80	libtext-soundex-perl
80	libwnck-common
80	libxcb-render0
80	libxrandr2
80	signon-plugin-password
80	software-center-aptdaemon-plugins
80	telepathy-indicator
80	unity-scope-clementine
80	x11proto-xf86vidmode-dev
80	xorg
81	gir1.2-gnomekeyring-1.0
81	gir1.2-signon-1.0
81	gnome-session-canberra
81	libdatrie1
81	libsm6
81	libsm6
81	libxau-dev
81	signon-keyring-extension
81	unity-scope-gmusicbrowser
81	unity-scope-musique
82	libaccount-plugin-1.0-0
82	libboost-system1.54.0
82	libepub0
82	libnotify4
82	libpolkit-agent-1-0
82	libsasl2-modules-db
82	libxcb-dri3-dev
82	lsb-base
82	unity-scope-audacious
82	unity-scope-guayadeque
83	libavahi-glib1
83	libgpm2
83	libntrack0
84	libgif4
84	libgoa-1.0-common
84	libperlio-gzip-perl
84	libsigc++-2.0-0c2a
84	qtchooser
85	cpp
85	gir1.2-atspi-2.0
85	libdebconfclient0
85	libdvdcss2
85	libtext-iconv-perl
85	libyaml-tiny-perl
85	whiptail
85	xserver-xorg-video-fbdev
86	inputattach
86	libdrm-nouveau2
86	libfs6
86	libjson-c2
86	libnet-http-perl
86	python-talloc
86	remmina-plugin-vnc
86	xauth
87	gir1.2-accounts-1.0
87	libalgorithm-diff-xs-perl
87	libfile-fcntllock-perl
87	libgconf2.0-cil
87	libhyphen0
87	libisccc90
87	libmimic0
87	libmodule-pluggable-perl
87	libplist1
87	libstartup-notification0
87	libxcb-present-dev
87	nux-tools
87	python-twisted-bin
88	burg
88	dh-apparmor
88	friends
88	gir1.2-goa-1.0
88	libcanberra-gtk3-module
88	libfile-copy-recursive-perl
88	libgtop2-common
88	libhtml-form-perl
88	libmission-control-plugins0
88	libpipeline1
88	plymouth-theme-ubuntu-text
88	python-smbc
89	gir1.2-totem-plparser-1.0
89	libmjpegutils-2.1-0
89	libpaper1
89	systemd-shim
89	xserver-xorg-video-vesa
90	libclutter-gtk-1.0-0
90	libdrm-nouveau2
90	libiw30
90	libspeechd2
90	libtalloc2
90	libwayland-client0
90	libwayland-egl1-mesa
90	libzip2
91	libnuma1
91	libpcsclite1
91	libxxf86vm-dev
91	xul-ext-websites-integration
92	acpi-support
92	gir1.2-javascriptcoregtk-3.0
92	gstreamer0.10-nice
92	gstreamer1.0-nice
92	landscape-client-ui-install
92	libatk1.0-data
92	libgl1-mesa-dev
92	libgpg-error0
92	libieee1284-3
92	libipc-system-simple-perl
92	liblocale-gettext-perl
92	vorbisgain
92	xinput
92	xserver-xorg-video-ati
93	hwdata
93	ibus-gtk
93	ibus-gtk3
93	libgomp1
93	libjbig0
93	libsoup-gnome2.4-1
93	libv4l2rds0
93	mono-runtime
93	python-qt4-dbus
94	libcogl-pango15
94	libtevent0
95	libappindicator1
95	libappindicator3-1
95	libgsm1
95	libgssdp-1.0-3
95	libunity-misc4
95	phonon-backend-gstreamer-common
96	crda
96	libiec61883-0
96	libnet-libidn-perl
96	libxcb-shape0-dev
96	linux-sound-base
97	libxfixes-dev
98	file
98	gstreamer1.0-clutter
98	libkubuntu0
98	liblinear-tools
99	libatasmart4
99	libcap2-bin
99	libcupsimage2-dev
99	libfriends0
99	libmpcdec6
99	libspectre1
99	printer-driver-ptouch
100	debugedit
100	libarchive-extract-perl
100	libaudio-scrobbler-perl
100	liblwp-mediatypes-perl
100	libmail-sendmail-perl
100	libunity-gtk3-parser0
100	mp3info
100	python3
100	x11-xfs-utils
100	xdg-user-dirs-gtk
101	libindicator7
101	libslv2-9
101	ubuntu-system-service
101	update-inetd
101	xorg-sgml-doctools
102	libgudev-1.0-0
102	libsocket6-perl
102	libthai0
102	python-glade2
102	ssl-cert
103	libcomerr2
103	libheimntlm0-heimdal
103	libxcb-randr0
103	libzephyr4
104	gir1.2-gmenu-3.0
104	libclass-accessor-perl
104	libdconf1
104	libhttp-cookies-perl
104	libunity-gtk2-parser0
104	libwnck-3-common
104	xinit
104	xserver-xorg-video-modesetting
105	libcolorhug1
105	libdrm2
105	libsignon-extension1
106	apturl
106	libassuan0
106	libdrm2
106	libraw1394-11
106	libxtables10
106	mono-gac
107	gir1.2-cogl-1.0
107	libbind9-90
107	libgdbm3
107	liblinear1
107	libsbc1
107	libxi6
107	python-notify
108	appmenu-qt
108	indicator-applet-complete
108	libmms0
108	libproxy1-plugin-gsettings
108	libuuid1
108	libuuid1
108	libwayland-server0
108	plainbox-provider-resource-generic
109	liba52-0.7.4
109	netcat-openbsd
109	readline-common
110	dconf-gsettings-backend
110	libfaac0
110	libxdmcp-dev
110	mono-4.0-gac
110	qtdeclarative5-window-plugin
110	sensible-utils
111	geoclue
111	libupower-glib1
111	tcpd
111	xfonts-mathml
112	iputils-tracepath
112	libcdaudio1
112	libchromaprint0
112	libpci3
112	libunique-3.0-0
112	libvdpau1
112	python-aptdaemon.gtk3widgets
112	python-reportlab-accel
112	unity-scope-video-remote
112	whoopsie
113	libbz2-1.0
113	libmotif-common
113	librsync1
113	libthumbnailer0
113	python3-aptdaemon.gtk3widgets
113	sgml-base
113	unity-scope-gdrive
114	libindicator3-7
114	printer-driver-pxljr
114	python3-piston-mini-client
114	xserver-xorg-input-vmmouse
115	indicator-applet-session
115	libdrm-radeon1
115	libnss3-nssdb
115	libopencore-amrwb0
115	libspeexdsp1
115	libss2
115	libtdb1
115	python-piston-mini-client
115	qtdeclarative5-qtfeedback-plugin
115	remmina-plugin-rdp
115	unity-voice-service
116	cups-bsd
116	dconf-cli
116	gsfonts-x11
116	libavahi-common-data
116	libgnomekbd-common
116	speech-dispatcher-audio-plugins
117	irqbalance
117	kerneloops-daemon
117	libavahi-gobject0
117	libmessaging-menu0
117	network-manager-pptp
117	printer-driver-min12xxw
118	gir1.2-wnck-3.0
118	libapparmor1
118	libavahi-common3
118	libdrm-radeon1
118	libshout3
118	libsystemd-login0
118	libtinyxml2.6.2
119	bzip2
119	cdparanoia
119	libkate1
119	overlay-scrollbar-gtk2
119	time
120	libfont-afm-perl
120	libtiffxx5
120	libxext6
120	lsb-release
120	system-config-printer-udev
120	xserver-xorg-video-s3
121	initramfs-tools-bin
121	libbalooxapian4
121	libpulse-mainloop-glib0
121	libwrap0
121	libxext6
121	libxpm4
121	pcmciautils
122	ed
122	libntdb1
123	gir1.2-dee-1.0
123	gir1.2-udisks-2.0
123	mtr-tiny
123	overlay-scrollbar-gtk3
124	libwrap0-dev
124	ureadahead
125	makedev
125	qtdeclarative5-unity-action-plugin
126	libheimbase1-heimdal
126	libhud2
126	xserver-xorg-video-tdfx
127	compiz
127	liblwres90
127	libpod-latex-perl
127	librest-0.7-0
127	python-gpgme
127	syslinux-legacy
127	usbmuxd
127	xorg-docs-core
128	libjson-glib-1.0-common
128	libklibc
128	libpopt0
128	nautilus-share
128	python-renderpm
129	libclutter-gst-2.0-0
129	libgcc1
129	libopenvg1-mesa
129	libxcb-dri2-0-dev
129	ssh-askpass-gnome
130	libdbusmenu-gtk3-4
130	libdbusmenu-gtk4
130	libgeoclue0
130	libkmod2
130	libmpc3
130	libqt4-dbus
130	libtasn1-6
130	popularity-contest
130	unity-webapps-common
131	fonts-lao
131	thunderbird-gnome-support
131	ttf-mscorefonts-installer
131	xserver-xorg-input-mouse
131	xserver-xorg-video-neomagic
132	libudev1
132	pppoeconf
133	libkxmlrpcclient4
133	libnet-ip-perl
133	libpam-systemd
133	libqt5feedback5
133	libsoundtouch0
133	pkg-config
133	python3-tz
134	libfontembed1
134	libgles2-mesa
134	liblqr-1-0
134	python3-software-properties
135	libbaloocore4
135	libboost-date-time1.54.0
135	libudev1
135	python3-httplib2
136	libalgorithm-diff-perl
136	libbonoboui2-common
136	libfribidi0
136	libgpg-error-dev
136	libjbig2dec0
136	libxft2
136	policykit-1-gnome
136	unity-lens-video
137	flashplugin-installer
137	libcanberra0
137	libid3tag0
137	libio-pty-perl
137	libnautilus-extension1a
137	libusb-1.0-0
137	mpg321
137	xserver-xorg-video-sisusb
138	gstreamer0.10-plugins-base-apps
138	libavahi-client3
138	libkactivities-models1
138	libprocps3
138	libspeex1
138	libunity-control-center1
138	xserver-xorg-input-evdev
139	dbus-x11
139	indicator-appmenu
139	libfile-mimeinfo-perl
139	libnm-glib-vpn1
139	libtimedate-perl
139	python3-minimal
139	python3-xkit
139	uuid-runtime
140	intltool-debian
140	libts-0.0-0
140	libvo-amrwbenc0
141	fonts-kacst-one
141	xserver-xorg-video-cirrus
142	gnome-video-effects
142	libgbm1
142	libice6
142	libnss-mdns
142	libsensors4
142	python3-oneconf
143	gir1.2-atk-1.0
143	gir1.2-json-1.0
143	libaccounts-qt5-1
143	librtmp0
143	mime-support
143	os-prober
143	python-oneconf
143	thunderbird-locale-en-gb
143	thunderbird-locale-en-us
144	cabextract
144	dconf-service
144	ftp
144	libaudit1
144	libflac++6
145	gstreamer1.0-plugins-base-apps
145	libbsd0
145	libcgmanager0
145	libgtop2-7
145	libnetfilter-conntrack3
145	libpolkit-backend-1-0
146	libbrlapi0.6
146	libxcb-sync-dev
146	libxklavier16
146	unity-lens-friends
147	libice6
147	libkactivities6
147	libnih1
147	x11proto-gl-dev
148	libaccounts-glib0
148	liblightdm-gobject-1-0
148	libnih1
148	plymouth-theme-ubuntu-logo
148	pptp-linux
148	qtdeclarative5-localstorage-plugin
149	iw
149	libsrtp0
149	libvo-aacenc0
149	lsb-core
149	python-gnomekeyring
150	libhtml-format-perl
151	avahi-autoipd
151	gstreamer1.0-plugins-bad-faad
151	libao4
151	libcupsmime1
151	libva1
151	libxcb-glx0
151	libxmu6
151	python-ldb
152	fuse
152	lame
152	libcgmanager0
152	libcrack2
152	libgcc1
153	avahi-utils
153	dc
153	gir1.2-peas-1.0
153	libart-2.0-2
153	libgxps2
153	python3-pkg-resources
154	libcdparanoia0
154	libxcb-glx0
155	appmenu-qt5
155	gir1.2-unity-5.0
155	libconfig-inifiles-perl
155	python-support
156	libgtk-3-bin
156	libpolkit-gobject-1-0
156	update-manager-core
157	libgnomekbd8
157	libmplex2-2.1-0
157	libpulsedsp
158	gir1.2-ebook-1.2
158	libframe6
158	libroken18-heimdal
158	libwildmidi1
158	qtdeclarative5-ubuntu-ui-extras-browser-plugin
159	iputils-ping
159	libdbusmenu-glib4
159	logrotate
160	adium-theme-ubuntu
160	comerr-dev
160	eject
160	libcupsimage2
160	libgail-3-0
160	libgpod-common
160	libitm1
160	libqt5sql5-sqlite
160	libsignon-glib1
160	network-manager-pptp-gnome
160	python-gconf
161	indicator-application
161	libpangox-1.0-0
161	libtwolame0
162	libfribidi-dev
162	libkrb5support0
163	libgraphite2-3
163	liblouis2
163	libyaml-0-2
163	printer-driver-c2esp
163	telnet
164	libelf1
164	libreoffice-presentation-minimizer
164	libxcb-xkb1
164	pulseaudio-module-x11
164	python3-cairo
165	libaa1
165	libieee1284-3-dev
165	libkcompactdisc4
165	webapp-container
166	libdv4
166	libkrb5-dev
166	libsasl2-2
167	libboost-iostreams1.54.0
167	libdvdread4
167	liblangtag1
167	libnl-3-200
167	python-minimal
168	apturl-common
168	libelf1
168	libofa0
168	librarian0
168	notification-daemon
168	python-httplib2
168	virtuoso-minimal
169	gir1.2-soup-2.4
169	language-selector-gnome
169	python-webkit
170	libproxy1
170	zlib1g
171	indicator-power
171	libaudio2
171	libgexiv2-2
171	libmad0
171	liborbit2
171	libqjson0
171	libsystemd-journal0
171	zlib1g
172	hyphen-en-us
172	libclutter-1.0-common
172	libgrail6
172	liblist-moreutils-perl
172	libmono-i18n4.0-cil
172	rtkit
173	gir1.2-packagekitglib-1.0
173	python3-problem-report
173	python-zeitgeist
174	bind9-host
174	lib32z1
174	libfakeroot
174	libunity-action-qt1
175	gstreamer1.0-alsa
175	libcdio-cdda1
175	libcdio-paranoia1
175	liblzo2-2
176	gksu
176	xserver-xorg-video-siliconmotion
177	libkpimutils4
177	xserver-xorg-video-r128
178	anacron
178	libgstreamer-plugins-good1.0-0
178	libpurple-bin
178	libxcb-xfixes0-dev
179	libglapi-mesa
179	syslinux
180	apg
180	gir1.2-ebookcontacts-1.2
180	libelfg0
180	libimobiledevice4
180	python3-xdg
180	python-xdg
181	dmsetup
181	libxcb1
181	pax
182	libautodie-perl
182	libbaloowidgets4
182	libkdb5-7
182	python-pkg-resources
183	insserv
183	libpcrecpp0
183	libxml2-utils
184	gir1.2-gnomedesktop-3.0
184	gnome-screenshot
184	libass4
184	libgnomeui-common
184	parted
184	software-properties-common
184	zeitgeist-datahub
185	autotools-dev
185	glib-networking
185	gnome-settings-daemon-schemas
185	python-pyorbit
185	sni-qt
185	wavpack
186	libdrm-intel1
186	libwbclient0
186	libzeitgeist-1.0-1
186	media-player-info
187	libido3-0.1-0
188	acpid
188	libbaloofiles4
188	libdecoration0
188	libdrm-intel1
188	libnewt0.52
188	libxcb1
188	python3-debian
188	python-pexpect
188	xml-core
189	libcupscgi1
189	libgcr-3-common
189	libiso9660-8
189	python3-speechd
189	python-cairo
190	libisccfg90
191	cups-browsed
191	dmidecode
191	libcloog-isl4
192	acl
192	libselinux1
192	libsensors4-dev
193	libgweather-3-6
193	librpmbuild3
193	libselinux1
193	python3-pyparsing
194	at
194	bsdutils
194	libopenjpeg2
194	libxkbfile1
195	libv4l-0
195	python3-urllib3
196	aptdaemon
196	gnome-font-viewer
196	libkadm5clnt-mit9
196	libnetpbm10
196	printer-driver-splix
197	libapparmor-perl
197	mawk
198	libbluetooth3
198	libpango1.0-0
198	libuchardet0
198	unity-scope-musicstores
198	usb-modeswitch
199	libglade2-0
199	liblircclient0
199	libmrm4
201	libasan0
201	libgeis1
201	libmpeg2-4
201	libqt4-sql-sqlite
201	libzvbi-common
201	multiarch-support
201	xserver-xorg-video-trident
202	ttf-punjabi-fonts
203	apport-gtk
203	libcairomm-1.0-1
203	libopencore-amrnb0
204	libgnome-menu-3-0
204	libhttp-message-perl
204	python3-requests
205	gstreamer0.10-alsa
207	cups-core-drivers
207	libwavpack1
207	obexd-client
208	at-spi2-core
208	indicator-keyboard
208	libcupsfilters1
208	python-apt-common
209	xserver-xorg-video-savage
210	alien
210	libsgutils2-2
210	libupstart1
210	trash-cli
211	gcc-4.9-base
211	gcc-4.9-base
211	python3-pycurl
212	gcc-4.8-base
212	gcc-4.8-base
212	growisofs
212	libatk-bridge2.0-0
212	libauthen-sasl-perl
212	libmhash2
212	usb-modeswitch-data
213	dosfstools
213	libmpeg2encpp-2.1-0
213	xserver-xorg-video-mga
214	gir1.2-edataserver-1.2
214	libdca0
214	python3-pyatspi
215	libatspi2.0-0
215	python-pycurl
216	libmono-cairo4.0-cil
216	libpangomm-1.4-1
216	libpeas-common
216	libvdpau-dev
216	python-dateutil
217	librsvg2-common
217	qtdeclarative5-privatewidgets-plugin
217	ubuntu-release-upgrader-gtk
217	ubuntu-session
218	bluez-cups
218	liburi-perl
218	python-ibus
218	qdbus
219	ghostscript-x
219	indicator-printers
219	patch
220	icoutils
220	libgupnp-1.0-4
220	nautilus-data
220	pppconfig
220	unity-services
220	virtuoso-opensource-6.1-common
221	gstreamer1.0-pulseaudio
221	libgnome-keyring0
221	libkntlm4
221	sysv-rc
222	libdvdnav4
222	python-cupshelpers
222	usb-creator-gtk
223	initscripts
223	libavahi-client-dev
223	xbitmaps
224	libatk1.0-0
224	libportaudio2
224	psmisc
224	telepathy-idle
225	libpam0g
225	libpam-modules-bin
226	libkadm5srv-mit9
226	libmbim-glib0
226	libqapt2-runtime
226	librpmio3
226	signon-plugin-oauth2
227	libavahi-common-dev
227	libio-socket-ssl-perl
227	libwpg-0.2-2
228	dash
228	mlocate
228	patchutils
228	xserver-xorg-input-synaptics
229	libsasl2-modules
229	python-cups
229	ucf
230	libdbus-glib-1-2
230	liblua5.2-0
230	libmailtools-perl
230	libwind0-heimdal
230	xserver-xorg-video-mach64
231	fakeroot
231	libvorbis0a
232	apt-transport-https
232	libgdata-common
232	libparse-debianchangelog-perl
233	ghostscript
233	libgssrpc4
234	ifupdown
234	libx11-xcb1
235	libreoffice-avmedia-backend-gstreamer
235	libx11-xcb1
235	python3-feedparser
236	cups-ppdc
236	gzip
236	libedit2
236	libmono-i18n-west4.0-cil
236	python-simplejson
237	libpolkit-qt-1-1
237	libwacom-common
238	unity-lens-music
239	libflac8
239	libkpty4
240	bc
240	gadmin-rsync
240	gir1.2-gtksource-3.0
240	libgphoto2-port10
240	libmeanwhile1
240	libnm-gtk0
240	ntpdate
241	libdbusmenu-qt2
241	libenca0
241	python3-update-manager
241	resolvconf
242	libglapi-mesa
242	libpangoxft-1.0-0
242	libtelepathy-logger3
242	libxcb-render0-dev
242	odbcinst1debian2
242	sysvinit-utils
242	xserver-xorg-video-vmware
243	libglade2.0-cil
243	libkonq5-templates
244	gsettings-desktop-schemas
244	libgeoip1
244	telepathy-haze
244	x11-session-utils
245	binfmt-support
245	gir1.2-gnomebluetooth-1.0
245	libxfont1
245	toshset
246	libdbusmenu-qt5
246	libdc1394-22
246	libmount1
247	libblkid1
247	libhtml-parser-perl
247	libkmediaplayer4
248	libcogl-common
248	libegl1-mesa
248	unity-lens-files
249	gstreamer0.10-plugins-bad-multiverse
249	gstreamer0.10-pulseaudio
249	libakonadiprotocolinternals1
249	libdmapsharing-3.0-2
250	libneon27-gnutls
250	libsignon-qt5-1
251	libglamor0
251	libtxc-dxtn-s2tc0
252	base-passwd
252	desktop-file-utils
252	libcupsppdc1
252	libidl0
252	libkonq-common
252	libkpathsea6
252	libperl4-corelibs-perl
252	unattended-upgrades
253	friends-dispatcher
253	liblcms1
253	libx11-xcb-dev
254	obex-data-server
254	python-compizconfig
255	cuetools
255	gstreamer1.0-fluendo-mp3
255	libbamf3-2
255	libvcdinfo0
255	python-debian
256	libmpdec2
256	p11-kit-modules
257	libstreams0
257	libx86-1
258	libkdeclarative5
258	libkidletime4
258	libnice10
259	libapt-pkg-perl
259	libpangocairo-1.0-0
260	gir1.2-networkmanager-1.0
260	libgcj-common
260	libgirepository-1.0-1
260	libtxc-dxtn-s2tc0
260	p11-kit
260	unity-lens-photos
261	gstreamer1.0-plugins-bad-videoparsers
262	mountall
263	libsemanage1
263	xdg-utils
265	libenchant1c2a
265	qtdeclarative5-accounts-plugin
266	install-info
266	libustr-1.0-1
266	libv4lconvert0
266	ubuntu-drivers-common
268	gstreamer0.10-fluendo-mp3
268	libtotem-plparser18
269	gir1.2-pango-1.0
269	libkemoticons4
270	evolution-data-server-online-accounts
270	hdparm
270	libknotifyconfig4
270	libqt5positioning5
270	libquadmath0
270	python3-aptdaemon.pkcompat
270	python3-checkbox-ng
272	libasound2-plugins
272	libfolks-telepathy25
272	libxkbcommon0
272	usb-creator-common
273	libarchive-zip-perl
273	libass-dev
273	libipc-run-perl
273	libqt5test5
273	libsidplay1
274	python3-brlapi
275	ruby1.9.1
276	aptdaemon-data
276	libgnutls-openssl27
276	libjson-glib-1.0-0
277	pulseaudio-utils
279	libva-dev
280	libhcrypto4-heimdal
280	update-notifier
281	libusb-1.0-0-dev
281	libzbar0
281	pulseaudio-module-bluetooth
282	gnome-session-flashback
282	kmod
282	libavahi-core7
282	libmagickcore5-extra
283	debianutils
283	libaudiofile1
283	libxext-dev
284	libdee-1.0-4
285	cli-common
285	libgoa-1.0-0b
285	python-sip
287	gvfs-fuse
287	libgc1c2
287	libjs-jquery
288	less
288	libcdio13
289	libsmbclient
289	nepomuk-core-data
290	libebook-contacts-1.2-0
292	libbonobo2-common
292	libncurses5
293	t1utils
294	gstreamer1.0-x
294	libpangoft2-1.0-0
295	imagemagick-common
295	qtdeclarative5-qtquick2-plugin
296	indicator-bluetooth
296	libthreadweaver4
296	mousetweaks
297	libavutil52
297	libgnomecanvas2-0
297	libgnutlsxx27
298	libfolks-eds25
298	libpocketsphinx1
298	librdf0
299	libkdecorations4abi1
299	unrar
300	cron
300	libcolumbus1
300	libpam-runtime
301	libdevmapper1.02.1
301	xserver-xorg-input-wacom
301	xserver-xorg-video-nouveau
302	libk5crypto3
302	libplymouth2
302	libqt4-test
303	python2.7-dev
304	cups-pk-helper
304	libglib2.0-cil
304	libunity-webapps0
304	sed
305	libebook-1.2-14
305	liblzma5
305	libpng12-0
305	system-config-printer-common
308	gstreamer0.10-x
308	libpng12-0
308	libvisual-0.4-0
308	ubuntu-release-upgrader-core
309	dh-python
309	libbabl-0.1-0
309	libkdesu5
309	libkldap4
311	libevent-2.0-5
312	gtk2-engines-murrine
313	gir1.2-gst-plugins-base-1.0
313	libcheese-gtk23
313	libpcap0.8
314	mp3gain
315	libkresources4
316	remmina-common
317	libp11-kit0
317	vim-common
318	libnettle4
318	libwnck22
319	libfreerdp-plugins-standard
320	cpio
320	evolution-data-server-common
320	gir1.2-totem-1.0
320	libfaad2
320	make
321	libfuse2
322	libsepol1
323	dvd+rw-tools
323	libgssapi3-heimdal
323	libtsan0
324	libkrosscore4
324	libpanel-applet-4-0
325	ethtool
325	libespeak1
325	libopus0
325	python3.4
326	libatkmm-1.6-1
326	libtelepathy-farstream3
328	apt-xapian-index
328	wireless-tools
330	aspell-en
330	libsphinxbase1
331	libjpeg-turbo8
331	libpeas-1.0-0
332	libcairo-gobject2
333	libcolord1
333	libcupsfilters-dev
333	python3-mako
334	libxcb-randr0-dev
334	m4
334	pm-utils
334	shntool
334	unity-scope-home
335	libcheese7
336	im-config
336	libburn4
336	libmpg123-0
337	libpam-gnome-keyring
338	libasound2-data
339	libcroco3
341	dkms
341	gir1.2-ibus-1.0
341	gstreamer1.0-libav
342	mtools
343	libtbb2
343	zenity
344	fonts-lklug-sinhala
344	gettext-base
344	gnome-menus
344	gnome-session-common
344	libmodplug1
344	libopencv-highgui2.4
345	libkdewebkit5
345	xpdf
347	avahi-daemon
347	libgstreamer-plugins-bad0.10-0
347	libnspr4
347	libunity-protocol-private0
347	libwnck-3-0
347	python2.7
348	libexif12
348	libmono-system-configuration4.0-cil
348	libupnp6
351	libpoppler-glib8
352	libgtk-3-common
352	libnm-glib4
354	fontconfig-config
354	remmina
356	libjasper1
356	libnl-route-3-200
356	libssh-4
357	busybox-initramfs
357	libmono-system-security4.0-cil
358	gir1.2-gdata-0.0
358	sysinfo
359	flac
359	libsecret-1-0
360	bamfdaemon
361	libreadline5
361	python-ubuntu-sso-client
363	ltrace
364	aspell
364	cups-filters-core-drivers
364	garminplugin
364	gnome-power-manager
364	libaccountsservice0
364	libkonq5abi1
364	libqt5xml5
365	initramfs-tools
366	libwebp5
366	xserver-xorg
366	xtrans-dev
367	fonts-opensymbol
367	gir1.2-webkit-3.0
367	libidn11
367	mobile-broadband-provider-info
367	ncurses-base
368	libgettextpo0
368	libgme0
368	qtdeclarative5-dialogs-plugin
369	dnsutils
369	libhx509-5-heimdal
369	libt1-5
369	nautilus-dropbox
370	indicator-sound
370	libkdnssd4
370	libqca2-plugin-ossl
372	gvfs-common
372	libc-dev-bin
373	libexpat1
373	libkfilemetadata4
374	libncursesw5
374	python3-checkbox-support
375	libqt5sql5
375	libwww-perl
375	libyelp0
376	libedata-book-1.2-20
377	gconf-service
377	libp11-kit-gnome-keyring
377	xul-ext-ubufox
379	libdbus-1-3
379	libopencv-video2.4
380	libedata-cal-1.2-23
380	libgee2
380	libqt5qml-graphicaleffects
381	unzip
382	libdjvulibre-text
384	xz-utils
385	fonts-tlwg-garuda
386	libharfbuzz0b
387	klibc-utils
387	rarian-compat
388	libwebkitgtk-1.0-common
388	libwebkitgtk-3.0-common
389	libcairo-perl
390	libexpat1
390	libgnome-bluetooth11
391	libgnome-desktop-3-7
391	liblcms2-2
391	xfonts-utils
392	libgck-1-0
392	python3-dbus
392	vorbis-tools
393	libldb1
394	libmetacity-private0a
396	ubuntu-sounds
397	bluez-alsa
397	libisofs6
397	libltdl7
398	libdbus-1-3
398	python-dbus
400	gir1.2-gconf-2.0
400	policykit-1
401	e2fslibs
401	libept1.4.12
401	rpm
402	fonts-tlwg-loma
402	libgssapi-krb5-2
402	libopenal1
403	python3-oauthlib
403	python-serial
404	libreadline6
404	libreoffice-ogltrans
406	python-mutagen
406	python-oauthlib
407	cheese
408	librsvg2-2
408	nautilus-sendto
408	xserver-xorg-video-qxl
410	libakonadi-kmime4
410	phonon-backend-gstreamer
412	libexttextcat-data
415	fonts-tlwg-sawasdee
416	gnome-screensaver
417	python-openssl
420	libqt4-sql
420	mount
421	libswscale2
422	libmp3lame0
422	software-properties-gtk
424	libgnomevfs2-common
424	rpm-common
427	fonts-tlwg-waree
427	katepart
428	accountsservice
428	diffutils
429	audio-recorder
431	libhunspell-1.3-0
431	libqapt2
432	ca-certificates
432	libqt5svg5
433	base-files
433	libtinfo5
435	libraptor2-0
435	libv4l-dev
436	gir1.2-vte-2.90
436	libibus-1.0-5
438	libclucene-contribs1
440	libisc95
441	libgstreamer-plugins-bad1.0-0
442	libzeitgeist-2.0-0
442	ubuntu-ui-toolkit-theme
442	zeitgeist-core
443	gpgv
443	po-debconf
443	rhythmbox-mozilla
443	zlib1g-dev
445	libqt4-xml
446	libreoffice-gnome
446	signon-ui
448	imagemagick
448	libnepomukutils4
448	libpoppler-qt4-4
448	python-aptdaemon
449	libgdiplus
449	libpackagekit-glib2-16
450	gconf-defaults-service
450	python3-aptdaemon
451	info
453	xul-ext-unity
454	libgtkglext1
455	libmtp9
456	libfluidsynth1
456	lsof
457	librpm3
457	plymouth
458	libpcre3
458	libxt6
459	libogg-dev
460	doc-base
460	gvfs-bin
460	libkcddb4
460	rhythmbox-plugin-zeitgeist
462	consolekit
463	libpcre3
464	libvte-2.90-common
464	libxatracker2
465	fonts-tlwg-typewriter
465	libkcmutils4
466	libgnome2-bin
467	fonts-tlwg-typist
467	libopencv-flann2.4
467	unity-control-center-signon
468	fonts-tlwg-typo
468	libasound2-dev
469	fonts-tlwg-mono
471	libtinfo5
471	libvncserver0
473	libgpgme11
473	rhythmbox-plugin-cdrecorder
473	x11-xkb-utils
476	x11proto-input-dev
477	libilmbase6
481	libecal-1.2-16
482	libgd3
484	gcr
484	libgl1-mesa-glx
484	libsdl1.2debian
484	poppler-utils
485	libglu1-mesa
486	libxslt1.1
488	unity-webapps-service
489	libudisks2-0
490	x11-xserver-utils
492	strace
492	x11-common
493	libfontconfig1
494	libpulse-dev
494	libxaw7
496	librasqal3
498	libfontconfig1
499	libgmime-2.6-0
500	deborphan
500	libglu1-mesa
500	ubuntuone-client-data
502	alsa-base
505	libgtksourceview2.0-0
505	libnepomukquery4a
506	heirloom-mailx
506	libhtml-tree-perl
507	libldap-2.4-2
507	libwmf0.2-7
508	xserver-xorg-video-radeon
510	libgl1-mesa-glx
511	libgmp10
511	libnm-util2
511	libpango-perl
511	qt-at-spi
514	libsndfile1
515	python3-uno
516	gconf2-common
516	upower
520	unity-asset-pool
521	libcurl3-gnutls
523	ncurses-bin
523	python3-apport
524	sane-utils
525	libmspub-0.0-0
526	libopencv-ml2.4
526	libp11-kit-dev
528	xserver-xorg-video-openchrome
530	libpango-1.0-0
531	telepathy-mission-control-5
532	libopencv-objdetect2.4
532	xfonts-scalable
533	libgpod4
534	libqt5sensors5
535	libqt5opengl5
536	libvisual-0.4-plugins
538	libktexteditor4
541	libcompizconfig0
541	rhythmbox-plugin-magnatune
541	sound-theme-freedesktop
543	qpdf
544	libblas3
544	lightdm
545	libcurl3
547	libgksu2-0
548	unity-lens-applications
549	libbonoboui2-0
552	fontconfig
553	grub-pc
555	bsdmainutils
556	mac
561	libgdk-pixbuf2.0-0
566	libfolks25
567	fonts-tlwg-umpush
567	thunderbird-locale-en
569	python-chardet
570	libgtk2.0-bin
571	fonts-khmeros-core
571	libparted0debian1
572	vino
573	libgconf-2-4
577	gvfs
577	libtiff5
578	gconf-service-backend
579	libmusicbrainz5-0
579	libqt5printsupport5
581	gir1.2-rb-3.0
581	libgail18
581	libqt4-svg
582	libphonon4
583	libgcrypt11
583	libmng2
589	zip
590	libuil4
594	liborc-0.4-0
595	libkparts4
595	x11-utils
596	gucharmap
596	libdirac-encoder0
596	libgjs0e
598	soprano-daemon
600	gnome-desktop3-data
600	nano
603	libgnome2-0
604	gtk2-engines-pixbuf
604	liblastfm1
606	libjack-jackd2-0
607	libthai-data
607	libxcb-glx0-dev
608	gconf2
609	debconf
609	foomatic-db-compressed-ppds
613	cracklib-runtime
615	libcups2
617	language-pack-gnome-en
617	libglewmx1.10
617	liboil0.3
617	openoffice.org-hyphenation
619	gir1.2-glib-2.0
621	garmin-forerunner-tools
622	fonts-tlwg-kinnari
622	libebackend-1.2-7
622	myspell-en-au
624	xpad
625	gnome-session-bin
628	gvfs-libs
629	libical1
629	libkmime4
629	liblzma-dev
629	libqt5dbus5
630	libgcr-ui-3-1
631	xserver-xorg-video-sis
632	simple-scan
634	rsync
636	unity-greeter
636	wget
637	python3-distupgrade
638	samba-common
639	libqt5webkit5-qmlwebkitplugin
642	libqt5organizer5
643	libopencv-calib3d2.4
643	python3-apt
644	adduser
645	python-apt
646	intel-gpu-tools
647	liborbit-2-0
647	python-zope.interface
648	dnsmasq-base
649	libkrb5-26-heimdal
653	gir1.2-clutter-1.0
654	gnome-codec-install
655	libpng12-dev
661	libmp3lame-dev
662	shared-desktop-ontologies
663	libqtdbus4
663	myspell-en-za
663	totem-mozilla
663	unity-webapps-qml
664	fonts-tlwg-purisa
666	libknewstuff3-4
666	signond
668	apt-utils
668	xfonts-encodings
670	python3-gi
671	lp-solve
671	python
671	python-gtksourceview2
672	arp-scan
672	libgnome2-common
675	libnet-dns-perl
676	libfarstream-0.2-2
679	libmm-glib0
680	libmono-security4.0-cil
680	procps
680	python3-chardet
685	gir1.2-evince-3.0
689	libgettextpo-dev
691	libumfpack5.6.2
692	libsnmp-base
693	libarchive13
693	libzvbi0
695	gvfs-daemons
695	libopencv-features2d2.4
696	libglew1.10
698	brasero-cdrkit
699	usbutils
703	libfarstream-0.1-0
705	libfreerdp1
705	libgtksourceview-3.0-1
708	net-tools
709	python-gi
711	libtheora0
712	grep
713	libnux-4.0-common
717	totem
720	fonts-tlwg-norasi
722	libopus-dev
726	hunspell-en-us
728	activity-log-manager
728	libpixman-1-0
731	ufw
732	libgtk2.0-common
733	xdiagnose
735	gnome-terminal
735	libapt-inst1.5
736	gnome-icon-theme-symbolic
738	libvisio-0.0-0
740	libdrm-dev
741	libtotem0
743	gdisk
744	ibus-table
746	libopenexr6
746	libpcre3-dev
747	printer-driver-gutenprint
752	checkbox-gui
756	libkactivities-bin
757	libcogl15
761	libmpfr4
763	libgee-0.8-2
763	python-gnome2
764	lshw
772	libgcr-base-3-1
776	ntfs-config
778	libtasn1-6-dev
782	krb5-multidev
784	liborcus-0.6-0
784	tar
785	libwps-0.2-2
785	qapt-batch
787	libreoffice-pdfimport
789	notify-osd
800	gstreamer0.10-tools
803	libasn1-8-heimdal
804	indicator-datetime
804	myspell-en-gb
805	libxcb1-dev
808	libtext-unidecode-perl
816	findutils
816	libgnomeui-0
825	libunity9
826	libreoffice-gtk
828	printer-driver-foo2zjs
832	cups
834	libspandsp2
838	libsqlite3-0
840	libpam-modules
842	xsane
844	libqt4-help
849	libedataserver-1.2-18
851	libpulse0
852	metacity
852	udisks2
859	libqpdf13
862	wodim
864	gnome-user-share
864	libglib-perl
866	libsoup2.4-1
868	gnome-sushi
872	indicator-session
872	transmission-common
878	libdbus-1-dev
878	libfreetype6
881	libschroedinger-1.0-0
883	libcholmod2.1.2
886	amule-utils
892	libxvidcore4
894	smbclient
895	libfreetype6
896	vcdimager
903	libqt4-scripttools
904	libexpat1-dev
905	libcdr-0.0-0
905	libevview3-3
906	openssl
908	baobab
909	manpages
910	printer-driver-pnm2ppa
911	gstreamer1.0-tools
912	python-gobject-2
914	kdelibs-bin
916	transmission-gtk
917	libkfile4
918	libltdl-dev
920	ppp
921	python-libxml2
923	dictionaries-common
929	bash-completion
929	libgail-common
931	vim-tiny
932	gir1.2-gtk-3.0
932	hud
936	x11proto-xext-dev
941	account-plugin-aim
941	account-plugin-jabber
941	account-plugin-salut
941	account-plugin-yahoo
948	gnome-contacts
950	cups-daemon
951	libglu1-mesa-dev
951	libopencv-contrib2.4
952	systemd-services
954	nautilus-sendto-empathy
957	gnome-tweak-tool
960	firefox-locale-en
961	libgdata13
963	rhythmbox
964	totem-plugins
973	dbus
978	libmono-system-drawing4.0-cil
986	libkrb5-3
989	libx264-123
990	wamerican
990	wbritish
991	libwpd-0.9-9
995	debhelper
1003	libtiff5-dev
1009	fonts-kacst
1011	libnet-ssleay-perl
1021	libgnomevfs2-0
1021	libqt5multimedia5
1029	mcp-account-manager-uoa
1032	kbd
1032	libattica0.4
1039	cups-client
1045	libtheora-dev
1049	libcaca0
1059	libbonobo2-0
1059	update-manager
1061	gir1.2-gstreamer-1.0
1064	metacity-common
1065	libtag1-vanilla
1066	brasero
1072	libgnutls26
1074	gnome-icon-theme
1076	libmtp-common
1083	libprotobuf8
1086	pciutils
1088	libcwidget3
1091	fonts-sil-abyssinica
1095	gstreamer1.0-plugins-ugly
1097	libopencv-legacy2.4
1098	libvte-2.90-9
1100	python-gst0.10
1101	tcpdump
1104	debconf-i18n
1108	speech-dispatcher
1112	gnome-bluetooth
1114	libgcrypt11-dev
1114	libnepomuk4
1115	libcups2-dev
1123	python-pil
1126	libexempi3
1127	grub2-common
1132	libkjsapi4
1136	dialog
1147	iproute2
1151	libunistring0
1153	libqca2
1153	libstdc++6
1156	gnome-system-log
1162	alacarte
1163	libasound2
1164	duplicity
1172	gnome-terminal-data
1172	libusb-1.0-doc
1172	systemsettings
1172	telepathy-salut
1174	indicator-applet
1176	login
1178	xdg-user-dirs
1180	libasound2
1181	apparmor
1184	libnepomukcore4abi1
1186	libspice-server1
1190	libjpeg-turbo8-dev
1192	evince
1192	libgsoap4
1197	notify-osd-icons
1201	libgfortran3
1205	libmagickwand5
1208	gnome-disk-utility
1211	libstdc++6
1215	libevdocument3-4
1219	baloo
1219	branding-ubuntu
1224	compiz-core
1224	ibus
1228	libqt4-opengl
1229	libkabc4
1241	x11proto-kb-dev
1245	libsolid4
1263	gstreamer0.10-plugins-ugly
1264	apport
1294	libraw9
1296	mono-runtime-common
1297	cdrdao
1304	gnome-mines
1307	libisl10
1311	libkde3support4
1332	python-xapian
1338	flacon
1340	libglib2.0-data
1360	sgml-data
1370	libkjsembed4
1373	libcairo2
1377	light-themes
1384	colord
1384	python-crypto
1385	libqmi-glib0
1386	rhythmbox-plugins
1389	python3-crypto
1394	libstreamanalyzer0
1395	system-config-printer-gnome
1407	gnome-panel
1408	ibus-pinyin
1415	hicolor-icon-theme
1418	evolution-data-server
1424	libreoffice-math
1425	libglib2.0-bin
1426	libtool
1428	language-pack-en
1438	ntfs-3g
1440	libgstreamer-plugins-base0.10-0
1443	compiz-gnome
1447	liblangtag-common
1456	libssl-doc
1466	libslang2
1475	cups-filters
1478	libcmis-0.4-4
1480	bash
1492	automake
1496	shotwell-common
1500	libsamplerate0
1502	libx11-6
1509	libx11-6
1513	libclutter-1.0-0
1520	libdpkg-perl
1528	sudo
1529	console-setup
1531	libavformat54
1534	samba-common-bin
1536	gvfs-backends
1537	libgnome-control-center1
1540	projectm-data
1541	rsyslog
1543	genisoimage
1556	gnome-system-monitor
1575	iptables
1581	libx11-data
1596	webbrowser-app
1601	tzdata
1602	libsoprano4
1603	libcamel-1.2-45
1612	libgstreamer-plugins-base1.0-0
1624	gnome-control-center-shared-data
1634	dpkg-dev
1634	util-linux
1639	libexif-dev
1643	nautilus
1649	libdjvulibre21
1650	libwxbase2.8-0
1652	cups-common
1656	libgtksourceview-3.0-common
1656	yasm
1659	xterm
1676	gnupg
1681	upstart
1684	zenity-common
1699	plasma-scriptengine-javascript
1712	libvpx1
1725	libdb5.3
1731	librhythmbox-core8
1739	gstreamer1.0-plugins-base
1746	libclucene-core1
1759	menu
1762	xserver-common
1764	python-twisted-web
1768	isc-dhcp-common
1768	libbrasero-media3-1
1768	mesa-common-dev
1775	x11proto-core-dev
1800	libxml2
1808	texi2html
1823	isc-dhcp-client
1834	manpages-dev
1851	libfontconfig1-dev
1857	fonts-sil-padauk
1859	liboxideqt-qmlplugin
1860	k3b
1863	yelp-xsl
1873	espeak-data
1888	file-roller
1890	autoconf
1904	bleachbit
1912	gparted
1916	libdns100
1926	telepathy-gabble
1932	totem-common
1955	libdirectfb-1.2-9
1956	qtdeclarative5-ubuntu-ui-toolkit-plugin
1960	libqt5network5
1976	nepomuk-core-runtime
1980	network-manager-gnome
1984	busybox-static
1984	libunity-core-6.0-9
2000	network-manager
2028	gnome-calculator
2032	burg-pc
2037	libqt4-network
2046	x11-apps
2056	kdoctools
2056	rhythmbox-data
2060	man-db
2071	libopencv-imgproc2.4
2087	update-notifier-common
2100	plainbox-provider-checkbox
2108	modemmanager
2114	libfftw3-double3
2117	libcaca-dev
2119	fonts-liberation
2120	yelp
2122	gstreamer0.10-plugins-base
2128	brasero-common
2145	docbook-xml
2154	ncurses-term
2156	alsa-utils
2166	libfftw3-single3
2171	libx264-142
2177	libslang2-dev
2185	vim
2185	wpasupplicant
2215	libglibmm-2.4-1c2a
2240	libtk8.6
2252	gnome-sudoku
2263	libaspell15
2272	uno-libs3
2293	language-selector-common
2301	libexiv2-12
2304	keyboard-configuration
2306	libopencv-core2.4
2312	seahorse
2319	libgegl-0.2-0
2323	libgnutls-dev
2325	python-reportlab
2330	libgtk2.0-cil
2337	passwd
2402	libxapian22
2408	meld
2440	e2fsprogs
2459	printer-driver-foo2zjs-common
2460	python3-lxml
2464	ttf-indic-fonts-core
2468	memtest86+
2470	libvirtodbc0
2482	python-lxml
2484	gufw
2490	libtelepathy-glib0
2497	libpython2.7-minimal
2503	libpoppler44
2539	bluez
2549	unity-tweak-tool
2568	libk3b6
2580	shared-mime-info
2592	libsdl1.2-dev
2604	libgstreamer0.10-0
2606	libx11-dev
2607	gedit
2635	libmono-system-xml4.0-cil
2656	unity-settings-daemon
2660	krb5-locales
2680	evince-common
2692	cups-server-common
2716	eog
2736	burg-common
2761	libmagic1
2765	xserver-xorg-video-intel
2772	libgstreamer1.0-0
2795	grub-pc-bin
2796	groff-base
2812	empathy
2817	libreoffice-base-core
2824	libqt4-script
2836	xkb-data
2875	libapt-pkg4.12
2888	libreoffice-l10n-en-gb
2898	fonts-dejavu-core
2906	libkatepartinterfaces4
2912	libgimp2.0
2913	libvorbisenc2
2927	libxm4
2929	libmono-corlib4.0-cil
2929	libssl1.0.0
2940	aisleriot
2944	software-center
2956	deja-dup
3001	dolphin
3002	libmono-corlib4.5-cil
3047	libakonadi-kde4
3070	libgtk2-perl
3088	onboard
3100	libsane-common
3102	ubuntu-sso-client-qt
3117	libreoffice-style-human
3151	etherape
3151	libnux-4.0-0
3153	ksh
3160	libsnmp30
3165	libkio5
3187	pdftk
3188	filezilla
3198	lintian
3231	libpython3.4-minimal
3238	syslinux-common
3328	gedit-common
3333	libkdecore5
3337	python-gtk2
3367	libgphoto2-6
3400	python2.7-minimal
3404	pulseaudio
3420	gconf-editor
3435	openssh-client
3436	gettext
3449	libc-bin
3460	libplasma3
3462	dmz-cursor-theme
3471	libmono-system4.0-cil
3493	libpython2.7
3506	chromium-codecs-ffmpeg-extra
3515	libfreetype6-dev
3532	cheese-common
3560	gnome-keyring
3566	oxideqt-codecs-extra
3576	apt
3596	libnss3
3669	xserver-xorg-core
3672	libgweather-common
3699	libtcl8.6
3704	linux-libc-dev
3732	libgpac2
3733	libgtksourceview2.0-common
3736	libqt4-qt3support
3784	ubuntu-wallpapers
3857	ubuntu-tweak
3872	libvorbis-dev
3881	geoip-database
3887	grub-customizer
3936	ttf-ubuntu-font-family
3957	netpbm
3959	openprinting-ppds
3972	gnome-mahjongg
3992	command-not-found-data
4039	libqt5quick5
4043	compiz-plugins-default
4076	language-pack-en-base
4088	xcursor-themes
4092	burg-emu
4099	python3.4-minimal
4112	unity-control-center
4133	ubuntu-mono
4180	aptitude-common
4198	libgs9-common
4220	virtualbox-dkms
4232	libqt4-declarative
4249	libtimezonemap1
4286	libpython3.4
4336	libgucharmap-2-90-7
4405	gstreamer1.0-plugins-bad
4407	amule
4420	libqt5qml5
4449	fonts-tibetan-machine
4481	libqt4-xmlpatterns
4548	qtcore4-l10n
4577	kdelibs5-plugins
4593	aptitude
4596	libglib2.0-0
4602	xsane-common
4656	libglib2.0-0
4691	gnome-accessibility-themes
4764	gsfonts
4796	libgtkmm-2.4-1c2a
4840	python3-plainbox
4858	perl-base
4868	empathy-common
4908	gstreamer1.0-plugins-good
4939	libpurple0
4975	libkdeui5
5012	amule-common
5032	gstreamer0.10-plugins-bad
5053	libqtcore4
5118	libqt5core5a
5124	libcrypto++9
5144	udev
5196	gstreamer0.10-plugins-good
5308	ure
5322	libreoffice-impress
5434	sphinx-voxforge-lm-en
5487	libgtkmm-3.0-1
5561	k3b-data
5744	snmp-mibs-downloader
5770	shotwell
5774	libgcc-4.8-dev
5798	liblapack3
5815	liblouis-data
5834	libmozjs-24-0
5918	libmagickcore5
5921	python-twisted-core
5932	gnome-orca
5996	unity
6024	coreutils
6136	libgtk2.0-0
6163	libssl-dev
6170	fonts-takao-pgothic
6197	gnome-shell-common
6217	example-content
6239	dpkg
6315	gdb
6425	python-samba
6546	libgtk-3-0
6671	libegl1-mesa-drivers
6822	libjavascriptcoregtk-1.0-0
6822	libjavascriptcoregtk-3.0-0
7019	language-pack-gnome-en-base
7072	libqt5widgets5
7084	brltty
7129	libqt5gui5
7147	libavcodec-extra-54
7492	kdelibs5-data
7591	fonts-droid
7676	synaptic
7843	libgutenprint2
8048	burg-themes-common
8161	libsnmp-dev
8175	ubuntu-wallpapers-trusty
8280	xfonts-base
8316	libkhtml5
8448	burg-themes
8486	libqt4-designer
8490	libpython2.7-stdlib
8609	kde-runtime
8836	libx11-doc
8852	libopencc1
8969	libgpac-dev
8970	libsane
9136	locales
9254	libc6
9342	libpython3.4-stdlib
9383	libreoffice-draw
9475	filezilla-common
9568	gnome-panel-data
9580	libglib2.0-dev
9631	libc6-i386
9849	kate-data
10009	libwxgtk2.8-0
10341	guile-2.0-libs
10496	libc6
10613	fonts-freefont-ttf
11150	libstdc++-4.8-dev
11193	gcj-4.8-jre-lib
11436	binutils
11484	grub-common
11837	libgphoto2-dev
11849	poppler-data
11946	libgs9
12084	libruby1.9.1
12139	libc6-dev
12445	kde-runtime-data
12713	libqtgui4
12957	linux-headers-3.13.0-24-generic
12969	linux-headers-3.13.0-27-generic
12973	linux-headers-3.13.0-29-generic
13239	my-weather-indicator
13792	virtuoso-opensource-6.1-bin
13845	python-qt4
14100	cpp-4.8
14454	docbook-xsl
14658	humanity-icon-theme
14700	gimp-data
15207	iso-codes
15249	libsane-dev
15290	gcc-4.8
15370	gimp
16133	perl-modules
16627	mono-runtime-sgen
17179	nmap
17317	perl
17764	g++-4.8
17887	samba-libs
18174	onboard-data
20694	virtualbox-qt
21181	mythes-en-us
21855	libreoffice-calc
22097	clementine
22300	libc6-dbg
24164	libflite1
24632	libreoffice-help-en-gb
24648	libreoffice-help-en-us
25141	fonts-nanum
25186	vim-runtime
26227	libllvm3.4
26354	libllvm3.4
27283	libicu52
28046	sphinx-voxforge-hmm-en
29161	gnome-user-guide
29234	nautilus-actions
30398	oxygen-icon-theme
32390	libgl1-mesa-dri
32571	libwebkitgtk-3.0-0
32576	libwebkitgtk-1.0-0
32757	libgl1-mesa-dri
32956	libpython2.7-dev
33224	freepats
34225	libqt5webkit5
34737	libqtwebkit4
36216	app-install-data
37570	libreoffice-writer
40636	linux-image-3.13.0-24-generic
40719	linux-image-3.13.0-27-generic
40732	linux-image-3.13.0-29-generic
51183	ubuntu-docs
53983	libgcj14
57210	virtualbox
58472	linux-firmware
60983	libpyzy-1.0-0
61736	linux-headers-3.13.0-24
61752	linux-headers-3.13.0-27
61760	linux-headers-3.13.0-29
64460	thunderbird
73647	liboxideqtcore0
74016	libreoffice-common
80000	teamviewer
80703	firefox
113632	libreoffice-core
147869	linux-image-extra-3.13.0-24-generic
147968	linux-image-extra-3.13.0-27-generic
147985	linux-image-extra-3.13.0-29-generic
182617	google-earth-stable
```
**root@dadubuntu:~# gksudo nautilus /root/.local/share/Trash/files # Be sure to enable viewing of hidden files.**
The output of this file is shown below.  If I select all the files and show their Properties they combine (size wise) to 2.3KB

---

### Post by steeldriver on 2014-06-18
If it is safe to do so i.e. **if you are not currently running any backups or recording/streaming to/from your mediastore partition **then please do

```

sudo umount /media/{backup,store}

sudo du -hd3 /media

```

Once it's done, you can remount the filesystems

```

sudo mount /media/backup
sudo mount /media/store

```

We may need to do the same for /home - but it's more complicated so let's not go there yet

---

### Post by Quarkrad on 2014-06-18
dad@dadubuntu:~$ sudo umount /media/{backup,store}
[sudo] password for dad: 
dad@dadubuntu:~$ sudo du -hd3 /media
4.0K	/media/dad
592K	/media/backup/dad/.gimp-2.8
16K	/media/backup/dad/.adobe
68K	/media/backup/dad/.winff
36K	/media/backup/dad/.pki
4.0K	/media/backup/dad/Public
660K	/media/backup/dad/.compiz
3.1G	/media/backup/dad/Documents
4.0K	/media/backup/dad/.gvfs
2.6G	/media/backup/dad/Desktop
4.0K	/media/backup/dad/winff out
8.0K	/media/backup/dad/.cups
3.2M	/media/backup/dad/.thumbnails
820K	/media/backup/dad/.gconf
4.0K	/media/backup/dad/Videos
207M	/media/backup/dad/.googleearth
540K	/media/backup/dad/.kde
58M	/media/backup/dad/.mozilla
7.5G	/media/backup/dad/.local
232M	/media/backup/dad/.VirtualBox
4.0K	/media/backup/dad/Templates
8.0K	/media/backup/dad/.sane
4.0K	/media/backup/dad/Map Overlays
4.0K	/media/backup/dad/Pictures
4.0K	/media/backup/dad/france ride
4.0K	/media/backup/dad/ffmpeg_sources
4.0K	/media/backup/dad/bin
20M	/media/backup/dad/.config
3.6G	/media/backup/dad/.aMule
4.0K	/media/backup/dad/Dropbox
12K	/media/backup/dad/.dbus
4.0K	/media/backup/dad/house
1.7G	/media/backup/dad/.thunderbird
668K	/media/backup/dad/.gstreamer-0.10
4.0K	/media/backup/dad/ffmpeg_build
8.0K	/media/backup/dad/.hplip
4.0K	/media/backup/dad/.gnome2_private
4.0K	/media/backup/dad/aptdaemon-8erw4q
4.0K	/media/backup/dad/Music
316K	/media/backup/dad/.arista
8.0M	/media/backup/dad/.teamviewer
28K	/media/backup/dad/.unison
36K	/media/backup/dad/.filezilla
102M	/media/backup/dad/Audio
16K	/media/backup/dad/.dropbox-master
721M	/media/backup/dad/.cache
16K	/media/backup/dad/.dvdcss
16K	/media/backup/dad/.gnome2
1.9M	/media/backup/dad/.dropbox
132K	/media/backup/dad/Downloads
32K	/media/backup/dad/.macromedia
8.0K	/media/backup/dad/.mplayer
4.0K	/media/backup/dad/lizgraham
21G	/media/backup/dad
4.0K	/media/backup/store/DVD
4.0K	/media/backup/store/Copy of drivers
4.0K	/media/backup/store/.Trash-1000
16K	/media/backup/store
21G	/media/backup
4.0K	/media/store
21G	/media
dad@dadubuntu:~$

---

### Post by Impavidus on 2014-06-18
> **steeldriver said:**
> So I think the most likely explanation is that you wrote a bunch of files to /media/backup, /media/store, or possibly /home either before you created separate partitions for them, or at some point when they weren't mounted for some reason. That space now counts as 'used' as far as the disk is concerned, but doesn't appear anywhere in your running filesystem because the subsequent mounts are hiding it.

You will need to unmount those partitions and have a look - for /media/backup and /media/store you can probably do that from the running system - if you need to dig underneath /home you will only be able to do that either from recovery mode or from a live CD/USB

+1

Unmount these file systems with```
sudo umount /media/backup
sudo umount /media/store
```and then check again what is in those directories. They ought to be empty, but in your case they might not. Move or delete everything you find in these directories before remounting /media/backup and /media/store.

To check for files hidden beneath your home directory, boot into recovery mode and drop to a root shell. Run```
ls  -A  /home
``` to see whether anything is present there. Your /home partition is not mounted when you boot into recovery mode. If there are files present in the /home directory, use these commands to move them somewhere else:```
mount  -o  rw,remount  /
mv  /home  /home2
mkdir  /home
```
Then reboot into normal mode:```
reboot
```You'll find the files that were hiding under your /home partition in /home2. See which of these files can be deleted and which you want to store somewhere else. Then delete the /home2 directory.

Google Earth does not depend on wine. Your /root directory contains a lot of files that shouldn't be there, like config files of applications that you never need to run as root, but it's still only 18MB so it's not causing your full drive.

Edit: Ah, ninja'ed.

Anyway, you had backups hiding under your backup partition. It seems you once ran your backup tool when the backup partition wasn't mounted. If these are old backups, you can delete then. If you want to keep them, move them away with```
sudo  mv  /media/backups  /media/backups2
sudo  mkdir  /media/backups
sudo  mount  /media/backups
sudo  mount  /media/store
```
and move the files from /media/backups2 to /media/backups, before deleting the /media/backups2 directory.

---

### Post by Quarkrad on 2014-06-18
Sorry to ask, as I am ignorant here, but I'm slightly worried when you say '......delete everything in these directories...'.  media/store is empty after running the umount command but media/backup isn't.  The 'panic' in me just want's to ask the question re deleting - apologies.

---

### Post by steeldriver on 2014-06-18
Well it's really up to you to make sure there's nothing in there that you need to keep - you could start by looking at the DATES on the files to verify that it is old stuff (i.e. pre-dates when you created the separate backup partition)

---

### Post by Impavidus on 2014-06-18
I wrote "move or delete".

The /media/store directory was empty after unmounting, which is good. The /media/backups directory was not. It contains a backup that was filling your hard drive and that had been hidden behind another backup as long as the backup partition was mounted. I can't see which of the two backups is the more recent, but you'll know. It may be best to move the previously hidden backup away as indicated in my edit of my previous post. Then check which backups you want to keep and move those to the backup partition.

---

### Post by Quarkrad on 2014-06-18
Forgive my ignorance - I think I have lost my understanding.  My **sda7, media/store** contains all my historic valuable personal data which is on HD1 and **sdb1 media/backup** on HD2, is my backup of sda7.  (sdb1 also contains a backup of sda6 - my **/home** partition).  Are you actually saying it's up me whether I delete all my personal data and the backup of that data?

---

### Post by Quarkrad on 2014-06-18
This will take me some time as I will have to move **media/backup** to another HD.  I will copy it to my other old HDs (I'll have to do both as one was failing) and then reformat the **media/backup** HD2.  I'll make another backup of **/home** and **media/store** to the newly re-formatted HD2 and get back.  Be interesting, for me, to see how re-formating/configuring HD2 is going to reduce the **/** partition on HD1.  Would you confirm this is the right thing to do as there is a good few hours work here please.

---

### Post by steeldriver on 2014-06-18
[COLOR=#ff0000]**WE ARE NOT ASKING YOU TO DO ANYTHING TO HD2 (sdb)**[/COLOR] we are suggesting you remove [COLOR=#ff0000]**stale**[/COLOR] content from /media/backup on your / (sda5) partition which is eating up your space on that partition. You can then remount the [COLOR=#ff0000]**unmodified**[/COLOR] sdb1 on the (now empty, as a mount point should be) /media/backup.

If this is not clear then [COLOR=#ff0000]**STOP NOW** [/COLOR]and we can break down the steps more clearly

---

### Post by Quarkrad on 2014-06-18
Sorry for the 'glitch'.  I've umounted and there were some folders in **media/backup** that I deleted.  I rebooted into Recovery Mode and carried out the commands - there were some findings:  Trash-0, admin, dad, lost&found.  I carried on with the commands and at the point of moving **/home** I got:  **mv:cannot move '/home' to '/home2' : Device or resource busy**.

---

### Post by steeldriver on 2014-06-18
What commands? I explicitly said NOT to do anything with /home yet - and in fact since you already found 21G of 'stuff' hiding under /media/backup - which accounts for all of the missing disk space - there is no need to do so. **You just need to unmount sdb1 from /media/backup, move or delete the 'stuff' that appears under the mount point (AFTER verifying that it's old / unneeded) and then remount sdb1 as /media/backup**.

---

### Post by Quarkrad on 2014-06-18
I sorry - I'm loosing confidence in myself at the moment.  I followed the instructions in post #29 following my hesitation and got the results in #36.  I have since carried out your words in bold above and rebooted.  My / partition is still the same, 29.76GB total and 26.69GB used.

---

### Post by steeldriver on 2014-06-18
How exactly did you move/delete the files from the exposed /media/backup after unmounting 'it' (command line? gksu nautilus? ... ) - it seems like they didn't really go

---

### Post by Quarkrad on 2014-06-18
I used gksudo nautilus.  I have just run **sudo umount /media/backup** - **sudo umount /media/store** again and via nautilus those folders are empty.

---

### Post by steeldriver on 2014-06-18
Yes but maybe you just moved them to **root's Trash** folder?

---

### Post by Quarkrad on 2014-06-18
There were two folders in root's Trash, backup and dad.  I deleted these and also ran **Bleachbit as Root**.  This cleared a lot of files and now my **/** partition is only 7GB!  Thank you very much for your patience and support - invaluable help.

---

### Post by steeldriver on 2014-06-18
Whew! glad we got it figured out - thanks for marking the thread as [SOLVED]

---

