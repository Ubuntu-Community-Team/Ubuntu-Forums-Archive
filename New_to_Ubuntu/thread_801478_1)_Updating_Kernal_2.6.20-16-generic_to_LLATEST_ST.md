---
title: "1) Updating Kernal 2.6.20-16-generic to :LLATEST STABLE one in UBUNTU 7.04"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by wesleyjackson on 2008-05-20
To Ubuntu Users,

Well I have finally rid my PC on Windows (I wore out the REBOOT button).

Please excuse my novice like language.

1) I have installed Ubuntu 7.04 (FEB 2007 I think) it has the 2.6.20-16-generic kernel (from uname -r).

I was wanting to update the kernal and any other UPDATES or ADDITIONS to the latest stable as to make my machine, some how run VMWARE.

I am also installing VMWARE workstation (verison 6.0.0.45731) but I have the infamous error of not being able to bridge my ATH0 to vmnet, hence the error comes up and does not allow me to start VMWARE. I can get it to work without virtual networking, through use of the vmware-config.pl, but I need wireless up on the VMWARE as this is my only internet connection.

My first POST so I hope all is cool, I appreciate all comments I get.

Regards

Wesley

---

### Post by Xiong Chiamiov on 2008-05-26
If you're connected to the internet, everything installed through apt will update automatically as new versions are put in the repositories.

If you really want to stay with Fiesty (7.04's Fiesty, right?), but have the updated stuff, you can enable the Hardy repos.

Open the file for writing:
```

gksudo gedit /etc/apt/sources.list

```
then add these lines:
```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

```
I believe that's it.

---

