---
title: "Items cannot be installed or removed until the package catalog is repaired"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by Iltesham on 2013-03-16
Hi,
I cannot install or remove any thing from my laptop.
When ever i click Ubuntu Software center i get this message;
Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?

when i click the "Repair" button, nothing happens and the same screen comes up again.

I tried Sudo apt-get update
and 
Sudo apt-get -f install

but to no avail,
and this is what it gave me;
[ATTACH=CONFIG]240238[/ATTACH]

I am absolutely new to ubuntu and no nothing about the commands.
Can any body help please?
I will really appreciate it.
thanks,
Iltesham Z Syed

---

### Post by oldos2er on 2013-03-16
Can you post the output of ```
cat /etc/apt/sources.list
``` ? You can copy and paste the output into a post.

---

### Post by Iltesham on 2013-03-16
Thanks for the response,
here is what i get with the command you gave me;
iltesham@iltesham-Inspiron-1525:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
iltesham@iltesham-Inspiron-1525:~$ 


thanks for the help;
Iltesham Syed

---

### Post by oldos2er on 2013-03-16
That looks ok. Can you do the same for ```
ls /etc/apt/sources.list.d/
```

---

### Post by Iltesham on 2013-03-16
Hi,
thanks for the reply,
here is what i get with this command;

iltesham@iltesham-Inspiron-1525:~$ ls /etc/apt/sources.list.d/
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
oneiric-partner.list
oneiric-partner.list.distUpgrade
oneiric-partner.list.save
openfoam.list
openfoam.list.distUpgrade
openfoam.list.save
weather-indicator-team-ppa-oneiric.list
weather-indicator-team-ppa-oneiric.list.distUpgrade
iltesham@iltesham-Inspiron-1525:~$

---

### Post by oldos2er on 2013-03-16
Are you running Precise (12.04)? The problem is the oneiric-partner files, so let's get rid of those: ```
sudo rm /etc/apt/sources.list.d/oneiric*
```  Now try ```
sudo apt-get update
``` again, and the error should be gone.

---

### Post by Iltesham on 2013-03-16
Thanks again,
but this time i get this message;

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
iltesham@iltesham-Inspiron-1525:~$

---

### Post by Iltesham on 2013-03-16
Hi,
and when i click the software center i again get the same error and when i press the repair button, this time i get this message;

An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

---

### Post by oldos2er on 2013-03-16
That's odd. I wonder if updating the package lists will help. ```
[COLOR=#000000]sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```[/COLOR]

---

### Post by Iltesham on 2013-03-16
still the same error.

---

### Post by oldos2er on 2013-03-16
Try ```
sudo apt-get clean
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Iltesham on 2013-03-16
And i am getting this error message on the taskbar with in a Red circle which goes like this : An error occured. Please run package manager from the right click menu or apt-get in a terminal to see what is wrong. The Error message was, Error: BrokenCount >0'. This usually means that your installed packages have unmet dependencies.

Please help me out here.

thanks,
Iltesham Z Syed

---

### Post by Iltesham on 2013-03-16
sudo apt-get install -f gave this error

iltesham@iltesham-Inspiron-1525:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae
  linux-headers-generic linux-headers-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-38
The following packages will be upgraded:
  linux-headers-3.2.0-38-generic-pae linux-headers-generic
  linux-headers-generic-pae
3 upgraded, 1 newly installed, 0 to remove and 232 not upgraded.
4 not fully installed or removed.
Need to get 12.7 MB of archives.
After this operation, 67.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-38 all 3.2.0-38.61 [11.7 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-38-generic-pae i386 3.2.0-38.61 [981 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic i386 3.2.0.38.46 [2,590 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic-pae i386 3.2.0.38.46 [2,602 B]
Fetched 12.7 MB in 6s (2,061 kB/s)                                             
(Reading database ... 
dpkg: warning: files list file for package `linux-headers-3.2.0-38-generic-pae' missing, assuming package has no files currently installed.
(Reading database ... 464544 files and directories currently installed.)
Unpacking linux-headers-3.2.0-38 (from .../linux-headers-3.2.0-38_3.2.0-38.61_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.61_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-38/include/net/addrconf.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-38/include/net/addrconf.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace linux-headers-3.2.0-38-generic-pae 3.2.0-38.61 (using .../linux-headers-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-38-generic-pae ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-38-generic-pae/include/config/net/dsa/tag': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.61_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
This:
> **Iltesham said:**
> unable to create `/usr/src/linux-headers-3.2.0-38/include/net/addrconf.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-38/include/net/addrconf.h'): [COLOR=red]No space left on device[/COLOR]Please see [thread=1122670]this thread[/thread] on how to free up disk space.

---

### Post by Iltesham on 2013-03-16
hi,
I have atleast 70 GB free on this machine. DOnt know why it is showing no space left.

---

### Post by ibjsb4 on 2013-03-16
This is not a matter of disk space.  This is about /boot being full of old kernels.  There are several ways to remove old kernels.

Ubuntu Tweak is the simplest way.
[https://launchpad.net/~tualatrix/+archive/ppa?field.series_filter=precise](https://launchpad.net/~tualatrix/+archive/ppa?field.series_filter=precise)

My way is using Synaptic Package Manager
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9)

Other ways here
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

If you want to see whats going on in /boot, open a terminal and enter:

```
ls /boot
```

Got questions, just post back :)

---

### Post by schragge on 2013-03-16
@**ibjsb4**
Nope. It's *not* about /boot. The failed dpkg action tried to write to [COLOR=red]/usr/src[/COLOR]. It could be a similar issue only if /usr/src were on a separate partition.

@**Iltesham**
Please post the output of following commands:
```

df -hT
df -hi
mount

```

---

### Post by Iltesham on 2013-03-16
Cannot even install ubuntu tweak;
it gives me this error;
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [657 B]
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [660 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Fetched 1,784 kB in 6s (257 kB/s)                                              
Reading package lists... Done
iltesham@iltesham-Inspiron-1525:~$ sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-38-generic : Depends: linux-headers-3.2.0-38 but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-35-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-35-generic-pae but it is not going to be installed
 ubuntu-tweak : Depends: python-lxml but it is not going to be installed
                Depends: python-compizconfig but it is not going to be installed
                Depends: gir1.2-unique-3.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
iltesham@iltesham-Inspiron-1525:~$

---

### Post by ibjsb4 on 2013-03-16
/usr/scr and /boot go together :)  kernels and headers

---

### Post by Iltesham on 2013-03-16
> **schragge said:**
> @**ibjsb4**
Nope. It's *not* about /boot. The failed dpkg action tried to write to [COLOR=red]/usr/src[/COLOR]. It could be a similar issue only if /usr/src were on a separate partition.

@**Iltesham**
Please post the output of following commands:
```

df -hT
df -hi
mount

```

here is what i get with the above commands

iltesham@iltesham-Inspiron-1525:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda8      ext4      7.3G  5.8G  1.2G  84% /
udev           devtmpfs  995M  4.0K  995M   1% /dev
tmpfs          tmpfs     401M  924K  400M   1% /run
none           tmpfs    1003M  156K 1002M   1% /run/shm
/dev/sda6      ext4       64G  934M   60G   2% /media/50c17553-f47c-4928-a68e-277c6f946cb9
iltesham@iltesham-Inspiron-1525:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda8        472K  472K   138  100% /
udev             210K   622  210K    1% /dev
tmpfs            214K   556  213K    1% /run
none             214K     7  214K    1% /run/shm
/dev/sda6        4.1M   15K  4.1M    1% /media/50c17553-f47c-4928-a68e-277c6f946cb9
iltesham@iltesham-Inspiron-1525:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /media/50c17553-f47c-4928-a68e-277c6f946cb9 type ext4 (rw,nosuid,nodev,uhelper=udisks)
iltesham@iltesham-Inspiron-1525:~$

---

### Post by ibjsb4 on 2013-03-16
```
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [657 B]
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [660 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Fetched 1,784 kB in 6s (257 kB/s)                                              
Reading package lists... Done
iltesham@iltesham-Inspiron-1525:~$ sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-38-generic : Depends: linux-headers-3.2.0-38 but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-35-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-35-generic-pae but it is not going to be installed
 ubuntu-tweak : Depends: python-lxml but it is not going to be installed
                Depends: python-compizconfig but it is not going to be installed
                Depends: gir1.2-unique-3.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
iltesham@iltesham-Inspiron-1525
```

Oops, should of seen that one coming.  Give me a few minutes to find the proper terminal way.  BB

---

### Post by schragge on 2013-03-16
First, you have only 1.2G left on /, not 70G. The rest is on your data partition mounted under /media:
```

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda8      ext4      7.3G  5.8G 1.2G  84%  /

```But this should still be enough for an upgrade. The real problem however is this
```

Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda8      472K   [COLOR=red]472K[/COLOR]  138   [COLOR=red]100%[/COLOR]  /

```You have over 480000 files on your root filesystem. :shock: That means the disk space used doesn't matter, it's the *number of files* that your filesystem cannot deal with anymore, even if they were small or empty. Normally, you shouldn't run out of inodes. There's going something strange with your filesystem.

Try to free up some inodes by moving old log files to your data partition
```

mkdir /media/50c17553-f47c-4928-a68e-277c6f946cb9/log
sudo mv /var/log/*.{gz,1,log} /media/50c17553-f47c-4928-a68e-277c6f946cb9/log

```
Then clean APT archives
```

sudo apt-get clean

```

Finally, force the full filesystem check on the next reboot
```
sudo touch /forcefsck
``` and reboot.

The next step would be using your data partition on */media* as temporary store for */var/cache/apt/archives* as described [here]("http://www.debian.org/releases/testing/amd64/release-notes/ch-upgrading.en.html#sufficient-space"). But first, report back with what you will get after reboot.

---

### Post by ibjsb4 on 2013-03-16
Ok, found it :)

[URL="https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels"]https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels
[/URL]
EDIT: Just be sure not to delete the current running kernel (uname -r)

---

### Post by Iltesham on 2013-03-16
Thanks for the reply. But what is the solution to this problem?
Can you please guide me through it. I am a novice in ubuntu/linux.

---

### Post by ibjsb4 on 2013-03-16
Yes, I can see the confusion.  So let me step out of the picture and go with "schragge".  Ill be on the side for the moment :)

---

### Post by schragge on 2013-03-16
I've updated [post=12560501]my post[/post] with proposed actions. There's clearly going something very weird like some process writing tons of empty files or something like this.

---

### Post by Iltesham on 2013-03-16
> **ibjsb4 said:**
> Ok, found it :)

[URL="https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels"]https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels
[/URL]
EDIT: Just be sure not to delete the current running kernel (uname -r)

hi ,
even this is not working. Here is what i get

iltesham@iltesham-Inspiron-1525:~$ uname -r
3.2.0-35-generic
iltesham@iltesham-Inspiron-1525:~$ dpkg -l | grep linux-image-
rc  linux-image-3.0.0-12-generic           3.0.0-12.20                             Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-14-generic           3.0.0-14.23                             Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-15-generic           3.0.0-15.26                             Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic           3.0.0-16.29                             Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic           3.0.0-17.30                             Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-19-generic           3.0.0-19.33                             Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic           3.0.0-20.34                             Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.2.0-24-generic           3.2.0-24.39                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-25-generic           3.2.0-25.40                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-26-generic           3.2.0-26.41                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic           3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic           3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.35.40                             Generic Linux kernel image
iltesham@iltesham-Inspiron-1525:~$ sudo apt-get autoremove linux-image-3.2.0-32-generic
[sudo] password for iltesham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-38-generic : Depends: linux-headers-3.2.0-38 but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-35-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-35-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Please follow the steps I outlined in [post=12560501]that post[/post].

---

### Post by Iltesham on 2013-03-16
hi,
i cannot even create a dir
here is what i am getting;

iltesham@iltesham-Inspiron-1525:~$ sudo mkdir /media/50c17553-f47c-4928-a68e-277c6f946cb9/log
mkdir: cannot create directory `/media/50c17553-f47c-4928-a68e-277c6f946cb9/log': No such file or directory
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Wait, what does *ls /media* show? How do you mount your data partition? By clicking on its label in the file manager?

Anyway, let's do it the hard way:
```

sudo find /var/log -name \*.gz -o -name \*.old -o -name \*.1 -delete
sudo apt-get clean
sudo touch /forcefsck
reboot

```

---

### Post by Iltesham on 2013-03-16
hi,

iltesham@iltesham-Inspiron-1525:~$ ls/media
bash: ls/media: No such file or directory
iltesham@iltesham-Inspiron-1525:~$

and yes i click on its label

---

### Post by schragge on 2013-03-16
You've missed the space between ls and /media: ```
ls /media
```
Anyway, let's do it the hard way:
```

sudo find /var/log -name \*.gz -o -name \*.old -o -name \*.1 -delete
sudo apt-get clean
sudo touch /forcefsck
sudo reboot

```

---

### Post by Iltesham on 2013-03-16
Hi,
sudo /forcefsck not recognized;

iltesham@iltesham-Inspiron-1525:~$ ls/media
bash: ls/media: No such file or directory
iltesham@iltesham-Inspiron-1525:~$ sudo find /var/log -name \*.gz -o -name \*.old -o -name \*.1 -delete
[sudo] password for iltesham: 
iltesham@iltesham-Inspiron-1525:~$ sudo apt-get clean
iltesham@iltesham-Inspiron-1525:~$ sudo /forcefsck
sudo: /forcefsck: command not found

---

### Post by schragge on 2013-03-16
Sorry I've missed *touch*: ```
sudo touch /forcefsck
sudo reboot

```

---

### Post by Iltesham on 2013-03-16
hi,
I finally rebooted it, but still it gives me the same error of package catalog

---

### Post by schragge on 2013-03-16
Good. Please post the output of the *df *command once again:
```

df -hi

```

---

### Post by Iltesham on 2013-03-16
hi,
here is what it gives me;
iltesham@iltesham-Inspiron-1525:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda8        472K  472K   153  100% /
udev             210K   622  210K    1% /dev
tmpfs            214K   554  213K    1% /run
none             214K     3  214K    1% /run/lock
none             214K     6  214K    1% /run/shm
/dev/mmcblk0p1      0     0     0     - /media/438B-0831
/dev/sr1            0     0     0     - /media/magicJack
/dev/sdb            0     0     0     - /media/C8A2-A786
iltesham@iltesham-Inspiron-1525:~$

---

### Post by Iltesham on 2013-03-16
hi,
here is what it gives me;
iltesham@iltesham-Inspiron-1525:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda8        472K  472K   153  100% /
udev             210K   622  210K    1% /dev
tmpfs            214K   554  213K    1% /run
none             214K     3  214K    1% /run/lock
none             214K     6  214K    1% /run/shm
/dev/mmcblk0p1      0     0     0     - /media/438B-0831
/dev/sr1            0     0     0     - /media/magicJack
/dev/sdb            0     0     0     - /media/C8A2-A786
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Not much better. Have it checked the filesystem during reboot? There were only 138 free file inodes, now we have 153. Let's move APT cache to your data partition temporarily:
```

sudo -i
apt-get clean
rm /etc/apt/sources.list.d/*{save,distUpgrade,oneiric*}
rm /var/lib/apt/lists/*
mount /dev/sda6 /mnt
cp -ax /var/cache/apt/archives /mnt
mount --bind /mnt/archives /var/cache/apt/archives
apt-get update
apt-get --reinstall --no-upgrade install linux-headers-3.2.0-38
apt-get install -f
umount /mnt/archives
umount /mnt
exit

```

---

### Post by Iltesham on 2013-03-16
hi;
it is giving me this;
root@iltesham-Inspiron-1525:~# rm /etc/apt/sources.list.d/*{save,distUpgrade,oneiric*}
rm: cannot remove `/etc/apt/sources.list.d/*save': No such file or directory
rm: cannot remove `/etc/apt/sources.list.d/*distUpgrade': No such file or directory
rm: cannot remove `/etc/apt/sources.list.d/*oneiric*': No such file or directory
root@iltesham-Inspiron-1525:~#

---

### Post by schragge on 2013-03-16
Okey, no problem. Please proceed with further commands.

---

### Post by Iltesham on 2013-03-16
Now i get this,
Should i proceed with the next command?

root@iltesham-Inspiron-1525:~# rm /var/lib/apt/lists/*
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
root@iltesham-Inspiron-1525:~#

---

### Post by schragge on 2013-03-16
Yes, please.

---

### Post by Iltesham on 2013-03-16
Hi,
Now this is what i get;


root@iltesham-Inspiron-1525:~# apt-get --reinstall --no-upgrade install linux-headers-3.2.0-38
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.2.0-35-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-35-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@iltesham-Inspiron-1525:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae
  linux-headers-generic linux-headers-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-38
The following packages will be upgraded:
  linux-headers-3.2.0-38-generic-pae linux-headers-generic
  linux-headers-generic-pae
3 upgraded, 1 newly installed, 0 to remove and 232 not upgraded.
4 not fully installed or removed.
Need to get 12.7 MB of archives.
After this operation, 67.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-38 all 3.2.0-38.61 [11.7 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-38-generic-pae i386 3.2.0-38.61 [981 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic i386 3.2.0.38.46 [2,590 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic-pae i386 3.2.0.38.46 [2,602 B]
Fetched 12.7 MB in 6s (1,830 kB/s)                                             
(Reading database ... 
dpkg: warning: files list file for package `linux-headers-3.2.0-38-generic-pae' missing, assuming package has no files currently installed.
(Reading database ... 464544 files and directories currently installed.)
Unpacking linux-headers-3.2.0-38 (from .../linux-headers-3.2.0-38_3.2.0-38.61_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.61_all.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-38/net/nfc': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace linux-headers-3.2.0-38-generic-pae 3.2.0-38.61 (using .../linux-headers-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-38-generic-pae ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-38-generic-pae/include/config/net/sch/prio.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-38-generic-pae/include/config/net/sch/prio.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.61_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@iltesham-Inspiron-1525:~#

---

### Post by schragge on 2013-03-16
:( So, the inodes we've freed up by removing old logs and putting /var/cache/apt/archives onto /dev/sda6 were not enough for those linux-headers packages to be successfully installed. Let's try to free up some more by removing old kernels and configuration files:
```

dpkg --get-selections|sed -n 's/\<deinstall$/purge/p'|sudo dpkg --set-selections
sudo dpkg -P -a
sudo dpkg -P linux-image-3.2.0-{24,25,26,29,31,32,33}-generic
sudo apt-get install -f

```

---

### Post by Iltesham on 2013-03-16
now i get this;

iltesham@iltesham-Inspiron-1525:~$ dpkg --get-selections|sed -n 's/\<deinstall$/purge/p'|dpkg --set-selection
dpkg: error: unknown option --set-selection

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Sorry, I made a typo. I've edited my post above. Please try it again.

---

### Post by Iltesham on 2013-03-16
hi,
Now again i get these ;

iltesham@iltesham-Inspiron-1525:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae
  linux-headers-generic linux-headers-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-38
The following packages will be upgraded:
  linux-headers-3.2.0-38-generic-pae linux-headers-generic
  linux-headers-generic-pae
3 upgraded, 1 newly installed, 0 to remove and 232 not upgraded.
4 not fully installed or removed.
Need to get 0 B/12.7 MB of archives.
After this operation, 67.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 
dpkg: warning: files list file for package `linux-headers-3.2.0-38-generic-pae' missing, assuming package has no files currently installed.
(Reading database ... 433933 files and directories currently installed.)
Unpacking linux-headers-3.2.0-38 (from .../linux-headers-3.2.0-38_3.2.0-38.61_all.deb) ...
Preparing to replace linux-headers-3.2.0-38-generic-pae 3.2.0-38.61 (using .../linux-headers-3.2.0-38-generic-pae_3.2.0-38.61_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-38-generic-pae ...
Setting up linux-headers-3.2.0-38 (3.2.0-38.61) ...
Setting up linux-headers-3.2.0-38-generic (3.2.0-38.61) ...
Setting up linux-headers-3.2.0-38-generic-pae (3.2.0-38.61) ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-35-generic; however:
  Package linux-headers-3.2.0-35-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-35-generic-pae; however:
No apport report written because MaxReports is reached already
                                                                Package linux-headers-3.2.0-35-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-generic
 linux-headers-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
iltesham@iltesham-Inspiron-1525:~$

---

### Post by Iltesham on 2013-03-16
And df -hi gives the following

iltesham@iltesham-Inspiron-1525:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda8        472K  464K  8.6K   99% /
udev             210K   589  210K    1% /dev
tmpfs            214K   518  213K    1% /run
none             214K     3  214K    1% /run/lock
none             214K     7  214K    1% /run/shm
/dev/mmcblk0p1      0     0     0     - /media/438B-0831
/dev/sda6        4.1M   15K  4.1M    1% /mnt
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Did the other commands work? Please post the output of ```
ls /boot
```

Anyway, try
```

sudo dpkg -P --force-remove-reinstreq linux-headers-generic{,-pae}

```

---

### Post by Iltesham on 2013-03-16
Hi,
Yes all the previous commands worked and only the final "install -f" gave that error;
Here is ls /boot

iltesham@iltesham-Inspiron-1525:~$ ls /boot
abi-3.0.0-19-generic         memtest86+.bin
abi-3.2.0-34-generic         memtest86+_multiboot.bin
abi-3.2.0-35-generic         System.map-3.0.0-19-generic
config-3.0.0-19-generic      System.map-3.2.0-34-generic
config-3.2.0-34-generic      System.map-3.2.0-35-generic
config-3.2.0-35-generic      vmcoreinfo-3.0.0-19-generic
grub                         vmlinuz-3.0.0-19-generic
initrd.img-3.0.0-19-generic  vmlinuz-3.2.0-34-generic
initrd.img-3.2.0-34-generic  vmlinuz-3.2.0-35-generic
initrd.img-3.2.0-35-generic
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Okey. Try
```

sudo dpkg -P linux-image-3.0.0-19-generic
sudo dpkg -P --force-remove-reinstreq linux-headers-generic{,-pae}
sudo apt-get install -f

```

---

### Post by Iltesham on 2013-03-16
Actually i had already tried "sudo dpkg -P --force-remove-reinstreq linux-headers-generic{,-pae}"

and i got this

iltesham@iltesham-Inspiron-1525:~$ sudo dpkg -P --force-remove-reinstreq linux-headers-generic{,-pae}
[sudo] password for iltesham: 
(Reading database ... 456250 files and directories currently installed.)
Removing linux-headers-generic ...
Removing linux-headers-generic-pae ...
iltesham@iltesham-Inspiron-1525:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 232 not upgraded.
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Good. Now, let's look at the output of *df* one last time
```
df -hi
```

---

### Post by Iltesham on 2013-03-16
I dont get that error message when i click software center now? does this mean that the issue is resolved?
shoudld i try updating the Ubuntu?

---

### Post by Iltesham on 2013-03-16
> **schragge said:**
> Good. Now, let's look at the output of *df* one last time
```
df -hi
```

hi,
here is df -hi

iltesham@iltesham-Inspiron-1525:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda8        472K  460K   13K   98% /
udev             210K   589  210K    1% /dev
tmpfs            214K   518  213K    1% /run
none             214K     3  214K    1% /run/lock
none             214K     7  214K    1% /run/shm
/dev/mmcblk0p1      0     0     0     - /media/438B-0831
/dev/sda6        4.1M   15K  4.1M    1% /mnt
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Yes, the issue with the package catalog is resolved, but I'd like to see if we still have enough free inodes to handle 232 upgrades apt-get is reporting about.

[highlight]Update.[/highlight]
Oh I see. Yep, go ahead with updates. 13000 inodes should be enough.

---

### Post by Iltesham on 2013-03-16
i tried sudo apt-get upgrade and here is what i get;

230 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 235 MB of archives.
After this operation, 5,619 kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by Iltesham on 2013-03-16
Should i go ahead?
and press Y

---

### Post by schragge on 2013-03-16
The two not upgraded should be related to new kernel (linux-image-3.2.0-38). You can upgrade them afterwards with
```
sudo apt-get dist-upgrade
```I'd say Y at this point. At least, it's worth a try. :)

---

### Post by Iltesham on 2013-03-16
Hi,
I pressed Y and it went upgrading for 10-12 minutes and gave me this;

Processing triggers for install-info ...
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-docs_12.04.6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Okey, try this
```

sudo apt-get clean
sudo dpkg -C

``` and post here the results.

---

### Post by Iltesham on 2013-03-16
Hi,
here is what i get;
iltesham@iltesham-Inspiron-1525:~$ sudo apt-get clean
[sudo] password for iltesham: 
iltesham@iltesham-Inspiron-1525:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 xserver-common       common files used by various X servers
 python-aptdaemon     Python module for the server and client of aptdaemon
 unity-greeter        Unity Greeter
 libreoffice-style-human office productivity suite -- Human symbol style
 libgl1-mesa-dri      free implementation of the OpenGL API -- DRI modules
 ure                  LibreOffice UNO runtime environment
 sudo                 Provide limited super user privileges to specific users
 libfreetype6         FreeType 2 font engine, shared library files
 pulseaudio-module-x11 X11 module for PulseAudio sound server
 duplicity            encrypted bandwidth-efficient backup
 initramfs-tools      tools for generating an initramfs
 libgnome-control-center1 utilities to configure the GNOME desktop
 flashplugin-downloader Adobe Flash Player plugin installer (transitional packa
 cups-ppdc            Common UNIX Printing System(tm) - PPD manipulation utilit
 indicator-weather    indicator that displays weather information
 compiz-plugins-default OpenGL window and compositing manager - default plugins
 man-db               on-line manual pager
 pulseaudio-utils     Command line tools for the PulseAudio sound server
 libavcodec53         Libav codec library
 isc-dhcp-common      common files used by all the isc-dhcp* packages
 unity                Interface designed for efficiency of space and interactio
 gnome-settings-daemon daemon handling the GNOME session settings
 compiz               OpenGL window and compositing manager
 libreoffice-math     office productivity suite -- equation editor
 language-pack-en     translation updates for language English
 libqtgui4            Qt 4 GUI module
 python-aptdaemon.pkcompat PackageKit compatibilty for AptDaemon
 libreoffice-impress  office productivity suite -- presentation
 libqt4-sql-sqlite    Qt 4 SQLite 3 database driver
 jockey-common        user interface and desktop integration for driver managem
 aptdaemon-data       data files for clients
 firefox-globalmenu   Unity appmenu integration for Firefox
 apport-gtk           GTK+ frontend for the apport crash report system
 unity-services       Services for the Unity interface
 libnm-util2          network management framework (shared library)
 libqt4-sql           Qt 4 SQL module
 language-selector-gnome Language selector for Ubuntu
 openssl              Secure Socket Layer (SSL) binary and related cryptographi
 xorg                 X.Org X Window System
 libtelepathy-glib0   Telepathy framework - GLib library
 language-pack-gnome-en-base GNOME translations for language English
 libusbmuxd1          USB multiplexor daemon for iPhone and iPod Touch devices 
 thunderbird-globalmenu Unity appmenu integration for Thunderbird
 libdbus-glib-1-2     simple interprocess messaging system (GLib-based shared l
 ubuntu-standard      The Ubuntu standard system
 grub-common          GRand Unified Bootloader (common files)
 unity-common         Common files for the Unity interface.
 pulseaudio-module-gconf GConf module for PulseAudio sound server
 xserver-xorg-core    Xorg X server - core server
 libqt4-declarative   Qt 4 Declarative module
 libdrm2              Userspace interface to kernel DRM services -- runtime
 libdrm-nouveau1a     Userspace interface to nouveau-specific kernel DRM servic
 cups-client          Common UNIX Printing System(tm) - client programs (SysV)
 libpulse-mainloop-glib0 PulseAudio client libraries (glib support)
 apt-transport-https  https download transport for APT
 activity-log-manager-control-center blacklist configuration for Zeitgeist (con
 python-apport        apport crash report handling library
 grub-pc-bin          GRand Unified Bootloader, version 2 (PC/BIOS binaries)
 activity-log-manager-common blacklist configuration for Zeitgeist (assets)
 libreoffice-style-tango office productivity suite -- Tango symbol style
 libpurple0           multi-protocol instant messaging library
 libpurple-bin        multi-protocol instant messaging library - extra utilitie
 mountall             filesystem mounting tool
 transmission-common  lightweight BitTorrent client (common files)
 libqt4-svg           Qt 4 SVG module
 xserver-xorg-video-qxl X.Org X server -- QXL display driver
 gnome-control-center-data configuration applets for GNOME - data files
 software-center      Utility for browsing, installing, and removing software
 overlay-scrollbar    Scrollbar overlayed widget
 linux-libc-dev       Linux Kernel Headers for development
 libreoffice-writer   office productivity suite -- word processor
 libdrm-radeon1       Userspace interface to radeon-specific kernel DRM service
 libdecoration0       Compiz window decoration library
 libqtcore4           Qt 4 core module
 python-aptdaemon.gtk3widgets Python GTK+ 3 widgets to run an aptdaemon client
 nautilus-data        data files for nautilus
 gnome-sudoku         Sudoku puzzle game for GNOME
 xserver-xorg         X.Org X server
 libglu1-mesa         Mesa OpenGL utility library (GLU)
 libapt-inst1.4       deb package format runtime library
 libcupsmime1         Common UNIX Printing System(tm) - MIME library
 xserver-xorg-video-all X.Org X server -- output driver metapackage
 libreoffice-base-core office productivity suite -- shared library
 libreoffice-gnome    office productivity suite -- GNOME integration
 libcupsdriver1       Common UNIX Printing System(tm) - Driver library
 cups-common          Common UNIX Printing System(tm) - common files
 libcups2             Common UNIX Printing System(tm) - Core library
 mysql-common         MySQL database common files, e.g. /etc/mysql/my.cnf
 bamfdaemon           Window matching library - daemon
 libplymouth2         graphical boot animation and logger - shared libraries
 libqt4-network       Qt 4 network module
 mahjongg             classic Eastern tile game for GNOME
 libnspr4             NetScape Portable Runtime Library
 compiz-core          OpenGL window and compositing manager
 plymouth-theme-ubuntu-logo graphical boot animation and logger - ubuntu-logo t
 libqt4-sql-mysql     Qt 4 MySQL database driver
 libbamf0             Window matching library - shared library
 libpulsedsp          PulseAudio OSS pre-load library
 gnome-control-center utilities to configure the GNOME desktop
 checkbox             System testing application
 initramfs-tools-bin  binaries used by initramfs-tools
 libqt4-script        Qt 4 script module
 libreoffice-emailmerge office productivity suite -- email mail merge
 libbamf3-0           Window matching library - shared library
 libdevmapper1.02.1   The Linux Kernel Device Mapper userspace library
 libxatracker1        X acceleration library -- runtime
 liblvm2app2.2        LVM2 application library
 libqt4-dbus          Qt 4 D-Bus module
 libreoffice-common   office productivity suite -- arch-independent files
 libswscale2          Libav video scaling library
 libpulse0            PulseAudio client libraries
 liboverlay-scrollbar3-0.2-0 Scrollbar overlayed widget - shared lib
 evince               Document (PostScript, PDF) viewer
 evince-common        Document (PostScript, PDF) viewer - common files
 libglapi-mesa        free implementation of the GL API -- shared library
 thunderbird          Email, RSS and newsgroup client with integrated spam filt
 libdevmapper-event1.02.1 The Linux Kernel Device Mapper userspace library
 flashplugin-installer Adobe Flash Player plugin installer
 libgl1-mesa-glx      free implementation of the OpenGL API -- GLX runtime
 transmission-gtk     lightweight BitTorrent client (GTK interface)
 libqt4-opengl        Qt 4 OpenGL module
 uno-libs3            LibreOffice UNO runtime environment -- public shared libr
 language-pack-en-base translations for language English
 libnm-gtk-common     network management framework (common files for wifi and m
 plymouth-theme-ubuntu-text graphical boot animation and logger - ubuntu-logo t
 libpoppler-glib8     PDF rendering library (GLib-based shared library)
 thunderbird-gnome-support Email, RSS and newsgroup client - GNOME support
 x11-common           X Window System (X.Org) infrastructure
 liboverlay-scrollbar-0.2-0 Scrollbar overlayed widget - shared lib
 libunity-core-5.0-5  Core library for the Unity interface.
 unattended-upgrades  automatic installation of security upgrades
 libnautilus-extension1a libraries for nautilus components - runtime version
 checkbox-gtk         GTK interface for checkbox
 tomboy               desktop note taking program using Wiki style links
 plymouth-label       graphical boot animation and logger - label control
 plymouth             graphical boot animation and logger - main package
 unity-lens-applications Application lens for unity
 python-problem-report Python library to handle problem reports
 libqt4-designer      Qt 4 designer module
 libnss3-1d           Network Security Service libraries
 upstart              event-based init daemon
 libmysqlclient18     MySQL database client library
 python-aptdaemon.gtkwidgets Python GTK+ 2 widgets to run an aptdaemon client
 liblightdm-gobject-1-0 LightDM GObject client library
 xserver-xorg-video-nouveau X.Org X server -- Nouveau display driver
 libqt4-help          Qt 4 help module
 jockey-gtk           GNOME user interface and desktop integration for driver m
 libnm-gtk0           network management framework (GNOME dialogs for wifi and 
 nautilus             file manager and graphical shell for GNOME
 libssh-4             tiny C SSH library
 libnih1              NIH Utility Library
 gnomine              popular minesweeper puzzle game for GNOME
 libgnutls26          GNU TLS library - runtime library
 poppler-utils        PDF utilities (based on Poppler)
 grub-pc              GRand Unified Bootloader, version 2 (PC/BIOS version)
 ubuntu-desktop       The Ubuntu desktop system
 libavutil51          Libav utility library
 firefox-gnome-support Safe and easy web browser from Mozilla - GNOME support
 deja-dup             Back up your files
 google-talkplugin    Google Talk Plugin
 vino                 VNC server for GNOME
 aptdaemon            transaction based package management service
 dmsetup              The Linux Kernel Device Mapper userspace library
 gstreamer0.10-pulseaudio GStreamer plugin for PulseAudio
 pulseaudio-esound-compat PulseAudio ESD compatibility layer
 gnome-games-data     data files for the GNOME games
 lightdm              Display Manager
 libqt4-scripttools   Qt 4 script tools module
 qdbus                Qt 4 D-Bus tool
 fonts-opensymbol     OpenSymbol TrueType font
 python-aptdaemon-gtk Transitional dummy package
 im-switch            Input method switch framework
 xserver-xorg-video-intel X.Org X server -- Intel i8xx, i9xx display driver
 cups-bsd             Common UNIX Printing System(tm) - BSD commands
 libevince3-3         Document (PostScript, PDF) rendering library
 libnm-glib4          network management framework (GLib shared library)
 network-manager      network management framework (daemon and userspace tools)
 libcupscgi1          Common UNIX Printing System(tm) - CGI library
 libdrm-intel1        Userspace interface to intel-specific kernel DRM services
 language-pack-gnome-en GNOME translation updates for language English
 libavformat53        Libav file format library
 gstreamer0.10-gconf  GStreamer plugin for getting the sink/source information 
 libpciaccess0        Generic PCI access library for X
 libqt4-qt3support    Qt 3 compatibility library for Qt 4
 alsa-base            ALSA driver configuration files
 libnss3              Network Security Service libraries
 libqt4-xml           Qt 4 XML module
 xserver-xorg-input-all X.Org X server -- input driver metapackage
 libpostproc52        Libav video postprocessing library
 libnspr4-0d          NetScape Portable Runtime Library
 acpi-support         scripts for handling many ACPI events
 firefox              Safe and easy web browser from Mozilla
 libreoffice-gtk      office productivity suite -- GTK+ integration
 libcupsppdc1         Common UNIX Printing System(tm) - PPD manipulation librar
 libnih-dbus1         NIH D-Bus Bindings Library
 libqt4-test          Qt 4 test module
 language-selector-common Language selector for Ubuntu
 firefox-locale-en    English language pack for Firefox
 grub2-common         GRand Unified Bootloader (common files for version 2)
 gstreamer0.10-plugins-good GStreamer plugins from the "good" set
 libnm-glib-vpn1      network management framework (GLib VPN shared library)
 apt-utils            package managment related utility programs
 compiz-gnome         OpenGL window and compositing manager - GNOME window deco
 libqt4-xmlpatterns   Qt 4 XML patterns module
 libpoppler19         PDF rendering library
 python-uno           Python-UNO bridge
 libreoffice-draw     office productivity suite -- drawing
 ubuntu-minimal       Minimal core of Ubuntu
 libreoffice-help-en-us office productivity suite -- English_american help
 network-manager-gnome network management framework (GNOME frontend)
 apport               automatically generate crash reports for debugging
 libreoffice-calc     office productivity suite -- spreadsheet
 pulseaudio           PulseAudio sound server
 isc-dhcp-client      ISC DHCP client
 libreoffice-core     office productivity suite -- arch-dependent files
 linux-sound-base     base package for ALSA and OSS sound systems
 ttf-opensymbol       transitional package for fonts-opensymbol
 libcupsimage2        Common UNIX Printing System(tm) - Raster image library
 checkbox-qt          QT4 interface for checkbox
 usbmuxd              USB multiplexor daemon for iPhone and iPod Touch devices
 cups                 Common UNIX Printing System(tm) - server
 pulseaudio-module-bluetooth Bluetooth module for PulseAudio sound server

iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Okey, then try
```
sudo dpkg --configure -a
```

---

### Post by Iltesham on 2013-03-16
Seems to have no issues; but i dont know. Here is what i get at the end;

Found Ubuntu 11.10 (11.10) on /dev/sda6
done
Setting up libreoffice-help-en-us (1:3.5.7-0ubuntu4) ...
Setting up plymouth-theme-ubuntu-logo (0.8.2-2ubuntu31) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for libreoffice-common ...
Setting up libreoffice-emailmerge (1:3.5.7-0ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Looks good. Now, there was a problem with *ubuntu-docs* reported by dpkg when running *apt-get upgrade*. So, let's try
```

sudo apt-get clean
sudo apt-get install ubuntu-docs

```

---

### Post by Iltesham on 2013-03-16
Showed this error;

ltesham@iltesham-Inspiron-1525:~$ sudo apt-get install ubuntu-docs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ubuntu-docs
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,450 kB of archives.
After this operation, 41.0 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main ubuntu-docs all 12.04.6 [1,450 kB]
Fetched 1,450 kB in 1s (1,221 kB/s)    
(Reading database ... 452045 files and directories currently installed.)
Preparing to replace ubuntu-docs 12.04.5 (using .../ubuntu-docs_12.04.6_all.deb) ...
Unpacking replacement ubuntu-docs ...
dpkg: error processing /var/cache/apt/archives/ubuntu-docs_12.04.6_all.deb (--unpack):
 unable to make backup symlink for `./usr/share/help/zh_TW/ubuntu-help/color.page': No space left on device
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-docs_12.04.6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
So, we are back to the same problem: [COLOR=red]no space left on device[/COLOR]. Let's remove some more kernel stuff. For this, please post the output of ```
dpkg -l linux-\*|grep -o '^i.. [^ ]*'
```

---

### Post by Iltesham on 2013-03-16
Hi,
here is what i get;

iltesham@iltesham-Inspiron-1525:~$ dpkg -l linux-\*|grep -o '^i.. [^ ]*'
ii  linux-firmware
ii  linux-generic
ii  linux-headers-3.2.0-24
ii  linux-headers-3.2.0-24-generic
ii  linux-headers-3.2.0-24-generic-pae
ii  linux-headers-3.2.0-25
ii  linux-headers-3.2.0-25-generic
ii  linux-headers-3.2.0-25-generic-pae
ii  linux-headers-3.2.0-26
ii  linux-headers-3.2.0-26-generic
ii  linux-headers-3.2.0-26-generic-pae
ii  linux-headers-3.2.0-29
ii  linux-headers-3.2.0-29-generic
ii  linux-headers-3.2.0-29-generic-pae
ii  linux-headers-3.2.0-31
ii  linux-headers-3.2.0-31-generic
ii  linux-headers-3.2.0-31-generic-pae
ii  linux-headers-3.2.0-32
ii  linux-headers-3.2.0-32-generic
ii  linux-headers-3.2.0-32-generic-pae
ii  linux-headers-3.2.0-33
ii  linux-headers-3.2.0-33-generic
ii  linux-headers-3.2.0-33-generic-pae
ii  linux-headers-3.2.0-34
ii  linux-headers-3.2.0-34-generic
ii  linux-headers-3.2.0-34-generic-pae
ii  linux-headers-3.2.0-35
in  linux-headers-3.2.0-35-generic
in  linux-headers-3.2.0-35-generic-pae
ii  linux-headers-3.2.0-38
ii  linux-headers-3.2.0-38-generic
ii  linux-headers-3.2.0-38-generic-pae
ii  linux-image-3.2.0-34-generic
ii  linux-image-3.2.0-35-generic
ii  linux-image-generic
ii  linux-libc-dev
ii  linux-sound-base

---

### Post by Iltesham on 2013-03-16
> **schragge said:**
> So, we are back to the same problem: [COLOR=red]no space left on device[/COLOR]. Let's remove some more kernel stuff. For this, please post the output of ```
dpkg -l linux-\*|grep -o '^i.. [^ ]*'
```

hi,
here is what i get;

iltesham@iltesham-Inspiron-1525:~$ dpkg -l linux-\*|grep -o '^i.. [^ ]*'
ii  linux-firmware
ii  linux-generic
ii  linux-headers-3.2.0-24
ii  linux-headers-3.2.0-24-generic
ii  linux-headers-3.2.0-24-generic-pae
ii  linux-headers-3.2.0-25
ii  linux-headers-3.2.0-25-generic
ii  linux-headers-3.2.0-25-generic-pae
ii  linux-headers-3.2.0-26
ii  linux-headers-3.2.0-26-generic
ii  linux-headers-3.2.0-26-generic-pae
ii  linux-headers-3.2.0-29
ii  linux-headers-3.2.0-29-generic
ii  linux-headers-3.2.0-29-generic-pae
ii  linux-headers-3.2.0-31
ii  linux-headers-3.2.0-31-generic
ii  linux-headers-3.2.0-31-generic-pae
ii  linux-headers-3.2.0-32
ii  linux-headers-3.2.0-32-generic
ii  linux-headers-3.2.0-32-generic-pae
ii  linux-headers-3.2.0-33
ii  linux-headers-3.2.0-33-generic
ii  linux-headers-3.2.0-33-generic-pae
ii  linux-headers-3.2.0-34
ii  linux-headers-3.2.0-34-generic
ii  linux-headers-3.2.0-34-generic-pae
ii  linux-headers-3.2.0-35
in  linux-headers-3.2.0-35-generic
in  linux-headers-3.2.0-35-generic-pae
ii  linux-headers-3.2.0-38
ii  linux-headers-3.2.0-38-generic
ii  linux-headers-3.2.0-38-generic-pae
ii  linux-image-3.2.0-34-generic
ii  linux-image-3.2.0-35-generic
ii  linux-image-generic
ii  linux-libc-dev
ii  linux-sound-base
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Ok, so let's remove some old linux-headers
```

sudo dpkg -P linux-headers-3.2.0-{24,25,26,29,31,32,33}{,-generic,-generic-pae}

```
Then try it once again
```
sudo apt-get install ubuntu-docs
```

---

### Post by Iltesham on 2013-03-16
Hi,
it gave me the following; 

(Reading database ... 236987 files and directories currently installed.)
Preparing to replace ubuntu-docs 12.04.5 (using .../ubuntu-docs_12.04.6_all.deb) ...
Unpacking replacement ubuntu-docs ...
Setting up ubuntu-docs (12.04.6) ...
iltesham@iltesham-Inspiron-1525:~$

---

### Post by Iltesham on 2013-03-16
but do i need to install those two upgrades which it missed out of 232 separately or are they already taken care of?

---

### Post by schragge on 2013-03-16
Try this:
```
sudo apt-get dist-upgrade
```

---

### Post by Iltesham on 2013-03-16
Hi,
It did not give any error message, Following is what i get. Does this mean the issue is resolved finally?

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda3
Found Microsoft Windows XP Embedded on /dev/sda5
Found Ubuntu 11.10 (11.10) on /dev/sda6
done
Setting up linux-image-generic (3.2.0.38.46) ...
Setting up linux-headers-generic (3.2.0.38.46) ...
Setting up linux-generic (3.2.0.38.46) ...
iltesham@iltesham-Inspiron-1525:~$

---

### Post by schragge on 2013-03-16
Yep. Now reboot. After rebooting, *uname -r* should show something like 3.2.0-38. This means you're now using the latest linux kernel. Keep an eye on old kernels, they take up precious inode space on your root partition. If all goes well, you can also remove the 3.2.0-34 kernel packages:
```
sudo apt-get purge '3\.2\.0-34.*'
``` This will free up some more inodes for future updates.
[highlight]Edit.[/highlight]
The [COLOR=red]apt-get purge 3.2.0-34\*[/COLOR] I first suggested was just plain wrong: it erased _all_ kernels including the current one on the OP's system. *apt-get* uses [regular expressions]("http://en.wikipedia.org/wiki/Regular_expression"), not [shell globbing patterns]("http://en.wikipedia.org/wiki/Glob_(programming)"). ](*,)

---

### Post by Iltesham on 2013-03-16
Thank you so very much schragge. I really appreciate your help and tireless effort to resolve this issue. God bless you and all the others who are helping people like me to get our issues resolved.
thanks again and keep up the good work.
I will mark this thread as resolved now.
thanks and have a good night.

---

### Post by Iltesham on 2013-03-16
> **schragge said:**
> Yep. Now reboot. After rebooting, *uname -r* should show something like 3.2.0-38. This means you're now using the latest linux kernel. Keep an eye on old kernels, they take up precious inode space on your root partition. If all goes well, you can also remove the 3.2.0-34 kernel packages:
```
sudo apt-get purge 3.2.0-34\*
``` This will free up some more inodes for future updates.

Hi schragge,
Some thing happened after i did sudo apt-get purge 3.2.0-34\* and now i cannot see the ubuntu option at all when i reboot. I had dual boot with Windows vista and that is where i am replying from.
what could be done? I will really appreciate your help. I am desperate now for the help.

---

### Post by schragge on 2013-03-16
:oops: What options *do* show up in your boot menu? Does the computer boots straight into Windows? Can you force display of the boot menu by pressing **Shift** while booting?

---

### Post by Iltesham on 2013-03-16
It does give me the option where i press "C" to go to command prompt. where i get some thing like this
grub>

---

### Post by schragge on 2013-03-16
At the *grub>* prompt try
```
ls (hd0,sda8)/boot
``` It should show something like
```
config-3.2.0-35-generic config-3.2.0-38-generic grub initrd.img-3.2.0-35-generic initrd.img-3.2.0-38-generic
grub System.map-3.2.0-35-generic System.map-3.2.0-38-generic vmlinuz-3.2.0-35-generic vmlinuz-3.2.0-38-generic
```
Have you got an Ubuntu Live medium (LiveCD/LiveUSB)? You will need one with Boot-Repair  ([uhelp]community/Boot-Repair[/uhelp]).

---

### Post by Iltesham on 2013-03-16
when ever i reboot i see a black screen at the top of which i see this written "GNU GRUB Version 1.99-21ubuntu3.9"
and then i have three option with the first two being memory test and the third one with Windows vista and at the bottom i see the option to press e for escape and C for command prompt and so on. When i press C the screen turns into Command prompt with something like this
grub>

---

### Post by Iltesham on 2013-03-16
> **schragge said:**
> At the *grub>* prompt try
```
ls (hd0,sda8)/boot
``` It should show something like
```
config-3.2.0-35-generic config-3.2.0-38-generic grub initrd.img-3.2.0-35-generic initrd.img-3.2.0-38-generic
grub System.map-3.2.0-35-generic System.map-3.2.0-38-generic vmlinuz-3.2.0-35-generic vmlinuz-3.2.0-38-generic
```
Have you got an Ubuntu Live medium (LiveCD/LiveUSB)? You will need one with Boot-Repair  ([uwiki]community/Boot-Repair[/uwiki]).

i do have a cd but it is version 11.0 and very old

---

### Post by schragge on 2013-03-16
The link in my previous post was wrong. I've fixed it. Please read that page. Do you have a spare USB stick? In Windows, download [UnetBootin]("http://unetbootin.sourceforge.net/"). Insert the USB stick, launch UnetBootin and select Distribution: Ubuntu, 12.04_Live. This will create a bootable pendrive.

---

### Post by Iltesham on 2013-03-16
> **schragge said:**
> At the *grub>* prompt try
```
ls (hd0,sda8)/boot
``` It should show something like
```
config-3.2.0-35-generic config-3.2.0-38-generic grub initrd.img-3.2.0-35-generic initrd.img-3.2.0-38-generic
grub System.map-3.2.0-35-generic System.map-3.2.0-38-generic vmlinuz-3.2.0-35-generic vmlinuz-3.2.0-38-generic
```
Have you got an Ubuntu Live medium (LiveCD/LiveUSB)? You will need one with Boot-Repair  ([uhelp]community/Boot-Repair[/uhelp]).

HI,
I have tried 

ls (hd0,sda8)/boot
and it said no such partition. I am downloading the boot repair files u pointed me to. Can you please tell me the steps which i should follow once i get the bootrepair ready.
thanks,
Iltesham Z Syed

---

### Post by Iltesham on 2013-03-17
> **schragge said:**
> The link in my previous post was wrong. I've fixed it. Please read that page. Do you have a spare USB stick? In Windows, download [UnetBootin]("http://unetbootin.sourceforge.net/"). Insert the USB stick, launch UnetBootin and select Distribution: Ubuntu, 12.04_Live. This will create a bootable pendrive.

Hi schragge,
I finally got the reboot back. I followed the links you provided and it repaired the boot. Thank you so very much for everything. I really appreciate your help. I will always be thankful to you for this.
Good night.

---

### Post by schragge on 2013-03-17
Glad you got it back. I feel awfully sorry, it was my fault. The purge command I suggested erased all kernels on your system including the latest. ](*,)

---

