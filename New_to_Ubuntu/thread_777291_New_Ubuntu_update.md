---
title: "New Ubuntu update"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by pfodor on 2008-05-01
Hi,

I got today an email to update my gusty Ubuntu to a new ubuntu. After installing, it tried to reboot and it got stuck. It says:

* Running local boot scripts (/etc/rc.local)

I restarted in safe mode and logged in in text mode.

I tried to "startx" and it says: X server not found.

Please tell me what should I do?

Thanks,
Paul.

---

### Post by PmDematagoda on 2008-05-01
What do you mean you received "an e-mail"? Could you please be more specific as to how you upgraded Ubuntu.

---

### Post by Myglaren on 2008-05-01
Inded.  Never get any emails from Ubuntu but the Update Manager screen has advised of an Upgrade since the 24th.
I waited a few days for the feeding frenzy to abate a bit and updated yesterday.  All went very smoothly.  It asked a couple of times about retaining configuration files and to reboot.
After the reboot (less than a minute) all has been well, no problems encountered at all.

---

### Post by pfodor on 2008-05-01
I am sorry. I did not get an email. I got a popup in the right upper corner of the Desktop that new updates are available and a new version of Ubuntu is available.
I said "ok" and it started to update to the new version. It took 1h and it asked me from time to time if I want to update some libraries. 

When it tried to reboot, it couldn't.

I tried to reboot in safe mode and do: sudo dpkg-reconfigure xserver-xorg

it said that it created a new /etc/X11/xorg.conf and that the old one was backed up.

I tried:

startx 

X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
pfodor@silk:~$ sudo startx

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux silk 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  1 10:36:39 2008
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 139 of section DRI in file /etc/X11/xorg.conf
        Unexpected EOF. Missing EndSection keyword?
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

sudo startx

Is there a way to go back to my previous Ubuntu version?

Regards,
Paul.

---

### Post by Paqman on 2008-05-01
> **pfodor said:**
> 
I got today an email to update my gusty Ubuntu to a new ubuntu. 

That sounds extremely dodgy.

---

### Post by lazyart on 2008-05-01
> **pfodor said:**
>  
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  1 10:36:39 2008
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 139 of section DRI in file /etc/X11/xorg.conf
        Unexpected EOF. Missing EndSection keyword?
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

sudo startx

Is there a way to go back to my previous Ubuntu version?

Regards,
Paul.

Looks like a simple edit of the config file will make it all go away.

sudo nano /etc/X11/xorg.conf

Scroll down to the bottom see if it's missing the line EndSection.  And if so, add it, then save and try starting X.

---

### Post by PmDematagoda on 2008-05-02
If the above doesn't work then try executing:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then start the X-Server again.

---

