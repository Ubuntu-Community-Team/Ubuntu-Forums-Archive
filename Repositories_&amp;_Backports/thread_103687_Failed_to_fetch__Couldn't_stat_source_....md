---
title: "Failed to fetch / Couldn't stat source ..."
date: 2005-12-14
forum: Repositories &amp; Backports
---

### Post by Smaskens on 2005-12-14
I have a strange problem when updating my system with apt-get. For example xine-ui installation fails always even I tried many different sources.lists from this forum. 

**Xine-ui**

```

$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package xine-ui has no installation candidate
$

```

**sudo apt-get update**

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

**My sources.list**
```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

```

---

### Post by NotJustANewbie on 2005-12-14
I see you're using Ubuntu. Instead of xine-ui, try gxine (GUI for xine under Gnome)

---

### Post by moidib on 2005-12-14
I'm getting the same thing.

---

### Post by Smaskens on 2005-12-15
[QUOTE=NotJustANewbie]I see you're using Ubuntu. Instead of xine-ui, try gxine (GUI for xine under Gnome)[/QUOTE]

Thanks for answer, but there are still problem with repository.

Ubuntu_demon's source.list have been under test, but still there are some fetch failures (see second code sentence). 

Ubuntu_Demons recommended sources.list is here with instructions, it should be quite reliable.
[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

**sudo apt-get update ; sudo apt-get upgrade**
```

Fetched 6B in 32s (0B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

I tried Automatix, which should solve most of the noob problems but it caused a probably the lock problem which is now solved.
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

**FIXED: gxine installation fails due of lock problem**
```

$ sudo apt-get gxine
E: Invalid operation gxine
$ sudo apt-get install gxine
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Lock problem fixed with following commands (hopefully correct):
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

**gxine installation fails due of "Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages  **
```

:/var/lib/dpkg$ sudo apt-get gxine
E: Invalid operation gxine
:/var/lib/dpkg$ sudo apt-get install gxine
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gxine

```

---

### Post by Smaskens on 2005-12-18
This drives me nuts, sources.list is in order but the problem still exists. I have been trying to solve this problem now for a week every day. What is the root reason?

**Problem**
```

$ sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://security.ubuntu.com breezy-security/main Packages
Ign http://packages.freecontrib.org breezy Release.gpg
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Ign http://packages.freecontrib.org breezy Release
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Ign http://packages.freecontrib.org breezy/free Packages
Ign http://packages.freecontrib.org breezy/non-free Packages
Ign http://packages.freecontrib.org breezy/free Sources
Ign http://packages.freecontrib.org breezy/non-free Sources
Hit http://packages.freecontrib.org breezy/free Packages
Hit http://packages.freecontrib.org breezy/non-free Packages
Hit http://packages.freecontrib.org breezy/free Sources
Hit http://packages.freecontrib.org breezy/non-free Sources
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://archive.ubuntu.com breezy-backports Release
Ign http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Get:5 http://archive.ubuntu.com breezy/main Packages [769kB]
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 4s (1B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
$

```

**sources.list**
```

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

```

---

### Post by Smaskens on 2005-12-18
Pff, this was a hard one to solve! Probably the root reason was faulty file at /var/lib/apt/lists/partial folder. However solution was to remove all the files from these two folders and then just do the normal apt-get stuff.

cd /var/lib/apt/lists
sudo rm * -f
cd partial
sudo rm * -f
sudo apt-get update

---

### Post by mEtho on 2005-12-18
hello Ubuntu community!!!

i am really glad to see that somebody was able to solve this nightmare!!!! but unfortuntaly i am still suffering from it!!! i followed your guide i.e. deleting the files /var/lib/apt/lists and partial but the thing is that i still get the error messages and also i cant download any sort of software i get the error messeges that you were getting. i posted it below so you can understand better!!!!!

> W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
root@ubuntu:/# cd /var/lib/apt/lists/
root@ubuntu:/var/lib/apt/lists# ls -l
total 17688
-rw-r--r--  1 root root  3943645 2005-11-23 21:29 ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
-rw-r--r--  1 root root  1338839 2005-11-23 21:05 ca.archive.ubuntu.com_ubuntu_dists_breezy_main_source_Sources
-rw-r--r--  1 root root    30892 2005-11-23 21:38 ca.archive.ubuntu.com_ubuntu_dists_breezy_Release
-rw-r--r--  1 root root      189 2005-11-23 21:38 ca.archive.ubuntu.com_ubuntu_dists_breezy_Release.gpg
-rw-r--r--  1 root root    31521 2005-10-24 21:09 ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages
-rw-r--r--  1 root root     5287 2005-10-24 21:17 ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_source_Sources
-rw-r--r--  1 root root 12203111 2005-11-23 21:04 ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages
-rw-r--r--  1 root root   107031 2005-11-24 00:06 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages
-rw-r--r--  1 root root    14857 2005-11-23 23:40 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_source_Sources
-rw-r--r--  1 root root    19617 2005-12-18 18:40 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_Release
-rw-r--r--  1 root root      189 2005-12-18 18:40 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_Release.gpg
-rw-r--r--  1 root root        0 2005-11-20 21:51 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages
-rw-r--r--  1 root root        0 2005-11-20 21:51 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_source_Sources
-rw-r-----  1 root root        0 2005-12-19 11:59 lock
drwxr-xr-x  2 root root     4096 2005-12-19 11:57 partial
-rw-r--r--  1 root root   139250 2005-12-16 13:06 security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages
-rw-r--r--  1 root root    29368 2005-12-16 13:09 security.ubuntu.com_ubuntu_dists_breezy-security_main_source_Sources
-rw-r--r--  1 root root    19627 2005-12-18 23:40 security.ubuntu.com_ubuntu_dists_breezy-security_Release
-rw-r--r--  1 root root      189 2005-12-18 23:40 security.ubuntu.com_ubuntu_dists_breezy-security_Release.gpg
-rw-r--r--  1 root root    29348 2005-11-23 21:48 security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages
-rw-r--r--  1 root root     3802 2005-11-22 12:30 security.ubuntu.com_ubuntu_dists_breezy-security_restricted_source_Sources
-rw-r--r--  1 root root   104747 2005-12-13 17:03 security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages
-rw-r--r--  1 root root     8587 2005-12-13 17:04 security.ubuntu.com_ubuntu_dists_breezy-security_universe_source_Sources
root@ubuntu:/var/lib/apt/lists# rm * -f
rm: cannot remove `partial': Is a directory
root@ubuntu:/var/lib/apt/lists# rm ca.archive.ubuntu.com_ubuntu_dists_breezy_main-i386_packages
rm: cannot remove `ca.archive.ubuntu.com_ubuntu_dists_breezy_main-i386_packages': No such file or directory
root@ubuntu:/var/lib/apt/lists# rm /var/lib/dpkg/lock
root@ubuntu:/var/lib/apt/lists# dpkg --configure -a
root@ubuntu:/var/lib/apt/lists# cp -a partial /home/metho/Desktop/partial2
root@ubuntu:/var/lib/apt/lists# rmdir partial/
rmdir: `partial/': Directory not empty
root@ubuntu:/var/lib/apt/lists# cd partial/
root@ubuntu:/var/lib/apt/lists/partial# rm * -f
root@ubuntu:/var/lib/apt/lists/partial# ls -l
total 0
root@ubuntu:/var/lib/apt/lists/partial# cd ..
root@ubuntu:/var/lib/apt/lists# ls -l
total 4
drwxr-xr-x  2 root root 4096 2005-12-19 12:07 partial
root@ubuntu:/var/lib/apt/lists# ls -l
total 4
drwxr-xr-x  2 root root 4096 2005-12-19 12:07 partial
root@ubuntu:/var/lib/apt/lists# rm * -f
rm: cannot remove `partial': Is a directory
root@ubuntu:/var/lib/apt/lists# ls -l
total 4
drwxr-xr-x  2 root root 4096 2005-12-19 12:07 partial
root@ubuntu:/var/lib/apt/lists# apt-get update
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
Err cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release [1793B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:5 [http://kubuntu.org](http://kubuntu.org) breezy/main Packages [80.1kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg [189B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [26.0kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [8422B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [26.0kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [8422B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [19.4kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [2831B]
99% [12 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Sub-process bzip2 returned an error code (2)
99% [13 Packages bzip2 0] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages - open (2 No such file or directory)
99% [14 Sources bzip2 0] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_breezy-security_main_source_Sources - open (2 No such file or directory)
99% [15 Sources bzip2 0] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_source_Sources - open (2 No such file or directory)
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release [30.9kB]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages [586kB]
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Sources [232kB]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages [17.9kB]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Sources [5088B]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Fetched 3381kB in 21s (161kB/s)
Failed to fetch cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages - open (2 No such file or directory)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_breezy-security_main_source_Sources - open (2 No such file or directory)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_source_Sources - open (2 No such file or directory)
Reading package lists... Done
W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/var/lib/apt/lists# ls -l
total 18612
-rw-r--r--  1 root root  3943645 2005-11-23 21:29 ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
-rw-r--r--  1 root root  1338839 2005-11-23 21:05 ca.archive.ubuntu.com_ubuntu_dists_breezy_main_source_Sources
-rw-r--r--  1 root root    30892 2005-11-23 21:38 ca.archive.ubuntu.com_ubuntu_dists_breezy_Release
-rw-r--r--  1 root root      189 2005-11-23 21:38 ca.archive.ubuntu.com_ubuntu_dists_breezy_Release.gpg
-rw-r--r--  1 root root    31521 2005-10-24 21:09 ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages
-rw-r--r--  1 root root     5287 2005-10-24 21:17 ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_source_Sources
-rw-r--r--  1 root root 12203111 2005-11-23 21:04 ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages
-rw-r--r--  1 root root   107031 2005-11-24 00:06 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages
-rw-r--r--  1 root root    14857 2005-11-23 23:40 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_source_Sources
-rw-r--r--  1 root root    19617 2005-12-18 18:40 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_Release
-rw-r--r--  1 root root      189 2005-12-18 18:40 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_Release.gpg
-rw-r--r--  1 root root        0 2005-11-20 21:51 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages
-rw-r--r--  1 root root        0 2005-11-20 21:51 ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_source_Sources
-rw-r--r--  1 root root   929994 2005-12-14 19:53 kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages
-rw-r--r--  1 root root     1793 2005-12-14 19:56 kubuntu.org_packages_kde35_dists_breezy_Release
-rw-r--r--  1 root root      189 2005-12-14 19:56 kubuntu.org_packages_kde35_dists_breezy_Release.gpg
-rw-r-----  1 root root        0 2005-12-19 12:08 lock
drwxr-xr-x  2 root root     4096 2005-12-19 12:08 partial
-rw-r--r--  1 root root   139250 2005-12-16 13:06 security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages
-rw-r--r--  1 root root    29368 2005-12-16 13:09 security.ubuntu.com_ubuntu_dists_breezy-security_main_source_Sources
-rw-r--r--  1 root root    19627 2005-12-18 23:40 security.ubuntu.com_ubuntu_dists_breezy-security_Release
-rw-r--r--  1 root root      189 2005-12-18 23:40 security.ubuntu.com_ubuntu_dists_breezy-security_Release.gpg
-rw-r--r--  1 root root    29348 2005-11-23 21:48 security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages
-rw-r--r--  1 root root     3802 2005-11-22 12:30 security.ubuntu.com_ubuntu_dists_breezy-security_restricted_source_Sources
-rw-r--r--  1 root root   104747 2005-12-13 17:03 security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages
-rw-r--r--  1 root root     8587 2005-12-13 17:04 security.ubuntu.com_ubuntu_dists_breezy-security_universe_source_Sources
root@ubuntu:/var/lib/apt/lists#


here is my source.list!!!!

> metho@ubuntu:~/Desktop$ more sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main r
estricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted unive
rse multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted u
niverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# Ubuntu 5.10 KDE 3.5 Repository
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) pool-breezy main

 deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy multiverse



---

### Post by ubuntu_demon on 2005-12-18
mEtho : try my sources.list

$sudo gedit /etc/apt/sources.list

and to put it into effect :

$sudo apt-get update

if there are still errors post them.(it's possible but unlikely that you need to do the same as Smaskens)

---

