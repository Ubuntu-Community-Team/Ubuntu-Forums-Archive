---
title: "Wine/play on linux problem trusty tahr"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-04-23
I'm running 14.04 and wanted to install wine and play on linux.
However, I'm getting a message that I will need to remove nvidia-libopencl1-331.
Is it safe to this, will it break anything. Somehow I believe it will mess with my proprietary drivers...

---

### Post by ibjsb4 on 2014-04-23
Looks to be a bit buggy.

[http://askubuntu.com/questions/449507/installing-wine-14-04-with-nvidia-proprietary-drivers-enabled](http://askubuntu.com/questions/449507/installing-wine-14-04-with-nvidia-proprietary-drivers-enabled)

[http://www.google.com/search?client=qupzilla&q=nvidia-libopencl1-331%20bugs](http://www.google.com/search?client=qupzilla&q=nvidia-libopencl1-331%20bugs)

---

### Post by Dr. McKay on 2014-04-24
I think I'll wait until it's fixed...

---

### Post by keithcleaver2010 on 2014-04-24
I've installed both this morning with no problems, although I installed Wine from the CLI rather than software-center.

---

### Post by Dr. McKay on 2014-04-24
> **keithcleaver2010 said:**
> I've installed both this morning with no problems, although I installed Wine from the CLI rather than software-center.

Any problems with Steam games ?  Sure nothing will be broken if I use CLI install as well ?

---

### Post by keithcleaver2010 on 2014-04-24
I've installed Steam, and downloaded & launched a game with no problems.

Not managed to play a game within Wine & POL as yet as I'm having a problem with the DVDs of the game I wished to install, but did manage to install the World of Warcraft installer with no issues.

The code for the CLI installation of wine was taken from the Ubuntu Manual, found at [http://ubuntu-manual.org/?lang=en_US](http://ubuntu-manual.org/?lang=en_US). Here's the steps I followed direct from the manual:

```
To install Wine Version 1.6, follow the following steps:


*If you have a previous version of Wine installed, uninstall Wine before continuing*
*using the command, sudo apt-get remove --purge wine1.* winetricks &&*
*sudo apt-get autoremove*

1. Open the terminal and type: **sudo apt-add-repository ppa:ubuntu-wine/ppa** . This will install the Official Wine PPA.


2. After the terminal has finished installing the Wine PPA, type: **sudo apt-get update** . This will update the PPA list.


3. Once the terminal has finished refreshing the PPA list, type: **sudo apt-get install -y wine1.6 winetricks**. This will install Wine 1.6 and
Winetricks. Winetricks is a software center for Wine, and is, in mostcases, optional.
```

NB: I'm a brand new user to Linux, so I just followed the instructions as listed, so I don't know what the -y means in the last step.

---

