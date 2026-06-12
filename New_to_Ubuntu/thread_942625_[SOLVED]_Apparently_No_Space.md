---
title: "[SOLVED] Apparently No Space"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by expatCM on 2008-10-09
I just ran out of space on my main drive which was a bit of a surprise.  Moved some files out of /home to another drive to free up a bit of space .......  but I cannot understand where the space has gone ....  I get conflicting information .....

If I open Disk Usage Analyzer it tells me that the 

size is 141.8GB
used = 134.2GB
free = 7.6GB 

But the detailed analysis which is listed by size shows 

Total 16.3GB
/var  8.5GB
/ home 2.6GB
and then a number of directories using MB.

So these two items do not tie up.  If the total size is 141.8GB and only 16.3GB is used then where is the 125.5GB or what is using it?

I then opened Partition Editor and took a look at the partition.  Again I am confused.  Here I learn that the partition is 117.19GB with 113.4GB used and 3.79GB free.

Looking for something else to use I opened Gnome-Commander and that tells me that there is only 221.8MB free.

So I really am wondering what to believed and what I can trust ....  and then where has all the space gone ....


Any ideas?

---

### Post by halitech on 2008-10-09
can you open a terminal and post the output of
```
sudo df -h
```this should help us determine where the space has gone

---

### Post by Nxion on 2008-10-09
> **expatCM said:**
> I just ran out of space on my main drive which was a bit of a surprise.  Moved some files out of /home to another drive to free up a bit of space .......  but I cannot understand where the space has gone ....  I get conflicting information .....

If I open Disk Usage Analyzer it tells me that the 

size is 141.8GB
used = 134.2GB
free = 7.6GB 

But the detailed analysis which is listed by size shows 

Total 16.3GB
/var  8.5GB
/ home 2.6GB
and then a number of directories using MB.

So these two items do not tie up.  If the total size is 141.8GB and only 16.3GB is used then where is the 125.5GB or what is using it?

I then opened Partition Editor and took a look at the partition.  Again I am confused.  Here I learn that the partition is 117.19GB with 113.4GB used and 3.79GB free.

Looking for something else to use I opened Gnome-Commander and that tells me that there is only 221.8MB free.

So I really am wondering what to believed and what I can trust ....  and then where has all the space gone ....


Any ideas?

Try this and please post the output.

```
df -h
```

---

### Post by jerome1232 on 2008-10-09
Gparted might be displaying some free space because ext3 reserves 5% of the disk space, so that if the disk fills up you are still able to boot and it also is supposed to help with file fragmentation on a full disk.

Disk Usuage Analyzer could be off sometimes because it includes the whole filesystem (including /media ). I like DUA for the pie chart of what using what it shows on the right, I ignore the totals it displays ( :) )

A couple commands that should help.
```
df -h
sudo du -hx --max-depth=1 /
```

the -h makes du human readable, -x makes it ignore other files systems (so this will only measure the filesystem that your / is on)

---

### Post by Nxion on 2008-10-09
Also try this,

```
du -h ~ | grep GB
```

This will list the space that all the gigabyte size files are taking up. you can sub "GB" for "MB" to list the megabyte usage for files as well.

---

### Post by Nxion on 2008-10-09
> **jerome1232 said:**
> 
A couple commands that should help.
```
df -h
sudo du -hx --max-depth=1 /
```the -h makes du human readable, -x makes it ignore other files systems (so this will only measure the filesystem that your / is on)

Much more efficient then mine :). I will have to keep that one in mind.

---

### Post by drs305 on 2008-10-09
If it might be undeleted trash lurking around your system, check this link out:

[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by expatCM on 2008-10-09
wow ... that was fast ....

df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              71G   68G  209M 100% /
varrun               1014M  128K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   76K 1014M   1% /dev
devshm               1014M  128K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1             185G   46G  130G  27% /media/sdb
/dev/sdb1             185G   58G  118G  33% /media/sdc
/dev/sdc3             341G  1.7G  323G   1% /media/sde

```
I unmounted all the drives / partitions originally.  sdc1 is the partition with the os and /home.


sudo du -h ~ | grep GB

```
du: cannot access `/home/user/.gvfs': Permission denied
20K	/home/user/.songbird2/wa4blb78.default/extensions/shoutcast-radio@songbirdnest.com/chrome/locale/en-GB

```

sudo du -hx --max-depth=1 /

```
16K	/lost+found
20K	/media
305M	/opt
140K	/tmp
4.0K	/srv
51G	/root
107M	/boot
4.0K	/initrd
7.1M	/sbin
du: cannot access `/home/user/.gvfs': Permission denied
2.6G	/home
717M	/lib
8.6G	/var
5.5M	/bin
8.0K	/mnt
15M	/etc
4.1G	/usr
0	/dev
0	/sys
0	/proc
67G	/

```

---

### Post by Nxion on 2008-10-09
> [/code]sudo du -hx --max-depth=1 /

```
16K    /lost+found
20K    /media
305M    /opt
140K    /tmp
4.0K    /srv
51G    /root
107M    /boot
4.0K    /initrd
7.1M    /sbin
du: cannot access `/home/user/.gvfs': Permission denied
2.6G    /home
717M    /lib
8.6G    /var
5.5M    /bin
8.0K    /mnt
15M    /etc
4.1G    /usr
0    /dev
0    /sys
0    /proc
67G    /

```

Well there you go. There is something in the root directory that is taking up 67GB of your space. as well as 56GB in the /root. Have you emptied the trash like drs305 suggested?

---

### Post by jerome1232 on 2008-10-09
> **expatCM said:**
> wow ... that was fast ....

df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              71G   68G  209M 100% /
varrun               1014M  128K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   76K 1014M   1% /dev
devshm               1014M  128K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1             185G   46G  130G  27% /media/sdb
/dev/sdb1             185G   58G  118G  33% /media/sdc
/dev/sdc3             341G  1.7G  323G   1% /media/sde

```
According to that you have 209MB free


sudo du -h ~ | grep GB

```
du: cannot access `/home/user/.gvfs': Permission denied
20K	/home/user/.songbird2/wa4blb78.default/extensions/shoutcast-radio@songbirdnest.com/chrome/locale/en-GB

```

sudo du -hx --max-depth=1 /

```
16K	/lost+found
20K	/media
305M	/opt
140K	/tmp
4.0K	/srv
[COLOR="Red"]51G	/root[/COLOR]
107M	/boot
4.0K	/initrd
7.1M	/sbin
du: cannot access `/home/user/.gvfs': Permission denied
2.6G	/home
717M	/lib
[COLOR="Red"]8.6G	/var[/COLOR]
5.5M	/bin
8.0K	/mnt
15M	/etc
4.1G	/usr
0	/dev
0	/sys
0	/proc
67G	/

```

8.6GB !!!!!! /var
51GB !!!!  /root

I think you deleted alot of crap in a root nautilus session and it went to root trash, which is sometimes located under /root/.local/share/Trash

/var is pretty big too, did you run the simple backup utility? Might want to get rid of some old logs

/ is just a total of everything and can be ignored

---

### Post by ahsile on 2008-10-09
Should note that even though the disk usage analyzer sees free space, this is (mostly) on three other partitions... sda1, and sdb1, and sdc3. It is your root partition which is full (sdc1).

---

### Post by expatCM on 2008-10-10
I am pleased that I asked this question .... and that there is great help available .....   I did not realize that the root trash was hidden away at /root/.local/share/Trash
I had sort of assumed that it was automatically deleted directly like on the server.  So the situation now is much improved.....  I cannot actually see how it would be better but I have run the commands and put the output below just in case I am mistaken. 

Yes, /var is 8.6GB ...  8.0 is /var/lib/vmware.  Since I do not use it or XP that is installed perhaps it can go .... 

I have run 
sudo find / -type d -iname *Trash* | grep Trash
and investigated all the instances on the partition but they are now all empty.


 sudo du -h ~ | grep GB

 

```
du: cannot access `/home/user/.gvfs': Permission denied

20K	/home/user/.songbird2/wa4blb78.default/extensions/shoutcast-radio@songbirdnest.com/chrome/locale/en-GB


```

sudo du -hx --max-depth=1 /
```

16K	/lost+found

20K	/media

305M	/opt

300K	/tmp

4.0K	/srv

10M	/root

107M	/boot

4.0K	/initrd

7.1M	/sbin

du: cannot access `/home/user/.gvfs': Permission denied

2.6G	/home

717M	/lib

8.6G	/var

5.5M	/bin

8.0K	/mnt

15M	/etc

4.1G	/usr

0	/dev

0	/sys

0	/proc

17G	/


```

 df -h
```

Filesystem            Size  Used Avail Use% Mounted on

/dev/sdc1              71G   17G   51G  25% /

varrun               1014M  132K 1014M   1% /var/run

varlock              1014M     0 1014M   0% /var/lock

udev                 1014M   76K 1014M   1% /dev

devshm               1014M     0 1014M   0% /dev/shm

lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile

/dev/sda1             185G   46G  130G  27% /media/sdb

/dev/sdb1             185G   58G  118G  33% /media/sdc

/dev/sdc3             341G  1.7G  323G   1% /media/sde

gvfs-fuse-daemon       71G   17G   51G  25% /home/peter/.gvfs


```

Is this gvfs a duplicate 71GB since it is the same size as sdc1 or just a duplicate entry saying it is there?

---

### Post by drs305 on 2008-10-10
> **expatCM said:**
> 
Is this gvfs a duplicate 71GB since it is the same size as sdc1 or just a duplicate entry saying it is there?

Yes it is. It is hardy's virtual file system (but not to be confused with Gnome's Virtual File System, it's predecessor) - it registers as disk usage but doesn't physically exist. If you use baobab/Disk Usage Analyzer you can go to Edit, Preferences and deselect the GVFS reporting to exclude gvfs information.

---

