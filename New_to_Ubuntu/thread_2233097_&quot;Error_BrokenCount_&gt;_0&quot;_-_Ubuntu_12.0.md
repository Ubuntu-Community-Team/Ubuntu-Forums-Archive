---
title: "&quot;Error: BrokenCount &gt; 0&quot; - Ubuntu 12.04"
date: 2014-07-06
forum: New to Ubuntu
---

### Post by emcquinn8 on 2014-07-06
This is the message I am getting from the top of my screen, when clicking on the circular red icon with a white dash through it.

Running the command apt-get -f install on the terminal returns:

```
max@max:~$ sudo apt-get -f install
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cinelerra-cv libguicast1-cv libmpeg3cine-cv libopencv-legacy2.3
  libopencv-video2.3 libquicktimecine-cv
The following NEW packages will be installed:
  libopencv-legacy2.3 libopencv-video2.3
The following packages will be upgraded:
  cinelerra-cv libguicast1-cv libmpeg3cine-cv libquicktimecine-cv
4 upgraded, 2 newly installed, 0 to remove and 153 not upgraded.
1 not fully installed or removed.
Need to get 16.9 MB of archives.
After this operation, 1,796 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu/ precise/main cinelerra-cv amd64 1:2.2.git.20140703b-0~ppa1~precise1 [12.7 MB]
Get:2 http://ie.archive.ubuntu.com/ubuntu/ precise/universe libopencv-video2.3 amd64 2.3.1-7 [108 kB]
Get:3 http://ie.archive.ubuntu.com/ubuntu/ precise/universe libopencv-legacy2.3 amd64 2.3.1-7 [306 kB]
Get:4 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu/ precise/main libguicast1-cv amd64 1:2.2.git.20140703b-0~ppa1~precise1 [510 kB]
Get:5 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu/ precise/main libmpeg3cine-cv amd64 1:2.2.git.20140703b-0~ppa1~precise1 [2,824 kB]
Get:6 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu/ precise/main libquicktimecine-cv amd64 1:2.2.git.20140703b-0~ppa1~precise1 [385 kB]
Fetched 16.9 MB in 40s (414 kB/s)                                              
(Reading database ... 462952 files and directories currently installed.)
Preparing to replace libguicast1-cv 1:2.2.git.20140527-0~ppa1~precise1 (using .../libguicast1-cv_1%3a2.2.git.20140703b-0~ppa1~precise1_amd64.deb) ...
Unpacking replacement libguicast1-cv ...
Preparing to replace libmpeg3cine-cv 1:2.2.git.20140527-0~ppa1~precise1 (using .../libmpeg3cine-cv_1%3a2.2.git.20140703b-0~ppa1~precise1_amd64.deb) ...
Unpacking replacement libmpeg3cine-cv ...
Selecting previously unselected package libopencv-video2.3.
Unpacking libopencv-video2.3 (from .../libopencv-video2.3_2.3.1-7_amd64.deb) ...
Selecting previously unselected package libopencv-legacy2.3.
Unpacking libopencv-legacy2.3 (from .../libopencv-legacy2.3_2.3.1-7_amd64.deb) ...
Preparing to replace libquicktimecine-cv 1:2.2.git.20140527-0~ppa1~precise1 (using .../libquicktimecine-cv_1%3a2.2.git.20140703b-0~ppa1~precise1_amd64.deb) ...
Unpacking replacement libquicktimecine-cv ...
Setting up libguicast1-cv (1:2.2.git.20140703b-0~ppa1~precise1) ...
Setting up libmpeg3cine-cv (1:2.2.git.20140703b-0~ppa1~precise1) ...
Setting up libopencv-video2.3 (2.3.1-7) ...
Setting up libopencv-legacy2.3 (2.3.1-7) ...
Setting up libquicktimecine-cv (1:2.2.git.20140703b-0~ppa1~precise1) ...
dpkg: dependency problems prevent configuration of cinelerra-cv:
 cinelerra-cv depends on libguicast1-cv (= 1:2.2.git.20140522-0~ppa1~precise1); however:
  Version of libguicast1-cv on system is 1:2.2.git.20140703b-0~ppa1~precise1.
 cinelerra-cv depends on libmpeg3cine-cv (= 1:2.2.git.20140522-0~ppa1~precise1); however:
  Version of libmpeg3cine-cv on system is 1:2.2.git.20140703b-0~ppa1~precise1.
 cinelerra-cv depends on libquicktimecine-cv (= 1:2.2.git.20140522-0~ppa1~precise1); however:
  Version of libquicktimecine-cv on system is 1:2.2.git.20140703b-0~ppa1~precise1.
dpkg: error processing cinelerra-cv (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cinelerra-cv
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

---

### Post by sandyd on 2014-07-06
What PPAs do you have installed - some packages seem to be conflicting
```

sudo cat /etc/apt/sources.list.d/*
```

---

### Post by ibjsb4 on 2014-07-06
Don't think that works sandyd ..
```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by sandyd on 2014-07-06
> **ibjsb4 said:**
> Don't think that works sandyd ..
```
ls /etc/apt/sources.list.d/*.list
```

I like viewing the contents more :P

---

### Post by emcquinn8 on 2014-07-06
```
~$ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list
/etc/apt/sources.list.d/cwayne18-doge-precise.list
/etc/apt/sources.list.d/disper-dev-ppa-precise.list
/etc/apt/sources.list.d/google-earth.list
/etc/apt/sources.list.d/google-talkplugin.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
/etc/apt/sources.list.d/upubuntu-com-multimedia-precise.list
```

---

### Post by emcquinn8 on 2014-07-06
> **ibjsb4 said:**
> Don't think that works sandyd ..
```
ls /etc/apt/sources.list.d/*.list
```


```
~$ ~$ ls /etc/apt/sources.list.d/*.list
~$: command not found
max@max:~$ /etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list
bash: /etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list: Permission denied
max@max:~$ /etc/apt/sources.list.d/cwayne18-doge-precise.list
bash: /etc/apt/sources.list.d/cwayne18-doge-precise.list: Permission denied
max@max:~$ /etc/apt/sources.list.d/disper-dev-ppa-precise.list
bash: /etc/apt/sources.list.d/disper-dev-ppa-precise.list: Permission denied
max@max:~$ /etc/apt/sources.list.d/google-earth.list
bash: /etc/apt/sources.list.d/google-earth.list: Permission denied
max@max:~$ /etc/apt/sources.list.d/google-talkplugin.list
bash: /etc/apt/sources.list.d/google-talkplugin.list: Permission denied
max@max:~$ /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
bash: /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list: Permission denied
max@max:~$ /etc/apt/sources.list.d/upubuntu-com-multimedia-precise.list
bash: /etc/apt/sources.list.d/upubuntu-com-multimedia-precise.list: Permission denied


```

---

### Post by sandyd on 2014-07-06
Fixed typo

---

### Post by sandyd on 2014-07-06
Seems like a problem with the ppa
cinelerra-cv (= 1:2.2.git.20140703b-0~ppa1~precise1) depends on libguicast1-cv (= 1:2.2.git.20140522-0~ppa1~precise1) while it should be depending on libguicast1-cv (= 1:2.2.git.20140703b-0~ppa1~precise1).

Maybe if you pin libguicast1-cv to the version 1:2.2.git.20140522-0~ppa1~precise1, cinelerra-cv can install.

---

### Post by emcquinn8 on 2014-07-06
> **sandyd said:**
> Seems like a problem with the ppa
cinelerra-cv (= 1:2.2.git.20140703b-0~ppa1~precise1) depends on libguicast1-cv (= 1:2.2.git.20140522-0~ppa1~precise1) while it should be depending on libguicast1-cv (= 1:2.2.git.20140703b-0~ppa1~precise1).

Maybe if you pin libguicast1-cv to the version 1:2.2.git.20140522-0~ppa1~precise1, cinelerra-cv can install.

hi Sandyd, if i just uninstall cinelerra would that solve the problem? I don't use cinelerra very often and am in a hurry to resolve this issue.

---

### Post by ibjsb4 on 2014-07-06
Open up your software sources and just uncheck or remove it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by sandyd on 2014-07-06
> **emcquinn8 said:**
> hi Sandyd, if i just uninstall cinelerra would that solve the problem? I don't use cinelerra very often and am in a hurry to resolve this issue.

Yes, it will fix the issue.

---

### Post by emcquinn8 on 2014-07-07
solved - thanks

---

