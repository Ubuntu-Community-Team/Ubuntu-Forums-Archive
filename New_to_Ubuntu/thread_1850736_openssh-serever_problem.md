---
title: "openssh-serever problem"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by med linux on 2011-09-27
good morning 
I want install openssh serever with shell by this cmd
```
user@user-Compaq-610:~$ sudo apt-get install openssh-server
``````

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:5.5p1-4ubuntu4) but 1:5.5p1-4ubuntu6 is to be installed
E: Broken packages

```when I tried to install openssh-client  .... 
```
user@user-Compaq-610:~$ sudo apt-get install openssh-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 65 not upgraded.

```but synaptic shows me that 1:5.5p1-4ubuntu6  is installled !! 
what should i do ??

---

### Post by ptn107 on 2011-10-06
Make sure your /etc/apt/sources.list allows for 'maverick-updates':
```
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
```

Then try:
```
sudo apt-get update && sudo apt-get install openssh-client=1:5.5p1-4ubuntu6 openssh-server=1:5.5p1-4ubuntu6
```

If that fails pop open synaptic and make sure you didn't hold them at an older version.

---

