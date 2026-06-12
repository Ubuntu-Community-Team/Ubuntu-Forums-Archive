---
title: "Installing vsftpd"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by Marcello_De_Feo on 2013-09-22
Hi, I'm running into an issue installing anything. I've tried everything I could find on various forums and even talked to someone who works with Ubuntu and had no luck. Here's what I've tried your typical update and upgrade stuff as well as the following:

mdefeo@ubuntu:~$ sudo apt-get install vsftpd
mdefeo@ubuntu:~$ apt-cache search vsftpd
mdefeo@ubuntu:~$ apt-cache policy vsftpd
N: Unable to locate package vsftpd
mdefeo@ubuntu:~$ sudo apt-cache search vsftpd
[sudo] password for mdefeo: 
mdefeo@ubuntu:~$ sudo apt-cache policy vsftpd
N: Unable to locate package vsftpd
mdefeo@ubuntu:~$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vsftpd

mdefeo@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:b2:fb:37  
          inet addr:10.0.1.51  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb2:fb37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3193263 (3.1 MB)  TX bytes:1113250 (1.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2668358 (2.6 MB)  TX bytes:2668358 (2.6 MB)


virbr0    Link encap:Ethernet  HWaddr c6:ff:75:03:a7:33  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Does anyone have any suggestions? I'm sure it's something obvious I'm missing but I just don't know what.

---

### Post by Bashing-om on 2013-09-22
@ Marcello_De_Feo; Hi ! Welcome to the forum .

That package is available in the supported repository. Makes one wonder, what version and distro are you running ?
> 
sysop@1304mini:~$ apt-cache search vsftpd
vsftpd - lightweight, efficient FTP server written for security
ccze - A robust, modular log coloriser
ftpd - File Transfer Protocol (FTP) server
yasat - simple stupid audit tool
sysop@1304mini:~$

Is your sources list(s) in order ? What mirror are you accessing for software ?

[INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT]

---

### Post by oldos2er on 2013-09-22
Posts moved to their own thread.

---

### Post by Marcello_De_Feo on 2013-09-24
@Bashing-om: Thank you! I believe I'm running Ubuntu Server 12.04. I only installed it about two weeks ago. I can double check when I get home from work tonight.

@oldos2er Thanks. 

Do you guys think there's a chance there is a firewall issue?

---

### Post by Bashing-om on 2013-09-24
Marcello_De_Feo; Hello ;

Let's see if we can get an indication of what is not going on:
What results from terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
[INDENT][INDENT]start at the beginning of it all
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-29
Here you go:

```
mdefeo@ubuntu:~$ sudo apt-get update
[sudo] password for mdefeo: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Ign mirror://mirrors.ubuntu.com precise Release.gpg
Ign mirror://mirrors.ubuntu.com precise-updates Release.gpg          
Ign mirror://mirrors.ubuntu.com precise-backports Release.gpg        
Ign mirror://mirrors.ubuntu.com precise-security Release.gpg         
Ign mirror://mirrors.ubuntu.com precise Release                      
Ign mirror://mirrors.ubuntu.com precise-updates Release              
Ign mirror://mirrors.ubuntu.com precise-backports Release            
Ign mirror://mirrors.ubuntu.com precise-security Release             
Ign mirror://mirrors.ubuntu.com precise/main TranslationIndex        
Ign mirror://mirrors.ubuntu.com precise/multiverse TranslationIndex  
Ign mirror://mirrors.ubuntu.com precise/restricted TranslationIndex  
Ign mirror://mirrors.ubuntu.com precise/universe TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Ign mirror://mirrors.ubuntu.com precise-updates/main TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-updates/multiverse TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-updates/restricted TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-updates/universe TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-backports/main TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-backports/multiverse TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-backports/restricted TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-backports/universe TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/multiverse TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/restricted TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources
  404  Not Found
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Err mirror://mirrors.ubuntu.com precise/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-updates/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-backports/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com precise/main Translation-en_US
Ign mirror://mirrors.ubuntu.com precise/main Translation-en
Ign mirror://mirrors.ubuntu.com precise/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com precise/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Ign mirror://mirrors.ubuntu.com precise/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com precise/restricted Translation-en
Ign mirror://mirrors.ubuntu.com precise/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com precise/universe Translation-en
Ign mirror://mirrors.ubuntu.com precise-updates/main Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-updates/main Translation-en
Ign mirror://mirrors.ubuntu.com precise-updates/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-updates/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com precise-updates/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-updates/restricted Translation-en
Ign mirror://mirrors.ubuntu.com precise-updates/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-updates/universe Translation-en
Ign mirror://mirrors.ubuntu.com precise-backports/main Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-backports/main Translation-en
Ign mirror://mirrors.ubuntu.com precise-backports/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-backports/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com precise-backports/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-backports/restricted Translation-en
Ign mirror://mirrors.ubuntu.com precise-backports/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/main Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-security/main Translation-en
Ign mirror://mirrors.ubuntu.com precise-security/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-security/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com precise-security/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-security/restricted Translation-en
Ign mirror://mirrors.ubuntu.com precise-security/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com precise-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-backports/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-backports/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-backports/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-backports/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  404  Not Found


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
mdefeo@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2013-09-29
Marcello_De_Feo; Ouch !
We need to know for sure what operating system and version you have; post the out puts of terminal codes:
```

lsb_release -a
uname -a

```

Next is to look at your sources.list files
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```

Place these outputs between code tags : tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-29
Here you are:

```

mdefeo@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

mdefeo@ubuntu:~$ uname -a
Linux ubuntu 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux

mdefeo@ubuntu:~$ cat -n /etc/apt/sources.list
     1	# 
     2	deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe multiverse
     3	deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe multiverse
     4	deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe multiverse
     5	deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe multiverse
     6	# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted
     7	
     8	#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted
     9	
    10	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    11	# newer versions of the distribution.
    12	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
    13	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
    14	
    15	## Major bug fix updates produced after the final release of the
    16	## distribution.
    17	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    18	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    21	## team. Also, please note that software in universe WILL NOT receive any
    22	## review or updates from the Ubuntu security team.
    23	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    24	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    25	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    26	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    27	
    28	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    29	## team, and may not be under a free licence. Please satisfy yourself as to 
    30	## your rights to use the software. Also, please note that software in 
    31	## multiverse WILL NOT receive any review or updates from the Ubuntu
    32	## security team.
    33	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    34	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    35	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    36	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    37	
    38	## N.B. software from this repository may not have been tested as
    39	## extensively as that contained in the main release, although it includes
    40	## newer versions of some applications which may provide useful features.
    41	## Also, please note that software in backports WILL NOT receive any review
    42	## or updates from the Ubuntu security team.
    43	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    44	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    45	
    46	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    47	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    48	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    49	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    50	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    51	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    52	
    53	## Uncomment the following two lines to add software from Canonical's
    54	## 'partner' repository.
    55	## This software is not part of Ubuntu, but is offered by Canonical and the
    56	## respective vendors as a service to Ubuntu users.
    57	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    58	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    59	
    60	## Uncomment the following two lines to add software from Ubuntu's
    61	## 'extras' repository.
    62	## This software is not part of Ubuntu, but is offered by third-party
    63	## developers who want to ship their latest software.
    64	#deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    65	#deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    66	
    67	#Chromium
    68	#deb [http://ppa.launchpad.net/chromium-daily/stable/ubuntu](http://ppa.launchpad.net/chromium-daily/stable/ubuntu) precise main
    69	#deb-src [http://ppa.launchpad.net/chromium-daily/stable/ubuntu](http://ppa.launchpad.net/chromium-daily/stable/ubuntu) precise main

mdefeo@ubuntu:~$ ls -la /etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 Jul 16 14:03 .
drwxr-xr-x 6 root root 4096 Sep 13 11:19 ..
```

---

### Post by Bashing-om on 2013-09-29
Marcello_De_Feo;
Well;

these:
> 
2	deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe multiverse
3	deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe multiverse
4	deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe multiverse
5	deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe multiverse

are NOT valid sources for the package management system.
Also if this is a production server is is strongly advised NOT to enable the back port repositories.

Make a backup of the current file, and remove those lines with your favorite text editor..
then run the update routine once more.
```

sudo apt-get update
sudo apt-get upgrade

```

Advise now where you stand, I expect with the correction to the indexing database all should be well.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-29
Thanks. I added those as an attempt to solve this problem. I removed those lines. Here is the output now:

mdefeo@ubuntu:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources
  404  Not Found
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  404  Not Found


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
mdefeo@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by Bashing-om on 2013-09-29
Marcello_De_Feo; Huh ?

Are you behind a proxy ? Do you have a filewall set up ?

do this:
paste this into the address bar of your browser:
> 
[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

and tell me that you DO get a page with the heading of:
> 
Index of /

	Name	Last modified	Size
	ubuntu/	30-Sep-2013 01:03	 -


Else I will be rebooting into my 12.04

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-29
[h=1]Index of /[/h][TABLE]
[TR]
[TH][IMG]http://us.archive.ubuntu.com/icons/blank.gif[/IMG][/TH]
[TH][Name]("http://us.archive.ubuntu.com/?C=N;O=D")[/TH]
[TH][Last modified]("http://us.archive.ubuntu.com/?C=M;O=A")[/TH]
[TH][Size]("http://us.archive.ubuntu.com/?C=S;O=A")[/TH]
[/TR]
[TR]
[TH="colspan: 4"][HR][/HR][/TH]
[/TR]
[TR]
[TD][IMG]http://us.archive.ubuntu.com/icons/folder.gif[/IMG][/TD]
[TD][ubuntu/]("http://us.archive.ubuntu.com/ubuntu/")[/TD]
[TD="align: right"]30-Sep-2013 02:18[/TD]
[TD="align: right"]-[/TD]
[/TR]
[TR]
[TH="colspan: 4"][HR][/HR][/TH]
[/TR]
[/TABLE]
Apache/2.2.22 (Ubuntu) Server at us.archive.ubuntu.com Port 80

I

---

### Post by Bashing-om on 2013-09-29
Marcello_De_Feo; Beats me !

Lemme boot into 12.04 and do some comparisons.

[INDENT]sometimes I do not know, other times I wonder
[/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-29
Thanks for all of your help. This really has me stumped. I even reinstalled. I'm able to SSH in from my laptop and even ping sites:

mdefeo@ubuntu:~$ ping google.com
PING google.com (74.125.228.39) 56(84) bytes of data.
64 bytes from iad23s06-in-f7.1e100.net (74.125.228.39): icmp_req=1 ttl=55 time=13.9 ms
64 bytes from iad23s06-in-f7.1e100.net (74.125.228.39): icmp_req=2 ttl=55 time=13.7 ms
64 bytes from iad23s06-in-f7.1e100.net (74.125.228.39): icmp_req=3 ttl=55 time=13.4 ms
64 bytes from iad23s06-in-f7.1e100.net (74.125.228.39): icmp_req=4 ttl=55 time=12.5 ms

---

### Post by Bashing-om on 2013-09-29
Marcello_De_Feo; Well;

I find no fault in the current sources.list file;
We know there is no fault with the internet connectivity
We know you have access from your system to "http://us.archive.ubuntu.com"

So I must conclude there is a fault in other index files on the system.

lets try this:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo apt-get clean
sudo apt-get update

```
those indexes will be rebuilt by "apt-get update" command.

else: this is going to be a real learning experience !

[INDENT][INDENT]if at first you do not succeed (skydiving is excepted !)
 [/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-29
Marcello_De_Feo; Hey -

I am done for the spell .. will sleep on this and pursue it on my AM ...

[INDENT][INDENT]all things can happen to the good
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-30
Marcello_De_Feo; Good Morning .

I have slept on it .. and if you have not complied with my last, might be a good thing not to yet. That Might address some of the issues but I do not see how it how it could relate to the major one. In that I think  apt-get is not opening a communications port; thus the 404 error.

I will direct my efforts to finding out what port is supposed to open and how to determine that the respective port is indeed open.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-30
Marcello_De_Feo; Hey ,

I have garnered a few thoughts.
Control files:
what is contained in:
```

cat /run/resolvconf/resolv.conf
cat /etc/network/interfaces
cat /proc/sys/net/ipv4/ip_local_port_range

```
and can you get out on common ports ?
```

dig www.linode.com
host www.linode.com

```
and now .. what is the state of UFW ?
```

ufw status

```
[INDENT][INDENT]good of place as most to start again
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-30
Thanks again for your help. Sorry I disappeared last night. I had to do some stuff for work.

mdefeo@ubuntu:~$ sudo rm /var/lib/apt/lists/*
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
mdefeo@ubuntu:~$ sudo rm /var/lib/apt/lists/partial/*
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory

mdefeo@ubuntu:~$ cat /run/resolvconf/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 10.0.1.1
search hsd1.nj.comcast.net




mdefeo@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp

mdefeo@ubuntu:~$ cat /proc/sys/net/ipv4/ip_local_port_range
32768	61000

mdefeo@ubuntu:~$ dig [www.linode.com](www.linode.com)


; <<>> DiG 9.8.1-P1 <<>> [www.linode.com](www.linode.com)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15515
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;[www.linode.com](www.linode.com).			IN	A


;; ANSWER SECTION:
[www.linode.com](www.linode.com).		139	IN	A	69.164.200.202
[www.linode.com](www.linode.com).		139	IN	A	72.14.180.202
[www.linode.com](www.linode.com).		139	IN	A	72.14.191.202


;; Query time: 30 msec
;; SERVER: 10.0.1.1#53(10.0.1.1)
;; WHEN: Mon Sep 30 21:29:06 2013
;; MSG SIZE  rcvd: 80

mdefeo@ubuntu:~$ host [www.linode.com](www.linode.com)
[www.linode.com](www.linode.com) has address 69.164.200.202
[www.linode.com](www.linode.com) has address 72.14.180.202
[www.linode.com](www.linode.com) has address 72.14.191.202
[www.linode.com](www.linode.com) has IPv6 address 2600:3c00::22
[www.linode.com](www.linode.com) has IPv6 address 2600:3c00::32
[www.linode.com](www.linode.com) has IPv6 address 2600:3c00::12




mdefeo@ubuntu:~$ ufw status
ERROR: You need to be root to run this script
mdefeo@ubuntu:~$ sudo ufw status
Status: inactive

---

### Post by Bashing-om on 2013-09-30
Marcello_De_Feo; Maybe !

Are you networking such that another  computer is providing "name server" service ? (nameserver 10.0.1.1)
for reference my output:
> 
sysop@1304mini:~$ cat /run/resolvconf/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 208.180.42.68
nameserver 208.180.42.100
nameserver 0.0.0.0
sysop@1304mini:~$


maybe all we need to do is find you a name server ! However, that do beg the question as to how names are resolved to IP address as the "dig" and "host" commands resolved and your browser also !

As UFW is not a factor .. I will look elsewhere for a reason to have any ports blocked - if indeed there are any (unknown at this time).

[INDENT][INDENT]what to do, oh what to do
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-30
If I'm understanding you correctly, I'm using my laptop to SSH in (although the problem exists when I work directly on the box).

It could be the name server. How do I set that up?

---

### Post by Bashing-om on 2013-09-30
Marcello_De_Feo;
On your server I see a "nameserver" ;10.0.1.1
> 
mdefeo@ubuntu:~$ cat /run/resolvconf/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
# DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 10.0.1.1
search hsd1.nj.comcast.net

which should be another computer on your LAN. Quite frankly I am way behind the times on networking .. but I do not recognize "search hsd1.nj.comcast.net" nor understand how that could work. Is your ISP comcast ?
If so, the more reliable thing to do is call them and get the IP nameserver address direct from them.

The config files to edit have changed since I last messed with setting up internet connection .. will take me a bit to research and get up to date on the proper file to edit to change the nameserver.

I can find the docs .. and we can use google's nameserver till we can find a better alternative.

[INDENT][INDENT]worth a try
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-09-30
Comcast is my ISP. I'll get in touch with them. Thanks!

---

### Post by Marcello_De_Feo on 2013-09-30
I updated named.conf.options with this:

         forwarders {
                10.0.1.1;
        };

It didn't help anything but I thought I'd give it a shot.

---

### Post by Bashing-om on 2013-10-01
Marcello_De_Feo; Yeah .. That do explain !

I am still trying to wrap my head around the changes in how networking is now implemented.
some conflicts in my thought processes.
> 
"Editing" is as simple as using the resolvconf command line like an api.
e.g.
echo nameserver 8.8.8.8 | resolvconf -a eth0.goog
Here the . is a separator and the part after the interface is the name of the config for that interface.
And if you want to remove this name server just name the interface and configuration and use -d to delete
resolvconf -d eth0.goog
In a server/cloud scenario, this is all you need.

as opposed to the official documentation:
[https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution)

Still trying to understand how /run/resolvconf/resolv.conf &  /etc/resolv.conf are populated and originated. The "resolvconf" process must be a wonder to behold !

For consideration at this time only; do you have "resolvconf" installed ?
```

dpkg -l resolvconf

```

It has become past my witching hour here, and becoming difficult to focus my thinking. so I am calling it a night and will pick this up in my AM.

[INDENT][INDENT][INDENT]progress can be made in small steps
[/INDENT][/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-10-01
mdefeo@ubuntu:~$ dpkg -l resolvconf
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  resolvconf             1.63ubuntu16           name server information handler

---

### Post by Bashing-om on 2013-10-01
Marcello_De_Feo; Evening.

Then, I think I got a plan. Let's try:
edit the "/etc/network/interfaces" file;
make it similar:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
           dns-nameservers 8.8.8.8 8.8.4.4

```
all we are doing is appending google's nameservers to this file. - 8.8.8.8 space 8.8.4.4 -

(you did make a backup of the file prior to editing ... PPPPPPP !)
save the file and reboot ...
run:
```

sudo apt-get update ## if that runs now do:
sudo apt-get upgrade

```

[INDENT][INDENT]tell me then that all is rosey
[/INDENT][/INDENT]

---

### Post by Marcello_De_Feo on 2013-10-06
Good news. I finally gave up and reinstalled for a third time and everything worked fine. I don't know what changed. I did everything the same but it works now. Thank you so much for all of your help!

---

### Post by Bashing-om on 2013-10-06
Marcello_De_Feo; Great ! That is one sure way to fix !

Please mark the thread as "solved" 1st post ->thread tools, This aides others in seeking a solution and helps keep the forum tidy.

[INDENT]ain't ubuntu wonderful[/INDENT]

---

### Post by Marcello_De_Feo on 2013-10-07
Will do. Thanks!

---

