---
title: "Java install"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by virgodave61 on 2012-07-31
I tried to install Java plugin with:
sudo apt-get install sun-java6-plugin

and get

The following packages have unmet dependencies:
 sun-java6-plugin : Depends: xulrunner-1.9 but it is not installable
E: Broken packages

Tried fixing broken packages thru Synaptic, but does nothing.

I've been searching the net for days trying to get Java done to no avail.

---

### Post by Miljet on 2012-07-31
Sun Java is now owned by Oracle. It is no longer in the Ubuntu repositories. Here is a link to one guide to installing Oracle Java

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by virgodave61 on 2012-08-01
I followed those instructions very carefully, and this is what happened.
```
dave@ubuntu-desktop:~$ cd
dave@ubuntu-desktop:~$ sudo mkdir -p  /usr/lib/jvm/ #just in case
[sudo] password for dave: 
dave@ubuntu-desktop:~$ sudo mv java-7-oracle/ /usr/lib/jvm/
dave@ubuntu-desktop:~$ sudo add-apt-repository ppa:nilarimogard/webupd8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 1DB29AFFF6C70907B57AA31F531EE72F4C9D234C
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: key 4C9D234C: public key "Launchpad webupd8" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
dave@ubuntu-desktop:~$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg [198 B]                      
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release [39.8 kB]                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [39.8 kB]              
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg [189 B]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,736 B]                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [14.8 kB]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [1,292 B]  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [39.8 kB]            
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources [4,104 B]            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [106 kB]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [21.9 kB]             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources [862 kB]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release [65.9 kB]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [1,633 B]  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [27.5 kB]    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,104 B]         
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [862 kB]                
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [350 kB]   
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [4,787 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [97.2 kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [3,560 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,380 kB]          
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]        
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]        
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]   
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,021 kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [2,103 B] 
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [167 kB]        
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [3,106 B] 
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [48.5 kB]   
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [484 kB]  
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [6,261 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [156 kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [6,380 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse i386 Packages [179 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en               
Fetched 15.0 MB in 15min 9s (16.5 kB/s)                                        
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dave@ubuntu-desktop:~$ sudo apt-get install update-java
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-kb-dev libxdmcp-dev xtrans-dev
  x11proto-core-dev libxt-dev tzdata-java x11proto-input-dev
  libpthread-stubs0-dev libxau-dev libpthread-stubs0 libx11-dev
  ca-certificates-java libxcb1-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  update-java
0 upgraded, 1 newly installed, 0 to remove and 153 not upgraded.
Need to get 4,318 B of archives.
After this operation, 45.1 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) natty/main update-java all 0.5.2-2~webupd8 [4,318 B]
Fetched 4,318 B in 4s (909 B/s)  
Selecting previously deselected package update-java.
(Reading database ... 177062 files and directories currently installed.)
Unpacking update-java (from .../update-java_0.5.2-2~webupd8_all.deb) ...
Setting up update-java (0.5.2-2~webupd8) ...
dave@ubuntu-desktop:~$ sudo update-java
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/appletviewer to provide /usr/bin/appletviewer (appletviewer) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/apt to provide /usr/bin/apt (apt) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/extcheck to provide /usr/bin/extcheck (extcheck) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/idlj to provide /usr/bin/idlj (idlj) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jar to provide /usr/bin/jar (jar) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/java to provide /usr/bin/java (java) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javac to provide /usr/bin/javac (javac) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javah to provide /usr/bin/javah (javah) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javap to provide /usr/bin/javap (javap) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jhat to provide /usr/bin/jhat (jhat) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jps to provide /usr/bin/jps (jps) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jsadebugd to provide /usr/bin/jsadebugd (jsadebugd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jvisualvm to provide /usr/bin/jvisualvm (jvisualvm) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/native2ascii to provide /usr/bin/native2ascii (native2ascii) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/schemagen to provide /usr/bin/schemagen (schemagen) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/wsgen to provide /usr/bin/wsgen (wsgen) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/wsimport to provide /usr/bin/wsimport (wsimport) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/xjc to provide /usr/bin/xjc (xjc) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode.
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode.
update-alternatives: warning: skip creation of /usr/share/binfmts/jar because associated file /usr/lib/jvm/java-7-oracle/jre/lib/jar.binfmt (of link group jexec) doesn't exist.
dave@ubuntu-desktop:~$ java -version
bash: /usr/bin/java: cannot execute binary file
dave@ubuntu-desktop:~$ javac -version
bash: /usr/bin/javac: cannot execute binary file
dave@ubuntu-desktop:~$
```

Did a search of file system and found a copy of jar.binfmt so I pasted a copy of it into: /usr/lib/jvm/java-7-oracle/jre/lib/ then ran: sudo apt-get install update-java again then the following:
```
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-java is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-kb-dev libxdmcp-dev xtrans-dev
  x11proto-core-dev libxt-dev tzdata-java x11proto-input-dev
  libpthread-stubs0-dev libxau-dev libpthread-stubs0 libx11-dev
  ca-certificates-java libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 153 not upgraded.
So I did what it said:
dave@ubuntu-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ca-certificates-java libice-dev libpthread-stubs0 libpthread-stubs0-dev
  libsm-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxt-dev
  tzdata-java x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev
0 upgraded, 0 newly installed, 15 to remove and 153 not upgraded.
After this operation, 19.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 177064 files and directories currently installed.)
Removing ca-certificates-java ...
Removing libxt-dev ...
Removing libsm-dev ...
Removing libice-dev ...
Removing libx11-dev ...
Removing libxcb1-dev ...
Removing libpthread-stubs0-dev ...
Removing libpthread-stubs0 ...
Removing libxau-dev ...
Removing libxdmcp-dev ...
Removing tzdata-java ...
Removing x11proto-input-dev ...
Removing x11proto-core-dev ...
Removing x11proto-kb-dev ...
Removing xtrans-dev ...
Processing triggers for man-db ...
dave@ubuntu-desktop:~$ java -version
bash: /usr/bin/java: cannot execute binary file
```

---

### Post by anewguy on 2012-08-01
Check the permissions of /usr/bin/java  - it could be that the execution bit is not set.  I don't know a thing about java so I don't know what it should look like.

---

### Post by virgodave61 on 2012-08-01
Did:

dave@ubuntu-desktop:~$ sudo ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2012-08-01 04:14 /usr/bin/java -> /etc/alternatives/java

is this right?

If I use the file manager or gedit it shows me /usr/bin/java folder doesn't exist.

So I tried:

mkdir /usr/bin/java
mkdir: cannot create directory `/usr/bin/java': File exists

A java file is in /usr/bin but not a directory, I was thinking I could just copy the jar.binfmt file into it.

Now totally confused, I'm a noob of coarse so that is easy to do,but have learned alot about Linux with all the problems I've had

---

### Post by Cheesemill on 2012-08-01
The easy way to install Oracle Java:
```
 
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

```

---

### Post by virgodave61 on 2012-08-01
Tried what you said again about permissions, been looking at a book:

dave@ubuntu-desktop:~$ ls -ld /usr/bin/java/
ls: cannot access /usr/bin/java/: Not a directory

---

### Post by Karlchen on 2012-08-01
Hello, virgodave61.

About the **_file_** /usr/bin/java, a symlink as a matter of fact:

```
karl@pangolin:/usr/bin$ ls -al java
lrwxrwxrwx 1 root root 22 Jul 28 20:14 java -> /etc/alternatives/java
``` OK, so let us check /etc/alternatives/java.
```
karl@pangolin:/usr/bin$ ls -al /etc/alternatives/java
lrwxrwxrwx 1 root root 33 Jul 28 20:14 /etc/alternatives/java -> /opt/java/32/jre1.6.0_33/bin/java
```Yet, another symlink pointing to /opt/java/32/jre1.6.0_33/bin/java. 

This path will look differently if you have installed Java 7.

The crucial thing is ```
java -version
java version "1.6.0_33"
Java(TM) SE Runtime Environment (build 1.6.0_33-b03)
Java HotSpot(TM) Server VM (build 20.8-b03, mixed mode)
``` should simply work and return the installed Java version. 1.6.0_33 in my case, 7-something in your case.

Similarly, visiting this webpage, [**Verified Java Version**](http://www.java.com/en/download/installed.jsp) and clicking on the button [Verify Java Version]  should take a while and then display the confirmation that you have the recommended Java version installed.

Kind regards,
Karl

---

### Post by virgodave61 on 2012-08-01
Thanks,
I will have to wait a few minutes, I'm trying Cheesemill's suggestion, terminal is running sudo add-apt-repository ppa:webupd8team/java at the moment

Now running sudo apt-get update

sudo apt-get install oracle-java7-installer is running.

OMG I'm so F'in happy check this out!

```
dave@ubuntu-desktop:~$ java -version
java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b05)
Java HotSpot(TM) Server VM (build 23.1-b03, mixed mode)
dave@ubuntu-desktop:~$ javac -version
javac 1.7.0_05
```
 
Went to test Java page and it says Java is working !!!!!!!!!!!!!!:D

Thanks to everyone for there help, esp. Cheesemill for a way that works, and to Karlchen for forcing me to learn what symlink's are!

You guys are awesome!:P

---

### Post by JoeTheJuggler on 2012-08-03
I'm having trouble enabling Java.  (And it had been working fine up until recently, so I'm not sure what happened.)

When I type ~$ java -version, I get:

java version "1.7.0_03"
OpenJDK Runtime Environment (IcedTea7 2.1.1pre) (7~u3-2.1.1~pre1-1ubuntu3)
OpenJDK 64-Bit Server VM (build 22.0-b10, mixed mode)

In both my browsers (Chromium and Firefox) I have IceTea-Web plugin enabled.  

When I go to the Java test page, I just get blank white space where the applet should be (ditto with the NY Times crossword applet, which is my main concern).  If I disable IceTea, I get the puzzle piece icon (and grey box where the applet is) telling me the plug-in is disabled.

What am I missing?

---

### Post by Cheesemill on 2012-08-03
You've probably come across the situation where some websites refuse to acknowledge the open source version of Java (OpenJDK), even though it is the reference standards compliant version that every site should work with.

Try installing the closed source Oracle version instead, this should solve your problem.

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by JoeTheJuggler on 2012-08-03
Thanks.  I'm trying this.  

I don't understand why support would have changed suddenly (and apparently so universally).  Things worked fine for me for months up until a few days ago.

Thanks, Cheesemill.  That did the trick.  

After installing Oracle's Java, "java -version" told me I was still running the OpenJDK version, so I had to do

```
sudo update-alternatives --config java
```

and select the Oracle version.

---

