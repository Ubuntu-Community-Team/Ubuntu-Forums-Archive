---
title: "Help with package installation errors"
date: 2016-05-10
forum: New to Ubuntu
---

### Post by Amit_Mishra on 2016-05-10
root@XeNiA:~# dpkg --configure -a
Setting up libx32gcc1 (1:6.0.1-0ubuntu1) ...
Setting up lib32gomp1 (5.3.1-14ubuntu2) ...
Setting up libx32stdc++6 (5.3.1-14ubuntu2) ...
Setting up lib32atomic1 (5.3.1-14ubuntu2) ...
Setting up libx32atomic1 (5.3.1-14ubuntu2) ...
Setting up libx32gomp1 (5.3.1-14ubuntu2) ...
Setting up libx32asan2 (5.3.1-14ubuntu2) ...
Setting up libx32itm1 (5.3.1-14ubuntu2) ...
Setting up lib32mpx0 (5.3.1-14ubuntu2) ...
Setting up gcc-5 (5.3.1-14ubuntu2) ...
Setting up lib32quadmath0 (5.3.1-14ubuntu2) ...
dpkg: dependency problems prevent configuration of libc6-dev-x32:
 libc6-dev-x32 depends on libc6-dev-i386 (= 2.23-0ubuntu3); however:
  Package libc6-dev-i386 is not installed.


dpkg: error processing package libc6-dev-x32 (--configure):
 dependency problems - leaving unconfigured
Setting up lib32itm1 (5.3.1-14ubuntu2) ...
Setting up libx32quadmath0 (5.3.1-14ubuntu2) ...
Setting up lib32gcc1 (1:6.0.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of gcc-5-multilib:
 gcc-5-multilib depends on libc6-dev-i386 (>= 2.11); however:
  Package libc6-dev-i386 is not installed.
 gcc-5-multilib depends on libc6-dev-x32 (>= 2.11); however:
  Package libc6-dev-x32 is not configured yet.


dpkg: error processing package gcc-5-multilib (--configure):
 dependency problems - leaving unconfigured
Setting up libx32cilkrts5 (5.3.1-14ubuntu2) ...
Setting up libx32ubsan0 (5.3.1-14ubuntu2) ...
dpkg: dependency problems prevent configuration of gcc-multilib:
 gcc-multilib depends on gcc-5-multilib (>= 5.3.1-3~); however:
  Package gcc-5-multilib is not configured yet.

```

dpkg: error processing package gcc-multilib (--configure):
 dependency problems - leaving unconfigured
Setting up gcc (4:5.3.1-1ubuntu1) ...
Setting up lib32stdc++6 (5.3.1-14ubuntu2) ...
Setting up lib32ubsan0 (5.3.1-14ubuntu2) ...
Setting up lib32cilkrts5 (5.3.1-14ubuntu2) ...
Setting up lib32asan2 (5.3.1-14ubuntu2) ...
Setting up lib32gcc-5-dev (5.3.1-14ubuntu2) ...
Setting up libx32gcc-5-dev (5.3.1-14ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 libc6-dev-x32
 gcc-5-multilib
 gcc-multilib
```

can someone please help me with this..!!

---

### Post by Bucky Ball on 2016-05-10
Welcome, Well, as you have given a lot of code but no indication of what you are trying to install or how you are trying to install it, that might be difficult unless somewhere is willing to go through the code and try to work out what you are trying to install and do. Or you could just share that with us in a post here. ;)

Please use code tags for terminal output. See the green link in my signature at the bottom of this post for how. Thanks.

---

### Post by Amit_Mishra on 2016-05-10
I was trying to install steam on Ubuntu and later synaptic package manager..!
every time i m trying to install i get the message waiting to install and its stuck there..!
Most of the time i get the error about unmet dependencies, nd broken packages..!

---

### Post by Bucky Ball on 2016-05-10
You have no issue installing other things, just Steam?

---

### Post by Amit_Mishra on 2016-05-10
I am unable to install other things as well, every time i try  installing things my new friend greets me with this error of unmet dependencies and broken packages..!!

---

### Post by Bashing-om on 2016-05-10
Amit_Mishra; Hello;

Let us look at the error condition :
Post back the outputs - Between Code Tags - of terminal commands :
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
To show where to isolate our thought processes to.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Amit_Mishra on 2016-05-11
**Output for sudo apt update**

```
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [64.3 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [62.2 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [15.0 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [15.0 kB]
Fetched 251 kB in 1s (153 kB/s)                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

**Output for Sudo apt upgrade.**

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
```

**Output for sudo apt -f install.**


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  diffstat fakeroot gettext intltool-debian libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libclone-perl libdata-alias-perl
  libemail-valid-perl libexporter-tiny-perl libfakeroot libgettextpo-dev
  libgettextpo0 libio-pty-perl libipc-run-perl liblist-moreutils-perl
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libperlio-gzip-perl
  libstdc++-5-dev libtext-levenshtein-perl libyaml-libyaml-perl patchutils
  t1utils
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gcc-multilib libc6-dev-i386
The following NEW packages will be installed:
  gcc-multilib libc6-dev-i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,267 kB of archives.
After this operation, 6,948 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 240562 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Selecting previously unselected package gcc-multilib.
Preparing to unpack .../gcc-multilib_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking gcc-multilib (4:5.3.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bucky Ball on 2016-05-11
> **Bucky Ball said:**
> Please use code tags for terminal output. See the green link in my signature at the bottom of this post for how. Thanks.

You missed this? Use them, please.

---

### Post by Amit_Mishra on 2016-05-11
Error mounting /dev/sdg1 at /media/amzy/XENIA: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdg1" "/media/amzy/XENIA"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

every time i try to plug in a pen drive or hardisk i am getting this error..!

---

### Post by Amit_Mishra on 2016-05-12
Guys i have been stuck to the problem for a long time now, have tried almost everything available on the forums..!
Maybe i am not doing it right this is my first time with Ubuntu, out of pure curiousness towards the OS, i don`t want this to end negative..!

---

### Post by Bashing-om on 2016-05-12
Amit_Mishra; Morning .

This conflict may be a knotty one to resolve - perhaps the reason there is a slow response to your need.

What is the reason that you have installed the development packaging ?
Show us by the output of terminal commands:
```

apt-cache policy libc6-dev-amd64
apt-cache policy libc6-dev-i386
apt-cache policy gcc-multilib

```
what is installed, and where these packages came from.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

There is a conflict, and something must be removed in order to satisfy the package manager.

[INDENT][INDENT]package manager not happy
[INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Amit_Mishra on 2016-05-13
The Output for apt-cache libc6-dev-amd64

```
libc6-dev-amd64:i386:  Installed: 2.23-0ubuntu3
  Candidate: 2.23-0ubuntu3
  Version table:
 *** 2.23-0ubuntu3 500
        500 http://mirror.metrocast.net/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status



```

The output for [COLOR=#000000][FONT=Ubuntu Mono]apt-cache policy libc6-dev-i386

```
[/FONT][/COLOR]libc6-dev-i386:  Installed: (none)
  Candidate: 2.23-0ubuntu3
  Version table:
     2.23-0ubuntu3 500
        500 http://mirror.metrocast.net/ubuntu xenial/main amd64 Packages


[COLOR=#000000][FONT=Ubuntu Mono]
```

the Output for [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]apt-cache policy gcc-multilib

```
[/FONT][/COLOR]gcc-multilib:  Installed: 4:5.3.1-1ubuntu1
  Candidate: 4:5.3.1-1ubuntu1
  Version table:
 *** 4:5.3.1-1ubuntu1 500
        500 http://mirror.metrocast.net/ubuntu xenial/main amd64 Packages

        100 /var/lib/dpkg/status[COLOR=#000000][FONT=Ubuntu Mono]
```[/FONT][/COLOR]

---

### Post by oldfred on 2016-05-13
Your exfat issue is another totally different issue.
Exfat is proprietary to Microsoft, but developers have reversed engineered a driver.
You should probably not normally use exfat, but a few devices now require it.

You need to install the driver.

fuse-exfat is a read and write driver implementing
the extended file allocation table as a filesystem in userspace.

sudo apt-get install fuse-exfat

---

### Post by Bucky Ball on 2016-05-13
oldfred: I think you need exfat-utils and exfat-fuse. At least that's what I need on two of my computers to access the 64Gb card I use with my HD camera (that's how the camera formats it so no choice). Installed those two and worked instantly.

---

### Post by Amit_Mishra on 2016-05-13
Output for [COLOR=#000000]sudo apt-get install fuse-exfat

```
[/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
E: Unable to locate package fuse-exfat


[COLOR=#000000]
```[/COLOR]

---

### Post by Amit_Mishra on 2016-05-13
also tried using sudo apt-get install exfat-utils, output.

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

This is what my primary problem is, of unmet dependencies, unable to install anything including the updates.

---

### Post by Bucky Ball on 2016-05-13
As oldfred said:

> **oldfred said:**
> Your exfat issue is another totally different issue.

Forget about that for the moment. We digress. :)

---

### Post by Bashing-om on 2016-05-13
Amit_Mishra; Hey ...

Addressing the dependency issue;
I am not familiar, and do not recognize " [http://mirror.metrocast.net/](http://mirror.metrocast.net/) " . How does this source play in this ?
Post back the results:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Let's see if it is a PPA at the root of this. See what direction we get pointed to .

[INDENT][INDENT]together, we can
[/INDENT][/INDENT]

---

### Post by oldfred on 2016-05-13
Metrocast is a United States mirror.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by Amit_Mishra on 2016-05-14
Output for [COLOR=#000000][FONT=Ubuntu Mono]cat -n /etc/apt/sources.list[/FONT][/COLOR]

```
1	# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://mirror.metrocast.net/ubuntu/ xenial main restricted
     6	# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://mirror.metrocast.net/ubuntu/ xenial-updates main restricted
    11	# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team, and may not be under a free licence. Please satisfy yourself as to
    15	## your rights to use the software. Also, please note that software in
    16	## universe WILL NOT receive any review or updates from the Ubuntu security
    17	## team.
    18	deb http://mirror.metrocast.net/ubuntu/ xenial universe
    19	# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial universe
    20	deb http://mirror.metrocast.net/ubuntu/ xenial-updates universe
    21	# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates universe
    22	
    23	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24	## team, and may not be under a free licence. Please satisfy yourself as to 
    25	## your rights to use the software. Also, please note that software in 
    26	## multiverse WILL NOT receive any review or updates from the Ubuntu
    27	## security team.
    28	deb http://mirror.metrocast.net/ubuntu/ xenial multiverse
    29	# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial multiverse
    30	deb http://mirror.metrocast.net/ubuntu/ xenial-updates multiverse
    31	# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    32	
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	deb http://mirror.metrocast.net/ubuntu/ xenial-backports main universe multiverse restricted
    39	# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	# deb http://archive.canonical.com/ubuntu xenial partner
    46	# deb-src http://archive.canonical.com/ubuntu xenial partner
    47	
    48	deb http://mirror.metrocast.net/ubuntu/ xenial-security main restricted
    49	# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    50	deb http://mirror.metrocast.net/ubuntu/ xenial-security universe
    51	# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    52	deb http://mirror.metrocast.net/ubuntu/ xenial-security multiverse
    53	# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse



```



Output for [COLOR=#000000][FONT=Ubuntu Mono]tail -v -n +1 /etc/apt/sources.list.d/*

```
[/FONT][/COLOR]==> /etc/apt/sources.list.d/google-chrome.list <==### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
#deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.


==> /etc/apt/sources.list.d/steam.list <==


==> /etc/apt/sources.list.d/steam.list.save <==


[COLOR=#000000][FONT=Ubuntu Mono]
```[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-05-14
Amit_Mishra; Hey ....

All looks  proper to me; except there is :
> 
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3


what results:
```

sudo apt remove libc6-dev-amd64

```
 And now get a new status:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

See where we go from here .

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by Amit_Mishra on 2016-05-14
hey there..
output for [COLOR=#000000][FONT=Ubuntu Mono]sudo apt remove libc6-dev-amd64

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]```
[/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


[COLOR=#000000][FONT=Ubuntu Mono]
```

every time i try to install something i get this same error.[/FONT][/COLOR]

---

### Post by Amit_Mishra on 2016-05-14
output for sudo apt update

```
Hit:1 http://mirror.metrocast.net/ubuntu xenial InReleaseGet:2 http://mirror.metrocast.net/ubuntu xenial-updates InRelease [94.5 kB]    
Hit:3 http://mirror.metrocast.net/ubuntu xenial-backports InRelease            
Get:4 http://mirror.metrocast.net/ubuntu xenial-security InRelease [93.3 kB]   
Get:5 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 Packages [85.5 kB]
Get:6 http://mirror.metrocast.net/ubuntu xenial-updates/main i386 Packages [83.1 kB]
Get:7 http://mirror.metrocast.net/ubuntu xenial-updates/universe amd64 Packages [26.1 kB]
Get:8 http://mirror.metrocast.net/ubuntu xenial-updates/universe i386 Packages [26.2 kB]
Fetched 409 kB in 7s (55.6 kB/s)                                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.



```

outpt for apt list --upgradeable

```
Listing... Doneaccountsservice/xenial-updates 0.6.40-2ubuntu11 amd64 [upgradable from: 0.6.40-2ubuntu10]
dpkg/xenial-updates 1.18.4ubuntu1.1 amd64 [upgradable from: 1.18.4ubuntu1]
file-roller/xenial-updates 3.16.5-0ubuntu1 amd64 [upgradable from: 3.16.4-1ubuntu3]
fwupd/xenial-updates 0.7.0-0ubuntu4.1 amd64 [upgradable from: 0.7.0-0ubuntu4]
libaccountsservice0/xenial-updates 0.6.40-2ubuntu11 amd64 [upgradable from: 0.6.40-2ubuntu10]
libdfu1/xenial-updates 0.7.0-0ubuntu4.1 amd64 [upgradable from: 0.7.0-0ubuntu4]
libdpkg-perl/xenial-updates,xenial-updates 1.18.4ubuntu1.1 all [upgradable from: 1.18.4ubuntu1]
libfwupd1/xenial-updates 0.7.0-0ubuntu4.1 amd64 [upgradable from: 0.7.0-0ubuntu4]
libnm-gtk-common/xenial-updates,xenial-updates 1.2.0-0ubuntu0.16.04.1 all [upgradable from: 1.1.93-1ubuntu1]
libnm-gtk0/xenial-updates 1.2.0-0ubuntu0.16.04.1 amd64 [upgradable from: 1.1.93-1ubuntu1]
libnma-common/xenial-updates,xenial-updates 1.2.0-0ubuntu0.16.04.1 all [upgradable from: 1.1.93-1ubuntu1]
libnma0/xenial-updates 1.2.0-0ubuntu0.16.04.1 amd64 [upgradable from: 1.1.93-1ubuntu1]
libpam-systemd/xenial-updates 229-4ubuntu5 amd64 [upgradable from: 229-4ubuntu4]
libplymouth4/xenial-updates 0.9.2-3ubuntu13.1 amd64 [upgradable from: 0.9.2-3ubuntu13]
libsystemd0/xenial-updates 229-4ubuntu5 amd64 [upgradable from: 229-4ubuntu4]
libudev1/xenial-updates 229-4ubuntu5 amd64 [upgradable from: 229-4ubuntu4]
network-manager-gnome/xenial-updates 1.2.0-0ubuntu0.16.04.1 amd64 [upgradable from: 1.1.93-1ubuntu1]
plymouth/xenial-updates 0.9.2-3ubuntu13.1 amd64 [upgradable from: 0.9.2-3ubuntu13]
plymouth-label/xenial-updates 0.9.2-3ubuntu13.1 amd64 [upgradable from: 0.9.2-3ubuntu13]
plymouth-theme-ubuntu-logo/xenial-updates 0.9.2-3ubuntu13.1 amd64 [upgradable from: 0.9.2-3ubuntu13]
plymouth-theme-ubuntu-text/xenial-updates 0.9.2-3ubuntu13.1 amd64 [upgradable from: 0.9.2-3ubuntu13]
snapd/xenial-updates 2.0.3 amd64 [upgradable from: 2.0.2]
sudo/xenial-updates 1.8.16-0ubuntu1.1 amd64 [upgradable from: 1.8.16-0ubuntu1]
systemd/xenial-updates 229-4ubuntu5 amd64 [upgradable from: 229-4ubuntu4]
systemd-sysv/xenial-updates 229-4ubuntu5 amd64 [upgradable from: 229-4ubuntu4]
udev/xenial-updates 229-4ubuntu5 amd64 [upgradable from: 229-4ubuntu4]
```

output for sudo apt upgrade

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.



```

output for sudo apt -f install

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  diffstat fakeroot gettext intltool-debian libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl libarchive-zip-perl libasprintf-dev libclone-perl libdata-alias-perl
  libemail-valid-perl libexporter-tiny-perl libfakeroot libgettextpo-dev libgettextpo0 libio-pty-perl libipc-run-perl liblist-moreutils-perl libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl
  libperlio-gzip-perl libstdc++-5-dev libtext-levenshtein-perl libyaml-libyaml-perl patchutils t1utils
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,265 kB of archives.
After this operation, 6,940 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 240564 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

output for sudo dpkg -C

```
The following packages have been unpacked but not yet configured.They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 gcc-5-multilib       GNU C compiler (multilib support)
 gcc-multilib         GNU C compiler (multilib files)
 libc6-dev-x32        GNU C Library: X32 ABI Development Libraries for AMD64
```


if this could help.!

---

### Post by Bashing-om on 2016-05-14
Amit_Mishra; Welo ....

I really do not understand why there is a conflict;
look at :
[http://packages.ubuntu.com/xenial/gcc-5-multilib](http://packages.ubuntu.com/xenial/gcc-5-multilib)
it has as dependencies both:
libc6-dev-amd64 (>= 2.11) [i386]
libc6-dev-i386 (>= 2.11) [amd64]

Let's work on getting the package manager consistent, and the system fully updated.


What results now:
```

sudo apt remove gcc-5-multilib
sudo apt update
sudo apt full-upgrade

```
then see what it will take to install the C compiler .

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Amit_Mishra on 2016-05-14
output for [COLOR=#000000][FONT=Ubuntu Mono]sudo apt remove gcc-5-multilib

```
[/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-multilib : Depends: gcc-5-multilib (>= 5.3.1-3~) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


[COLOR=#000000][FONT=Ubuntu Mono]
```

output for sudo apt update

```
[/FONT][/COLOR]Hit:1 http://mirror.metrocast.net/ubuntu xenial InReleaseGet:2 http://mirror.metrocast.net/ubuntu xenial-updates InRelease [94.5 kB]    
Hit:3 http://mirror.metrocast.net/ubuntu xenial-backports InRelease            
Get:4 http://mirror.metrocast.net/ubuntu xenial-security InRelease [93.3 kB]   
Get:5 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 Packages [85.5 kB]
Get:6 http://mirror.metrocast.net/ubuntu xenial-updates/main i386 Packages [83.1 kB]
Get:7 http://mirror.metrocast.net/ubuntu xenial-updates/universe amd64 Packages [26.1 kB]
Get:8 http://mirror.metrocast.net/ubuntu xenial-updates/universe i386 Packages [26.2 kB]
Fetched 409 kB in 8s (51.1 kB/s)                                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.


[COLOR=#000000][FONT=Ubuntu Mono]
```

output for sudo apt full-upgrade

```
[/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.


[COLOR=#000000][FONT=Ubuntu Mono]
```
[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-05-14
Amit_Mishra; Ouch !

Let's try:
```

sudo apt remove gcc-5-multilib gcc-multilib 

```

get it straight what gets removed first in this dependency tree. Attempting to get the package manager in a consistent state .

[INDENT][INDENT]if at 1st you do not succeed 
[INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-05-14
I get there must be a conflict between these two packages. Are both required for your application?

libc6-dev-i386
GNU C Library: 32-bit development libraries for AMD64
libc6-dev-amd64:i386
GNU C Library: 64bit Development Libraries for AMD64

I would try to install one or the other, which ever makes the most sense.

---

### Post by Bashing-om on 2016-05-14
@oldfred; Yuk !

I am confused .

When we look at Package: gcc-5-multilib : ( that the OP is trying to install )
[http://packages.ubuntu.com/xenial/gcc-5-multilib](http://packages.ubuntu.com/xenial/gcc-5-multilib)
we see that both:
libc6-dev-amd64 (>= 2.11) [i386]
libc6-dev-i386 (>= 2.11) [amd64]
are required as dependencies . 

But yet the package manager says they are mutually exclusive.

Presently I am stonewalled by my ignorance.

[INDENT][INDENT]short on smarts
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-05-14
> **Bashing-om said:**
> @oldfred; Yuk !

I am confused .

When we look at Package: gcc-5-multilib : ( that the OP is trying to install )
[http://packages.ubuntu.com/xenial/gcc-5-multilib](http://packages.ubuntu.com/xenial/gcc-5-multilib)
we see that both:
libc6-dev-amd64 (>= 2.11) [i386]
libc6-dev-i386 (>= 2.11) [amd64]
are required as dependencies . 

But yet the package manager says they are mutually exclusive.

Presently I am stonewalled by my ignorance.
[INDENT][INDENT]short on smarts
[/INDENT]
[/INDENT]

Your not alone Old Friend.:)
[http://ubuntuforums.org/showthread.php?t=2323409](http://ubuntuforums.org/showthread.php?t=2323409)

[http://ubuntuforums.org/showthread.php?t=2322216](http://ubuntuforums.org/showthread.php?t=2322216)

---

### Post by Bashing-om on 2016-05-14
@runrickus ; Yikes !

Do we have a plague on our hands ..

Where then is CDC ?

Should we get say ian-weisser - the guru of package management - involved ?

[INDENT][INDENT]who ya gonna call ?
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-05-14
> **Bashing-om said:**
> @runrickus ; Yikes !

Do we have a plague on our hands ..

Where then is CDC ?

Should we get say ian-weisser - the guru of package management - involved ?[INDENT][INDENT]who ya gonna call ?
[/INDENT]
[/INDENT]

ian-weisser is who I was hoping would come in here but....
Anyway I think a word of caution should be made here when installing steam from their site on Xenial only.
I actually went in to /var/lib/dpkg and hand deleted those two .debs witch left me with a broken OS.
So maybe a confirmation from ian-weisser would help.:confused:

---

### Post by Amit_Mishra on 2016-05-15
> **Bashing-om said:**
> Amit_Mishra; Ouch !

Let's try:
```

sudo apt remove gcc-5-multilib gcc-multilib 

```

get it straight what gets removed first in this dependency tree. Attempting to get the package manager in a consistent state .[INDENT][INDENT]if at 1st you do not succeed[INDENT][INDENT]try something else
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



otput for sudo apt remove gcc-5-multilib gcc-multilib

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```


AGAIN..!! :confused:

---

### Post by Bashing-om on 2016-05-15
Amit_Mishra; K:

Let us back up one more step.
```

sudo apt remove libc6-dev-x32

```

As we work to get to the bottom of this.

[INDENT]then
[INDENT][INDENT]work our way back up
[/INDENT][/INDENT][/INDENT]

---

### Post by Amit_Mishra on 2016-05-15
output for [COLOR=#000000][FONT=Ubuntu Mono]sudo apt remove libc6-dev-x32

```
[/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
                  Depends: libc6-dev-x32 (>= 2.11) but it is not going to be installed

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[COLOR=#000000][FONT=Ubuntu Mono]
```[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-05-15
Amit_Mishra; K; Maybe !

What now :
```

sudo apt remove gcc-5-multilib

```

See if the package manager will now cooperate .

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by Amit_Mishra on 2016-05-15
> **Bashing-om said:**
> Amit_Mishra; K; Maybe !

What now :
```

sudo apt remove gcc-5-multilib

```

See if the package manager will now cooperate .
[INDENT][INDENT]maybe yes ?
[/INDENT]
[/INDENT]



output for [COLOR=#000000][FONT=Ubuntu Mono]sudo apt remove gcc-5-multilib

```
[/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-multilib : Depends: gcc-5-multilib (>= 5.3.1-3~) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


[COLOR=#000000][FONT=Ubuntu Mono]
```    
[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-05-16
Amit_Mishra; Why, OH why ....

We are not seeing something, somewhere .

OK:
```

sudo apt remove libc6-dev-i386 libc6-dev-x32 gcc-5-multilib gcc-multilib

```

If and when this too fails .. I guess we best look at the dependencies as per:
apt show gcc-multilib
> 
Replaces: gcc (<< 4.6.1-2ubuntu5)
Depends: cpp (>= 4:4.8.2-1ubuntu6), gcc (>= 4:4.8.2-1ubuntu6), gcc-4.8-multilib (>= 4.8.2-5~), linux-libc-dev (>= 3.0.0-2)
Pre-Depends: linux-libc-dev (>= 2.6.38-8.42)


seeking to know the why and
[INDENT][INDENT]what the stoppage may be
[/INDENT][/INDENT]

---

### Post by miguel62 on 2016-05-16
i am stuck with this same problem, but mine started after updating to 14.04. I have a black login screen, but regardless of the command i enter i am left with the same unmet dependencies issues. I am happy to know i am not alone, but hopefully someone will be able to help us

---

### Post by Amit_Mishra on 2016-05-17
output for sudo apt remove libc6-dev-i386 libc6-dev-x32 gcc-5-multilib gcc-multilib

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package 'libc6-dev-i386' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  diffstat fakeroot gettext intltool-debian libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libclone-perl libdata-alias-perl
  libemail-valid-perl libexporter-tiny-perl libfakeroot libgettextpo-dev
  libgettextpo0 libio-pty-perl libipc-run-perl liblist-moreutils-perl
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libperlio-gzip-perl
  libstdc++-5-dev libtext-levenshtein-perl libyaml-libyaml-perl patchutils
  t1utils
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  gcc-5-multilib gcc-multilib libc6-dev-x32
0 upgraded, 0 newly installed, 3 to remove and 32 not upgraded.
3 not fully installed or removed.
After this operation, 8,246 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 240563 files and directories currently installed.)
Removing gcc-multilib (4:5.3.1-1ubuntu1) ...
Removing gcc-5-multilib (5.3.1-14ubuntu2) ...
Removing libc6-dev-x32 (2.23-0ubuntu3) ...



```

output for apt show gcc-multilib

```
Package: gcc-multilibVersion: 4:5.3.1-1ubuntu1
Priority: optional
Section: devel
Source: gcc-defaults (1.150ubuntu1)
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 8,192 B
Depends: cpp (>= 4:5.3.1-1ubuntu1), gcc (>= 4:5.3.1-1ubuntu1), gcc-5-multilib (>= 5.3.1-3~), linux-libc-dev (>= 3.0.0-2)
Conflicts: gcc-4.9-aarch64-linux-gnu, gcc-4.9-alpha-linux-gnu, gcc-4.9-arm-linux-gnueabi, gcc-4.9-arm-linux-gnueabihf, gcc-4.9-hppa-linux-gnu, gcc-4.9-m68k-linux-gnu, gcc-4.9-mips-linux-gnu, gcc-4.9-mips64-linux-gnuabi64, gcc-4.9-mips64el-linux-gnuabi64, gcc-4.9-mipsel-linux-gnu, gcc-4.9-powerpc-linux-gnu, gcc-4.9-powerpc-linux-gnuspe, gcc-4.9-powerpc64-linux-gnu, gcc-4.9-powerpc64le-linux-gnu, gcc-4.9-s390x-linux-gnu, gcc-4.9-sh4-linux-gnu, gcc-4.9-sparc-linux-gnu, gcc-4.9-sparc64-linux-gnu, gcc-5-aarch64-linux-gnu, gcc-5-alpha-linux-gnu, gcc-5-arm-linux-gnueabi, gcc-5-arm-linux-gnueabihf, gcc-5-hppa-linux-gnu, gcc-5-m68k-linux-gnu, gcc-5-mips-linux-gnu, gcc-5-mips64-linux-gnuabi64, gcc-5-mips64el-linux-gnuabi64, gcc-5-mipsel-linux-gnu, gcc-5-powerpc-linux-gnu, gcc-5-powerpc-linux-gnuspe, gcc-5-powerpc64-linux-gnu, gcc-5-powerpc64le-linux-gnu, gcc-5-s390x-linux-gnu, gcc-5-sh4-linux-gnu, gcc-5-sparc-linux-gnu, gcc-5-sparc64-linux-gnu, gcc-6-aarch64-linux-gnu, gcc-6-alpha-linux-gnu, gcc-6-arm-linux-gnueabi, gcc-6-arm-linux-gnueabihf, gcc-6-hppa-linux-gnu, gcc-6-m68k-linux-gnu, gcc-6-mips-linux-gnu, gcc-6-mips64-linux-gnuabi64, gcc-6-mips64el-linux-gnuabi64, gcc-6-mipsel-linux-gnu, gcc-6-powerpc-linux-gnu, gcc-6-powerpc-linux-gnuspe, gcc-6-powerpc64-linux-gnu, gcc-6-powerpc64le-linux-gnu, gcc-6-s390x-linux-gnu, gcc-6-sh4-linux-gnu, gcc-6-sparc-linux-gnu, gcc-6-sparc64-linux-gnu
Supported: 5y
Download-Size: 1,212 B
APT-Sources: http://mirror.metrocast.net/ubuntu xenial/main amd64 Packages
Description: GNU C compiler (multilib files)
 This is the GNU C compiler, a fairly portable optimizing compiler for C.
 .
 A dependency package on architectures with multilib support; the package
 contains dependencies for the non-default multilib architecture(s).
```

---

### Post by QLee on 2016-05-17
> **Bashing-om said:**
> 
We are not seeing something, somewhere .

seeking to know the why and
[INDENT][INDENT]what the stoppage may be
[/INDENT][/INDENT]

Perhaps a fresh set of eyes on the problem can find something missed.

Back in post 7

> Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3


There are at least 2 unclosed bugs about it going back as far as 14.04.

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1365375](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1365375)

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1408173](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1408173)

The posters in those also ended up in what usually is termed "dependency hell".

---

### Post by QDR06VV9 on 2016-05-17
I was able to finally get somewhere with the "dependency-hell" with this method.
As root "sudo"
```
dpkg --purge --force-depends "gcc-multilib"
dpkg --purge --force-depends "lib32z1-dev"
dpkg --purge --force-depends "libc6-dev-x32"
```

Now, I'm able to use "apt" or the package manager as expected.
Hope this works here also.
Kind regards

---

### Post by Bashing-om on 2016-05-17
et al ; Wow !

Post #39 looks like the removal took ! Maybe we can put the force "purge" back in our back pocket .

@ QLee; As always your input and advise is a treasure .. sure to be heeded .

@ Amit_Mishra ; What now :
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

depending, we see what is to be restored .

[INDENT][INDENT]who wudda thunk it
[/INDENT][/INDENT]

---

### Post by QLee on 2016-05-18
> **Bashing-om said:**
> et al ; Wow !

When we work together we (forum posters) are awesome.  

It is like we are standing in the same virtual room and can make comments when we think of something that might help.

---

### Post by Amit_Mishra on 2016-05-18
> **runrickus said:**
> I was able to finally get somewhere with the "dependency-hell" with this method.
As root "sudo"
```
dpkg --purge --force-depends "gcc-multilib"
dpkg --purge --force-depends "lib32z1-dev"
dpkg --purge --force-depends "libc6-dev-x32"
```

Now, I'm able to use "apt" or the package manager as expected.
Hope this works here also.
Kind regards


output for dpkg --purge --force-depends "gcc-multilib"

```
dpkg: warning: ignoring request to remove gcc-multilib which isn't installed
```

output for dpkg --purge --force-depends "lib32z1-dev"

```
dpkg: warning: ignoring request to remove lib32z1-dev which isn't installed
```

output for dpkg --purge --force-depends "libc6-dev-x32"

```
dpkg: warning: ignoring request to remove libc6-dev-x32 which isn't installed
```

---

### Post by Amit_Mishra on 2016-05-18
> **Bashing-om said:**
> et al ; Wow !

Post #39 looks like the removal took ! Maybe we can put the force "purge" back in our back pocket .

@ QLee; As always your input and advise is a treasure .. sure to be heeded .

@ Amit_Mishra ; What now :
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

depending, we see what is to be restored .
[INDENT][INDENT]who wudda thunk it
[/INDENT]
[/INDENT]


output for sudo apt update

```
Hit:1 http://mirror.metrocast.net/ubuntu xenial InReleaseGet:2 http://mirror.metrocast.net/ubuntu xenial-updates InRelease [94.5 kB]    
Hit:3 http://mirror.metrocast.net/ubuntu xenial-backports InRelease            
Get:4 http://mirror.metrocast.net/ubuntu xenial-security InRelease [93.3 kB]   
Get:5 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 Packages [87.3 kB]
Get:6 http://mirror.metrocast.net/ubuntu xenial-updates/main i386 Packages [85.1 kB]
Get:7 http://mirror.metrocast.net/ubuntu xenial-updates/main Translation-en [35.7 kB]
Get:8 http://mirror.metrocast.net/ubuntu xenial-updates/universe amd64 Packages [26.8 kB]
Get:9 http://mirror.metrocast.net/ubuntu xenial-updates/universe i386 Packages [26.9 kB]
Get:10 http://mirror.metrocast.net/ubuntu xenial-updates/universe Translation-en [16.4 kB]
Get:11 http://mirror.metrocast.net/ubuntu xenial-security/main amd64 Packages [52.6 kB]
Get:12 http://mirror.metrocast.net/ubuntu xenial-security/main i386 Packages [50.7 kB]
Get:13 http://mirror.metrocast.net/ubuntu xenial-security/main Translation-en [20.6 kB]
Get:14 http://mirror.metrocast.net/ubuntu xenial-security/universe amd64 Packages [7,896 B]
Get:15 http://mirror.metrocast.net/ubuntu xenial-security/universe i386 Packages [7,888 B]
Get:16 http://mirror.metrocast.net/ubuntu xenial-security/universe Translation-en [6,708 B]
Fetched 612 kB in 18s (33.1 kB/s)                                              
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
27 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

output for sudo apt full-upgrade

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  diffstat fakeroot gettext intltool-debian lib32asan2 lib32atomic1
  lib32cilkrts5 lib32gcc-5-dev lib32gcc1 lib32gomp1 lib32itm1 lib32mpx0
  lib32quadmath0 lib32stdc++6 lib32ubsan0 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libclone-perl libdata-alias-perl
  libemail-valid-perl libexporter-tiny-perl libfakeroot libgettextpo-dev
  libgettextpo0 libio-pty-perl libipc-run-perl liblist-moreutils-perl
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libperlio-gzip-perl
  libstdc++-5-dev libtext-levenshtein-perl libx32asan2 libx32atomic1
  libx32cilkrts5 libx32gcc-5-dev libx32gcc1 libx32gomp1 libx32itm1
  libx32quadmath0 libx32stdc++6 libx32ubsan0 libyaml-libyaml-perl patchutils
  t1utils
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  accountsservice dpkg file-roller fwupd libaccountsservice0 libdfu1
  libdpkg-perl libexpat1 libfwupd1 libnm-gtk-common libnm-gtk0 libnma-common
  libnma0 libpam-systemd libplymouth4 libsystemd0 libudev1
  network-manager-gnome plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text snapd sudo systemd systemd-sysv udev
27 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.0 MB of archives.
After this operation, 28.7 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 dpkg amd64 1.18.4ubuntu1.1 [2,083 kB]
Get:2 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libsystemd0 amd64 229-4ubuntu5 [208 kB]
Get:3 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libpam-systemd amd64 229-4ubuntu5 [115 kB]
Get:4 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 systemd amd64 229-4ubuntu5 [3,645 kB]
Get:5 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 udev amd64 229-4ubuntu5 [990 kB]
Get:6 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libudev1 amd64 229-4ubuntu5 [57.6 kB]
Get:7 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 systemd-sysv amd64 229-4ubuntu5 [15.0 kB]
Get:8 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libexpat1 amd64 2.1.0-7ubuntu0.16.04.1 [71.2 kB]
Get:9 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 sudo amd64 1.8.16-0ubuntu1.1 [389 kB]
Get:10 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 accountsservice amd64 0.6.40-2ubuntu11.1 [56.2 kB]
Get:11 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libaccountsservice0 amd64 0.6.40-2ubuntu11.1 [67.0 kB]
Get:12 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libplymouth4 amd64 0.9.2-3ubuntu13.1 [85.1 kB]
Get:13 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth-theme-ubuntu-logo amd64 0.9.2-3ubuntu13.1 [22.2 kB]
Get:14 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth-label amd64 0.9.2-3ubuntu13.1 [6,090 B]
Get:15 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth amd64 0.9.2-3ubuntu13.1 [107 kB]
Get:16 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth-theme-ubuntu-text amd64 0.9.2-3ubuntu13.1 [9,078 B]
Get:17 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 file-roller amd64 3.16.5-0ubuntu1 [303 kB]
Get:18 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libdfu1 amd64 0.7.0-0ubuntu4.1 [42.4 kB]
Get:19 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libfwupd1 amd64 0.7.0-0ubuntu4.1 [27.6 kB]
Get:20 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 fwupd amd64 0.7.0-0ubuntu4.1 [86.2 kB]
Get:21 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libdpkg-perl all 1.18.4ubuntu1.1 [195 kB]
Get:22 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnm-gtk0 amd64 1.2.0-0ubuntu0.16.04.1 [70.3 kB]
Get:23 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnm-gtk-common all 1.2.0-0ubuntu0.16.04.1 [5,514 B]
Get:24 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 network-manager-gnome amd64 1.2.0-0ubuntu0.16.04.1 [291 kB]
Get:25 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnma0 amd64 1.2.0-0ubuntu0.16.04.1 [66.3 kB]
Get:26 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnma-common all 1.2.0-0ubuntu0.16.04.1 [5,496 B]
Get:27 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 snapd amd64 2.0.3 [4,012 kB]
Fetched 13.0 MB in 1min 31s (142 kB/s)                                         
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../dpkg_1.18.4ubuntu1.1_amd64.deb ...
Unpacking dpkg (1.18.4ubuntu1.1) over (1.18.4ubuntu1) ...
Setting up dpkg (1.18.4ubuntu1.1) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../libsystemd0_229-4ubuntu5_amd64.deb ...
Unpacking libsystemd0:amd64 (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libsystemd0:amd64 (229-4ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_229-4ubuntu5_amd64.deb ...
Unpacking libpam-systemd:amd64 (229-4ubuntu5) over (229-4ubuntu4) ...
Preparing to unpack .../systemd_229-4ubuntu5_amd64.deb ...
Unpacking systemd (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Setting up systemd (229-4ubuntu5) ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../udev_229-4ubuntu5_amd64.deb ...
Unpacking udev (229-4ubuntu5) over (229-4ubuntu4) ...
Preparing to unpack .../libudev1_229-4ubuntu5_amd64.deb ...
Unpacking libudev1:amd64 (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libudev1:amd64 (229-4ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_229-4ubuntu5_amd64.deb ...
Unpacking systemd-sysv (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd-sysv (229-4ubuntu5) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../libexpat1_2.1.0-7ubuntu0.16.04.1_amd64.deb ...
Unpacking libexpat1:amd64 (2.1.0-7ubuntu0.16.04.1) over (2.1.0-7) ...
Preparing to unpack .../sudo_1.8.16-0ubuntu1.1_amd64.deb ...
Unpacking sudo (1.8.16-0ubuntu1.1) over (1.8.16-0ubuntu1) ...
Preparing to unpack .../accountsservice_0.6.40-2ubuntu11.1_amd64.deb ...
Unpacking accountsservice (0.6.40-2ubuntu11.1) over (0.6.40-2ubuntu10) ...
Preparing to unpack .../libaccountsservice0_0.6.40-2ubuntu11.1_amd64.deb ...
Unpacking libaccountsservice0:amd64 (0.6.40-2ubuntu11.1) over (0.6.40-2ubuntu10) ...
Preparing to unpack .../libplymouth4_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking libplymouth4:amd64 (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-theme-ubuntu-logo_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth-theme-ubuntu-logo (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-label_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth-label (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-theme-ubuntu-text_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../file-roller_3.16.5-0ubuntu1_amd64.deb ...
Unpacking file-roller (3.16.5-0ubuntu1) over (3.16.4-1ubuntu3) ...
Preparing to unpack .../libdfu1_0.7.0-0ubuntu4.1_amd64.deb ...
Unpacking libdfu1:amd64 (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../libfwupd1_0.7.0-0ubuntu4.1_amd64.deb ...
Unpacking libfwupd1:amd64 (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../fwupd_0.7.0-0ubuntu4.1_amd64.deb ...
Unpacking fwupd (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../libdpkg-perl_1.18.4ubuntu1.1_all.deb ...
Unpacking libdpkg-perl (1.18.4ubuntu1.1) over (1.18.4ubuntu1) ...
Preparing to unpack .../libnm-gtk0_1.2.0-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libnm-gtk0:amd64 (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnm-gtk-common_1.2.0-0ubuntu0.16.04.1_all.deb ...
Unpacking libnm-gtk-common (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../network-manager-gnome_1.2.0-0ubuntu0.16.04.1_amd64.deb ...
Unpacking network-manager-gnome (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma0_1.2.0-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libnma0:amd64 (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma-common_1.2.0-0ubuntu0.16.04.1_all.deb ...
Unpacking libnma-common (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../archives/snapd_2.0.3_amd64.deb ...
Unpacking snapd (2.0.3) over (2.0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:amd64 (2.48.0-1ubuntu4) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libpam-systemd:amd64 (229-4ubuntu5) ...
Setting up udev (229-4ubuntu5) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
Setting up libexpat1:amd64 (2.1.0-7ubuntu0.16.04.1) ...
Setting up sudo (1.8.16-0ubuntu1.1) ...
Setting up libaccountsservice0:amd64 (0.6.40-2ubuntu11.1) ...
Setting up accountsservice (0.6.40-2ubuntu11.1) ...
Setting up libplymouth4:amd64 (0.9.2-3ubuntu13.1) ...
Setting up plymouth (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up plymouth-label (0.9.2-3ubuntu13.1) ...
Setting up plymouth-theme-ubuntu-logo (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up file-roller (3.16.5-0ubuntu1) ...
Setting up libdfu1:amd64 (0.7.0-0ubuntu4.1) ...
Setting up libfwupd1:amd64 (0.7.0-0ubuntu4.1) ...
Setting up fwupd (0.7.0-0ubuntu4.1) ...
Setting up libdpkg-perl (1.18.4ubuntu1.1) ...
Setting up libnm-gtk-common (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnm-gtk0:amd64 (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnma-common (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnma0:amd64 (1.2.0-0ubuntu0.16.04.1) ...
Setting up network-manager-gnome (1.2.0-0ubuntu0.16.04.1) ...
Setting up snapd (2.0.3) ...
Installing new version of config file /etc/profile.d/apps-bin-path.sh ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for initramfs-tools (0.122ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
Processing triggers for libc-bin (2.23-0ubuntu3) ...
```

output for sudo apt -f install

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  diffstat fakeroot gettext intltool-debian lib32asan2 lib32atomic1
  lib32cilkrts5 lib32gcc-5-dev lib32gcc1 lib32gomp1 lib32itm1 lib32mpx0
  lib32quadmath0 lib32stdc++6 lib32ubsan0 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libclone-perl libdata-alias-perl
  libemail-valid-perl libexporter-tiny-perl libfakeroot libgettextpo-dev
  libgettextpo0 libio-pty-perl libipc-run-perl liblist-moreutils-perl
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libperlio-gzip-perl
  libstdc++-5-dev libtext-levenshtein-perl libx32asan2 libx32atomic1
  libx32cilkrts5 libx32gcc-5-dev libx32gcc1 libx32gomp1 libx32itm1
  libx32quadmath0 libx32stdc++6 libx32ubsan0 libyaml-libyaml-perl patchutils
  t1utils
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by QDR06VV9 on 2016-05-18
> **Amit_Mishra said:**
> output for sudo apt update

```
Hit:1 http://mirror.metrocast.net/ubuntu xenial InReleaseGet:2 http://mirror.metrocast.net/ubuntu xenial-updates InRelease [94.5 kB]    
Hit:3 http://mirror.metrocast.net/ubuntu xenial-backports InRelease            
Get:4 http://mirror.metrocast.net/ubuntu xenial-security InRelease [93.3 kB]   
Get:5 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 Packages [87.3 kB]
Get:6 http://mirror.metrocast.net/ubuntu xenial-updates/main i386 Packages [85.1 kB]
Get:7 http://mirror.metrocast.net/ubuntu xenial-updates/main Translation-en [35.7 kB]
Get:8 http://mirror.metrocast.net/ubuntu xenial-updates/universe amd64 Packages [26.8 kB]
Get:9 http://mirror.metrocast.net/ubuntu xenial-updates/universe i386 Packages [26.9 kB]
Get:10 http://mirror.metrocast.net/ubuntu xenial-updates/universe Translation-en [16.4 kB]
Get:11 http://mirror.metrocast.net/ubuntu xenial-security/main amd64 Packages [52.6 kB]
Get:12 http://mirror.metrocast.net/ubuntu xenial-security/main i386 Packages [50.7 kB]
Get:13 http://mirror.metrocast.net/ubuntu xenial-security/main Translation-en [20.6 kB]
Get:14 http://mirror.metrocast.net/ubuntu xenial-security/universe amd64 Packages [7,896 B]
Get:15 http://mirror.metrocast.net/ubuntu xenial-security/universe i386 Packages [7,888 B]
Get:16 http://mirror.metrocast.net/ubuntu xenial-security/universe Translation-en [6,708 B]
Fetched 612 kB in 18s (33.1 kB/s)                                              
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
27 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

output for sudo apt full-upgrade

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  diffstat fakeroot gettext intltool-debian lib32asan2 lib32atomic1
  lib32cilkrts5 lib32gcc-5-dev lib32gcc1 lib32gomp1 lib32itm1 lib32mpx0
  lib32quadmath0 lib32stdc++6 lib32ubsan0 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libclone-perl libdata-alias-perl
  libemail-valid-perl libexporter-tiny-perl libfakeroot libgettextpo-dev
  libgettextpo0 libio-pty-perl libipc-run-perl liblist-moreutils-perl
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libperlio-gzip-perl
  libstdc++-5-dev libtext-levenshtein-perl libx32asan2 libx32atomic1
  libx32cilkrts5 libx32gcc-5-dev libx32gcc1 libx32gomp1 libx32itm1
  libx32quadmath0 libx32stdc++6 libx32ubsan0 libyaml-libyaml-perl patchutils
  t1utils
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  accountsservice dpkg file-roller fwupd libaccountsservice0 libdfu1
  libdpkg-perl libexpat1 libfwupd1 libnm-gtk-common libnm-gtk0 libnma-common
  libnma0 libpam-systemd libplymouth4 libsystemd0 libudev1
  network-manager-gnome plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text snapd sudo systemd systemd-sysv udev
27 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.0 MB of archives.
After this operation, 28.7 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 dpkg amd64 1.18.4ubuntu1.1 [2,083 kB]
Get:2 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libsystemd0 amd64 229-4ubuntu5 [208 kB]
Get:3 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libpam-systemd amd64 229-4ubuntu5 [115 kB]
Get:4 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 systemd amd64 229-4ubuntu5 [3,645 kB]
Get:5 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 udev amd64 229-4ubuntu5 [990 kB]
Get:6 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libudev1 amd64 229-4ubuntu5 [57.6 kB]
Get:7 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 systemd-sysv amd64 229-4ubuntu5 [15.0 kB]
Get:8 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libexpat1 amd64 2.1.0-7ubuntu0.16.04.1 [71.2 kB]
Get:9 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 sudo amd64 1.8.16-0ubuntu1.1 [389 kB]
Get:10 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 accountsservice amd64 0.6.40-2ubuntu11.1 [56.2 kB]
Get:11 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libaccountsservice0 amd64 0.6.40-2ubuntu11.1 [67.0 kB]
Get:12 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libplymouth4 amd64 0.9.2-3ubuntu13.1 [85.1 kB]
Get:13 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth-theme-ubuntu-logo amd64 0.9.2-3ubuntu13.1 [22.2 kB]
Get:14 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth-label amd64 0.9.2-3ubuntu13.1 [6,090 B]
Get:15 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth amd64 0.9.2-3ubuntu13.1 [107 kB]
Get:16 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 plymouth-theme-ubuntu-text amd64 0.9.2-3ubuntu13.1 [9,078 B]
Get:17 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 file-roller amd64 3.16.5-0ubuntu1 [303 kB]
Get:18 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libdfu1 amd64 0.7.0-0ubuntu4.1 [42.4 kB]
Get:19 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libfwupd1 amd64 0.7.0-0ubuntu4.1 [27.6 kB]
Get:20 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 fwupd amd64 0.7.0-0ubuntu4.1 [86.2 kB]
Get:21 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libdpkg-perl all 1.18.4ubuntu1.1 [195 kB]
Get:22 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnm-gtk0 amd64 1.2.0-0ubuntu0.16.04.1 [70.3 kB]
Get:23 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnm-gtk-common all 1.2.0-0ubuntu0.16.04.1 [5,514 B]
Get:24 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 network-manager-gnome amd64 1.2.0-0ubuntu0.16.04.1 [291 kB]
Get:25 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnma0 amd64 1.2.0-0ubuntu0.16.04.1 [66.3 kB]
Get:26 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 libnma-common all 1.2.0-0ubuntu0.16.04.1 [5,496 B]
Get:27 http://mirror.metrocast.net/ubuntu xenial-updates/main amd64 snapd amd64 2.0.3 [4,012 kB]
Fetched 13.0 MB in 1min 31s (142 kB/s)                                         
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../dpkg_1.18.4ubuntu1.1_amd64.deb ...
Unpacking dpkg (1.18.4ubuntu1.1) over (1.18.4ubuntu1) ...
Setting up dpkg (1.18.4ubuntu1.1) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../libsystemd0_229-4ubuntu5_amd64.deb ...
Unpacking libsystemd0:amd64 (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libsystemd0:amd64 (229-4ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_229-4ubuntu5_amd64.deb ...
Unpacking libpam-systemd:amd64 (229-4ubuntu5) over (229-4ubuntu4) ...
Preparing to unpack .../systemd_229-4ubuntu5_amd64.deb ...
Unpacking systemd (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Setting up systemd (229-4ubuntu5) ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../udev_229-4ubuntu5_amd64.deb ...
Unpacking udev (229-4ubuntu5) over (229-4ubuntu4) ...
Preparing to unpack .../libudev1_229-4ubuntu5_amd64.deb ...
Unpacking libudev1:amd64 (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libudev1:amd64 (229-4ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_229-4ubuntu5_amd64.deb ...
Unpacking systemd-sysv (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd-sysv (229-4ubuntu5) ...
(Reading database ... 240512 files and directories currently installed.)
Preparing to unpack .../libexpat1_2.1.0-7ubuntu0.16.04.1_amd64.deb ...
Unpacking libexpat1:amd64 (2.1.0-7ubuntu0.16.04.1) over (2.1.0-7) ...
Preparing to unpack .../sudo_1.8.16-0ubuntu1.1_amd64.deb ...
Unpacking sudo (1.8.16-0ubuntu1.1) over (1.8.16-0ubuntu1) ...
Preparing to unpack .../accountsservice_0.6.40-2ubuntu11.1_amd64.deb ...
Unpacking accountsservice (0.6.40-2ubuntu11.1) over (0.6.40-2ubuntu10) ...
Preparing to unpack .../libaccountsservice0_0.6.40-2ubuntu11.1_amd64.deb ...
Unpacking libaccountsservice0:amd64 (0.6.40-2ubuntu11.1) over (0.6.40-2ubuntu10) ...
Preparing to unpack .../libplymouth4_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking libplymouth4:amd64 (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-theme-ubuntu-logo_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth-theme-ubuntu-logo (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-label_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth-label (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-theme-ubuntu-text_0.9.2-3ubuntu13.1_amd64.deb ...
Unpacking plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../file-roller_3.16.5-0ubuntu1_amd64.deb ...
Unpacking file-roller (3.16.5-0ubuntu1) over (3.16.4-1ubuntu3) ...
Preparing to unpack .../libdfu1_0.7.0-0ubuntu4.1_amd64.deb ...
Unpacking libdfu1:amd64 (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../libfwupd1_0.7.0-0ubuntu4.1_amd64.deb ...
Unpacking libfwupd1:amd64 (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../fwupd_0.7.0-0ubuntu4.1_amd64.deb ...
Unpacking fwupd (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../libdpkg-perl_1.18.4ubuntu1.1_all.deb ...
Unpacking libdpkg-perl (1.18.4ubuntu1.1) over (1.18.4ubuntu1) ...
Preparing to unpack .../libnm-gtk0_1.2.0-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libnm-gtk0:amd64 (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnm-gtk-common_1.2.0-0ubuntu0.16.04.1_all.deb ...
Unpacking libnm-gtk-common (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../network-manager-gnome_1.2.0-0ubuntu0.16.04.1_amd64.deb ...
Unpacking network-manager-gnome (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma0_1.2.0-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libnma0:amd64 (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma-common_1.2.0-0ubuntu0.16.04.1_all.deb ...
Unpacking libnma-common (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../archives/snapd_2.0.3_amd64.deb ...
Unpacking snapd (2.0.3) over (2.0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:amd64 (2.48.0-1ubuntu4) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libpam-systemd:amd64 (229-4ubuntu5) ...
Setting up udev (229-4ubuntu5) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
Setting up libexpat1:amd64 (2.1.0-7ubuntu0.16.04.1) ...
Setting up sudo (1.8.16-0ubuntu1.1) ...
Setting up libaccountsservice0:amd64 (0.6.40-2ubuntu11.1) ...
Setting up accountsservice (0.6.40-2ubuntu11.1) ...
Setting up libplymouth4:amd64 (0.9.2-3ubuntu13.1) ...
Setting up plymouth (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up plymouth-label (0.9.2-3ubuntu13.1) ...
Setting up plymouth-theme-ubuntu-logo (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up file-roller (3.16.5-0ubuntu1) ...
Setting up libdfu1:amd64 (0.7.0-0ubuntu4.1) ...
Setting up libfwupd1:amd64 (0.7.0-0ubuntu4.1) ...
Setting up fwupd (0.7.0-0ubuntu4.1) ...
Setting up libdpkg-perl (1.18.4ubuntu1.1) ...
Setting up libnm-gtk-common (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnm-gtk0:amd64 (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnma-common (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnma0:amd64 (1.2.0-0ubuntu0.16.04.1) ...
Setting up network-manager-gnome (1.2.0-0ubuntu0.16.04.1) ...
Setting up snapd (2.0.3) ...
Installing new version of config file /etc/profile.d/apps-bin-path.sh ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for initramfs-tools (0.122ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
Processing triggers for libc-bin (2.23-0ubuntu3) ...
```

output for sudo apt -f install

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  diffstat fakeroot gettext intltool-debian lib32asan2 lib32atomic1
  lib32cilkrts5 lib32gcc-5-dev lib32gcc1 lib32gomp1 lib32itm1 lib32mpx0
  lib32quadmath0 lib32stdc++6 lib32ubsan0 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libclone-perl libdata-alias-perl
  libemail-valid-perl libexporter-tiny-perl libfakeroot libgettextpo-dev
  libgettextpo0 libio-pty-perl libipc-run-perl liblist-moreutils-perl
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libperlio-gzip-perl
  libstdc++-5-dev libtext-levenshtein-perl libx32asan2 libx32atomic1
  libx32cilkrts5 libx32gcc-5-dev libx32gcc1 libx32gomp1 libx32itm1
  libx32quadmath0 libx32stdc++6 libx32ubsan0 libyaml-libyaml-perl patchutils
  t1utils
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Hey that is good news:D.
I had to use the big hammer on my test's....but you look like you escaped in fine fashion.
Nice and good job to you and our old friend Bashing-om.:KS
Best Regards

---

### Post by Bashing-om on 2016-05-18
Amit_Mishra; Uh Huh !

Looks like we have a stable system, and the package manager in a happy state.

So, what do you want now to restore ? At this point in installing development packages, we move slowly and look before we leap.

I say again
[INDENT][INDENT]'buntu, together we can
[/INDENT][/INDENT]

---

### Post by Amit_Mishra on 2016-05-19
I dunno what in the process solved the problem but now i`m able to install the programs.
i wasnt able to install any program because of unmet dependencies, but now its working fine.:D
Thanks a lot guys!

---

### Post by Bashing-om on 2016-05-19
Amit_Mishra; Great !

I can not tell you the why, as I do not know for sure what takes place in "kernel space" .
Just sometimes Ya got to give the package manager all the info in one wack - IN the proper order of operations; such that the package manager will proceed from point A to point D .

As you are now happy happy happy, and the system is stable:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-05-19
Marking this as Solved and nice work Bashing-om:D
@Amit_Mishra if this is not Solved.... please just post back here.
Best Regards

---

