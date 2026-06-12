---
title: "Cannot locate package message"
date: 2017-12-27
forum: New to Ubuntu
---

### Post by monsterbus on 2017-12-27
Hi,
   I'm completely new to the world of Ubuntu.
I'm booting a a 16.04.3 LTS (x86) .ISO file on a USB stick using grub4dos.

After downloading an installing binwalk, I'm unable to install some of its optional dependencies.

For example, typing:  sudo apt-get install python-lzma 

Gives the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-lzma

Can someone tell me how to go about resolving this please?

Thanks in advance.

---

### Post by deadflowr on 2017-12-27
Hmm, binwalk is available in the ubuntu archives for 16.04 and would have installed all dependencies including python-lzma if you installed from there.

Is the universe repository enabled?

post back the output for the sources.list file:
```
cat /etc/apt/sources.list
```
and for good measure the output for
```
sudo apt update
```
to see whether or not the package manager (apt) has issues.

---

### Post by monsterbus on 2017-12-27
Okay, here it is:
```
ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release i386 (20170801)]/ xenial main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted
```
 
```
ubuntu@ubuntu:~$ sudo apt update
Ign:1 cdrom://Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release i386 (20170801) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release i386 (20170801) xenial Release
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease         
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]       
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [640 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [373 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [180 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 DEP-11 Metadata [62.4 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [62.1 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages [7,472 B]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en [2,412 B]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [285 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 DEP-11 Metadata [307 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [228 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages [8,100 B]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en [2,672 B]
Fetched 2,364 kB in 37s (62.2 kB/s)                                            

** (appstreamcli:5626): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
303 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

---

### Post by Bashing-om on 2017-12-27
monsterbus; My Welcome to the forum .

A stripped down sane xenial sources.list file:
```


sysop@x1604:~$ cat /etc/apt/sources.list
deb http://mirror.steadfast.net/ubuntu xenial main restricted universe multiverse

deb http://mirror.steadfast.net/ubuntu xenial-security main restricted universe multiverse

deb http://mirror.steadfast.net/ubuntu xenial-updates main restricted universe multiverse

deb http://mirror.steadfast.net/ubuntu xenial-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu xenial partner

sysop@x1604:~$

```
where in this install I do not use source code .

[INDENT][INDENT]should help a bunch
[/INDENT][/INDENT]

---

### Post by monsterbus on 2017-12-27
Hi,
    I tried copying and pasting over the contents of the sources.list file with your deb entries but I don't have permission to do this.  How do I obtain permission please?

---

### Post by Bashing-om on 2017-12-27
monsterbus; Hey ..

/etc/apt/sources.list is a system file, and requires admin privileges to alter.
Always always make a backup of any file that you edit .. never can tell what might happen:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bad

```

Now open a text editor ( here gedit as a working example) with the elevated privileges in the target file :
```

sudo -H gedit /etc/apt/sources.list

```
-H is because gedit is a GUI app running from CLI ( there are other ways ), and we want to sandbox accesses .

copy and paste .. save the document.

Now --- what results:
```

sudo apt update
sudo apt full-upgrade

```

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by again? on 2017-12-27
Hi Bashing-om,
may not want to run full-upgrade on a Live ISO. 
You can also enable the universe and multiverse repositories, which are disabled in a Live ISO, with
```
sudo apt-add-repository universe
sudo apt-add-repository multiverse
```

---

### Post by Bashing-om on 2017-12-27
ouch !

> 
I'm booting a a 16.04.3 LTS (x86) .ISO file on a USB stick using grub4dos.


a thousand pardons monsterbus - I did so fail to read.

[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2017-12-27
In short, if you want to fix this and see what Ubuntu is really like, . . . . . just do a full install to the internal hdd or ssd.    Live ISO's on dvd or usb stick are just supposed to be to "preview" a live snapshot of Ubuntu.   Not designed for customization, updating, installing, uninstalling, yada yada yada.    Do the required reading so you understand, then do the full install.

Or another option is to use two usb sticks or better yet, use one usb-stick and one external usbv3 ssd and do the full install to the external SSD.    That provides the full installed experience.

[https://www.youtube.com/watch?time_continue=1&v=4qtr9QaYJ7U](https://www.youtube.com/watch?time_continue=1&v=4qtr9QaYJ7U)

---

### Post by monsterbus on 2017-12-28
Thanks to all for your assistance with this. I ran the apt update command overnight as my connection is painfully slow at present, was unable to complete because my PC went into standby.  So I aborted the resumed downloading this morning having read the updated posts.

As per guber2's advice, 
```

ubuntu@ubuntu:/media/ubuntu/SANDISK/binwalk-master$ sudo apt-add-repository universe
'universe' distribution component is already enabled for all sources.
ubuntu@ubuntu:/media/ubuntu/SANDISK/binwalk-master$ sudo apt-add-repository multiverse
'multiverse' distribution component is already enabled for all sources.
ubuntu@ubuntu:/media/ubuntu/SANDISK/binwalk-master$ sudo apt-get install python-lzma
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  python-lzma
0 upgraded, 1 newly installed, 0 to remove and 303 not upgraded.
Need to get 29.8 kB of archives.
After this operation, 89.1 kB of additional disk space will be used.
Get:1 http://mirror.steadfast.net/ubuntu xenial/universe i386 python-lzma i386 0.5.3-3 [29.8 kB]
Fetched 29.8 kB in 0s (33.2 kB/s)    
Selecting previously unselected package python-lzma.
(Reading database ... 194418 files and directories currently installed.)
Preparing to unpack .../python-lzma_0.5.3-3_i386.deb ...
Unpacking python-lzma (0.5.3-3) ...
Setting up python-lzma (0.5.3-3) ... 

```

Success!:)  I wonder if you someone can answer another question related to the installation of binwalk please?

In the [quick start guide]("https://github.com/ReFirmLabs/binwalk/wiki/Quick-Start-Guide"), it states: 
```

Debian users can install all optional and suggested extractors/dependencies using the included deps.sh script (recommended):

$ sudo ./binwalk-master/deps.sh



```

Am I right to think that this should work on Ubuntu as it's based on Debian? 

Typing this, I see:
```

ubuntu@ubuntu:/media/ubuntu/SANDISK/binwalk-master$ sudo ./binwalk-master/deps.sh
sudo: ./binwalk-master/deps.sh: command not found

```

To be clear, deps.sh is present in the binwalk-master folder.

---

### Post by Holger_Gehrke on 2017-12-28
> **monsterbus said:**
> 
...
In the [quick start guide]("https://github.com/ReFirmLabs/binwalk/wiki/Quick-Start-Guide"), it states: 
```

Debian users can install all optional and suggested extractors/dependencies using the included deps.sh script (recommended):

$ sudo ./binwalk-master/deps.sh



```

Am I right to think that this should work on Ubuntu as it's based on Debian? 

Typing this, I see:
```

ubuntu@ubuntu:/media/ubuntu/SANDISK/binwalk-master$ sudo ./binwalk-master/deps.sh
sudo: ./binwalk-master/deps.sh: command not found

```

To be clear, deps.sh is present in the binwalk-master folder.

Look at your prompt. What's your current working directory ? Right, you already are in 'binwalk-master'. So the command you've given tells it to look for a directory named 'binwalk-master' in 'binwalk-master' and execute the script 'deps.sh' located in that directory. 

It should just be 'sudo ./deps.sh'

Holger

---

### Post by again? on 2017-12-28
> **monsterbus said:**
> 
I wonder if you someone can answer another question related to the installation of binwalk please?

In the [quick start guide]("https://github.com/ReFirmLabs/binwalk/wiki/Quick-Start-Guide"), it states: 
```

Debian users can install all optional and suggested extractors/dependencies using the included deps.sh script (recommended):

$ sudo ./binwalk-master/deps.sh



```

Am I right to think that this should work on Ubuntu as it's based on Debian? 

Typing this, I see:
```

ubuntu@ubuntu:/media/ubuntu/SANDISK/binwalk-master$ sudo ./binwalk-master/deps.sh
sudo: ./binwalk-master/deps.sh: command not found

```

To be clear, deps.sh is present in the binwalk-master folder.

Once you cd to the binwalk-master directory you only need to run (use sudo if not prompted for password)...
```
./deps.sh
```

eg
```
**[COLOR="#006400"]glen@GU17:~$[/COLOR] cd /home/glen/git/binwalk**
**[COLOR="#006400"]glen@GU17:~/git/binwalk$[/COLOR] ls**
API.md  deps.sh  images  INSTALL.md  LICENSE  README.md  setup.py  src  testing
**[COLOR="#006400"]glen@GU17:~/git/binwalk$[/COLOR] ./deps.sh**

WARNING: This script will download and install all required and optional dependencies for binwalk.
         This script has only been tested on, and is only intended for, Debian based systems.
         Some dependencies are downloaded via unsecure (HTTP) protocols.
         This script requires internet access.
         This script requires root privileges.

         Ubuntu 17 detected

Continue [y/N]?
``` 

Don't know what you are doing but have you looked at [**Kali Linux**]("https://www.kali.org/").

---

### Post by monsterbus on 2017-12-28
Many thanks for the guidance, I should have noticed this.  My lack of knowledge of "." notation is clearly evident.  I'll need to read up on the shell basics.

---

