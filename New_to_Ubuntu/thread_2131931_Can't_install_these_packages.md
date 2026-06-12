---
title: "Can't install these packages"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by whitefish10 on 2013-04-03
Hi please help me.

ahmed@ahmed-PH67A-UD3-B3:~$ sudo apt-get install git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk2.8-dev squashfs-tools build-essential zip curl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zip is already the newest version.
gnupg is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 curl : Depends: libcurl3 (= 7.27.0-1ubuntu1) but 7.27.0-1ubuntu1.1 is to be installed
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
                 Depends: libpulse-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ahmed@ahmed-PH67A-UD3-B3:~$ 


And thank you.

---

### Post by schragge on 2013-04-03
Let's tackle them one by one. First, install the packages that _can_ be installed:
```

sudo apt-get update
sudo apt-get install build-essential git-core flex bison gperf lib{esd0,wxgtk2.8}-dev squashfs-tools
```
Then try:
```
sudo apt-get install libcurl3 curl
```
```
sudo apt-get install lib{pulse,glu1-mesa,sdl1.2}-dev
```

---

