---
title: "Problems installing skype"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by zeemanCharmz on 2012-11-19
Hallo Internet!!.. I am having problems installing skype. I am on version 12.10. After following the guidelines on this URL: [http://www.itworld.com/software/315353/install-skype-41-ubuntu-1210](http://www.itworld.com/software/315353/install-skype-41-ubuntu-1210)
Here is what I got: 

```
nyasha@ubuntu:/tmp$ sudo dpkg -i skype-ubuntu*.deb
Selecting previously unselected package skype.
(Reading database ... 209255 files and directories currently installed.)
Unpacking skype (from skype-ubuntu-precise_4.1.0.20-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-dbus (>= 4:4.5.3); however:
  Package libqt4-dbus:i386 is not installed.
 skype depends on libqt4-network (>= 4:4.8.0); however:
  Package libqt4-network:i386 is not installed.
 skype depends on libqt4-xml (>= 4:4.5.3); however:
  Package libqt4-xml:i386 is not installed.
 skype depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4:i386 is not installed.
 skype depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:i386 is not installed.
 skype depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4:i386 is not installed.
 skype depends on libxss1; however:
  Package libxss1:i386 is not installed.
 skype depends on libxv1; however:
  Package libxv1:i386 is not installed.

dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 skype
nyasha@ubuntu:/tmp$ 

```
So please help me! I kinda stuck @ this stage and do not know how to fix this!!..
Thanx in advance!!..

---

### Post by squakie on 2012-11-19
Why get a separate download for Skype?  I would remove everything you've done so far, then:

sudo apt-get install skype

This should install the skype package correct for your version of ubuntu, and it *should* install the dependencies as well.

It has all worked for me each new release.

---

### Post by zeemanCharmz on 2012-11-19
Thanx Squakie!! 
Is there some shorter way of removing what I have done so far??..

---

### Post by fibercut on 2012-11-19
FYI

Dependencies are things the program needs to run or install. The error is pretty obvious there is things that the program needs but are not installed. Install the dependencies and it will install.

> dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-dbus (>= 4:4.5.3); however:
  Package libqt4-dbus:i386 is not installed.
 skype depends on libqt4-network (>= 4:4.8.0); however:
  Package libqt4-network:i386 is not installed.

---

### Post by squakie on 2012-11-19
> **fibercut said:**
> FYI

Dependencies are things the program needs to run or install. The error is pretty obvious there is things that the program needs but are not installed. Install the dependencies and it will install.

No need to do that if you use the package manager to do it from the repositories.  Not to mention, the downloads seem to be looking at precise things, when, if 12.10 is installed, would be wrong.  Notice it is talking about some libs that need to be newer than what the OP has installed.  Trying to download dependencies can get you in a progressively worse loop.  Apt allows trying to do that via sudo apt-get build-dep <package name>, but again, using the package manager and the standard repositories is the easiest way.

For zeemanCharmz, try just doing the install as I noted, without deleting anything, and see if it works.  If not, we'll try backing it out.  This should also guarantee that the correct dependencies are installed.  BTW - what version of Ubuntu are you running?

---

### Post by zeemanCharmz on 2012-11-19
This is what I did:
I discovered that there were certain system packages which were broken:
[img] http://ubuntuforums.org/attachment.php?attachmentid=227384&stc=1&d=1353311212[/img]
After that I ran the following commands:
```
 sudo apt-fast istall -f
sudo apt-fast install skype
```
and it worked

Thanx guys for all your advices!!..

---

