---
title: "Broken QGIS ppa in 12.04"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by myotis on 2012-04-28
I had a ppa set up for QGIS in 11.10, but after upgrading to 12.04 (yesterday), trying to run QGIS gave an Ubuntu internal error message.

I edited the ppa repository address so it referred to precision, and ran update, but no updates were identified.

I then disabled the original ppa and added the nightly build ppa, this installed QGIS 1.9, rather than the current 1.7 version.

Then seeing in a blog that the release version of QGIS was now available for 12.04, so I did a complete uninstall of QGIS 1.9, disabled the nightly build ppa and re-enabled the current ppa for QGIS 1.7. However, this did not re-install 1.7, indeed nothing happened, but I then realised that installing 1.9 had not uninstalled 1.7.

I tried to reinstall 1.7, but got an error message that QGIS couldn't be found, so I did a complete unintstall of QGIS 1.7.

Deleted all the ppa details and started afresh with the ppa for 1.7 on precise, but after reloading the repository list I am now just getting a message that QGIS isn't available if I use the command line or the Software centre.

I have obviously done something stupid here, and would appreciate some help to get QGIS 1.7 reinstalled in Precise.

Many thanks,

Graham

---

### Post by myotis on 2012-04-28
To reply to myself, re-enabling the nightly build ppa gives me access to QGIS 1.9 again, I wonder if there is in fact no precise version of 1.7 actually in the ppa for that build?

Graham

---

### Post by kaplis on 2012-04-28
Hei!

There are Qgis version to all previous distributions, so there have to be for 12.04 as well (lets hope). In fact, so far Qgis 1.9 is working quite well for me and it seems even much better than 1.7.

Software center provides the 1.9 version, which seems quite uncommon for Ubuntu:)

Good luck.

---

### Post by myotis on 2012-04-28
Thanks, but the problem is that I can't get any version through the Ubuntu repository.

For now, I have 1.9 through ppa, but still don't understand why I get the message through theSoftware centre that QGis isn't available.

Graham

---

### Post by Jolicoeur on 2012-04-28
Me too.  It is listed in the Software Center but it is not available to download.  anybody have any ideas on how to load this program and when it will be available?  It was available in 11.10.:(



> **myotis said:**
> Thanks, but the problem is that I can't get any version through the Ubuntu repository.

For now, I have 1.9 through ppa, but still don't understand why I get the message through theSoftware centre that QGis isn't available.

Graham

---

### Post by myotis on 2012-04-29
> **Jolicoeur said:**
> Me too.  It is listed in the Software Center but it is not available to download.  anybody have any ideas on how to load this program and when it will be available?  It was available in 11.10.:(

That changes things a bit, as I assumed that I had broken something, but this sounds more fundamental. However, Kaplis said that the software centre provides 1.9 so it doesm
N't seem broken for everyone.

Graham

---

### Post by webwurst on 2012-04-29
It seems GQIS packages are removed from Ubunte Precise:
[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=qgis](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=qgis)
[http://www.ubuntuupdates.org/package/core/precise/universe/base/qgis](http://www.ubuntuupdates.org/package/core/precise/universe/base/qgis)

There we have a bug report stating it is removed from because of building erros and lack of maintanance:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=662195](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=662195)

But concerning packages were from version 1.4.0. There have never been newer Version.


Can you please tell me what repository/ppa works with Ubuntu Precise?
"ppa:ubuntugis/ubuntugis-unstable" did not work for me.

---

### Post by myotis on 2012-04-29
> **webwurst said:**
> Can you please tell me what repository/ppa works with Ubuntu Precise?"ppa:ubuntugis/ubuntugis-unstable" did not work for me.

It didn't work for me either in precise (but was working with 1.7 in 11.10)

I ended up with the daily build ppa, its further down the install page that has the unstable ppa.

I haven't done anything more than launch it an load a project with it, so I can't promise it will work - or keep working.

Graham

---

### Post by arlen on 2012-05-03
Check [http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master](http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master)

I just installed QGIS in Precise by adding the sources, adding the public key, and installing using apt.

---

### Post by myotis on 2012-05-03
> **arlen said:**
> Check [http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master](http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master)

I just installed QGIS in Precise by adding the sources, adding the public key, and installing using apt.

I will give it another try, it certainly wasn't working before, which is why I ended up with the weekly build.

Thanks,

Graham

---

### Post by kjano on 2012-05-08
bad news, I really need QGIS. I ave 1.7 running on my 12.04 right now but many plug-ins are not working. I will try to switch to 1.9.

---

### Post by kjano on 2012-05-09
Installed 1.9 still getting the following error:

Warning: loading of qgis translation failed [/usr/share/qgis/i18n//qgis_en_US]
Warning: loading of qt translation failed [/usr/share/qt4/translations/qt_en_US]
qgis.bin: /build/buildd/sip4-4.13.2/siplib/siplib.c:10938: sipEnumType_alloc: Assertion `(((currentType)->td_flags & 0x0007) == 0x0003)' failed.
Aborted (core dumped)

---

### Post by notbitmonk on 2012-05-13
There is no Precise package for the stable release. Look at [http://ppa.launchpad.net/ubuntugis/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubuntugis/ppa/ubuntu/dists/) and you will not see Precise in there. If you go to [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/dists/](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/dists/) you will see Precise. In the packages list ([http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/dists/precise/main/binary-i386/Packages)) QGIS is not included. That means that it has not been packaged for Precise (I hope that it happens soon). Looking at bug 935395 ([https://bugs.launchpad.net/ubuntu/precise/+source/qgis/+bug/935395](https://bugs.launchpad.net/ubuntu/precise/+source/qgis/+bug/935395)), it appears that the current version was deleted.

---

### Post by notbitmonk on 2012-05-13
Look at [http://trac.osgeo.org/ubuntugis/wiki/PackageUpdates?version=8](http://trac.osgeo.org/ubuntugis/wiki/PackageUpdates?version=8). Wildintellect is working on the Precise port.

---

### Post by kjano on 2012-05-13
I played around a bit more and got the following repositories to work:
deb     [http://qgis.org/debian-nightly](http://qgis.org/debian-nightly) precise main
deb-src [http://qgis.org/debian-nightly](http://qgis.org/debian-nightly) precise main

(I am sure I tried them without sucess some days ago)

---

### Post by Jolicoeur on 2012-05-14
I did this too, twice. both times the program worked but did not allow me to add plugins. so I removed it and re-installed 12.04. Now  I am waiting for a fully working version to show up in the software store.

any ideas when QGIS will be added?

> **arlen said:**
> Check [http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master](http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master)

I just installed QGIS in Precise by adding the sources, adding the public key, and installing using apt.

---

### Post by mountaintrekker on 2012-07-06
In the address:  [http://hub.qgis.org/projects/quantum-gis/wiki/Download](http://hub.qgis.org/projects/quantum-gis/wiki/Download) appears the following:  "QGIS is available on Windows, MacOS X, Linux and Android. Binary  packages are provided for the current version. The current version is  QGIS 1.8.0 and was released in June 2012"  I had try to install qgis 1.8.0 on ubuntu 12.04 without success, each time I read the message "qgis package not available" Perhaps we have to wait.

---

### Post by Daniel Wing on 2012-07-25
This is how I solved it step by step. I'm trying to keep this as easier as possible for newbies so you might gonna find many annoying comments or lines that could sound obvious for some expertise levels.

All keys and repositories are the QGIS official ones. You can corroborate here: [http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master](http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master)

1. Open "Synaptic Package manager" or "Ubuntu Software Center" and add the repositories as follows:

In "Synaptic Package manager" the path is: Settings-Repositories-Other Software-Add.
In "Ubuntu Software Center" the path is: Edit-Software sources-Other Software-Add.

Once there, enter each one of the lines below at a time.

deb [http://qgis.org/ubuntugis-nightly](http://qgis.org/ubuntugis-nightly) precise main
deb-src [http://qgis.org/ubuntugis-nightly](http://qgis.org/ubuntugis-nightly) precise main
deb [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) precise main

2. Now we need to add the public keys of QGIS as follow:

Open a terminal and type:

gpg --keyserver keyserver.ubuntu.com --recv 1F9ADD375CA44993 089EBE08314DF160
Hit enter or return (wherever you call it, for me is the same). It may ask for your password, just type it in and hit enter again. Now add the next line.
gpg --export --armor 1F9ADD375CA44993 089EBE08314DF160 | sudo apt-key add -
Once again hit enter. Now type:
sudo get-apt update
Hit enter for the last time and close the terminal.

Now go the Ubuntu Software center or Synaptic Package Manager and install as usual. I would recomend to use Synaptic since it has been more realiable in my experience. Not only for QGIS but any software related issue.

This is my first post here so if it is not clear or if you need any help contact me at my email.

---

### Post by Daniel Wing on 2012-07-25
Sorry I forgot to add some info that may result important for some:

Notes:

A) By doing it this way you will use the nightly build but you can as well use the regular package. The repositories would be:

deb     [http://qgis.org/debian](http://qgis.org/debian) precise main
deb-src [http://qgis.org/debian](http://qgis.org/debian) precise main 

B) This is for the Precise distro. If you're running a differente one,  just check the web page for the right repositorie (or just change  "Precise" for whatever you distro is).

Regards.

---

### Post by gavinlamont on 2012-08-04
Don't kow much about these things, but I went into Synaptic Pacakage manager > settings > repositories > other software tab and added: <[http://qgis.org/debian](http://qgis.org/debian) precise main>.  In main synaptic screen > reload.  Then a Qgis became available, which I installed, again from Synaptic.  This turned out to be version 1.8 -- Lisboa -- not the 1.7 or 1.9 I see mentioned above.  But it seems work.

---

