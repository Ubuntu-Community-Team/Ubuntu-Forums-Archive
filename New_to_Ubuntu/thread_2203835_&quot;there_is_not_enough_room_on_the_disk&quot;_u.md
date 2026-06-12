---
title: "&quot;there is not enough room on the disk&quot; ubuntu 12.04"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by abexman on 2014-02-05
It looks like my root is full? What's the best way to clear this out? I always get confused what folders are actually "in" my root that I need to clear out? Was trying to install Tweak to help but cannot because of the error.

[IMG]http://s5.postimg.org/c1a1hefnr/free_space.jpg[/IMG]

---

### Post by Bashing-om on 2014-02-05
abexman; Hi !

Let's check and verify that it is indeed "root" that is full.
Post the output - between code tags - of terminal commands:
```

df -h
df -i
cd /
sudo du -sx * | sort -n
cd

```
Once known, we can direct you to an appropriate method to remove files.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by abexman on 2014-02-05
How's this?

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc6              14G   14G     0 100% /
udev                  2.0G  4.0K  2.0G   1% /dev
tmpfs                 806M  964K  805M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G  428K  2.0G   1% /run/shm
/dev/sda5             1.9T  875G  989G  47% /media/sda5
/dev/sdb1             699G  508G  192G  73% /media/sdb1
/dev/sdk1             233G  229G  4.7G  99% /media/sde1
/dev/sdc2              75G   49G   26G  66% /media/sdc2
/dev/sdc5             772G  116G  656G  15% /media/sdc5
/dev/sdc3             461M  126M  312M  29% /boot
/dev/sdc7              63G   27G   34G  44% /home
/home/cabal/.Private   63G   27G   34G  44% /home/cabal
javafs                107G   29G   79G  27% /home/cabal/WualaDrive
```

```
df -i
Filesystem               Inodes      IUsed      IFree IUse% Mounted on
/dev/sdc6                915712     451016     464696   50% /
udev                     205731        664     205067    1% /dev
tmpfs                    210954        623     210331    1% /run
none                     210954          5     210949    1% /run/lock
none                     210954         11     210943    1% /run/shm
/dev/sda5            1037089804       1219 1037088585    1% /media/sda5
/dev/sdb1             200757744     194657  200563087    1% /media/sdb1
/dev/sdk1               5393344      31720    5361624    1% /media/sde1
/dev/sdc2              27487776     159696   27328080    1% /media/sdc2
/dev/sdc5             687601040      28177  687572863    1% /media/sdc5
/dev/sdc3                121920        280     121640    1% /boot
/dev/sdc7               4177920      77533    4100387    2% /home
/home/cabal/.Private    4177920      77533    4100387    2% /home/cabal
javafs                      100 -999999900 1000000000     - /home/cabal/WualaDrive


```

Not sure if this one worked?

```
sudo du -sx * | sort -n
[sudo] password for cabal: 
du: cannot access `proc/24766/task/24766/fd/4': No such file or directory
du: cannot access `proc/24766/task/24766/fdinfo/4': No such file or directory
du: cannot access `proc/24766/fd/4': No such file or directory
du: cannot access `proc/24766/fdinfo/4': No such file or directory


```

---

### Post by Bashing-om on 2014-02-05
abexman; Yeah,

Making progress; We know for sure it is the '/' directory where we need to focus our attention.

Re-run the "du" command again, and give it plenty of time to search through all the file system. Takes a bit of time to complete !
```

cd /
sudo du -sx * | sort -n
cd

```
proc: you may disregard as it is a virtual file system and changing constantly, as "virtual" it has no relevance to the issue at hand.

Most likely it is /boot that will next hold our attention, but let's look to make sure.

[INDENT][INDENT]it is a process
[/INDENT][/INDENT]

---

### Post by jones quest on 2014-02-05
You can list installed packages by size with:
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n

---

### Post by abexman on 2014-02-05
```
du: cannot access `proc/24766/task/24766/fd/4': No such file or directory
du: cannot access `proc/24766/task/24766/fdinfo/4': No such file or directory
du: cannot access `proc/24766/fd/4': No such file or directory
du: cannot access `proc/24766/fdinfo/4': No such file or directory
0    initrd.img
0    initrd.img.old
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
4    cdrom
4    dev
4    mnt
4    selinux
4    srv
16    lost+found
964    run
2240    tmp
8784    bin
8868    sbin
17712    etc
50008    root
117854    boot
179328    media
550208    opt
571660    lib
5978804    var
6168740    usr
27121812    home


```

```

38055    ubuntu-docs
38874    libgcj12
41605    linux-firmware
41618    smbclient
45906    wine-mono0.0.8
47894    ffdiaporama
53804    openjdk-7-jre-headless
54064    scribus
54913    linux-headers-3.2.0-29
54917    linux-headers-3.2.0-30
54937    linux-headers-3.2.0-34
55018    linux-headers-3.2.0-58
60780    thunderbird
62641    firefox
62648    inkscape
77948    libobasis4.0-core05
80000    teamviewer7
80248    openjdk-6-jre-headless
87351    fonts-horai-umefont
106767    nvidia-304
110307    linux-image-3.2.0-29-generic-pae
110327    linux-image-3.2.0-30-generic-pae
110514    linux-image-3.2.0-34-generic-pae
110884    linux-image-3.2.0-58-generic-pae
115240    wine1.6-i386
124620    chromium-browser
130427    google-earth-stable
136224    libobasis4.0-core04
141596    plexmediaserver


```

---

### Post by Bashing-om on 2014-02-05
abexman; Yeah !

"/boot' is large. Let's get set to do some trimming in "/boot". We are going to remove those old unused kernels and headers.
So, let's see what we are working with:
```

uname -r ## so we know what kernel is booting - DO NOT remove this one !
dpkg -l | grep linux-image ## so we know what to remove
dpkg -l | grep linux-headers ## so we know what to remove

```

Once we know this we can "try" and remove them with the tools in the package management system. At 100% capacity, there is the probability of no operating room to work in.. But we will try the easier way first.

[INDENT][INDENT]easy does not always do it 
[/INDENT][/INDENT]

---

### Post by abexman on 2014-02-05
```
uname -r
3.2.0-58-generic-pae

```

```
 dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-29                            3.2.0-29.46                              Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic-pae                3.2.0-29.46                              Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-30                            3.2.0-30.48                              Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic-pae                3.2.0-30.48                              Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34                            3.2.0-34.53                              Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic-pae                3.2.0-34.53                              Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58                            3.2.0-58.88                              Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic-pae                3.2.0-58.88                              Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic-pae                         3.2.0.58.69                              Generic Linux kernel headers


```

```
dpkg -l | grep linux-image 
ii  linux-image-3.2.0-29-generic-pae                  3.2.0-29.46                              Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-30-generic-pae                  3.2.0-30.48                              Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic-pae                  3.2.0-34.53                              Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic-pae                  3.2.0-58.88                              Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                           3.2.0.58.69                              Generic Linux kernel image
cabal@cabal-OEM:~$ 


```

---

### Post by Bashing-om on 2014-02-05
abexman; Uhhmmm;

Not nearly as much as I had expected, as well I have no idea how the discontinuity between versions and kernels/headers could have happened.

But, let's do what we can.
```

sudo dpkg -P linux-image-3.2.0-{29,30}-generic-pae
sudo dpkg -P linux-headers-3.2.0-{29,30}-generic-pae

```
Then let's see what we may be missing by looking directly at  directory contents:
```

ls -la /boot
ls -la /usr/src

```

And , and -> take another look around .

[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT]

---

### Post by Impavidus on 2014-02-05
That /boot directory is quite large (twice as large as on my laptop), but better have a look at /var too. It's 6GB, 10 times the usual size. You may have accumulated a lot of cache or you may have an overflowing logfile.

---

### Post by SeijiSensei on 2014-02-05
On my newly-installed Kubuntu 14.04 desktop I have 3.5 GB in /usr and 945MB in /var.

Run the same "du -s *" method after entering "cd /var" so you can see the size of the directories beneath that.  If you have large MySQL or PostgreSQL databases, then /var/lib could be hefty.  My bet is /var/log is where the problem lies, though. As impavidus says, your machine might be logging a problem to /var/log/syslog or a similar file over and over again making the log file take up all the available space.

---

### Post by abexman on 2014-02-05
Thanks you guys! Very helpful.

I ran those commands, and then got the below. Does this help?

```
cabal@cabal-OEM:~$ ls -la /boot
total 56826
drwxr-xr-x  5 root root     3072 Feb  5 19:09 .
drwxr-xr-x 24 root root     4096 Jan 13 21:21 ..
-rw-r--r--  1 root root   801759 Nov 15  2012 abi-3.2.0-34-generic-pae
-rw-r--r--  1 root root   804938 Dec  3 14:02 abi-3.2.0-58-generic-pae
-rw-r--r--  1 root root   147452 Nov 15  2012 config-3.2.0-34-generic-pae
-rw-r--r--  1 root root   147576 Dec  3 14:02 config-3.2.0-58-generic-pae
drwxr-xr-x  3 root root     1024 Feb  5 19:09 extlinux
drwxr-xr-x  3 root root     7168 Feb  5 19:09 grub
-rw-r--r--  1 root root 20585753 Jan 13 21:24 initrd.img-3.2.0-34-generic-pae
-rw-r--r--  1 root root 20628843 Jan 13 21:28 initrd.img-3.2.0-58-generic-pae
drwx------  2 root root    12288 Sep  6  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2313866 Nov 15  2012 System.map-3.2.0-34-generic-pae
-rw-------  1 root root  2321986 Dec  3 14:02 System.map-3.2.0-58-generic-pae
-rw-------  1 root root  5017504 Nov 15  2012 vmlinuz-3.2.0-34-generic-pae
-rw-------  1 root root  5031904 Dec  3 14:02 vmlinuz-3.2.0-58-generic-pae
cabal@cabal-OEM:~$ ls -la /usr/src
total 40
drwxr-xr-x 10 root root 4096 Feb  5 19:10 .
drwxr-xr-x 11 root root 4096 Sep  6  2012 ..
drwxr-xr-x 24 root root 4096 Aug 17  2012 linux-headers-3.2.0-29
drwxr-xr-x 24 root root 4096 Sep  6  2012 linux-headers-3.2.0-30
drwxr-xr-x 24 root root 4096 Dec 11  2012 linux-headers-3.2.0-34
drwxr-xr-x  7 root root 4096 Dec 11  2012 linux-headers-3.2.0-34-generic-pae
drwxr-xr-x 24 root root 4096 Jan 13 21:13 linux-headers-3.2.0-58
drwxr-xr-x  7 root root 4096 Jan 13 21:13 linux-headers-3.2.0-58-generic-pae
drwxr-xr-x  3 root root 4096 Sep  6  2012 nvidia-173-173.14.35
drwxr-xr-x  3 root root 4096 Jan 13 21:13 nvidia-304-304.88
cabal@cabal-OEM:~$ ls -la /var
total 52
drwxr-xr-x 13 root root     4096 Jan 21 11:00 .
drwxr-xr-x 24 root root     4096 Jan 13 21:21 ..
drwxr-xr-x  2 root root     4096 Jan 17 07:00 backups
drwxr-xr-x 19 root root     4096 Jun 30  2013 cache
drwxrwsrwt  2 root whoopsie 4096 Jan 27 07:35 crash
drwxr-xr-x  2 root root     4096 Aug 17  2012 games
drwxr-xr-x 72 root root     4096 Sep 30 14:18 lib
drwxrwsr-x  2 root staff    4096 Apr 19  2012 local
lrwxrwxrwx  1 root root        9 Jan 21 11:00 lock -> /run/lock
drwxr-xr-x 15 root root     4096 Feb  5 07:36 log
drwxrwsr-x  2 root mail     4096 Aug 17  2012 mail
drwxr-xr-x  2 root root     4096 Aug 17  2012 opt
lrwxrwxrwx  1 root root        4 Jan 21 11:00 run -> /run
drwxr-xr-x  8 root root     4096 Jun 24  2013 spool
drwxrwxrwt  3 root root     4096 Feb  3 22:21 tmp


```

---

### Post by abexman on 2014-02-05
> **SeijiSensei said:**
> On my newly-installed Kubuntu 14.04 desktop I have 3.5 GB in /usr and 945MB in /var.

Run the same "du -s *" method after entering "cd /var" so you can see the size of the directories beneath that.  If you have large MySQL or PostgreSQL databases, then /var/lib could be hefty.  My bet is /var/log is where the problem lies, though. As impavidus says, your machine might be logging a problem to /var/log/syslog or a similar file over and over again making the log file take up all the available space.

```
cabal@cabal-OEM:~$ cd /var
cabal@cabal-OEM:/var$ sudo du -sx * | sort -n
[sudo] password for cabal: 

0    lock
0    run
4    crash
4    games
4    local
4    mail
4    opt
1316    spool
5708    backups
5932    log
12048    tmp
645152    cache
5292292    lib


```

---

### Post by Bashing-om on 2014-02-05
et al :

What in the world is "lib" so large for ? It is huge !

[INDENT][INDENT]sometimes I just do not know ![/INDENT][/INDENT]

---

### Post by SeijiSensei on 2014-02-06
Yes, let's see the results of 

```
cd /var/lib
sudo du -s * | sort -n

```

Generally the only really large objects that would be stored under /var/lib are MySQL and PostgreSQL databases.

---

### Post by abexman on 2014-02-06
Here's that command:

```
16    locales
16    NetworkManager
20    binfmts
24    sudo
24    update-notifier
28    pam
32    AccountsService
32    dictionaries-common
32    polkit-1
36    ghostscript
36    xml-core
52    belocs
52    xkb
116    ucf
124    samba
136    update-rc.d
180    lightdm
428    doc-base
456    usbutils
1376    ureadahead
1888    apt-xapian-index
3488    aspell
3536    gconf
25328    mlocate
29936    dropbox
85320    dpkg
98096    dkms
98692    apt
5182176    plexmediaserver


```

---

### Post by Vladlenin5000 on 2014-02-06
"plexmediaserver"... Hummm... Interesting.

---

### Post by SeijiSensei on 2014-02-07
I don't know what you have stored on all those other partitions in the original posting, but you might consider moving the plexmediaserver to another location with more space then creating a symbolic link to it in /var/lib like this:

```

cd /var/lib
sudo rsync -av plexmediaserver /path/to/new/location
sudo mv plexmediaserver plexmediaserver.old
sudo ln -s /path/to/new/location/plexmediaserver

```

After confirming that the data is intact, and that you can still access it as before, then you can delete the plexmediaserver.old directory.

---

### Post by abexman on 2014-02-11
For better or worse I tried deleting the whole var/lib/plexmedia directory, using sudo nautlius command, and removed the server from my computer. However it would not allow me to empty the trash? I closed that window and then tried to empty the trash from another nautlius command at the terminal. However I'm still showing
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc6              14G   14G     0 100% /

```

Also tried this, but no change. 
> 
[LIST]
[*]**To delete *your* Trash contents in your home folder:**
 	Code:
 	**[COLOR=DarkRed]rm -rf ~/.local/share/Trash/*[/COLOR]** 

[*]**To delete *root's* Trash contents in your home folder**:
Sometimes root trash ends up in your local Trash bin. You cannot delete  this without administrative powers. To accomplish the task, use "sudo"  to change ownership of the Trash folder contents to the user, then  delete the folder as above:
 	Code:
 	[COLOR=DarkRed][B]
sudo chown -R *username* ~/.local/share/Trash
rm -rf ~/.local/share/Trash/*[/B][/COLOR] 
[/LIST]


Am I missing something on how I'm supposed to empty the trash?

---

### Post by Impavidus on 2014-02-11
It could be in root's trash.```
sudo rm -rf /root/.local/share/Trash
```

---

