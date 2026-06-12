---
title: "NetbootCD - download and boot Linux installers w/ kexec"
date: 2008-12-02
forum: Other OS Talk
---

### Post by maybeway36 on 2008-12-02
I've just uploaded a new project to tuxfamily, called NetbootCD. It is a Debian live CD that uses an interactive menu to download a Linux netboot installer from the Internet and run it with kexec. This is useful if you want to install an up-to-date version of a development system (e.g. Fedora Rawhide, Debian testing, the next verison of Ubuntu.)

Main site: [http://netbootcd.tuxfamily.org/]("http://netbootcd.tuxfamily.org/")

Currently supported distributions are Ubuntu, Debian GNU/Linux, Fedora, openSUSE, Mandriva Linux and CentOS. You can also download and run [SliTaz]("http://www.slitaz.org/en"), or just use the Debian system on the CD (apt-get is fully functional.)

---

### Post by WaeV on 2008-12-02
Sounds cool.  It's the solution to the running-out-of-CDs-to-install-my-new-distro problem!

---

### Post by maybeway36 on 2008-12-02
Note: Version 1.0 has a problem where only CentOS works; please wait until version 1.1 to download (should be out within 24 hours.)

EDIT: Version 1.1 is out now, with the bug fixed. Try it out and tell me what you think.

---

### Post by LinuxGuy1234 on 2008-12-06
> **maybeway36 said:**
> I've just uploaded a new project to tuxfamily, called NetbootCD. It is a Debian live CD that uses an interactive menu to download a Linux netboot installer from the Internet and run it with kexec. This is useful if you want to install an up-to-date version of a development system (e.g. Fedora Rawhide, Debian testing, the next verison of Ubuntu.)

Main site: [http://netbootcd.tuxfamily.org/]("http://netbootcd.tuxfamily.org/")

Currently supported distributions are Ubuntu, Debian GNU/Linux, Fedora, openSUSE, Mandriva Linux and CentOS. You can also download and run [SliTaz]("http://www.slitaz.org/en"), or just use the Debian system on the CD (apt-get is fully functional.)

This might be cool! I personally hate to waste CDs and DVDs for openSUSE, Ubuntu, Debian and CentOS to virtualize.

---

### Post by Grant A. on 2008-12-06
I don't find CD wasting a problem. Especially when nice x4 writing speed CD-RWs are available for $4 USD :)

But it is quite a nice project for testing development distros in VMs. Great work.

---

### Post by maybeway36 on 2009-01-20
I just put out a new version of NetbootCD. Version 2.0 is based on the Slax core and is only 61.5MB. The supported distributions remain the same.
Note: on the new CD, login as "root" with password "toor", just like in Slax.

---

### Post by meborc on 2009-01-21
now if i put your project and [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) together, i would have a USB stick that could "do it all" :D

sweet, gonna try out now

---

### Post by maybeway36 on 2009-02-09
I just put out version 2.1, which fixes a couple bugs and adds the ability to update the script from the website while the Live CD is running.

---

### Post by cardinals_fan on 2009-02-09
This ought to make CentOS installs much easier.  Thank you!

---

