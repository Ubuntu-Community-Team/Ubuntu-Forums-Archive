---
title: "broken package manager for natty 11.04"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by monsterwizard on 2012-01-11
I have ubuntu natty narhwal 11.04 and Ive just tried to update my programs, I did and now it says that my package manager is broken.  I looked up some help on this forum and followed the instructions but very early on on following the steps I started to get different results than the other guy who had the same problem, 
first I tried 
sudo apt-get install -fand it didnt work, then I switched it around like the guy said to
sudo apt-get -f install
And got this, 
owner@ubuntu:~$ sudo apt-get -f install
[sudo] password for owner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  update-manager
The following packages will be upgraded:
  update-manager
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0 B/650 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: reading package info file '/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
owner@ubuntu:~$ 

so I then tried the other suggestion, 
sudo dpkg --configure -aand got this,

owner@ubuntu:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.38-11-generic (2.6.38-11.50) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.150.3); however:
  Version of update-manager-core on system is 1:0.150.5.1.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-11-generic
 update-manager
owner@ubuntu:~$ 

Im a beginner who just did this bit of research after hours of going in circles on my own and looked up help on this forum, but I cant seem to get a hold of the problem or fix it, can someone help me please? it would be greatly appreciated,
Scott

---

### Post by raja.genupula on 2012-01-11
sudo apt-get clean
sudo apt-get install -f
sudo apt-get update

execute all those things one by one and give the output what you got


all the best.

---

### Post by monsterwizard on 2012-01-11
Ok, the first command , sudo apt-get clean didnt give me any errors, then the sudo apt-get install -f did,
it gave me,
owner@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  update-manager
The following packages will be upgraded:
  update-manager
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 650 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main update-manager all 1:0.150.5.1 [650 kB]
Fetched 650 kB in 3s (184 kB/s)          
dpkg: error: reading package info file '/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
then I tried the sudo apt-get update command in the terminal and everything was gravy for that one.

---

### Post by raja.genupula on 2012-01-11
hi do this and let me know what it give back

sudo dpkg --clear-avail
sudo apt-get update

and if error still appears then use this 
[http://ubuntuforums.org/showpost.php?p=7943852&postcount=6](http://ubuntuforums.org/showpost.php?p=7943852&postcount=6)

all the best.:):)

---

### Post by monsterwizard on 2012-01-11
ok, I did those and it was all dandy then I tried to do this,
owner@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  update-manager
The following packages will be upgraded:
  update-manager
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0 B/650 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 174769 files and directories currently installed.)
Preparing to replace update-manager 1:0.150.3 (using .../update-manager_1%3a0.150.5.1_all.deb) ...
Unpacking replacement update-manager ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up linux-image-2.6.38-11-generic (2.6.38-11.50) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up update-manager (1:0.150.5.1) ...
Errors were encountered while processing:
 linux-image-2.6.38-11-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
owner@ubuntu:~$ sudo apt-get update
and got that error,
so I went and did what you told me, and nothing happened, Ill try again,
ok, I got the same error. well I gotta go for today, Ill be back tomorrow to see if I had a reply. If I get it fixed Ill let everybody know on this thread.
Thanks!
Scott

---

### Post by raja.genupula on 2012-01-11
Have you tried those things i have give you in the link ? 

Well,  Give a try for this 
Remove all of your old kernels , you can make it by doing 
sudo apt-get autoremove

and then .....
ok i am not sure about safe upgrade but i am sure that it wont give you a problem . I mean do this 

sudo aptitude safe-upgrade

try again with updating & lemme know what you got .

All the best.

---

### Post by monsterwizard on 2012-01-12
alright, I sent a bug report to Ubuntu and they said,
                 It looks like you may be having hardware issues with your disk:
Buffer I/O error on device sda1, logical block 6840134

        
                                             Changed in linux (Ubuntu):                                  **status**:                       Confirmed &#8594; Incomplete                                 **status**:                       Incomplete &#8594; Invalid       
Which I dont understand, does that help you help me? 
Anyways, When I followed what was written down in the link you gave me the commands worked fine, then I tried to update some software again, and it went all good until it tried to run depmod, but failed, here is what it said  at the point after it started to run depmod
Failed to run depmod 
dpkg: error processing linux-image-2.6.38-11-generic (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up freeglut3 (2.6.0-1ubuntu2) ... 
Setting up python-rsvg (2.32.0-0ubuntu2) ... 
Setting up glchess (1:2.32.1-0ubuntu5) ... 
Setting up libgtkglext1 (1.2.0-1.1ubuntu1) ... 
Setting up python-opengl (3.0.1~b2-1) ... 
Setting up python-gtkglext1 (1.1.0-6build1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for python-support ... 
Errors were encountered while processing: 
 linux-image-2.6.38-11-generic 
Setting up linux-image-2.6.38-11-generic (2.6.38-11.50) ... 
Running depmod. 
Failed to run depmod 
dpkg: error processing linux-image-2.6.38-11-generic (--configure): 
 subprocess installed post-installation script returned error exit status 1 

Anyways, Thats also what it said after I did the sudo apt-get autoremove.
Then I tried the sudo aptitude safe-upgrade and it just said,
sudo: aptitude: command not found

---

### Post by raja.genupula on 2012-01-12
aptitude not installed 
```
sudo apt-get install aptitude
```

and try again safe upgrade.

---

