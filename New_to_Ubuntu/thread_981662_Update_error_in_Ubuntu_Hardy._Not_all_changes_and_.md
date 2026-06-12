---
title: "Update error in Ubuntu Hardy. Not all changes and updates succeeded."
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Pitheas on 2008-11-13
Hi, i was updating my system, as usual, and after all the needed packages were downloaded, the 'Applying changes' window launched.
Then, it came up an error message that read:

> **Update is complete**
Not all changes and updates succeeded. For further details of the failure, please expand the terminal panel below. 


Details
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/available/'near line 1235 package 'example-content':
 field name 'Size2' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

I closed and reopened the Update manager and it kept showing me the same message. I restarted my computer and tried again, but it was the same. What can I do?

---

### Post by DougieFresh4U on 2008-11-14
I would suggest you open terminal-Applications>Accessories>Terminal, 
and type
```
sudo apt-get -f install
sudo dpkg --configure -a 
```

---

### Post by Pitheas on 2008-11-14
Tried and here's what I got.

> yasab@paites:~$ sudo apt-get -f install
[sudo] password for yasab: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
yasab@paites:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1235 package `example-content':
 field name `Size2' must be followed by colon

---

### Post by dd000d on 2008-11-18
I am having a similar problem here is what i get when i type that into my terminal

dan@dan-desktop:~$ sudo apt-get -f install
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
dan@dan-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19077 package `thunderbird':
 `Recommends' field, missing package name, or garbage where package name expected



is there a problem in thunderbird that is causing all this??? kind of doubt that would happen tho.

---

### Post by Pitheas on 2008-11-28
I asked my cousin (my "ubuntu migration officer", haha) and he told me that a file was corrupted and it was needed to download it again. He told me to write in the Terminal.
```
sudo apt-get update
sudo cp /var/lib/dpkg/available /var/lib/dpkg/available.bk
apt-cache dumpavail
```
Here the terminal will display a lot of code lines. Next, the user must become root user.
```
su -
```
and type the password.
```
apt-cache dumpavail > /var/lib/dpkg/available
exit
sudo apt-get dist-upgrade
```
And that's it. That should fix it.

Well, at least it worked for me.

---

