---
title: "The Package System is Broken"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by keith234 on 2012-05-27
Hi Everyone

I'm new to the wonderful world of Ubuntu (desktop), after losing Windows 7 on my netbook (long story I wont bore
 you with!)

I'm having some issues with installing updates. Get this Package System is Broken message. Tried running sudo apt-get install -f and it comes back with:  The following packages have unmet dependencies:

linux-headers-3.2.0-24-generic-pae: Depends: linux-headers-3.2.0-24 but it is not installed
smbclient: Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.1 is installed
thunderbird-globalmenu: Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is installed
thunderbird-gnome-support: Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is installed 

Where am I going wrong?

Thanks in advance

K

---

### Post by Cbjaxx on 2012-05-27
Have you tried sudo apt-get update && sudo apt-get upgrade?

---

### Post by Jimmyfj on 2012-05-27
Open a terminal (ctrl+alt+t) and enter this code:

```
sudo apt-get install synaptic
```

After install open Synaptic by typing:

```
sudo synaptic
```

Enter your root password and press Enter.

Inside Synaptic you look for a button named "Costum Filters" in the lower left corner of your screen. Click the button, and a line of new items show.
Find the filter called "Broken" and look at the main window. If it lists some packages mark them  and click "Apply".

---

### Post by keith234 on 2012-05-27
Hi Guys

Thanks for the quick response...still getting a pesky error message. For instance trying to load synaptic gets this:

keith@keith-1001PXD:~$ sudo apt-get install  synaptic
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-3.2.0-24-generic-pae : Depends: linux-headers-3.2.0-24 but it is not going to be installed
 smbclient : Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.1 is to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
 thunderbird-globalmenu : Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is to be installed
 thunderbird-gnome-support : Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
keith@keith-1001PXD:~$ 

:confused:
Thanks again to you both
K

---

### Post by nipunshakya on 2012-05-27
[FONT=Verdana, sans-serif][SIZE=1]i think this might help..
```
sudo dpkg --configure -a
```
and
```
sudo apt-get -f install
```

After that you can try Jimmyf's later part from post above
[/SIZE][/FONT]

---

### Post by keith234 on 2012-05-28
Hi Winux

Thanks for reply. Tried what you said but it comes back with this:

keith@keith-1001PXD:~$ sudo dpkg --configure -a
[sudo] password for keith: 
dpkg: dependency problems prevent configuration of thunderbird-globalmenu:
 thunderbird-globalmenu depends on thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1); however:
  Version of thunderbird on system is 11.0.1+build1-0ubuntu2.
dpkg: error processing thunderbird-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1); however:
  Version of thunderbird on system is 11.0.1+build1-0ubuntu2.
dpkg: error processing thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-3.2.0-24-generic-pae:
 linux-headers-3.2.0-24-generic-pae depends on linux-headers-3.2.0-24; however:
  Package linux-headers-3.2.0-24 is not installed.
dpkg: error processing linux-headers-3.2.0-24-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-24-generic-pae; however:
  Package linux-headers-3.2.0-24-generic-pae is not configured yet.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 thunderbird-globalmenu
 thunderbird-gnome-support
 linux-headers-3.2.0-24-generic-pae
 linux-headers-generic-pae
keith@keith-1001PXD:~$  sudo apt-get f install
E: Invalid operation f
keith@keith-1001PXD:~$ 

Hmmm...well it all leaves me puzzled (that admittedly isn't hard to do).

---

### Post by codingman on 2012-05-28
i get this a lot of the time, happening to me right now, just wait a bit, sometimes that's the case, if it doesn't get fixed, do the update and upgrade commands. Then restart.

---

### Post by cortman on 2012-05-28
Do what apt-get suggests and run

```
sudo apt-get install -f
```

---

### Post by ts3 on 2012-05-28
> **keith234 said:**
> keith@keith-1001PXD:~$  sudo apt-get f install
E: Invalid operation f
keith@keith-1001PXD:~$ 

Hmmm...well it all leaves me puzzled (that admittedly isn't hard to do).

The first command (dpkg) ran OK since it didn't throw out any errors and ended with a new command prompt.  You have a typo in the second command: should be -f not just f.  

Cheers and HTH

---

