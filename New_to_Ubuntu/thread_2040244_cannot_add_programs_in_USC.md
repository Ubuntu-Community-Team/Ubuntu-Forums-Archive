---
title: "cannot add programs in USC"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by chunk15 on 2012-08-10
cannot add or remove? programs in ubuntu software center.  Seems that there is 1 program (poker network) that is not fully removed.  From reading other threads it seemed the following would be helpful to share, however, I am very new to the terminal.

**sudo apt-get update**:
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg [198B]  
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed Release.gpg [198B]         
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release                               
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release [58.3kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed Release [58.3kB]             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [431kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages [633kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources [226kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [127kB]          
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [133kB]     
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]  
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages [275kB]    
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [40.7kB]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,370B]  
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,316B]   
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources [102kB]     
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB]
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources [5,818B]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/restricted Packages [14B]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/main Packages [132kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/multiverse Packages [14B]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/universe Packages [19.6kB]
Fetched 2,330kB in 7s (292kB/s)                                                
Reading package lists... Done
[B]
sudo apt-get upgrade[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libexpat1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 139kB of archives.
After this operation, 8,192B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main libexpat1 2.0.1-7ubuntu1.1 [139kB]
Fetched 139kB in 0s (196kB/s)
(Reading database ... 603023 files and directories currently installed.)
Preparing to replace libexpat1 2.0.1-7ubuntu1 (using .../libexpat1_2.0.1-7ubuntu1.1_i386.deb) ...
Unpacking replacement libexpat1 ...
Setting up python-poker-network (1.7.7-1) ...
/usr/bin/rsync --exclude CVS -a -v --ignore-existing /usr/share/poker-network/conf/ /etc/poker-network/
sending incremental file list

sent 93 bytes  received 12 bytes  210.00 bytes/sec
total size is 14004  speedup is 133.37
Config::checkVersion: /etc/poker-network/poker.bot.xml: up to date
Config::checkVersion: /etc/poker-network/poker.client.xml: up to date
Config::checkVersion: /etc/poker-network/poker.server.xml: up to date
dbconfig-common: writing config to /etc/dbconfig-common/python-poker-network.conf
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/twisted/plugin.py", line 200, in getPlugins
    allDropins = getCache(package)
  File "/usr/lib/python2.6/dist-packages/twisted/plugin.py", line 162, in getCache
    (pluginModule.filePath.getModificationTime() >= lastCached)):
  File "/usr/lib/python2.6/dist-packages/twisted/python/filepath.py", line 504, in getModificationTime
    self.restat()
  File "/usr/lib/python2.6/dist-packages/twisted/python/filepath.py", line 468, in restat
    self.statinfo = stat(self.path)
OSError: [Errno 2] No such file or directory: '/usr/lib/python2.6/dist-packages/twisted/plugins/notestplugin.py'
dpkg: error processing python-poker-network (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libexpat1 (2.0.1-7ubuntu1.1) ...

Processing triggers for python-central ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python-poker-network
E: Sub-process /usr/bin/dpkg returned an error code (1)
shonk@shonk-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-smartpm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-poker-network (1.7.7-1) ...
/usr/bin/rsync --exclude CVS -a -v --ignore-existing /usr/share/poker-network/conf/ /etc/poker-network/
sending incremental file list

sent 93 bytes  received 12 bytes  210.00 bytes/sec
total size is 14004  speedup is 133.37
Config::checkVersion: /etc/poker-network/poker.bot.xml: up to date
Config::checkVersion: /etc/poker-network/poker.client.xml: up to date
Config::checkVersion: /etc/poker-network/poker.server.xml: up to date
dbconfig-common: writing config to /etc/dbconfig-common/python-poker-network.conf
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/twisted/plugin.py", line 200, in getPlugins
    allDropins = getCache(package)
  File "/usr/lib/python2.6/dist-packages/twisted/plugin.py", line 162, in getCache
    (pluginModule.filePath.getModificationTime() >= lastCached)):
  File "/usr/lib/python2.6/dist-packages/twisted/python/filepath.py", line 504, in getModificationTime
    self.restat()
  File "/usr/lib/python2.6/dist-packages/twisted/python/filepath.py", line 468, in restat
    self.statinfo = stat(self.path)
OSError: [Errno 2] No such file or directory: '/usr/lib/python2.6/dist-packages/twisted/plugins/notestplugin.py'
dpkg: error processing python-poker-network (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 python-poker-network
E: Sub-process /usr/bin/dpkg returned an error code (1)

**sudo dpkg --configure -a**
Setting up python-poker-network (1.7.7-1) ...
/usr/bin/rsync --exclude CVS -a -v --ignore-existing /usr/share/poker-network/conf/ /etc/poker-network/
sending incremental file list

sent 93 bytes  received 12 bytes  210.00 bytes/sec
total size is 14004  speedup is 133.37
Config::checkVersion: /etc/poker-network/poker.bot.xml: up to date
Config::checkVersion: /etc/poker-network/poker.client.xml: up to date
Config::checkVersion: /etc/poker-network/poker.server.xml: up to date
dbconfig-common: writing config to /etc/dbconfig-common/python-poker-network.conf
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/twisted/plugin.py", line 200, in getPlugins
    allDropins = getCache(package)
  File "/usr/lib/python2.6/dist-packages/twisted/plugin.py", line 162, in getCache
    (pluginModule.filePath.getModificationTime() >= lastCached)):
  File "/usr/lib/python2.6/dist-packages/twisted/python/filepath.py", line 504, in getModificationTime
    self.restat()
  File "/usr/lib/python2.6/dist-packages/twisted/python/filepath.py", line 468, in restat
    self.statinfo = stat(self.path)
OSError: [Errno 2] No such file or directory: '/usr/lib/python2.6/dist-packages/twisted/plugins/notestplugin.py'
dpkg: error processing python-poker-network (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 python-poker-network


Any advice would be appreciated. Thanks in advance.

---

### Post by cariboo on 2012-08-10
As the package is broken, I'd suggest just removing it using the following command, in a terminal type:

```
sudo apt-get purge python-poker-network
```

I'm assuming that you don't want to run a poker network server, as that is what the package is.

---

### Post by chunk15 on 2012-08-10
Thanks for the response.  When I did that command, I received the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  python-poker-network*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,675kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 602875 files and directories currently installed.)
Removing python-poker-network ...
dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)

not quite sure what all of that means, except it looks like it didnt' work?

---

