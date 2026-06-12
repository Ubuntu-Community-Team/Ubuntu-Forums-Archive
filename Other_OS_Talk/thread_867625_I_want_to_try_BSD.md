---
title: "I want to try *BSD"
date: 2008-07-23
forum: Other OS Talk
---

### Post by L815 on 2008-07-23
So I've been distro hoppin for a while, and kind of want to switch things a bit. 
I hear good things about BSD based distros, but I also hear they are difficult to work with, more so than Linux. 


So I have a few questions:
How are the packages dealt with compared to Linux?
Is it easy to get up to date packages?
How big are the repos (if there are any)?
Can it be used for day to day desktop work? (audio, video, browsing, and programming )
What BSD based distro would you recommend me to try?

---

### Post by enlightenment now on 2008-07-23
> **L815 said:**
> So I've been distro hoppin for a while, and kind of want to switch things a bit. 
I hear good things about BSD based distros, but I also hear they are difficult to work with, more so than Linux. 


So I have a few questions:
How are the packages dealt with compared to Linux?
Is it easy to get up to date packages?
Is it hard to pick up?
Can it be used for day to day desktop work? (audio, video, browsing, and programming )
What BSD based distro would you recommend me to try?Actually, [PC-BSD]("http://www.pcbsd.org/") is a lot easier then any Linux distro to date, especially with the [PBI's]("http://www.pbidir.com/").

This would be my recommendation of where you should start, also while PC-BSD comes default with KDE, it also has an [Gnome PBI]("http://www.pbidir.com/bt/pbi/132").

Some more information about [PBI's are here]("http://www.pcbsd.org/content/view/20/26/"), about up to date packages I have found that PC-BSD is usually more up-to-date then Linux.

Anyway, have fun in your exploration and enjoy PC-BSD or any other variation of FreeBSD.

---

### Post by Bachstelze on 2008-07-23
(Note: this post mostly applies to Free- and OpenBSD, as I do not know the other ones enough to speak accurately about them)

> **L815 said:**
> 
I hear good things about BSD based distros, but I also hear they are difficult to work with, more so than Linux.

They're not, really. There is a learning curve, but it's true for each and every OS under the sun. Also, you musn't be afraid of the command line.


> **L815 said:**
> So I have a few questions:
How are the packages dealt with compared to Linux?


That really depends on the BSD version you're using. There are two major systems for managing third-party software: packages and ports. Packages are similar to what you see in most Linux distros: pre-compiled packages that you can install through a package management system that also takes care of all the dependencies. Ports, on the other hand, are similar to Gentoo's "Portage" system: they will fetch the sources for your software, compile them and install them for you.

Ultimately, there will be no difference: in both cases, you will have your software installed in the end, and the amount of work on your side isn't much different. There are differences, however: packages will ensure your system will remain consistent, avoid the need to install a compiling toolchain, and will obviously save a lot of time. Ports, on the other hand, will allow for more flexibility.

> **L815 said:**
> Is it easy to get up to date packages?

No less easy than in Linux: just a few commands to remember.

> **L815 said:**
> How big are the repos (if there are any)?

You can find a list of all packages available in OpenBSD 4.3 (current release at the time of writing) on the i386 architecture [here](ftp://ftp.openbsd.org/pub/OpenBSD/4.3/packages/i386/) and a list of all ports available in FreeBSD [here](http://www.freshports.org/categories.php).

> **L815 said:**
> Can it be used for day to day desktop work? (audio, video, browsing, and programming )

Certainly. However, the availability (or lack thereof) of drivers for your hardware will determine how convenient it will be, and that obviously depends on your hardware.


> **L815 said:**
> What BSD based distro would you recommend me to try?

I would recommend FreeBSD for desktop, daily use.

---

### Post by forger on 2008-07-23
It's more of an opinion, but pc-bsd would be better to start with.
A couple of info if you start with FreeBSD:
1) the ports (packages) are in /usr/ports/
2) the ports are separated in categories i.e. /usr/ports/ports-mgmt/portaudit
3) quick install commands, i.e. if you want to install portaudit:
pkg_add -r portaudit
cd /usr/ports/ports-mgmt/portaudit/
make install clean

uninstalling is easy too:
cd /usr/ports/ports-mgmt/portaudit/
make deinstall clean
4) for updating you need portsnap:
pkg_add -r portsnap

First time run:
portsnap fetch extract

After the first time, just update:
portsnap update

Check which packages need updating:
pkg_version -v | grep >

use **cd** to go to the ports' directory to install/upgrade and use:
make reinstall clean

5) use freebsd-update:
freebsd-update fetch
freebsd-update install

6) don't use port managers like portupgrade, tends to break stuff if you upgrade everything together :)

---

### Post by Bachstelze on 2008-07-23
> **forger said:**
> 
1) the ports (packages) are in /usr/ports/

Ports and packages are different things.

> **forger said:**
> 3) quick install commands, i.e. if you want to install portaudit:
pkg_add -r portaudit
cd /usr/ports/ports-mgmt/portaudit/
make install clean


No. That will install the package, then try to install the port, which will fail.


> **forger said:**
> uninstalling is easy too:
cd /usr/ports/ports-mgmt/portaudit/
make deinstall clean

Only if said software has been installed threough the ports. pkg_delete is usually the way to go, as it will work in both cases.

> **forger said:**
> 4) for updating you need portsnap:
pkg_add -r portsnap

First time run:
portsnap fetch extract

After the first time, just update:
portsnap update

Check which packages need updating:
pkg_version -v | grep >

use **cd** to go to the ports' directory to install/upgrade and use:
make reinstall clean

cvsup and portupgrade will make this all much simpler.

> **forger said:**
> 5) use freebsd-update:
freebsd-update fetch
freebsd-update install

Yeah. What does that do?

> **forger said:**
> 6) don't use port managers like portupgrade, tends to break stuff if you upgrade everything together :)

In years of using FreeBSD, portupgrade never broke anything for me.

All in all, just a bunch of random information that sometimes happen to be correct but thrown without explanations and that will therefore be more confusing than helpful.

---

### Post by L815 on 2008-07-23
Wow, thanks for the awesome responses; fast too.

I took a look at PC-BSD which I remember being interested in a while back. Right now I'm going to play with the vmware image since the live cd isn't out yet. 

FreeBSD I will look at second. (Hmm sounds like the Ubuntu - Debian relationship chart haha)


Anyway, I was looking through [http://www.pbidir.com/](http://www.pbidir.com/), PC-BSD's pbi site. Are these PC-BSD only, or can they also be used for FreeBSD and the like?

---

### Post by forger on 2008-07-23
I'm still a newbie around the BSD stuff. A bunch of random information gives a good starting point, without the need of a book. Then you start reading the book to go deeper!
Maybe they're confusing, my bad for that, but I didn't see anything from other people replies, no one mentioned commands for FreeBSD, so I thought to give some examples, *something* to mess around with in a virtual machine, until they figure out the best way to use freebsd

Every time I used portupgrade or portmanager, the kernel image (or something) got broken and I couldn't reboot afterwards :( Usually it's my fault, but anyway.. Sorry if I got you confused L815

---

### Post by Bachstelze on 2008-07-23
> **forger said:**
> 
Maybe they're confusing, my bad for that, but I didn't see anything from other people replies, no one mentioned commands for FreeBSD,

I might be wrong, but I think it's not really the purpose of this thread. The question is "which BSD system should I use", commands will come afterwards ;)

> **forger said:**
> Every time I used portupgrade or portmanager, the kernel image (or something) got broken and I couldn't reboot afterwards :(

This is really weird, because in all BSD systems, the base system (i.e. the kernel and other essential tools) are clearly separated from the third-party software, and both are managed in completely different ways. Portupgrade will never **ever** alter your kernel or base system in any way, it just manages ports.

---

### Post by forger on 2008-07-23
Hm.. it must've been portmanager then :redface: It's been a while, I'll try again and let you know hehe

---

### Post by kk0sse54 on 2008-07-23
I've tried PC-BSD before and while it's a good beginner BSD there is a lack of PBI's available. Don't get me wrong PBI's are really easy to install if you are used to the windows way of installing things but there isn't a lot of software out there. As for FreeBSD have the documentation handy at all times especially when you first try installing it and running it as it will really help you with things like getting a GUI. Another os you might want to look into is DesktopBSD which is directly based off FreeBSD(like pc-bsd but keep in mind neither are forks of FreeBSD) but is beginner oriented.

---

### Post by cardinals_fan on 2008-07-23
DesktopBSD is my recommendation for a first-time BSD user.  It's vanilla FreeBSD with a GUI included by default.

NetBSD is my personal favorite.

---

### Post by L815 on 2008-07-23
> **C!oud said:**
> I've tried PC-BSD before and while it's a good beginner BSD there is a lack of PBI's available. Don't get me wrong PBI's are really easy to install if you are used to the windows way of installing things but there isn't a lot of software out there. As for FreeBSD have the documentation handy at all times especially when you first try installing it and running it as it will really help you with things like getting a GUI. Another os you might want to look into is DesktopBSD which is directly based off FreeBSD(like pc-bsd but keep in mind neither are forks of FreeBSD) but is beginner oriented.

The pbi install was surprisingly identical to Windows. Although I'm not really picky in install methods, as long as I don't have to compile everything myself :p

It's kind of a bummer to hear there's a lack of pbi's, because I like to play with software; one of the reasons I came to Linux :/

---

### Post by kk0sse54 on 2008-07-23
> **L815 said:**
> 

It's kind of a bummer to hear there's a lack of pbi's, because I like to play with software; one of the reasons I came to Linux :/

For Linux software that isn't available for BSD there is a Linux  compatibility layer but I believe you have to install the software through ports and packages not PBI which due to the lack of software has pushed me away from PC-BSD. Try out DesktopBSD through a virtual machine, I don't know whether you prefer virtualbox or vmware but there is a VMware image available at [http://www.vmware.com/appliances/directory/1143](http://www.vmware.com/appliances/directory/1143)

---

### Post by enlightenment now on 2008-07-24
> **L815 said:**
> Wow, thanks for the awesome responses; fast too.

I took a look at PC-BSD which I remember being interested in a while back. Right now I'm going to play with the vmware image since the live cd isn't out yet. 

FreeBSD I will look at second. (Hmm sounds like the Ubuntu - Debian relationship chart haha)


Anyway, I was looking through [http://www.pbidir.com/](http://www.pbidir.com/), PC-BSD's pbi site. Are these PC-BSD only, or can they also be used for FreeBSD and the like?

PBI's are for PC-BSD only but don't get confused you can still use the manual install method in PC-BSD. Meaning for more experienced users or once you get more experience and comfortable you can still use the command line. 

also with the PBI builder you can essentially convert a FreeBSD port into a PBI file:

> The PBI builder is a powerful command-line script system, which can be used to convert a FreeBSD port into a PBI file. The configuration for this process is stored as a module, which can then be used to rebuild the PBI automatically. Developers can then submit these [finished  modules]("http://trac.pcbsd.org/browser/pbibuild/modules") to PC-BSD Software, where they will be added to a [build server]("http://www.pcbsd.org/content/view/48/30/"), which rebuilds the PBI every time the underlying port is updated.

Users with questions about the PBI Building process are encouraged to browse through the documentation, or contact us via mailing list. 

[PBI Builder HOWTO]("http://www.pcbsd.org/content/view/47/30/")
[PBI Developer Mailing List]("http://lists.pcbsd.org/mailman/listinfo/pbi-dev")[http://www.pbidir.com/bt/pbi/118/pbi_builder](http://www.pbidir.com/bt/pbi/118/pbi_builder)

> **C!oud said:**
> I've tried PC-BSD before and while it's a good beginner BSD there is a lack of PBI's available. Don't get me wrong PBI's are really easy to install if you are used to the windows way of installing things but there isn't a lot of software out there. As for FreeBSD have the documentation handy at all times especially when you first try installing it and running it as it will really help you with things like getting a GUI. Another os you might want to look into is DesktopBSD which is directly based off FreeBSD(like pc-bsd but keep in mind neither are forks of FreeBSD) but is beginner oriented.

Again see the post above, with PC-BSD the limitations on PBI are the ones you create yourself.

Keep in mind PC-BSD is based on FreeBSD.

> **L815 said:**
> The pbi install was surprisingly identical to Windows. Although I'm not really picky in install methods, as long as I don't have to compile everything myself :p

It's kind of a bummer to hear there's a lack of pbi's, because I like to play with software; one of the reasons I came to Linux :/Use the PBI Builder and actively contribute to PC-BSD and have fun doing so in the process.

PC-BSD is considered the Ubuntu of the BSD world, so if you like Ubuntu and it's concepts and philosophies but more importantly it's ease of use as a beginner OS, you will love PC-BSD. For those who want to more advanced, simply advance your level of usage and help build and develop PBI's. The only limitations are the ones we place upon ourselves, this is true for any distro whether Linux or BSD or other.

---

### Post by kk0sse54 on 2008-07-24
Sweet, I had no idea that there was a way of converting a FreeBSD port into a PBI yet for the average beginner to BSD who doesn't know how to install via ports and isn't advanced enough to build their own PBI the software selection is still quite limited which might push them away from PC-BSD.

---

