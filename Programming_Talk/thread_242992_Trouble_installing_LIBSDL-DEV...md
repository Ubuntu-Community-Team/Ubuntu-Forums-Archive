---
title: "Trouble installing LIBSDL-DEV.."
date: 2006-08-24
forum: Programming Talk
---

### Post by sadscientist on 2006-08-24
Hi,

Any idea how I can resolve the package conflicts?

:(

[B]andrew@deimos:~$ sudo apt-cache search libsdl-dev
[/B]libsdl1.2-dev - Simple DirectMedia Layer development files
[B]andrew@deimos:~$ sudo apt-get install libsdl1.2-dev
[/B]Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
[B]andrew@deimos:~$ sudo apt-get install libartsc0-dev
[/B]Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libartsc0-dev: Depends: libglib2.0-dev but it is not going to be installed
E: Broken packages
[B]andrew@deimos:~$ sudo apt-get install libglib2.0-dev
[/B]Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1                                                                                                    is to be installed
E: Broken packages
[B]andrew@deimos:~$ sudo apt-get install libglib2.0-0
[/B]Reading package lists... Done
Building dependency tree... Done
libglib2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@deimos:~$

---

### Post by sadscientist on 2006-08-24
This might help:

```
andrew@deimos:/etc/apt$ cat /etc/apt/sources.list
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
## Debian Sarge (stable) users:
##deb http://splashy.alioth.debian.org/debian stable main
## Debian Etch/Sid (testing/unstable) users:
##deb http://splashy.alioth.debian.org/debian unstable main

```

---

### Post by Anchakor on 2006-10-14
I got the same problem using the Synaptic...
I need to install libsdl1.2-dev, libsdl-image1.2-dev libsdl-mixer1.2-dev and they all have conflicts...

can anyone help?:neutral:

---

