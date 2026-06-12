---
title: "the package system is broken"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by xap1234 on 2013-12-22
it tell me this...

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

when i try apt-get install -f
I get 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Any help?

---

### Post by Frogs Hair on 2013-12-22
Make sure other package management applications are closed and add sudo to the command . ```
sudo apt-get -f install
``` If that fails post the output of the following. ```
 sudo apt-get update 
```

---

### Post by xap1234 on 2013-12-23
when I type sudo apt-get -f install i get this message

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunity6 linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic
  linux-headers-3.2.0-24-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-57-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-57-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 77 not upgraded.
2 not fully installed or removed.
Need to get 0 B/974 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 1195034 files and directories currently installed.)
Unpacking linux-headers-3.2.0-57-generic-pae (from .../linux-headers-3.2.0-57-generic-pae_3.2.0-57.87_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-57-generic-pae_3.2.0-57.87_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-57-generic-pae/include/config/comedi/ni/common.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-57-generic-pae/include/config/comedi/ni/common.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-57-generic-pae_3.2.0-57.87_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xap@xap-ubuntu-laptop:~$ 

when i type in
 sudo apt-get update i get this message

Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [430 kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,039 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [101 kB]   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,468 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [741 kB] 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.5 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [230 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.4 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [325 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [132 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Fetched 2,061 kB in 10s (206 kB/s)                                             
W: Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
xap@xap-ubuntu-laptop:~$ 
```

---

### Post by Frogs Hair on 2013-12-23
I am seeing no packages for a kernel ppa in the sources list . Try disabling the source from Software & Updates or Software Sources > Other Software.   

Page shows no activity.  [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

---

### Post by buzzingrobot on 2013-12-23
Right. Delete the kernel-ppa files from /etc/apt/sources.list.d. Then try to update again. It may not fix your probem, but those 404 messages in update's output mean that PPA's server is offline. I

---

### Post by ian-weisser on 2013-12-24
> **xap1234 said:**
> ```

Unpacking linux-headers-3.2.0-57-generic-pae (from .../linux-headers-3.2.0-57-generic-pae_3.2.0-57.87_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-57-generic-pae_3.2.0-57.87_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-57-generic-pae/include/config/comedi/ni/common.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-57-generic-pae/include/config/comedi/ni/common.h'): [COLOR=#ff0000]No space left on device[/COLOR]

```

The error message is way off to the right. Scroll to see it: *No space left on device*
Is the partition containing /usr full?

---

### Post by xap1234 on 2013-12-24
Hmmm now i am getting this message
Software index is broken.
it is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by Frogs Hair on 2013-12-24
See Ian's post and check your free disk space . ```
df -h 
```

---

### Post by xap1234 on 2013-12-26
when i type df -h i get

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        19G   17G  1.1G  94% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           788M  896K  787M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  484K  2.0G   1% /run/shm
/dev/sda1       4.6G  1.3G  3.1G  29% /boot
/dev/sda7       184G   13G  162G   8% /home
/dev/sda8        92G   66G   22G  76% /home/xap/Desktop/torrents
/dev/sda9        92G   50G   38G  57% /home/xap/Desktop/100storage
/dev/sda10       65G   51G   11G  84% /home/xap/Desktop/70storage

And please remember i am a complete newbie to linux when you post something i should do please tell me how to do it also...

---

### Post by Bashing-om on 2013-12-26
xap1234; Hi !


Looks to be a problem within the '/' directory.
To looksee:
Terminal codes:
```

df -i
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by xap1234 on 2013-12-26
okay so when i typed that in i got

du: cannot access `home/xap/.gvfs': Permission denied

what now?

---

### Post by Bashing-om on 2013-12-26
xap1234; Don't know (??)

Did you change directory " cd /" ?
Presently then, I can not imagine where " home/xap" would come into play. "xap" your user name ?
Keep in mind your '/' and '/home' and '/boot' are in separate partitions. We are looking at the "Disk Usage" at the partition/directory level. And it is "/" - sda6 - (root directory) that has space constraints.
We also need to assertion the "inode" situation. That the alotment of inodes has not been reached.
```

df -i

```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by xap1234 on 2013-12-30
when i type df -i i get
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda6       1220608 1219299     1309  100% /
udev             206332     530   205802    1% /dev
tmpfs            209988     471   209517    1% /run
none             209988       3   209985    1% /run/lock
none             209988       9   209979    1% /run/shm
/dev/sda1        305216     498   304718    1% /boot
/dev/sda7      12214272   40731 12173541    1% /home
/dev/sda8       6111232     450  6110782    1% /home/xap/Desktop/torrents
/dev/sda9       6111232     338  6110894    1% /home/xap/Desktop/100storage
/dev/sda10      4284416     440  4283976    1% /home/xap/Desktop/70storage

when i type cd / i get nothing

when i type 
sudo du -sx * | sort -n i get 

du: cannot access `home/xap/.gvfs': Permission denied

---

### Post by xap1234 on 2013-12-30
how do i do that?

---

### Post by Bashing-om on 2013-12-30
These:
> 
when i type df -h i get

Filesystem Size Used Avail Use% Mounted on
/dev/sda6 19G 17G 1.1G 94% /

XXXX

when i type df -i i get
Filesystem Inodes IUsed IFree IUse% Mounted on
/dev/sda6 1220608 1219299 1309 100% /
 say that you have serious space constraints on the root partiton (sda6) .
So we want to look at '/' (root)
So change the Present working firectory of the terminal to that of '/' .. by:
```

cd /

```-notice that your prompt changes to reflect this -
Now we are looking to see what those big files may be:
```

sudo du -sx * | sort -n

``` with "sudo" elevating the privileges to admin level, enter your pass word to do so !
This command will take bit to complete, looking at all the files on the system.

Now you advise getting "du: cannot access `home/xap/.gvfs': Permission denied" which tells me you have not changed the directory, and are still in your home directory, located in partition sda7.

Else you may have greater problems than I can imagine !

Using the code tags renders your out puts readable and manageable .
//
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]getting to the bottom of this
[/INDENT][/INDENT]

---

### Post by xap1234 on 2014-01-03
when i type df-i  i get 

Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda6       1220608 1219298     1310  100% /
udev             206332     530   205802    1% /dev
tmpfs            209988     471   209517    1% /run
none             209988       3   209985    1% /run/lock
none             209988       7   209981    1% /run/shm
/dev/sda1        305216     498   304718    1% /boot
/dev/sda7      12214272   40618 12173654    1% /home
/dev/sda8       6111232     473  6110759    1% /home/xap/Desktop/torrents
/dev/sda10      4284416     440  4283976    1% /home/xap/Desktop/70storage
/dev/sda9       6111232     338  6110894    1% /home/xap/Desktop/100storage

when i type cd / nothing happens

when i type 
sudo du -sx * | sort -n  i get 

du: cannot access `home/xap/.gvfs': Permission denied

Any help on what to do next?

---

### Post by xap1234 on 2014-01-03
ahh i made a mistake when i type sudo du -sx * | sort -n
i get this

du: cannot access `home/xap/.gvfs': Permission denied
du: cannot access `proc/2537/task/2537/fd/4': No such file or directory
du: cannot access `proc/2537/task/2537/fdinfo/4': No such file or directory
du: cannot access `proc/2537/fd/4': No such file or directory
du: cannot access `proc/2537/fdinfo/4': No such file or directory
0    initrd.img
0    initrd.img.old
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
4    cdrom
4    dev
4    media
4    mnt
4    selinux
4    srv
16    lost+found
84    tmp
896    run
8532    bin
8824    sbin
15800    etc
29516    opt
42608    root
1181256    boot
4578016    var
6084588    usr
6181316    lib
12820128    home

---

### Post by ian-weisser on 2014-01-03
Your /boot, /var, and /lib seem *enormous* compared to mine.
75276 (74MB) boot - yours seems to be over 10x the size.
708664 (693MB) var - yours seems over 5x bigger.  
359072 (351MB) lib - your seems about 17x bigger.

---

### Post by Bashing-om on 2014-01-03
xap1234;

Ditto ^ ;
Mine:
59660   boot
337240  var
423212  lib
1123512 home

We must either trim the fat from these directories, OR (re-)install with larger partitions and extended inode alotments.

If you decide to trim out the fat:
With 94% usage, may have no head room at all for apt to operate in but let's try and see what happens:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean

```

Removing no-longer-needed files and getting some inodes back.
Else; going to have to manually delete lots of files to get the overhead room for the package manager to operate in.

[INDENT][INDENT]don't recon surgery is required at this point.[/INDENT][/INDENT]

---

### Post by king.of.random on 2014-01-03
You definitely don't have enough overhead space in /... and I believe this is your problem. It makes me wonder though, as pointed out earlier, what you have in / to take up 94% of available space? I think the easiest thing to do would be to reinstall, remembering you need to format root but can leave /home as is. Mind as a learning exercise finding out what is hogging / would be good experience.

---

### Post by deadflowr on 2014-01-04
I see no reason to scoot the pooch on this and reinstall, yet.
Run the clean commands Bashing-om posted
(the apt-get clean, autoremove, and autoclean commands)

Then run this 
```
dpkg -l | grep linux-image && dpkg -l | grep linux-headers
```
to see if you have any lingering kernels and all the extra header goodness.
I would suspect you do, given how fat your /lib directory is.
And your /boot is as well.
Post the out.

Hopefully, it'll be rather empty after running the autoremove command, but you never know...

---

