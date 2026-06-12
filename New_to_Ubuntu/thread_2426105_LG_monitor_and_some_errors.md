---
title: "LG monitor and some errors"
date: 2019-09-04
forum: New to Ubuntu
---

### Post by migteixas on 2019-09-04
Hello everyone,
I've had ubuntu 18.04 for almost 1 year on a secondary computer i use for gaming so i never explored much and am a total noob.

Today i changed my monitor to a LG 24MK400H-B and initially i plugged it with an HDMI cable. It said "No Signal" so i connected it with VGA to try and solve the HDMI problem. With the VGA cable i can use the monitor but the image is not that great and there is some really slow drag whenever i scroll. Watching videos, for example, is impossible.

At the same time i was searching for help regarding this and trying to update my drivers for the gpu, some other stuff was updating since i did not use the computer for a while. Suddenly it crashed and i had to reboot it. Now i have this message on Software Updater:

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

ibus: Depends: gir1.2-gtk-3.0 (>= 3.8.5) but 3.22.30-1ubuntu4 is installed
      Depends: gir1.2-ibus-1.0 (= 1.5.17-3ubuntu5) but 1.5.17-3ubuntu4 is installed
      Depends: python3:any (>= 3.3.2-2~) but it is a virtual package
      Depends: libatk1.0-0 (>= 1.12.4) but 2.28.1-1 is installed
      Depends: libc6 (>= 2.14) but 2.27-3ubuntu1 is installed
      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.36.11-2 is installed
      Depends: libglib2.0-0 (>= 2.37.3) but 2.56.4-0ubuntu0.18.04.4 is installed
      Depends: libgtk-3-0 (>= 3.21.5) but 3.22.30-1ubuntu4 is installed
      Depends: libpango-1.0-0 (>= 1.14.0) but 1.40.14-1ubuntu0.1 is installed
      Depends: libpangocairo-1.0-0 (>= 1.14.0) but 1.40.14-1ubuntu0.1 is installed
      Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.9-1 is installed


After using "apt-get install -f" this happens:

E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


I would really appreciate some help to solve this so that i can try and solve my monitor problems after that.

Thank you so much in advance

---

### Post by Frogs Hair on 2019-09-04
Hello and Welcome! 

> E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), [COLOR=#ff0000]are you root?[/COLOR]

did you use the following ? ```
sudo  apt-get install -f 
```

---

### Post by Autodave on 2019-09-04
First of all, listen to Frogs Hair and get that taken care of.  After that is fixed, then let's talk about the monitor.  What graphics card is in your machine?  Did you install any drivers for it?  If so, what ones and where did you get them from?

---

### Post by migteixas on 2019-09-04
Thank you for helping.

I did use that and the result is:

[COLOR=#000000]E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)[/COLOR]
[COLOR=#000000]E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?[/COLOR]

---

### Post by migteixas on 2019-09-04
> **Autodave said:**
> First of all, listen to Frogs Hair and get that taken care of.  After that is fixed, then let's talk about the monitor.  What graphics card is in your machine?  Did you install any drivers for it?  If so, what ones and where did you get them from?

I have a gtx960 and if i am not mistaken i installed some drivers a while ago through the terminal, but honestly i can't remember

Edit: I am currently using nvidia-driver-390

---

### Post by Frogs Hair on 2019-09-04
close the software updater or any other package mangers run the following and post the output of the second command.

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
```

```
sudo apt update
```

---

### Post by migteixas on 2019-09-04
> **Frogs Hair said:**
> close the software updater or any other package mangers run the following and post the output of the second command.

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
```

```
sudo apt update
```

Hit:1 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) bionic-updates InRelease                        
Hit:3 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) bionic-backports InRelease                      
Get:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease [21,3 kB]     
Get:5 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease [2842 B]                       
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease                         
Get:7 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise/steam Sources [549 B]              
Get:8 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise/steam amd64 Packages [604 B]
Get:9 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise/steam i386 Packages [801 B]
Get:10 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 Packages [23,0 kB]
Get:11 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main i386 Packages [16,7 kB]
Get:12 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main Translation-en [6596 B]
Fetched 72,3 kB in 1s (73,3 kB/s)                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
133 packages can be upgraded. Run 'apt list --upgradable' to see them.

---

### Post by Frogs Hair on 2019-09-04
Upgrade and post any errors:```
 sudo apt upgrade   
```

---

### Post by migteixas on 2019-09-04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 ibus : Depends: gir1.2-ibus-1.0 (= 1.5.17-3ubuntu5) but 1.5.17-3ubuntu4 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


This is the result

---

### Post by Frogs Hair on 2019-09-04
It looks like the steam repository goes back to 12.04 though I no nothing about the repository.  133 packages up-gradable  indicates you have not updated the system for a while.

Open software & updates/source and under the other software tab disable the steam repository. Then close it and run the following. ```
sudo apt clean
``` ```
sudo apt update && sudo apt upgrade
``` Post any errors.

---

### Post by migteixas on 2019-09-04
Thanks again, i don't have a clue what i am doing

Hit:1 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) bionic-updates InRelease                     
Hit:3 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) bionic-backports InRelease                      
Hit:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease               
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88,7 kB]           
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [22,7 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons [31,7 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [42,2 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [16,4 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [111 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2464 B]
Fetched 315 kB in 1s (258 kB/s)                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
132 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 ibus : Depends: gir1.2-ibus-1.0 (= 1.5.17-3ubuntu5) but 1.5.17-3ubuntu4 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by Frogs Hair on 2019-09-04
Try the suggestion below. I think the steampowered application may be the problem because it is for and end of life release.

```
sudo apt --fix-broken install
```

Edit: You can get newer source for steam, but you will have to remove the old version first which might require enabling the repository again.

---

### Post by migteixas on 2019-09-05
> **Frogs Hair said:**
> Try the suggestion below. I think the steampowered application may be the problem because it is for and end of life release.

```
sudo apt --fix-broken install
```

Edit: You can get newer source for steam, but you will have to remove the old version first which might require enabling the repository again.


Yesterday i opened Steam and it updated automatically.
Today used
```
sudo apt --fix-broken install
```

Everything is updated now.
Thank you so much Frogs Hair!

---

### Post by migteixas on 2019-09-05
> **migteixas said:**
> I have a gtx960 and if i am not mistaken i installed some drivers a while ago through the terminal, but honestly i can't remember

Edit: I am currently using nvidia-driver-390

Updated my drivers do nvidia-435 and nothing changed monitor wise

---

### Post by Frogs Hair on 2019-09-05
FYI ,steam is available for 18.04 without using any 3rd party repositories . You may want to start a new thread for the monitor issue and I'm glad the package system is up and running and you are updated.

---

