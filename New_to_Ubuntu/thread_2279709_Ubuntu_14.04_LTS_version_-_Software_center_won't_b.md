---
title: "Ubuntu 14.04 LTS version - Software center won't boot"
date: 2015-05-25
forum: New to Ubuntu
---

### Post by Ted_Tommikoski on 2015-05-25
So... Hello everyone!

I am going to jump straight into business. I am quite the greenhorn/newbie when it comes to Ubuntu - so I am putting my hopes in you guys :) 

As the title implies: My ubuntu software center will not boot. And this is the information that I receive when I try to "repair" the problem:
> installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 333410 files and directories currently installed.) 
Preparing to unpack .../linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb ... 
Unpacking linux-headers-3.16.0-38 (3.16.0-38.52~14.04.1) ... 
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb (--unpack): 
 cannot copy extracted data for './usr/src/linux-headers-3.16.0-38/scripts/kconfig/nconf.c' to '/usr/src/linux-headers-3.16.0-38/scripts/kconfig/nconf.c.dpkg-new': unexpected end of file or stream 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb 
Error in function:  
dpkg: dependency problems prevent configuration of linux-headers-3.16.0-38-generic: 
 linux-headers-3.16.0-38-generic depends on linux-headers-3.16.0-38; however: 
  Package linux-headers-3.16.0-38 is not installed. 
 
dpkg: error processing package linux-headers-3.16.0-38-generic (--configure): 
 dependency problems - leaving unconfigured 



Thank you for taking the time to read about my problems (and hopefully helping me reach a conclusion?) :popcorn: 

Cheers!

---

### Post by Bucky Ball on 2015-05-25
Welcome. Please run these commands in a terminal and post any and all errors. Please use code tags (see last link in my signature) so we can have a better idea of what's happening. Thanks.

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

(Please use [code] tags for any terminal output or commands you post. ;))

---

### Post by Ted_Tommikoski on 2015-05-25
Ah, right-o 

Appreciate the fast response :)

```

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 333410 files and directories currently installed.) 
Preparing to unpack .../linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb ... 
Unpacking linux-headers-3.16.0-38 (3.16.0-38.52~14.04.1) ... 
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb (--unpack): 
 cannot copy extracted data for './usr/src/linux-headers-3.16.0-38/scripts/kconfig/nconf.c' to '/usr/src/linux-headers-3.16.0-38/scripts/kconfig/nconf.c.dpkg-new': unexpected end of file or stream 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb 
Error in function:  
dpkg: dependency problems prevent configuration of linux-headers-3.16.0-38-generic: 
 linux-headers-3.16.0-38-generic depends on linux-headers-3.16.0-38; however: 
  Package linux-headers-3.16.0-38 is not installed. 
 
dpkg: error processing package linux-headers-3.16.0-38-generic (--configure): 
 dependency problems - leaving unconfigured 

 
```

---

### Post by Bucky Ball on 2015-05-25
No probs. Could you run the commands I posted previously (I edited my post) and show us the errors, please.

Is this a fresh install? Have you manually added any repositories or done anything that coincides with the issue arising? Bit confused. When you say SCentre won't boot, what happens when you launch it? It just doesn't launch? Please explain what you are doing/have done to try and fix it?

Your output is confusing, at least to me. Looks like you are trying to install the 3.16 kernel?

---

### Post by Ted_Tommikoski on 2015-05-25
I installed Ubuntu in February, so I wouldn't call this a fresh install :)

Ubuntu tells me that I have "updates" to install and then it asks for my administrative permission download and install the updates (and I usually just blindly accept and allow it to give it "what it wants") - since I've assumed that the updates recommended by Ubuntu to be trustworthy.

I haven't really installed or attempted to install that many new programs as of late. I attempted to install Skype (doesn't launch though), I've installed Gimp image editor, dropbox and and a few simpler programs (e.g. Tasque manager).

I just realized that I might be an idiot... Since the SC does boot, but only after i try to repair it, and cancel when it goes wrong (it still won't allow me to install anything though).

This is what I get when I run the first apt-get autoremove. 
```

ted@Teddey:~$ sudo apt-get autoremove
[sudo] password for ted: 
Sorry, try again.
[sudo] password for ted: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-3.16.0-38-generic : Depends: linux-headers-3.16.0-38 but it is not installed
E: Unmet dependencies. Try using -f.
ted@Teddey:~$  

```

```

ted@Teddey:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://se.archive.ubuntu.com trusty InRelease                              
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://se.archive.ubuntu.com trusty-updates InRelease                      
Get:2 http://dl.google.com stable Release [1 347 B]                            
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://se.archive.ubuntu.com trusty-backports InRelease                    
Get:3 http://dl.google.com stable/main amd64 Packages [1 195 B]      
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://se.archive.ubuntu.com trusty Release.gpg                            
Get:4 http://dl.google.com stable/main i386 Packages [1 177 B]        
Get:5 http://se.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Hit http://extras.ubuntu.com trusty Release                                    
Get:6 http://se.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://se.archive.ubuntu.com trusty Release                       
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:7 http://se.archive.ubuntu.com trusty-updates Release [63,5 kB]            
Get:8 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Get:9 http://se.archive.ubuntu.com trusty-backports Release [63,5 kB]          
Hit http://se.archive.ubuntu.com trusty/main Sources                           
Get:10 http://security.ubuntu.com trusty-security Release [63,5 kB]            
Hit http://se.archive.ubuntu.com trusty/restricted Sources                     
Hit http://se.archive.ubuntu.com trusty/universe Sources                       
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://se.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://se.archive.ubuntu.com trusty/main amd64 Packages                    
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://se.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://dl.google.com stable/main Translation-en                            
Hit http://se.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://se.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://se.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://se.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://se.archive.ubuntu.com trusty/universe i386 Packages               
Hit http://se.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://se.archive.ubuntu.com trusty/main Translation-en       
Hit http://se.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://se.archive.ubuntu.com trusty/restricted Translation-en 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://se.archive.ubuntu.com trusty/universe Translation-en                
Get:11 http://se.archive.ubuntu.com trusty-updates/main Sources [205 kB]
Get:12 http://security.ubuntu.com trusty-security/main Sources [81,4 kB]       
Get:13 http://se.archive.ubuntu.com trusty-updates/restricted Sources [3 433 B]
Get:14 http://se.archive.ubuntu.com trusty-updates/universe Sources [117 kB]   
Get:15 http://se.archive.ubuntu.com trusty-updates/multiverse Sources [5 152 B]
Get:16 http://se.archive.ubuntu.com trusty-updates/main amd64 Packages [524 kB]
Get:17 http://security.ubuntu.com trusty-security/restricted Sources [2 061 B] 
Get:18 http://security.ubuntu.com trusty-security/universe Sources [25,2 kB]   
Get:19 http://se.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11,8 kB]
Get:20 http://se.archive.ubuntu.com trusty-updates/universe amd64 Packages [280 kB]
Get:21 http://security.ubuntu.com trusty-security/multiverse Sources [2 333 B] 
Get:22 http://se.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11,9 kB]
Get:23 http://security.ubuntu.com trusty-security/main amd64 Packages [272 kB] 
Get:24 http://se.archive.ubuntu.com trusty-updates/main i386 Packages [513 kB] 
Get:25 http://se.archive.ubuntu.com trusty-updates/restricted i386 Packages [11,8 kB]
Get:26 http://se.archive.ubuntu.com trusty-updates/universe i386 Packages [281 kB]
Get:27 http://se.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12,1 kB]
Get:28 http://se.archive.ubuntu.com trusty-updates/main Translation-en [249 kB]
Hit http://se.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://se.archive.ubuntu.com trusty-updates/restricted Translation-en      
Get:29 http://se.archive.ubuntu.com trusty-updates/universe Translation-en [146 kB]
Get:30 http://se.archive.ubuntu.com trusty-backports/main Sources [5 851 B]    
Get:31 http://se.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:32 http://se.archive.ubuntu.com trusty-backports/universe Sources [25,9 kB]
Get:33 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8 875 B]
Get:34 http://se.archive.ubuntu.com trusty-backports/multiverse Sources [1 898 B]
Get:35 http://se.archive.ubuntu.com trusty-backports/main amd64 Packages [6 256 B]
Get:36 http://se.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:37 http://se.archive.ubuntu.com trusty-backports/universe amd64 Packages [29,7 kB]
Get:38 http://security.ubuntu.com trusty-security/universe amd64 Packages [104 kB]
Get:39 http://se.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1 245 B]
Get:40 http://se.archive.ubuntu.com trusty-backports/main i386 Packages [6 285 B]
Get:41 http://se.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:42 http://se.archive.ubuntu.com trusty-backports/universe i386 Packages [29,7 kB]
Get:43 http://se.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1 249 B]
Hit http://se.archive.ubuntu.com trusty-backports/main Translation-en   
Hit http://se.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://se.archive.ubuntu.com trusty-backports/restricted Translation-en
Get:44 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3 681 B]
Get:45 http://se.archive.ubuntu.com trusty-backports/universe Translation-en [26,3 kB]
Get:46 http://security.ubuntu.com trusty-security/main i386 Packages [260 kB] 
Ign http://se.archive.ubuntu.com trusty/main Translation-en_US
Ign http://se.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://se.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://se.archive.ubuntu.com trusty/universe Translation-en_US
Get:47 http://security.ubuntu.com trusty-security/restricted i386 Packages [8 846 B]
Get:48 http://security.ubuntu.com trusty-security/universe i386 Packages [104 kB]
Get:49 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3 840 B]
Get:50 http://security.ubuntu.com trusty-security/main Translation-en [139 kB]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Get:51 http://security.ubuntu.com trusty-security/universe Translation-en [58,9 kB]
Fetched 3 777 kB in 6s (557 kB/s)                                              
Reading package lists... Done

```

sudo apt-get upgrade
```

ted@Teddey:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-3.16.0-38-generic : Depends: linux-headers-3.16.0-38 but it is not installed
E: Unmet dependencies. Try using -f.
ted@Teddey:~$ 

```


sudo apt-get dist-upgrade
```

ted@Teddey:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-3.16.0-38-generic : Depends: linux-headers-3.16.0-38 but it is not installed
E: Unmet dependencies. Try using -f.
ted@Teddey:~$

``` 

I apologize for my tardiness, You da real MVP for putting up with me :)

---

### Post by Bashing-om on 2015-05-25
Ted_Tommikoski; Hello;

Allow me to jump in here and try and push this along for Bucky Ball - He might get real busy with other matters.

The 3.16.0-38 kernel in trusty indicates that you have implemented HardWare Enablemant stack (HWE).

Let's look at what is going on ->
do we have the headroom to operate in ?
show :
```

df -h
df -i

```

What does the system report for a HWE status ?
Show:
```

ls -al /usr/bin/hwe-support-status
hwe-support-status --verbose
hwe-support-status --show-all-unsupported

```

as we look for why:
> 
linux-headers-3.16.0-38 but it is not installed


Maybe we can push on it a bit and install the requirement ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Ted_Tommikoski on 2015-05-25
Hello to you [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1111508_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1111508") 				 				 					 						 	[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508")!


Do I have enough room? Well, yes - I would presume so.
```
 
ted@Teddey:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       106G   12G   90G  12% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            2,0G  4,0K  2,0G   1% /dev
tmpfs           396M  1,4M  394M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            2,0G  876K  2,0G   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sdc1       466G   27G  440G   6% /media/ted/Elements
/dev/sda1       926G   70G  856G   8% /media/ted/HD Of Yorn
ted@Teddey:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sdb1        7069696 383752   6685944    6% /
none              505922      2    505920    1% /sys/fs/cgroup
udev              503248    565    502683    1% /dev
tmpfs             505922    612    505310    1% /run
none              505922      3    505919    1% /run/lock
none              505922      9    505913    1% /run/shm
none              505922     31    505891    1% /run/user
/dev/sdc1      461007916   8748 460999168    1% /media/ted/Elements
/dev/sda1      897430772   3294 897427478    1% /media/ted/HD Of Yorn
ted@Teddey:~$ 

```

Did I do this right? I have no idea xD
```

ted@Teddey:~$ ls -al /usr/bin/hwe-support-status
ls: cannot access /usr/bin/hwe-support-status: No such file or directory
ted@Teddey:~$ ls -al /usr/bin/hwe-support-status
ls: cannot access /usr/bin/hwe-support-status: No such file or directory
ted@Teddey:~$ hwe-support-status --verbose
hwe-support-status: command not found
ted@Teddey:~$ hwe-support-status --show-all-unsupported
hwe-support-status: command not found
ted@Teddey:~$ 

```

---

### Post by Bashing-om on 2015-05-25
Ted_Tommikoski; Yuk;

That seems to show that HWE is not an issue here.
That begs the question:
Where does " linux-headers-3.16.0-38 " come into play as it is the kernel for utopic, not trusty's . - What have you done ?? -
So what have we on the system presently for kernel images ?
show:
```

dpkg -l | grep linux-
ls -al /boot

```

[INDENT][INDENT]when I know better
[INDENT][INDENT][INDENT]I will say better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Ted_Tommikoski on 2015-05-25
This is kind of exciting... hehe

Not really used to poke around like this with commands and ****.

```

ted@Teddey:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.12                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-utopic                              3.16.0.38.30                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-30                               3.16.0-30.40~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-30-generic                       3.16.0-30.40~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-31                               3.16.0-31.43~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-31-generic                       3.16.0-31.43~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-33                               3.16.0-33.44~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-33-generic                       3.16.0-33.44~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-34                               3.16.0-34.47~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic                       3.16.0-34.47~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-36                               3.16.0-36.48~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-36-generic                       3.16.0-36.48~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-37                               3.16.0-37.51~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-37-generic                       3.16.0-37.51~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
iU  linux-headers-3.16.0-38-generic                       3.16.0-38.52~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
iU  linux-headers-generic-lts-utopic                      3.16.0.38.30                                        amd64        Generic Linux kernel headers
ii  linux-image-3.16.0-30-generic                         3.16.0-30.40~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-31-generic                         3.16.0-31.43~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-33-generic                         3.16.0-33.44~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-34-generic                         3.16.0-34.47~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-36-generic                         3.16.0-36.48~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-37-generic                         3.16.0-37.51~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-38-generic                         3.16.0-38.52~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic                   3.16.0-30.40~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-31-generic                   3.16.0-31.43~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-33-generic                   3.16.0-33.44~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-34-generic                   3.16.0-34.47~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-36-generic                   3.16.0-36.48~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-37-generic                   3.16.0-37.51~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-38-generic                   3.16.0-38.52~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-utopic                        3.16.0.38.30                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-53.88                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies



``` 

```


ted@Teddey:~$ ls -al /boot
total 210312
drwxr-xr-x  3 root root     4096 maj 20 12:30 .
drwxr-xr-x 23 root root     4096 maj 20 12:30 ..
-rw-r--r--  1 root root  1207386 jan 15 19:22 abi-3.16.0-30-generic
-rw-r--r--  1 root root  1207327 mar 10 22:12 abi-3.16.0-31-generic
-rw-r--r--  1 root root  1207327 mar 13 12:12 abi-3.16.0-33-generic
-rw-r--r--  1 root root  1207327 apr 10 20:48 abi-3.16.0-34-generic
-rw-r--r--  1 root root  1206938 apr 15 16:10 abi-3.16.0-36-generic
-rw-r--r--  1 root root  1206938 maj  6 18:22 abi-3.16.0-37-generic
-rw-r--r--  1 root root  1207096 maj  8 12:44 abi-3.16.0-38-generic
-rw-r--r--  1 root root   171768 jan 15 19:22 config-3.16.0-30-generic
-rw-r--r--  1 root root   171802 mar 10 22:12 config-3.16.0-31-generic
-rw-r--r--  1 root root   171827 mar 13 12:12 config-3.16.0-33-generic
-rw-r--r--  1 root root   171827 apr 10 20:48 config-3.16.0-34-generic
-rw-r--r--  1 root root   171816 apr 15 16:10 config-3.16.0-36-generic
-rw-r--r--  1 root root   171816 maj  6 18:22 config-3.16.0-37-generic
-rw-r--r--  1 root root   171817 maj  8 12:44 config-3.16.0-38-generic
drwxr-xr-x  5 root root     4096 maj 20 12:30 grub
-rw-r--r--  1 root root 19439603 mar 20 22:49 initrd.img-3.16.0-30-generic
-rw-r--r--  1 root root 19437807 mar 20 23:00 initrd.img-3.16.0-31-generic
-rw-r--r--  1 root root 19440615 mar 24 21:47 initrd.img-3.16.0-33-generic
-rw-r--r--  1 root root 19436759 apr 14 15:09 initrd.img-3.16.0-34-generic
-rw-r--r--  1 root root 19441107 apr 30 16:18 initrd.img-3.16.0-36-generic
-rw-r--r--  1 root root 19438241 maj  7 19:24 initrd.img-3.16.0-37-generic
-rw-r--r--  1 root root 19437908 maj 20 12:30 initrd.img-3.16.0-38-generic
-rw-r--r--  1 root root   176500 mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3511040 jan 15 19:22 System.map-3.16.0-30-generic
-rw-------  1 root root  3511419 mar 10 22:12 System.map-3.16.0-31-generic
-rw-------  1 root root  3512061 mar 13 12:12 System.map-3.16.0-33-generic
-rw-------  1 root root  3512405 apr 10 20:48 System.map-3.16.0-34-generic
-rw-------  1 root root  3512899 apr 15 16:10 System.map-3.16.0-36-generic
-rw-------  1 root root  3512899 maj  6 18:22 System.map-3.16.0-37-generic
-rw-------  1 root root  3513313 maj  8 12:44 System.map-3.16.0-38-generic
-rw-r--r--  1 root root  6345120 mar 20 22:45 vmlinuz-3.16.0-30-generic
-rw-------  1 root root  6346448 mar 10 22:12 vmlinuz-3.16.0-31-generic
-rw-------  1 root root  6348624 mar 13 12:12 vmlinuz-3.16.0-33-generic
-rw-------  1 root root  6350864 apr 10 20:48 vmlinuz-3.16.0-34-generic
-rw-------  1 root root  6351504 apr 15 16:10 vmlinuz-3.16.0-36-generic
-rw-------  1 root root  6352688 maj  6 18:22 vmlinuz-3.16.0-37-generic
-rw-------  1 root root  6351952 maj  8 12:44 vmlinuz-3.16.0-38-generic


```

---

### Post by sandyd on 2015-05-25
Possible that archive is corrupt.

```

sudo rm "/var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb"
sudo apt-get -f install
```

---

### Post by Bashing-om on 2015-05-25
Ted_Tommikoski; Yeah;

It is fun delving into the system, see why it works.
But here someone is lying:
> 
Ubuntu 14.04 LTS version - Software center won't boot


So far I see this as utopic installed. What does the system think ?
```

lsb_release -a
cat /etc/issue

```

As we readjust the sights
[INDENT][INDENT]no longer shooting from the hip
[/INDENT][/INDENT]

---

### Post by Ted_Tommikoski on 2015-05-26
[QUOTE=Ted_Tommikoski]
I just realized that I might be an idiot... Since the SC does boot, but only after i try to repair it, and cancel when it goes wrong (it still won't allow me to install anything though).[/QUOTE]

Yeeah.... I realized that I might be an idiot - and announced it when I posted that screenshot on page 1 (which apparently was removed by an admin). :v 

- and yes, very exciting :) 

Thank you [**[COLOR=#C61919][B]sandyd**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=717412") for your contribution :)  - I will however try [**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508")'s suggestion before I try anything else. 

**lsb_release -a:**
```

ted@Teddey:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
ted@Teddey:~$ 

```

**cat /etc/issue:**
```

ted@Teddey:~$ cat /etc/issue
Ubuntu 14.04.2 LTS \n \l

```

---

### Post by Bucky Ball on 2015-05-26
You mean the pic in [this post]("http://ubuntuforums.org/showthread.php?t=2279709&p=13292105&viewfull=1#post13292105")? Your screenshot wasn't removed. It was attached and this was noted in the 'Reason for editing'. See the bottom of the post. Please consider those with vision issues or slow connections. Attach large pics using Go Advanced> paperclip icon rather than inserting them in the body of your post. Thanks. 

Apologies I didn't post to tell you what I'd done with that pic. The material world has been chaotic here lately and crashed in once again around that time. ;)

---

### Post by Ted_Tommikoski on 2015-05-26
Ah, I don't blame you in the slightest Bucky Ball :) 

It's your job to contain newbies rampaging your forum with stupid stuff like that (i.e. Me - the newbie). I appreciate it (y) 

 - And I didn't notice the thumbnail ^^'

---

### Post by Bucky Ball on 2015-05-26
All good. Sorry I didn't post that I'd done it when I did it. Most out of character! ;)

As for your issue, you have attempted to install the 3.16 kernel? As you are running a bog standard 14.04.2, that should have the 3.13 kernel by default. The 3.16 is the HWE (hardware enablement stack) kernel for 14.04 LTS is can only be installed manually at this time (I think it will become part of the 14.04 repository and automatically installed when the 14.04.3 point release becomes available, but don't quote me on that).

---

### Post by Ted_Tommikoski on 2015-05-26
I honestly can't tell you exactly what I've done - since I vaguely remember being asked by Ubuntu a number of times to accept updates (sometimes with linux kernel -ish stuffs mentioned... but I don't remember any specifics about it). And I always naively accepted the updates without giving it too much thought. 

I haven't attempted to do any manual or intentional installations of any thing kernel-ish (I'm not even sure what the "kernel" is or does).

---

### Post by Bucky Ball on 2015-05-26
Actually, possibly my mistake. I recently installed 14.04.2 which was downloaded from the Canonical site that day and it has the 3.16 kernel. My original 14.04.2 install on my laptop has the 3.13. That was installed a few months after it was released last year. :-k

---

### Post by Bashing-om on 2015-05-26
Ted_Tommikoski; Hey ;

My bad too; I had not considered that release 14.04.2 would have utopic's kernel by default. See, we are all at some point on the learning curve. (old thought processes do die hard)

Ok; situation at hand is getting linux-headers-3.16.0-38 to complete installation.
To that end; sandyd's post #10 does apply. Let's try the simpler approach before we manually intervene.
If that does not work, I have in mind an alternative.

Once the system is stable there is a bit of house cleaning that needs to be done.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Ted_Tommikoski on 2015-05-26
> **Bashing-om said:**
> Ted_Tommikoski; Hey ;

My bad too; I had not considered that release 14.04.2 would have utopic's kernel by default. See, we are all at some point on the learning curve. (old thought processes do die hard)

Ok; situation at hand is getting linux-headers-3.16.0-38 to complete installation.
To that end; sandyd's post #10 does apply. Let's try the simpler approach before we manually intervene.
If that does not work, I have in mind an alternative.

Once the system is stable there is a bit of house cleaning that needs to be done.[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Ok, you guys are awesome :) 

Do I just copy and past sandyd's code without any changes? (i.e. are the quotation marks supposed to be included (" " ? )

---

### Post by Vladlenin5000 on 2015-05-26
> **Ted_Tommikoski said:**
> Do I just copy and past sandyd's code without any changes? (i.e. are the quotation marks supposed to be included (" " ? )

Yes, exactly as posted.

---

### Post by Ted_Tommikoski on 2015-05-26
IT WORKED! 
Holy s**t - I love you guys. :guitar: 

I immediately jumped into downloading the program the I was after. :) - Now I'm finally able to write and edit decent LaTex documents for my studies :D 

Thank you so much for your time and dedication! you guys rock! :D 

sudo rm "/var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb"
```

ted@Teddey:~$ sudo rm "/var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb"
[sudo] password for ted: 
ted@Teddey:~$ 

```

**sudo apt-get -f install**
```

ted@Teddey:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libupstart1 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.16.0-38
The following NEW packages will be installed:
  linux-headers-3.16.0-38
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
3 not fully installed or removed.
Need to get 9 072 kB of archives.
After this operation, 64,5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.16.0-38 all 3.16.0-38.52~14.04.1 [9 072 kB]
Fetched 9 072 kB in 10s (903 kB/s)                                             
(Reading database ... 333410 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb ...
Unpacking linux-headers-3.16.0-38 (3.16.0-38.52~14.04.1) ...
Setting up linux-headers-3.16.0-38 (3.16.0-38.52~14.04.1) ...
Setting up linux-headers-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Setting up linux-headers-generic-lts-utopic (3.16.0.38.30) ...
Setting up linux-generic-lts-utopic (3.16.0.38.30) ...
ted@Teddey:~$ 

```

PS. How do I change the status to "problem solved" ? and how do I edit the title of the thread (so that it actually matches the problem) ? :)

---

### Post by Bashing-om on 2015-05-26
Ted_Tommikoski; YeaH ;

Great minds do reside here . All of us at one time or the other
"been there, done that" -> we share.

From me:
> 
Once the system is stable there is a bit of house cleaning that needs to be done.


Let's finish up:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

Finally make sure the package manager is in a happy state of mind:
```

sudo apt-get -f install
sudo dpkg -C

```

At that time I will feel comfortable closing this thread.

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-05-27
> **Bashing-om said:**
> 

Let's finish up:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

Finally make sure the package manager is in a happy state of mind:
```

sudo apt-get -f install
sudo dpkg -C

```

At that time I will feel comfortable closing this thread.



If all good after this, please mark the thread as solved (see the second link in my signature for how). This will not close the thread for further discussion but may help future travelers to find a fix. Good luck. ;)

---

### Post by Ted_Tommikoski on 2015-05-27
Ok - here we go :)

Let me know if everything looks alright ^^' 

**sudo apt-get clean**
```

ted@Teddey:~$ sudo apt-get clean
[sudo] password for ted: 

```

[B]
sudo apt-get autoclean[/B]
```

ted@Teddey:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ted@Teddey:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  account-plugin-windows-live libupstart1 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic
0 upgraded, 0 newly installed, 6 to remove and 8 not upgraded.
After this operation, 280 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 417467 files and directories currently installed.)
Removing account-plugin-windows-live (0.11+14.04.20140409.1-0ubuntu2) ...
Removing libupstart1:amd64 (1.12.1-0ubuntu4.2) ...
Removing linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Removing linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1) ...
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-38-generic
Found initrd image: /boot/initrd.img-3.16.0-38-generic
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found initrd image: /boot/initrd.img-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Found linux image: /boot/vmlinuz-3.16.0-31-generic
Found initrd image: /boot/initrd.img-3.16.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-38-generic
Found initrd image: /boot/initrd.img-3.16.0-38-generic
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found initrd image: /boot/initrd.img-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Found linux image: /boot/vmlinuz-3.16.0-31-generic
Found initrd image: /boot/initrd.img-3.16.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...


```

**sudo apt-get -f install**
```

ted@Teddey:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


```

**sudo dpkg -C**
```

ted@Teddey:~$ sudo dpkg -C

```

---

### Post by Bucky Ball on 2015-05-27
Yep, all looks good. ;) I also get no output from the last command so presuming that is correct.

I'd go for these three now and get your install completely up to date as you have upgrades waiting (the Software Update might be bugging you to update already):

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This will NOT upgrade your release to 14.10, only the 14.04 software installed in your current release.

There might have been a kernel upgrade so reboot and have a look and try.

---

### Post by Ted_Tommikoski on 2015-05-27
Thank you for sticking by - making sure that I'm good before ditching me :cool: Very reassuring. 


sudo apt-get update
```

ted@Teddey:~$ sudo apt-get update
[sudo] password for ted: 
Ign http://se.archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://extras.ubuntu.com trusty Release.gpg                              
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]         
Ign http://se.archive.ubuntu.com trusty-updates InRelease                      
Hit http://extras.ubuntu.com trusty Release                                  
Ign http://se.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty/main Sources                             
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:2 http://security.ubuntu.com trusty-security Release [63,5 kB]             
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://se.archive.ubuntu.com trusty Release.gpg                            
Get:3 http://se.archive.ubuntu.com trusty-updates Release.gpg [933 B]         
Get:4 http://se.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Hit http://se.archive.ubuntu.com trusty Release                                
Get:5 http://se.archive.ubuntu.com trusty-updates Release [63,5 kB]            
Get:6 http://se.archive.ubuntu.com trusty-backports Release [63,5 kB]          
Hit http://se.archive.ubuntu.com trusty/main Sources                           
Hit http://se.archive.ubuntu.com trusty/restricted Sources                     
Get:7 http://security.ubuntu.com trusty-security/main Sources [81,9 kB]        
Hit http://se.archive.ubuntu.com trusty/universe Sources                       
Get:8 http://security.ubuntu.com trusty-security/restricted Sources [2 061 B]  
Get:9 http://security.ubuntu.com trusty-security/universe Sources [25,2 kB]    
Get:10 http://security.ubuntu.com trusty-security/multiverse Sources [2 333 B] 
Get:11 http://security.ubuntu.com trusty-security/main amd64 Packages [273 kB] 
Hit http://se.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://se.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://se.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://se.archive.ubuntu.com trusty/universe amd64 Packages                
Ign http://dl.google.com stable InRelease                                      
Hit http://se.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://se.archive.ubuntu.com trusty/main i386 Packages                     
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://dl.google.com stable Release.gpg                           
Hit http://se.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://se.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://se.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Get:12 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8 875 B]
Hit http://dl.google.com stable/main i386 Packages                             
Get:13 http://security.ubuntu.com trusty-security/universe amd64 Packages [105 kB]
Hit http://se.archive.ubuntu.com trusty/main Translation-en                    
Hit http://se.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://se.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://se.archive.ubuntu.com trusty/universe Translation-en                
Get:14 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3 681 B]
Get:15 http://se.archive.ubuntu.com trusty-updates/main Sources [206 kB]       
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:16 http://security.ubuntu.com trusty-security/main i386 Packages [261 kB]  
Get:17 http://se.archive.ubuntu.com trusty-updates/restricted Sources [3 433 B]
Get:18 http://se.archive.ubuntu.com trusty-updates/universe Sources [117 kB]   
Get:19 http://security.ubuntu.com trusty-security/restricted i386 Packages [8 846 B]
Get:20 http://security.ubuntu.com trusty-security/universe i386 Packages [105 kB]
Get:21 http://se.archive.ubuntu.com trusty-updates/multiverse Sources [5 152 B]
Get:22 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3 840 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:23 http://se.archive.ubuntu.com trusty-updates/main amd64 Packages [525 kB]
Get:24 http://se.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11,8 kB]
Get:25 http://se.archive.ubuntu.com trusty-updates/universe amd64 Packages [281 kB]
Get:26 http://se.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11,9 kB]
Get:27 http://se.archive.ubuntu.com trusty-updates/main i386 Packages [512 kB] 
Get:28 http://se.archive.ubuntu.com trusty-updates/restricted i386 Packages [11,8 kB]
Get:29 http://se.archive.ubuntu.com trusty-updates/universe i386 Packages [281 kB]
Get:30 http://se.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12,1 kB]
Hit http://se.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://se.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://se.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://se.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:31 http://se.archive.ubuntu.com trusty-backports/main Sources [5 851 B]    
Get:32 http://se.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:33 http://se.archive.ubuntu.com trusty-backports/universe Sources [26,2 kB]
Get:34 http://se.archive.ubuntu.com trusty-backports/multiverse Sources [1 898 B]
Get:35 http://se.archive.ubuntu.com trusty-backports/main amd64 Packages [6 256 B]
Get:36 http://se.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:37 http://se.archive.ubuntu.com trusty-backports/universe amd64 Packages [29,9 kB]
Get:38 http://se.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1 245 B]
Get:39 http://se.archive.ubuntu.com trusty-backports/main i386 Packages [6 285 B]
Get:40 http://se.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:41 http://se.archive.ubuntu.com trusty-backports/universe i386 Packages [29,9 kB]
Get:42 http://se.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1 249 B]
Hit http://se.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://se.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://se.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://se.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://se.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://se.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://se.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://se.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3 160 kB in 34s (92,4 kB/s)                                            
Reading package lists... Done


```


**sudo apt-get upgrade**
```

ted@Teddey:~$ sudo apt-get upgrade
[sudo] password for ted: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  google-chrome-stable gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons
  gvfs-fuse gvfs-libs libldap-2.4-2
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 49,1 MB of archives.
After this operation, 35,8 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 43.0.2357.81-1 [48,3 MB]
Get:2 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main libldap-2.4-2 amd64 2.4.31-1+nmu2ubuntu8.1 [153 kB]
Get:3 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-bin amd64 1.20.3-0ubuntu1 [50,8 kB]
Get:4 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-backends amd64 1.20.3-0ubuntu1 [271 kB]
Get:5 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-fuse amd64 1.20.3-0ubuntu1 [13,2 kB]
Get:6 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs amd64 1.20.3-0ubuntu1 [89,5 kB]
Get:7 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-daemons amd64 1.20.3-0ubuntu1 [109 kB]
Get:8 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-libs amd64 1.20.3-0ubuntu1 [106 kB]
Get:9 http://se.archive.ubuntu.com/ubuntu/ trusty-updates/main gvfs-common all 1.20.3-0ubuntu1 [42,4 kB]
Fetched 49,1 MB in 49s (999 kB/s)                                              
(Reading database ... 388058 files and directories currently installed.)
Preparing to unpack .../libldap-2.4-2_2.4.31-1+nmu2ubuntu8.1_amd64.deb ...
Unpacking libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu8.1) over (2.4.31-1+nmu2ubuntu8) ...
Preparing to unpack .../google-chrome-stable_43.0.2357.81-1_amd64.deb ...
Unpacking google-chrome-stable (43.0.2357.81-1) over (43.0.2357.65-1) ...
Preparing to unpack .../gvfs-bin_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-bin (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-backends_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-backends (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-fuse_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-fuse (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs:amd64 (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-daemons_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-daemons (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-libs_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-libs:amd64 (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-common_1.20.3-0ubuntu1_all.deb ...
Unpacking gvfs-common (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu8.1) ...
Setting up google-chrome-stable (43.0.2357.81-1) ...
Setting up gvfs-common (1.20.3-0ubuntu1) ...
Setting up gvfs-bin (1.20.3-0ubuntu1) ...
Setting up gvfs-libs:amd64 (1.20.3-0ubuntu1) ...
Setting up gvfs-daemons (1.20.3-0ubuntu1) ...
Setting up gvfs:amd64 (1.20.3-0ubuntu1) ...
Setting up gvfs-backends (1.20.3-0ubuntu1) ...
Setting up gvfs-fuse (1.20.3-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

```
**sudo apt-get dist-upgrade**
```

ted@Teddey:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@Teddey:~$ 

```

---

### Post by Bashing-om on 2015-05-27
Ted_Tommikoski; Outstanding !

You look "good to go" !

I expect this matter is now concluded, and if there is nothing else to express;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-05-27
> **Bashing-om said:**
> Ted_Tommikoski; Outstanding !

You look "good to go" !

I expect this matter is now concluded, and if there is nothing else to express;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

^^^
This. ;)

---

### Post by Ted_Tommikoski on 2015-05-28
Thank you for your support - you guys rock  :guitar:

---

### Post by mcerruds on 2015-08-05
> **sandyd said:**
> Possible that archive is corrupt.

```

sudo rm "/var/cache/apt/archives/linux-headers-3.16.0-38_3.16.0-38.52~14.04.1_all.deb"
sudo apt-get -f install
```

Hello guys sorry for jumping into the wagon at this time. I had the same problem with another package, tried this to delete the corrupt file, apt-got that and voila! Thanks a lot!

---

