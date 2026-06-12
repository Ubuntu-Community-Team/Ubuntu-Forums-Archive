---
title: "Dependency problems with installing ia32-libs"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by Whitaye on 2012-07-15
I need to install the ia32-libs package on my Ubuntu server (version 11.10). When I try to install it via apt-get it says I need this dependency:

```
The following packages have unmet dependencies.
 ia32-libs : Depends: lib32v4l-0 (>= 0.5.0)
E: Unable to correct problems, you have held broken packages.
```

When I try and install lib32v4l-0 I get this dependency:

```
The following packages have unmet dependencies.
 lib32v4l-0 : Depends: libv4l-0 (= 0.8.0-1) but 0.8.5-3ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.
```

What can I do to successfully install lib32v4l-0 and ia32-libs?

Also, this is the output from sudo apt-get upgrade:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  at console-setup lvm2 ntpdate plymouth
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

---

### Post by Laiquendi on 2012-07-15
Try typing this in terminal to repair broken dependencies:
```
 sudo apt-get clean && sudo apt-get autoclean && sudo apt-get install -f
```
This should repair them.
If not, try changing mirror in software properties, it helps sometimes.

---

### Post by Whitaye on 2012-07-15
Nope, did nothing. :( still getting the same dependency errors.

---

### Post by NikTh on 2012-07-15
**Hello and Welcome to Ubuntu Forums ! **

Open a terminal and copy-paste these commands one at time .. 
```
cat /etc/lsb-release && uname -r 
apt-cache policy ia32-libs
ls /etc/apt/sources.list.d/
```
Paste results here inside [CODE] tags by highlighting the text and click at # symbol on top of message pane. 
Thanks

---

### Post by anewguy on 2012-07-15
You can also try:

sudo apt-get build-dependencies (not sure of the exact wording there - see help for apt-get) followed by the package name

---

