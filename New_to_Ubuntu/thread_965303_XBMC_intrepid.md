---
title: "XBMC intrepid"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Periswell on 2008-10-31
good day

after my computer crashed through the update from hardy to intrepid, i had to install a fresh ubuntu 8.10. this means that i don't have my programs anymore including the one im going to ask about which is XBMC. now i searched google for the repositories and i got these two:
> 
deb [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) intrepid main

i added them to my etc/apt/sources.list but when i go into synaptic i does not show XBMC and when i go into the terminal and type sudo apt-get install xbmc it says this:
> 
joshua@joshua-laptop:~$ sudo apt-get install xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xbmc: Depends: xbmc-common (= 8.10b2-hardy1) but it is not going to be installed
        Depends: xbmc-skin-pm3-hd (= 8.10b2-hardy1) but it is not going to be installed
        Depends: xbmc-web-pm3 (= 8.10b2-hardy1) but it is not going to be installed
E: Broken packages

only thing is synaptic says theres no broken packages. please help.

-joshua

---

### Post by talsemgeest on 2008-10-31
I'm afraid the packages needed to install xbmc are simply not there. You need to find out what packages are needed and install them manually.

---

### Post by a-converted-sparky on 2008-11-01
Try

deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main

Taken from [http://xbmc.org/forum/showthread.php?p=185738](http://xbmc.org/forum/showthread.php?p=185738)

---

### Post by nimes on 2008-11-02
hi, my solution:

download libbluetooth2:
[http://mirror.clarkson.edu/pub/distributions/ubuntu/pool/main/b/bluez-libs/libbluetooth2_3.29-0ubuntu1_i386.deb](http://mirror.clarkson.edu/pub/distributions/ubuntu/pool/main/b/bluez-libs/libbluetooth2_3.29-0ubuntu1_i386.deb)

install:
dpkg -i libbluetooth2_2.29-ubuntu1_i386.deb

and xbmc install:
sudo apt-get install xbmc

that's all. it's working...

---

### Post by orgads on 2008-11-13
They've opened an intrepid repository:

```
deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
```

---

### Post by -Sparx- on 2008-11-13
Does this work on a 64bit system as well? if you add the repositories does it download the right version?

---

### Post by redbob on 2008-11-13
I upgraded my computer to Intrepid, I passed by this situation. When I was almost decided to begin everything again from zero-point, I run Synaptics and uninstalled all broken packages it detected. So I got successful.

---

