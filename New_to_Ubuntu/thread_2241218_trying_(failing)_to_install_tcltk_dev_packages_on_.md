---
title: "trying (failing) to install tcl/tk dev packages on 14.04.01"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by bron2 on 2014-08-25
I'm trying to install the Tcl/Tk development packages onto Ubuntu 14.04.0 (which I just installed on a new laptop).  After some struggle, I was able to eventually install tcl8.6-dev, although to do so, I had to install dpkg-dev, which in turn required me to down-grade perl from the default installed version (i.e. 1.17.5ubuntu5.3) to version 1.17.5ubuntu5.  But so far I have unable to install tk8.6-dev.  When I try, it fails because it depends on libxft-dev, the install of which fails in turn because it depends on libfontconfig1-dev, which fails in turn because it depends on libfontconfig1 version=2.11.0-0ubuntu4, whereas version=2.11.0-0ubuntu4.1 is the version that is installed.  When I try to down-grade, apt-get seems to run, but doesn't actually do anything.  i.e:

$ sudo apt-get install libfontconfig1=2.11.0-0ubuntu4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libfontconfig1
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Note the last line: nothing was done, and the system still claims that version 2.11.0-0ubuntu4.1 is installed.

Anyway, it's clear that I'm lost in the weeds at this point, and even if I manage to downgrade this, it seems unlikely that I'm actually getting any closer to my real goal of installing tk8.6-dev.  While I have a lot of experience writing compilers and such, I know almost nothing about Ubuntu system administration, so I'm hoping that I'm just doing something blantantly wrong here.  Suggestions?

---

### Post by steeldriver on 2014-08-25
Hello and welcome to the forums

Have you installed any software from PPAs? that can sometimes cause these kinds of situations. Also were you able to figure out why the installation of tcl8.6-dev required manual installation of dpkg-dev? Normally when packages are installed either via the Software Center or apt-get they pull in all the necessary dependencies automatically.

---

### Post by bron2 on 2014-08-25
I don't know what "PPA" stands for, but as far as installation goes: I made a 14.04.01 USB stick, then installed it in UEFI mode on the new computer, with no internet connection.  Once it was up, I connected to the net and installed the "restricted extras" package.  But that's it.

As to why it didn't auto-install dpkg-dev ... I don't know.  I'm guessing (just a guess mind you), that the problem is that the installation thinks it needs to downgrade one or more packages, and that it doesn't do that automatically. I tried using the "Ubuntu Software Center" app first, and when I tried to install tcl8.6-dev a pop-up window told me there were "unresolved dependencies", but when I clicked the "More Info" button, the list of reasons was blank.  So I reverted to the apt-get interface, and it told me that dpkg-dev needed to be installed "but that isn't going to happen" (that may not be an exact quote).  I then tried to use apt-get to manually install dpkg-dev, and it told me that it required a specific version of perl "( = 1.17.5ubuntu5)" verses the actual installed version 1.17.5.ubuntu5.3.  I thought that was kind weird that the requirement was "=" rather than ">=", but i was able to manually downgrade with "apt-get install perl=1.17.5.ubuntu5", which allowed me to install dpkg-dev, which allowed me to install tcl8.6-dev

Trying to do the same sort of thing with tk8.6-dev hasn't worked so far.  I get the same sort of unresolved dependencies that for some reason won't auto-install.  Manually tracing down one branch of the dependency tree leads me to the situation described in the original post: libfontconfig1-dev seems to depend on a specific version of libfontconfig1 ("=" rather than ">="), but for reasons I don't pretend to understand, the apt-get command does not downgrade the package.  But taking a step back from this makes me think I'm doing something more fundamentally wrong.  The installation shouldn't be requiring this much manual intervention and shouldn't be needing downgrades.  Plus this is only one branch of the tk8.6-dev dependencies; no doubt the other branch will have just as much uglyness.  So I'm thinking I screwed up something more basic.  But I'm currently clueless about what that might be.

---

### Post by steeldriver on 2014-08-26
That all sounds very odd - I just tried it on a 14.04.1 virtual machine (originally an Ubuntu Server install, but with a minimal lubuntu desktop installed on top) and both tcl8.6-dev and tk8.6-dev installed without requiring any additional intervention. Sorry I have no idea what could have gone wrong but I just wanted to assure you it's NOT normal.

---

### Post by bron2 on 2014-08-26
> **steeldriver said:**
> both tcl8.6-dev and tk8.6-dev installed without requiring any additional intervention
Wow.  That's lot more effort expended on my behalf than I expected.  Thanks for verifying that the install does in fact work correctly.  I don't know what's different about mine, but I'll try a clean re-install of ubuntu and see where that takes me.  One last question .. could you verify the versions of perl and libfontconfig1 that are on the machine that correctly did the install?  It might be instructive to know if, say, the perl on that machine is  1.17.5ubuntu5  or  1.17.5ubuntu5.3 (or something else entirely).

Many Thanks!

---

### Post by steeldriver on 2014-08-26
This is what I get

```

$ dpkg -l dpkg-dev libfontconfig1 perl tcl8.6-dev tk8.6-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-=======================================================================
ii  dpkg-dev                          1.17.5ubuntu5.3       all                   Debian package development tools
ii  libfontconfig1:amd64              2.11.0-0ubuntu4.1     amd64                 generic font configuration library - runtime
ii  perl                              5.18.2-2ubuntu1       amd64                 Larry Wall's Practical Extraction and Report Language
ii  tcl8.6-dev:amd64                  8.6.1-4ubuntu1        amd64                 Tcl (the Tool Command Language) v8.6 - development files
ii  tk8.6-dev:amd64                   8.6.1-3ubuntu2        amd64                 Tk toolkit for Tcl and X11 v8.6 - development files

```

```

$ uname -a
Linux trusty-server 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

```

I guess you're referring to **libdpkg-perl** being 1.17.5ubuntu?

```

$ dpkg -l libdpkg-perl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-=======================================================================
ii  libdpkg-perl                      1.17.5ubuntu5.3       all                   Dpkg perl modules

```

---

### Post by bron2 on 2014-08-26
libdpkg-perl, yes, right.

I really appreciate that, although I must admit I'm annoyed that the "Version" column is so narrow that it chopped off the part of the output I was interested in (i.e. the last couple of characters of the version id's of libfontconfig1 and libdpkg-perl); sorry to waste your time.  Thanks again.

---

### Post by steeldriver on 2014-08-26
oops my bad - please see edited version above

---

### Post by bron2 on 2014-08-26
Extra terrific!  That's useful to know.  I won't be able to re-install from scratch until tomorrow; I'll post again when (if) I find out anything useful.

---

### Post by bron2 on 2014-08-28
Doing a wipe and a full re-install seems to have solved this problem.

Obviously my previous install was screwed up in some way.  This time, I connected to the WiFi, and let it install the updates and the extras as part of the installation.  Once that came up, I was able to do "sudo apt-get install tcl-dev" and "sudo apt-get install tk-dev" without incident.  I admit I was surprised by the sheer number of packages that got pulled in to resolve the Tcl/Tk dependencies, but it all worked smoothly.

Many Thanks!!

---

