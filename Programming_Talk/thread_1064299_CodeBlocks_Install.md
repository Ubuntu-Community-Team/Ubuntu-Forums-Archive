---
title: "Code::Blocks Install"
date: 2009-02-08
forum: Programming Talk
---

### Post by wagb278 on 2009-02-08
If this is in the wrong forum - please move.

Need help installing Code::Blocks.  I followed instructions (see log included).  System is Ubuntu 8.04 LTS 64-bit

THIS IS A COPY OF THE INSTALL SESSION FOR CODEBLOCKS 
```
jim@green:~$ sudo gedit /etc/apt/sources.list
jim@green:~$ wget -q http://lgp203.free.fr/public.key -O- | sudo apt-key add -
OK
jim@green:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Get:1 http://lgp203.free.fr hardy Release.gpg [189B]                           
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Get:2 http://ppa.launchpad.net hardy Release.gpg [307B]                        
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://archive.canonical.com hardy Release                                 
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://ppa.launchpad.net hardy Release                                     
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://lgp203.free.fr hardy/universe Translation-en_US                     
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages            
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages      
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages      
Hit http://us.archive.ubuntu.com hardy-updates/main Sources             
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources       
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages        
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources         
Get:4 http://lgp203.free.fr hardy Release [7209B]                       
Get:5 http://lgp203.free.fr hardy/universe Packages [9135B]
Fetched 16.8kB in 2s (6611B/s) 
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: You may want to run apt-get update to correct these problems
jim@green:~$ sudo apt-get install libcodeblocks0 codeblocks libwxshithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libwxshithlib0
jim@green:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcodeblocks0: Depends: libwxbase2.8-0 (>= 2.8.8.1) but it is not going to be installed
                  Depends: libwxgtk2.8-0 (>= 2.8.8.1) but it is not going to be installed
E: Broken packages
jim@green:~$ sudo apt-get install gdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdb is already the newest version.
The following packages were automatically installed and are no longer required:
  libtagc0 libavahi1.0-cil po-debconf intltool-debian gettext libkarma0 libnjb5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@green:~$ sudo apt-get install automake autoconf libtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autoconf is already the newest version.
autoconf set to manually installed.
The following packages were automatically installed and are no longer required:
  libtagc0 libavahi1.0-cil po-debconf intltool-debian gettext libkarma0 libnjb5
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gcj gfortran fortran95-compiler libtool-doc
Recommended packages:
  libltdl3-dev
The following NEW packages will be installed:
  automake libtool
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 860kB of archives.
After this operation, 2687kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/main automake 1:1.10.1-2 [519kB]
Get:2 http://us.archive.ubuntu.com hardy/main libtool 1.5.26-1ubuntu1 [340kB]
Fetched 860kB in 7s (119kB/s)                                                               
Selecting previously deselected package automake.
(Reading database ... 213797 files and directories currently installed.)
Unpacking automake (from .../automake_1%3a1.10.1-2_all.deb) ...
Selecting previously deselected package libtool.
Unpacking libtool (from .../libtool_1.5.26-1ubuntu1_amd64.deb) ...
Setting up automake (1:1.10.1-2) ...

Setting up libtool (1.5.26-1ubuntu1) ...
jim@green:~$ sudo apt-get install libgtk2.0-dev libxmu-dev libxxf86vm-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libgtk2.0-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  libtagc0 libavahi1.0-cil po-debconf intltool-debian gettext libkarma0 libnjb5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxmu-headers libxt-dev x11proto-xf86vidmode-dev
The following NEW packages will be installed:
  libxmu-dev libxmu-headers libxt-dev libxxf86vm-dev x11proto-xf86vidmode-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 621kB of archives.
After this operation, 2216kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com hardy/main libxmu-headers 2:1.0.4-1 [21.1kB]
Get:2 http://us.archive.ubuntu.com hardy/main libxt-dev 1:1.0.5-3 [515kB]
Get:3 http://us.archive.ubuntu.com hardy/main x11proto-xf86vidmode-dev 2.2.2-4ubuntu1 [6596B]
Get:4 http://us.archive.ubuntu.com hardy/main libxxf86vm-dev 1:1.0.1-2 [15.1kB]
Get:5 http://us.archive.ubuntu.com hardy/main libxmu-dev 2:1.0.4-1 [63.3kB]
Fetched 621kB in 5s (115kB/s)        
Selecting previously deselected package libxmu-headers.
(Reading database ... 213953 files and directories currently installed.)
Unpacking libxmu-headers (from .../libxmu-headers_2%3a1.0.4-1_all.deb) ...
Selecting previously deselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.5-3_amd64.deb) ...
Selecting previously deselected package x11proto-xf86vidmode-dev.
Unpacking x11proto-xf86vidmode-dev (from .../x11proto-xf86vidmode-dev_2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86vm-dev.
Unpacking libxxf86vm-dev (from .../libxxf86vm-dev_1%3a1.0.1-2_amd64.deb) ...
Selecting previously deselected package libxmu-dev.
Unpacking libxmu-dev (from .../libxmu-dev_2%3a1.0.4-1_amd64.deb) ...
Setting up libxmu-headers (2:1.0.4-1) ...
Setting up libxt-dev (1:1.0.5-3) ...
Setting up x11proto-xf86vidmode-dev (2.2.2-4ubuntu1) ...
Setting up libxxf86vm-dev (1:1.0.1-2) ...
Setting up libxmu-dev (2:1.0.4-1) ...
jim@green:~$ sudo apt-get install libwxbase2.8-dev wx2.8-headers libwxgtk2.8-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtagc0 libavahi1.0-cil po-debconf intltool-debian gettext libkarma0 libnjb5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwxbase2.8-0 libwxgtk2.8-0
Suggested packages:
  wx2.8-doc wx-common
The following NEW packages will be installed:
  libwxbase2.8-0 libwxbase2.8-dev libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 5575kB of archives.
After this operation, 19.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com hardy/universe libwxbase2.8-0 2.8.7.1-0ubuntu3 [678kB]
Get:2 http://us.archive.ubuntu.com hardy/universe wx2.8-headers 2.8.7.1-0ubuntu3 [1086kB]
Get:3 http://us.archive.ubuntu.com hardy/universe libwxbase2.8-dev 2.8.7.1-0ubuntu3 [91.9kB]
Get:4 http://us.archive.ubuntu.com hardy/universe libwxgtk2.8-0 2.8.7.1-0ubuntu3 [3627kB]   
Get:5 http://us.archive.ubuntu.com hardy/universe libwxgtk2.8-dev 2.8.7.1-0ubuntu3 [92.2kB] 
Fetched 5575kB in 38s (145kB/s)                                                             
Selecting previously deselected package libwxbase2.8-0.
(Reading database ... 214330 files and directories currently installed.)
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.7.1-0ubuntu3_amd64.deb) ...
Selecting previously deselected package wx2.8-headers.
Unpacking wx2.8-headers (from .../wx2.8-headers_2.8.7.1-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libwxbase2.8-dev.
Unpacking libwxbase2.8-dev (from .../libwxbase2.8-dev_2.8.7.1-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libwxgtk2.8-0.
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.7.1-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libwxgtk2.8-dev.
Unpacking libwxgtk2.8-dev (from .../libwxgtk2.8-dev_2.8.7.1-0ubuntu3_amd64.deb) ...
Setting up libwxbase2.8-0 (2.8.7.1-0ubuntu3) ...

Setting up wx2.8-headers (2.8.7.1-0ubuntu3) ...
Setting up libwxbase2.8-dev (2.8.7.1-0ubuntu3) ...

Setting up libwxgtk2.8-0 (2.8.7.1-0ubuntu3) ...

Setting up libwxgtk2.8-dev (2.8.7.1-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jim@green:~$ codeblocks
bash: codeblocks: command not found

```

When I look in Synaptic Package Manager CodeBlocks is there but not installed and attempts there say I have unmet dependencies and will not install.

I installed Anjuta and Geany but neither seem to work correctly. I can compile simple Hello World programs created in GEDIT and compiled from the command line just fine.  But I want an IDE with debugging ability. I don't like Java to execute programs so I don't intend to try Eclipse. 

Thanks for any ideas,
Jim

---

### Post by SledgeHammer_999 on 2009-02-08
The version of wxWidgets needed by Codeblocks is higher than the one available on the repos. Use this to install newer versions of wxWidgets [link](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

---

### Post by Nexusx6 on 2009-02-09
2 weeks ago I had to install Code::blocks also. I just ran this through apt-get on 8.10, so I don't know if it will work for 8.04 repos but give it a shot.

[EDIT] Nevermind. I just double checked and saw you already tried what I was about to tell you. Another option is to go to the code::blocks website and click on the ubuntu .tar.gz binaries. Inside are all the .deb's you need to get CB running, just have to click on them to install in the right order (libraries first).

By the way, I'm just asking because I know there is at least one other person in my class running Ubuntu using Code::blocks, and the timing of your question; you don't happen to be in a CSCI 14 C++ class in california? :D

---

### Post by wagb278 on 2009-02-09
Thanks for the tips - it will be a couple of days until I get to try any of these.

No I am not in a class in California

---

### Post by wagb278 on 2009-02-13
I re-ran the install sequence and I now have Code:Blocks running. I must have fat-fingered something on my first attempt

Question: I am running on a 64-bit system, how do I determine if I am using 64-bit libraries - vice 32-bit?

Thanks

---

