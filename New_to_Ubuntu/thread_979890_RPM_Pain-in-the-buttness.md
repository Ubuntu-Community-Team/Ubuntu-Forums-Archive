---
title: "RPM Pain-in-the-buttness"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by know-it-some on 2008-11-12
I enjoy installing packages through Add/Remove Packages in the Applications menu because it will (can) install any needed dependencies for you.  Unfortunately sometimes I need to install an RPM from a vendor.  Today I went to install an RPM and ended up with an absurd list of dependencies (and I keep my ubuntu box completely up to date).  

Is there a way to install a downloaded RPM through 'Add/Remove Packages'? I tried to open the RPM with Synaptic but it doesn't recognize RPM's as a valid package to install.  Thanks all...

---

### Post by PartisanEntity on 2008-11-12
You can use Alien to convert your rpm in to a deb file:
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

---

### Post by know-it-some on 2008-11-12
That's a good tip. Ashame that rpm will not install your dependencies for you like dpkg will.  Seems like a pretty basic option. Thanks.

---

### Post by taurus on 2008-11-12
Sometimes, if there is no .deb available, it's better to get the source and build it yourself instead of playing around with .rpm.

---

### Post by Simian Man on 2008-11-12
> **know-it-some said:**
> That's a good tip. Ashame that rpm will not install your dependencies for you like dpkg will.  Seems like a pretty basic option. Thanks.

The problem is that Ubuntu is a .deb based distro whereas .rpm files are built for .rpm based distros like Fedora, Mandriva and Suse.  I frequently install .rpms on Fedora and, of course, the system handles dependencies automatically.

BTW dpkg does not install dependencies either, apt does.

---

### Post by jimmy the saint on 2008-11-12
Yeah, trying to install an .rpm on a debian distro is like putting gasoline in a Diesel.  You can try, but you won't like it.  By the way, what is the program?  Maybe someone has built a deb?

---

### Post by daviebasite on 2008-11-12
Hi guys,
how to proceed when alien makes a folder with a lot of stuff inside it instead of *.deb file?

10x in advance

---

### Post by shadanan on 2008-11-12
As others have pointed out, using alien to convert an .rpm to a .deb file should really be a last resort. If there is no .deb file available, building from source is often the cleanest route. 

Alien is experimental and will almost certainly break when there are dependencies. Sometimes, it is unavoidable, such as printer drivers provided closed source via .rpm. In these cases, alien works well because there are usually no dependencies. Your mileage may vary.

So the real question is, what are you trying to install that you only have an .rpm of?

---

### Post by sharkster2007 on 2008-11-12
Is this any help:

[http://packages.ubuntu.com/intrepid/]("http://packages.ubuntu.com/intrepid/")

It leads to the official Ubuntu webpage for downloading .deb files for ubuntu 8.10, hope it helps you :-)

---

### Post by daviebasite on 2008-11-13
> Is this any help:

[http://packages.ubuntu.com/intrepid/](http://packages.ubuntu.com/intrepid/)

It leads to the official Ubuntu webpage for downloading .deb files for ubuntu 8.10, hope it helps you 

thanks for reply,
the application that I'm trying to install is not listed there. I'm trying to install "autodesk maya 2009" and one of it's rpm files becomes to a folder not to deb file. I don't know how to use that folder.

---

### Post by bcschmerker on 2008-11-13
> **know-it-some said:**
> That's a good tip. Ashame that rpm will not install your dependencies for you like dpkg will.  Seems like a pretty basic option. Thanks.

I have experience with both installers.  In my particular case, gOS 1.2 Painful (itself a derivative of Ubuntu 7.10 Gutsy, LinUX Kernel 2.6.22) is consistent with Debian Synaptic, whereas neither Red Hat Package Manager nor GZip was allowed to create needed directories for some software I wanted to install (a system-specific issue).  My only failure to date with Debian Synaptic was an attempted upgrade of Adobe Flash from 9 to 10 (a needed package was outdated, as the Flash 10 DEB is designed for Ubuntu 8.0.x Hardy rather than 7.10.x Gutsy); all other DEBs needed for my system installed without problems.

GZip being denied permission to create needed directories scrubbed the source-code option for a local build I wished to attempt; but that may not be the case with your system.  If you've the source, the necessary permissions, and a compiler package for the source-code language, in most cases you can build it.

---

### Post by daviebasite on 2008-11-14
For anyone that have problems installing rpm's just try this method:
```
sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

sudo rpm -ivh --nodeps your_software.rpm
```

thanks to "derby_sv" suggestion I managed to install the software without any trouble :)

---

### Post by SunnyRabbiera on 2008-11-14
well so far for me alien converts rpms quite well and I never had a problem with it

---

### Post by MaindotC on 2008-11-14
I've never had a problem either and I've never understood why everyone says it should be a last resort, but I've never had to install anything majour from an .rpm and usually I can find an equivalent .deb somewhere.  I'm a user, not a programmer, and I have no concept of the nitty-gritty technical details of how alien does its conversion which I would imagine some of the gosu programmers here understand.

---

### Post by 666porcondissaum on 2008-11-23
> **daviebasite said:**
> For anyone that have problems installing rpm's just try this method:
```
sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

sudo rpm -ivh --nodeps your_software.rpm
```

thanks to "derby_sv" suggestion I managed to install the software without any trouble :)

And a bif thank you to your quick-and-successful advice.

---

### Post by gandaran on 2008-11-23
here's another way of installing rpm's, it's not difficult to do and for me is the best way, no messing up anything!
extract the rpm package (you need peazip for this) now just manually install the extracted program/folders any where you like, assuming all dependencies are met all you need now is make a launcher that's point to the application, easy!

---

### Post by Bubs on 2008-12-14
I too have Maya 2009 and Had the SAME problem with one of the RPM's turning into a file instead of a .deb

But I have one question.  Won't installing RPM on your ubuntu machine mess up apt?

I've been searching for a way to get a maya installed.  and if this works I'll try it.  but I don't want to mess up APT!

---

### Post by pushprod on 2009-01-08
> **daviebasite said:**
> For anyone that have problems installing rpm's just try this method:
```
sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

sudo rpm -ivh --nodeps your_software.rpm
```

thanks to "derby_sv" suggestion I managed to install the software without any trouble :)

Awesome!!! This is the only thing that worked for me to install wavemaker! Alien did not work in my case.

Thanks a million:KS

---

