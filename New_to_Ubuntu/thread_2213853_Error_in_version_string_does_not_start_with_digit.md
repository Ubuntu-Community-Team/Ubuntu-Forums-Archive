---
title: "Error in version string: does not start with digit"
date: 2014-03-29
forum: New to Ubuntu
---

### Post by aleva132 on 2014-03-29
So lately, when I try to update, a completely different package causes an abort.  I've tried and tried to remove that package and this is the result of the latest attempt:

```
$ sudo dpkg --force-bad-version -P robotfindskitten
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 36147 package 'robotfindskitten':
 error in Version string 'v1600003_201b-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/updates/0000' near line 8 package 'robotfindskitten':
 error in Version string 'v1600003_201b-1': version number does not start with digit


```

Please help.  I can't run security updates until I can get around this frakking thing.

---

### Post by panorain on 2014-03-29
Try 

sudo apt-get clean 
sudo dpkg --clear-avail 

and then try the update again and see if that clears it. 

I referenced the above commands from this website.

I hope this may help you.

[http://ubuntu.5.x6.nabble.com/ubuntu12-04-only-version-number-does-not-start-with-digit-td4994116.html](http://ubuntu.5.x6.nabble.com/ubuntu12-04-only-version-number-does-not-start-with-digit-td4994116.html)

Thanks,

---

### Post by aleva132 on 2014-03-29
tried that, here are the outputs:

```
~$ sudo apt-get clean
:~$ sudo dpkg --clear-avail
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ca-certificates ca-certificates-java clamav clamav-base clamav-freshclam
  libclamav6 libsmbclient libwbclient0 openssh-client samba-common
  samba-common-bin smbclient ssh-askpass-gnome winbind
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.8MB of archives.
After this operation, 1,831kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main ca-certificates 20130906ubuntu0.10.04.1 [194kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main openssh-client 1:5.3p1-3ubuntu7.1 [758kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main ca-certificates-java 20110426ubuntu0.10.04.2 [8,216B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libclamav6 0.98.1+dfsg-4ubuntu1~ubuntu10.04.2 [3,964kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main clamav-base 0.98.1+dfsg-4ubuntu1~ubuntu10.04.2 [330kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main clamav-freshclam 0.98.1+dfsg-4ubuntu1~ubuntu10.04.2 [341kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main clamav 0.98.1+dfsg-4ubuntu1~ubuntu10.04.2 [366kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main smbclient 2:3.4.7~dfsg-1ubuntu3.14 [11.4MB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main winbind 2:3.4.7~dfsg-1ubuntu3.14 [4,389kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main samba-common 2:3.4.7~dfsg-1ubuntu3.14 [402kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libwbclient0 2:3.4.7~dfsg-1ubuntu3.14 [108kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main samba-common-bin 2:3.4.7~dfsg-1ubuntu3.14 [4,800kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main ssh-askpass-gnome 1:5.3p1-3ubuntu7.1 [87.4kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libsmbclient 2:3.4.7~dfsg-1ubuntu3.14 [1,656kB]
Fetched 28.8MB in 1min 54s (252kB/s)                                           
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 36147 package 'robotfindskitten':
 error in Version string 'v1600003_201b-1': version number does not start with digit
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package `tzdata' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

It didn't work.  If it helps, I'm using 10.04 LTS.

---

### Post by panorain on 2014-03-30
Now I feel bad for not being able to help more and even posting. For what it's worth I subscribed to the thread and I will keep looking into the problem your having. 

Thank you,

---

### Post by panorain on 2014-04-02
Could you please try the following command in terminal.

apt-get update

apt-get upgrade

preceded by sudo.

Thanks,

Please let me know what your results are if you have the time.

---

### Post by aleva132 on 2014-04-03
Here they are:
```
:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Get:1 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/evorts/stable/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/spring/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Get:2 http://us.archive.ubuntu.com lucid-security Release.gpg [198B] 
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                       
Get:3 http://us.archive.ubuntu.com lucid-updates Release [58.3kB]    
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://us.archive.ubuntu.com lucid-security Release [57.3kB]             
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.getdeb.net lucid-getdeb Release.gpg                         
Hit http://ppa.launchpad.net lucid/main Packages                             
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/main Packages                         
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/games Translation-en_US     
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                  
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                   
Get:5 http://us.archive.ubuntu.com lucid-updates/main Packages [742kB]         
Hit http://archive.getdeb.net lucid-getdeb Release                             
Hit http://archive.getdeb.net lucid-getdeb/games Packages                      
Hit http://archive.canonical.com lucid/partner Packages                     
Hit http://archive.canonical.com lucid/partner Sources
Get:6 http://us.archive.ubuntu.com lucid-updates/restricted Packages [4,630B]  
Get:7 http://us.archive.ubuntu.com lucid-updates/main Sources [336kB]          
Get:8 http://us.archive.ubuntu.com lucid-updates/restricted Sources [2,196B]   
Get:9 http://us.archive.ubuntu.com lucid-updates/universe Packages [297kB]     
Get:10 http://us.archive.ubuntu.com lucid-updates/universe Sources [110kB]     
Get:11 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [11.5kB] 
Get:12 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [5,817B]  
Get:13 http://us.archive.ubuntu.com lucid-security/main Packages [547kB]       
Get:14 http://us.archive.ubuntu.com lucid-security/restricted Packages [2,867B]
Get:15 http://us.archive.ubuntu.com lucid-security/main Sources [241kB]        
Get:16 http://us.archive.ubuntu.com lucid-security/restricted Sources [1,267B] 
Get:17 http://us.archive.ubuntu.com lucid-security/universe Packages [150kB]   
Get:18 http://us.archive.ubuntu.com lucid-security/universe Sources [46.6kB]   
Get:19 http://us.archive.ubuntu.com lucid-security/multiverse Packages [5,366B]
Get:20 http://us.archive.ubuntu.com lucid-security/multiverse Sources [2,347B] 
Fetched 2,620kB in 40s (64.6kB/s)                                              
Reading package lists... Done
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ca-certificates ca-certificates-java clamav clamav-base clamav-freshclam
  libclamav6 libnss3-1d libnss3-1d-dbg libsmbclient libwbclient0
  openssh-client samba-common samba-common-bin smbclient ssh-askpass-gnome
  winbind
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,685kB/33.5MB of archives.
After this operation, 1,921kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libnss3-1d-dbg 3.15.4-0ubuntu0.10.04.2 [3,433kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libnss3-1d 3.15.4-0ubuntu0.10.04.2 [1,253kB]
Fetched 4,685kB in 1min 6s (70.9kB/s)                                          
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 36147 package 'robotfindskitten':
 error in Version string 'v1600003_201b-1': version number does not start with digit
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package `tzdata' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


```
Honestly, at this point I'm wondering if there's a way to manually remove the entry.

---

### Post by steeldriver on 2014-04-03
The fatal error seems to be the missing fileslist file for package tzdata - you can probably regenerate that from the deb file (you may have a copy of the deb in your local cache, otherwise you would need to download it). Post back if you want to go that route, or look here where a similar error with the gimp package was solved --> [http://ubuntuforums.org/showthread.php?t=2193011&page=2&p=12875012#post12875012](http://ubuntuforums.org/showthread.php?t=2193011&page=2&p=12875012#post12875012)

If the 'robotfindskitten' package continues to prevent update after that, you could try reverting to the status-old file.

Bear in mind that only the **server **version of Lucid is still supported

---

### Post by aleva132 on 2014-04-12
That worked.  My excuse for still using 10.04 is the upgrade tries to remove kde package manager then aborts when it realizes it shouldn't.

---

