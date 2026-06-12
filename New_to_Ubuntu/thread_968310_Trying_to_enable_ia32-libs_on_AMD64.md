---
title: "Trying to enable ia32-libs on AMD64"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by kvanbev1087 on 2008-11-02
I am trying to install programs that are not made for the AMD64 version of Ubuntu.  I read that I am supposed to run this:

$ sudo apt-get install ia32-libs

and when I did I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Does anyone have any idea what I should be doing for this?  The initial problem occurred when loading skype (a .deb file).  The error was:

Error: Wrong architecture 'i386'

Thanks!

---

### Post by phidia on 2008-11-02
The error from the system was when trying to install it-correct?

You don't have skype installed. I think you may need to install with the force option (see man dpkg)

---

### Post by kvanbev1087 on 2008-11-02
**I had initially tried the install command:**
sudo apt-get install skype-debian_2.0.0.72-1_i386.deb

**This is what happened:**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype-debian_2.0.0.72-1_i386.deb

**I then tried to install it like this:**
sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb

**And received this:**
dpkg: error processing skype-debian_2.0.0.72-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 skype-debian_2.0.0.72-1_i386.deb

**When I tried to force it with this command:**
sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb

**This is what I received:**
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package skype.
(Reading database ... 112714 files and directories currently installed.)
Unpacking skype (from skype-debian_2.0.0.72-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

That is when I tried to install ia32-libs and got the error I originally mentioned.

Thanks

---

### Post by jmszr on 2008-11-02
This may (repeat may) help: [http://ubuntuforums.org/showthread.php?t=432295&highlight=install+skype+64-bit](http://ubuntuforums.org/showthread.php?t=432295&highlight=install+skype+64-bit)

---

