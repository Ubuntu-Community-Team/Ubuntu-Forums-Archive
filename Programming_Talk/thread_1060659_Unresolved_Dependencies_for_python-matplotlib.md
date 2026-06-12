---
title: "Unresolved Dependencies for python-matplotlib"
date: 2009-02-05
forum: Programming Talk
---

### Post by Barriehie on 2009-02-05
I'm getting into python and want to be able to plot 2D numeric data.  I go to install python-matplotlib via synaptic and get an unresolved dependencies error stating that I should make sure all of the required repositories are added.  Does anyone know where I can find this?  I've searched but I'm not really sure what I'm looking for! :(   Or, best case, my ubuntu 8.04 has something installed already and I don't know what the library is!

Thank You,
Barrie

---

### Post by unutbu on 2009-02-05
Please post the output of 
```

apt-cache policy python-matplotlib
apt-cache depends python-matplotlib | awk '/Depends:/{print $2}' | sort | uniq | xargs apt-cache policy
sudo apt-get install python-matplotlib
```

---

### Post by Barriehie on 2009-02-05
> **unutbu said:**
> Please post the output of 
```

apt-cache policy python-matplotlib
apt-cache depends python-matplotlib | awk '/Depends:/{print $2}' | sort | uniq | xargs apt-cache policy
sudo apt-get install python-matplotlib
```



```

 /home/barrie $ >apt-cache policy python-matplotlib
python-matplotlib:
  Installed: (none)
  Candidate: 0.91.2-0ubuntu1
  Version table:
     0.91.2-0ubuntu1 0
        500 http://archive.ubuntu.com hardy/universe Packages
06:33:25 /home/barrie $ >apt-cache depends python-matplotlib | awk '/Depends:/{print $2}' | sort | uniq | xargs apt-cache policy
dvipng:
  Installed: (none)
  Candidate: 1.9-5
  Version table:
     1.9-5 0
        500 http://archive.ubuntu.com hardy/universe Packages
libatk1.0-0:
  Installed: 1.22.0-0ubuntu1
  Candidate: 1.22.0-0ubuntu1
  Version table:
 *** 1.22.0-0ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
libc6:
  Installed: 2.7-10ubuntu4
  Candidate: 2.7-10ubuntu4
  Version table:
 *** 2.7-10ubuntu4 0
        100 /var/lib/dpkg/status
     2.7-10ubuntu3 0
        500 http://archive.ubuntu.com hardy/main Packages
libcairo2:
  Installed: 1.6.0-0ubuntu2
  Candidate: 1.6.0-0ubuntu2
  Version table:
 *** 1.6.0-0ubuntu2 0
        100 /var/lib/dpkg/status
     1.6.0-0ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
libffi4:
  Installed: 4.2.4-1ubuntu3
  Candidate: 4.2.4-1ubuntu3
  Version table:
 *** 4.2.4-1ubuntu3 0
        100 /var/lib/dpkg/status
     4.2.3-2ubuntu7 0
        500 http://archive.ubuntu.com hardy/main Packages
libfreetype6:
  Installed: 2.3.5-1ubuntu4.8.04.1
  Candidate: 2.3.5-1ubuntu4.8.04.1
  Version table:
 *** 2.3.5-1ubuntu4.8.04.1 0
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     2.3.5-1ubuntu4 0
        500 http://archive.ubuntu.com hardy/main Packages
libgcc1:
  Installed: 1:4.2.4-1ubuntu3
  Candidate: 1:4.2.4-1ubuntu3
  Version table:
 *** 1:4.2.4-1ubuntu3 0
        100 /var/lib/dpkg/status
     1:4.2.3-2ubuntu7 0
        500 http://archive.ubuntu.com hardy/main Packages
libglib2.0-0:
  Installed: 2.16.6-0ubuntu1
  Candidate: 2.16.6-0ubuntu1
  Version table:
 *** 2.16.6-0ubuntu1 0
        100 /var/lib/dpkg/status
     2.16.3-1 0
        500 http://archive.ubuntu.com hardy/main Packages
libgtk2.0-0:
  Installed: 2.12.9-3ubuntu5
  Candidate: 2.12.9-3ubuntu5
  Version table:
 *** 2.12.9-3ubuntu5 0
        100 /var/lib/dpkg/status
     2.12.9-3ubuntu2 0
        500 http://archive.ubuntu.com hardy/main Packages
libpango1.0-0:
  Installed: 1.20.5-0ubuntu1
  Candidate: 1.20.5-0ubuntu1
  Version table:
 *** 1.20.5-0ubuntu1 0
        100 /var/lib/dpkg/status
     1.20.1-1 0
        500 http://archive.ubuntu.com hardy/main Packages
libpng12-0:
  Installed: 1.2.15~beta5-3
  Candidate: 1.2.15~beta5-3
  Version table:
 *** 1.2.15~beta5-3 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
libstdc++6:
  Installed: 4.2.4-1ubuntu3
  Candidate: 4.2.4-1ubuntu3
  Version table:
 *** 4.2.4-1ubuntu3 0
        100 /var/lib/dpkg/status
     4.2.3-2ubuntu7 0
        500 http://archive.ubuntu.com hardy/main Packages
python:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-central:
  Installed: 0.6.7ubuntu0.1
  Candidate: 0.6.7ubuntu0.1
  Version table:
 *** 0.6.7ubuntu0.1 0
        100 /var/lib/dpkg/status
     0.6.5ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
python-configobj:
  Installed: (none)
  Candidate: 4.4.0-2
  Version table:
     4.4.0-2 0
        500 http://archive.ubuntu.com hardy/universe Packages
python-dateutil:
  Installed: (none)
  Candidate: 1.3-1
  Version table:
     1.3-1 0
        500 http://archive.ubuntu.com hardy/universe Packages
python-dev:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-enthought-traits:
  Installed: (none)
  Candidate: 2.0.1b1-2ubuntu2
  Version table:
     2.0.1b1-2ubuntu2 0
        500 http://archive.ubuntu.com hardy/universe Packages
python-gd:
  Installed: (none)
  Candidate: 0.52.0-0ubuntu4
  Version table:
     0.52.0-0ubuntu4 0
        500 http://archive.ubuntu.com hardy/main Packages
python-gobject:
  Installed: 2.14.2-0ubuntu1
  Candidate: 2.14.2-0ubuntu1
  Version table:
 *** 2.14.2-0ubuntu1 0
        100 /var/lib/dpkg/status
     2.14.1-2ubuntu2 0
        500 http://archive.ubuntu.com hardy/main Packages
python-gtk2:
  Installed: 2.12.1-0ubuntu1
  Candidate: 2.12.1-0ubuntu1
  Version table:
 *** 2.12.1-0ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-matplotlib-data:
  Installed: (none)
  Candidate: 0.91.2-0ubuntu1
  Version table:
     0.91.2-0ubuntu1 0
        500 http://archive.ubuntu.com hardy/universe Packages
python-numarray-ext:
  Installed: (none)
  Candidate: 1.5.2-3ubuntu2
  Version table:
     1.5.2-3ubuntu2 0
        500 http://archive.ubuntu.com hardy/universe Packages
python-numeric-ext:
  Installed: (none)
  Candidate: 24.2-8ubuntu2
  Version table:
     24.2-8ubuntu2 0
        500 http://archive.ubuntu.com hardy/main Packages
python-numpy:
  Installed: (none)
  Candidate: 1:1.0.4-6ubuntu3
  Version table:
     1:1.0.4-6ubuntu3 0
        500 http://archive.ubuntu.com hardy/universe Packages
python-qt3:
  Installed: 3.17.4-1ubuntu4
  Candidate: 3.17.4-1ubuntu4
  Version table:
 *** 3.17.4-1ubuntu4 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-qt4:
  Installed: (none)
  Candidate: 4.3.3-2ubuntu4
  Version table:
     4.3.3-2ubuntu4 0
        500 http://archive.ubuntu.com hardy/main Packages
python-tk:
  Installed: 2.5.2-0ubuntu2
  Candidate: 2.5.2-0ubuntu2
  Version table:
 *** 2.5.2-0ubuntu2 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-tz:
  Installed: (none)
  Candidate: 2007k-0ubuntu2
  Version table:
     2007k-0ubuntu2 0
        500 http://archive.ubuntu.com hardy/main Packages
python-wxgtk2.8:
  Installed: 2.8.7.1-0ubuntu3
  Candidate: 2.8.7.1-0ubuntu3
  Version table:
 *** 2.8.7.1-0ubuntu3 0
        500 http://archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
tcl8.4:
  Installed: 8.4.16-4ubuntu1
  Candidate: 8.4.16-4ubuntu1
  Version table:
 *** 8.4.16-4ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
tk8.4:
  Installed: 8.4.16-2ubuntu1.1
  Candidate: 8.4.16-2ubuntu1.1
  Version table:
 *** 8.4.16-2ubuntu1.1 0
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     8.4.16-2ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
zlib1g:
  Installed: 1:1.2.3.3.dfsg-7ubuntu1
  Candidate: 1:1.2.3.3.dfsg-7ubuntu1
  Version table:
 *** 1:1.2.3.3.dfsg-7ubuntu1 0
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
W: Unable to locate package <python-pypaint>
06:33:25 /home/barrie $ >sudo apt-get install python-matplotlib

06:33:25 /home/barrie $ >sudo apt-get install python-matplotlib
[sudo] password for barrie: 
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

The following packages have unmet dependencies:
  python-matplotlib: Depends: python-numpy (>= 1:1.0.4-6) but it is not going to be installed or
                              python-numeric-ext but it is not going to be installed or
                              python-numarray-ext but it is not going to be installed
E: Broken packages
06:38:19 /home/barrie $ >



```What do you think???

Thank You,
Barrie

---

### Post by unutbu on 2009-02-05
Hm. I'm not sure. What output do you see when you type
```

sudo apt-get install python-numpy
```

---

### Post by Barriehie on 2009-02-05
> **unutbu said:**
> Hm. I'm not sure. What output do you see when you type
```

sudo apt-get install python-numpy
```

```

06:50:06 /home/barrie $ >sudo apt-get install python-numpy
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

The following packages have unmet dependencies:
  python-numpy: Depends: libgfortran2 (>= 4.2.1) but it is not going to be installed
E: Broken packages
06:50:15 /home/barrie $ >

```Barrie

---

### Post by Barriehie on 2009-02-05
Here is my sources.list file:

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# deb http://www.linuxmint.com/repository romeo/

## Added for Flight Gear - BCH
#
#    us.debian.org isn't being resolved
#
deb http://us.debian.org/debian sid main

# deb http://packages.medibuntu.org/ gutsy free non-free
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted


```Barrie

---

### Post by Barriehie on 2009-02-05
Don't know if this helps or not.  I can reach [http://archive.ubuntu.com](http://archive.ubuntu.com) via my browser and get to the matplotlib directory but the 1.9-5 number I see in the previous post isn't there.

Barrie

---

### Post by unutbu on 2009-02-05
I noticed you have these lines enabled in your /etc/apt/sources.list:
```

deb http://archive.canonical.com/ubuntu gutsy partner
deb http://us.debian.org/debian sid main
```

I'm not sure if this could cause the problem you are currently experiencing, but in general I think it is not good to mix repositories from different distributions. 

How about try commenting-out these lines, and then running
```

sudo apt-get update     # refresh apt's database of available packages
sudo apt-get install python-numpy

```
and if that is successful,
```

sudo apt-get install python-matplotlib
```

Also, if you type
```

gksu /usr/bin/software-properties-gtk
```

click on the "Download from" drop-down menu, and select "Other". Click the "Select Best Server" button. All official repository servers will be pinged, and the server with the fastest ping time will be reported. The terminal output will show the times of the best servers. Using this information, try a different server. Because so many people use archive.canonical.com, you will almost certainly improve your download speeds by doing this.

Be sure to run 
```

sudo apt-get update 
```

again after you choose a different server.

---

### Post by Barriehie on 2009-02-05
Okay, I commented out the 2 lines and updated the 'best server' and got:

```

12:49:31 /home/barrie $ >sudo apt-get install python-numpy
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

The following packages have unmet dependencies:
  python-numpy: Depends: libgfortran2 (>= 4.2.1) but it is not going to be installed
E: Broken packages
12:49:52 /home/barrie $ >


```When I went into synaptic to install libgfortran2 is says:

```

 libgfortran2:
  Depends: gcc-4.2-base (=4.2.3-2ubuntu7) but 4.2.4-1ubuntu3 is to be installed

```I look at gcc-4.2 gcc-4.2-base and they are both installed.

Barrie

---

### Post by unutbu on 2009-02-05
Okay, I think I see what is going on. 
libgfortran2 version 4.2.4-1ubuntu3 is provided by hardy-updates, but your current sources.list doesn't have hardy-updates enabled.

You could try going to System>Admin>Software Sources and enabling hardy-updates.

If that does not work, you may wish to try this:

Posted here [http://paste.ubuntu.com/114187/](http://paste.ubuntu.com/114187/) is a copy of the Hardy /etc/apt/sources.list from a fresh install.
```

cd /etc/apt
cp sources.list sources.list_20090205
sudo wget http://paste.ubuntu.com/114187/plain/ -O /etc/apt/sources.list

```

---

### Post by Barriehie on 2009-02-05
> **unutbu said:**
> Okay, I think I see what is going on. 
libgfortran2 version 4.2.4-1ubuntu3 is provided by hardy-updates, but your current sources.list doesn't have hardy-updates enabled.

You could try going to System>Admin>Software Sources and enabling hardy-updates.



Your rock!!!  That was it!  I can't find the 'Thank You' button on here or I'ld click it.  

:p Barrie

---

