---
title: "Wireless Network Card"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by brback on 2008-07-27
Hi! 

I recently installed Ubuntu at my pc and is pretty clueless at everything. The only thing preventing me from getting started to know Ubuntu better is my wireless network card. I got a D-Link DWA-547. D-Link doesn't provide any drivers so I'm hoping you have any suggestions on what to do next.

Thanks alot for any help at all!

---

### Post by UltraMathMan on 2008-07-27
Try checking out this thread: [http://ubuntuforums.org/showthread.php?t=668272]("http://ubuntuforums.org/showthread.php?t=668272")

-Hope this helps :)

---

### Post by brback on 2008-07-29
Okay, i followed the madwifi how to instructions and i got to the part where you type 'make'.

This is what i got

brback@Cosmos:~/Skrivebord/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/brback/Skrivebord/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
make[3]: Warning: File `/home/brback/Skrivebord/madwifi-0.9.4/ath/.if_ath_pci.o.cmd' has modification time 6.9e+03 s in the future
make[3]: warning:  Clock skew detected.  Your build may be incomplete.
make[3]: Warning: File `/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/.ah_os.o.cmd' has modification time 6.9e+03 s in the future
  HOSTCC  /home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/brback/Skrivebord/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/brback/Skrivebord/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

waaaaah :S

please make it go away :p

---

### Post by ModdTaco on 2008-07-29
Before you go crazy trying to get madwifi to compile have you tried just clicking on the wireless link on the top of your desktop to see if your card is already supported. The D-Link DWA-547 and the WDA-1320 have worked out of the box for me.

---

### Post by brback on 2008-07-29
nope, its not supported as i see it. The wireless link is marked with an orange exclamation mark

---

### Post by UltraMathMan on 2008-07-29
You'll need to make sure you have the build-essential package installed before running make.

```
sudo apt-get install build-essential
```

---

### Post by brback on 2008-07-30
then i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

I've tried this with the ubuntu cd inserted as well if it should have made any difference

---

### Post by UltraMathMan on 2008-07-30
Hmm, could you post the output of ```
cat /etc/apt/sources.list
```

---

### Post by halitech on 2008-07-30
> **brback said:**
> then i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

I've tried this with the ubuntu cd inserted as well if it should have made any difference

do you have a wired connection right now? Most times having a wired connection while trying to get the wireless going is much easier

---

### Post by brback on 2008-07-30
nope, only got access at wireless. So currently i am switching between from ubuntu to vista to get online, as my wireless card works okay in windows.

---

### Post by brback on 2008-07-30
> **UltraMathMan said:**
> Hmm, could you post the output of ```
cat /etc/apt/sources.list
```

I'll post you the output as soon as i get home from vacation as i left my desktop back home :p

---

### Post by brback on 2008-08-22
Sorry for not responding earlier, but i hope you're still able to help me with my problem.

The output for cat /etc/apt/sources.list

```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


```

---

### Post by UltraMathMan on 2008-08-22
Hmm, sources look ok - I missed this before in your output ```
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
make[3]: Warning: File `/home/brback/Skrivebord/madwifi-0.9.4/ath/.if_ath_pci.o.cmd' has modification time 6.9e+03 s in the future
make[3]: warning: Clock skew detected. Your build may be incomplete.
make[3]: Warning: File `/home/brback/Skrivebord/madwifi-0.9.4/ath_hal/.ah_os.o.cmd' has modification time 6.9e+03 s in the future
```

Make sure your clock is set to the correct time or try redownloading the file.

---

### Post by JokeDog on 2008-08-23
Hi UltraMathMan, I too have the same exact problem.  :-(


```
root@paq:/etc/apt# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
root@paq:/etc/apt# ls
apt.conf.d   sources.list    sources.list.edgy  trusted.gpg
secring.gpg  sources.list.d  trustdb.gpg        trusted.gpg~
root@paq:/etc/apt# mv sources.list sources.list.hardy
root@paq:/etc/apt# mv sources.list.edgy sources.list
root@paq:/etc/apt# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7925kB/7932kB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com edgy-updates/main libc6-dev 2.4-1ubuntu12.3
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/main libstdc++6-4.1-dev 4.1.1-13ubuntu5
  404 Not Found [IP: 91.189.88.45 80]
Err http://security.ubuntu.com edgy-security/main linux-libc-dev 2.6.17.1-11.37
  404 Not Found
Err http://us.archive.ubuntu.com edgy/main g++-4.1 4.1.1-13ubuntu5
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/main g++ 4:4.1.1-6ubuntu3
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/main dpkg-dev 1.13.22ubuntu7
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-11.37_i386.deb  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.3_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@paq:/etc/apt# 
root@paq:/etc/apt# uname -a
Linux paq 2.6.17-11-generic #2 SMP Tue Mar 13 23:32:38 UTC 2007 i686 GNU/Linux
root@paq:/etc/apt# wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-11.37_i386.deb 
--02:04:58--  http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-11.37_i386.deb
           => `linux-libc-dev_2.6.17.1-11.37_i386.deb'
Resolving security.ubuntu.com... 91.189.88.37
Connecting to security.ubuntu.com|91.189.88.37|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
02:04:59 ERROR 404: Not Found.



```

I use Edgy.  Looks like my source.list is outdated.  but when I use BRBACK's HARDY source.list  I get the same exact error he got, the one he displayed early.  Find not found.  Strange.

---

### Post by JokeDog on 2008-08-23
When I use Brback's source.list, I get same as his error:

```
root@paq:/etc/apt# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

```

---

### Post by JokeDog on 2008-08-23
yes I do have "wired" internet access.  I'm almost ashame not able to fix this as my wireless worked previous.  I haven't touch this ubuntu in a while, suddenly its not working and I can't "make" madwifi.  Argh!

---

### Post by brback on 2008-08-23
> **UltraMathMan said:**
> 
Make sure your clock is set to the correct time or try redownloading the file.

Okay, sorry for not knowing better, but what clock?
My first assumptions is the system clock, which i'm really guessing its not. What does that got to do with my problem anyways :P

---

