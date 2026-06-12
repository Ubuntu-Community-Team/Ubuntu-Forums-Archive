---
title: "Can't install Outrec."
date: 2013-06-22
forum: New to Ubuntu
---

### Post by cheapodonuts on 2013-06-22
I've used Outrec before on a previous Ubuntu distro. But now the Software Centre won't install it, saying, "Dependency is not satisfiable: gambas2-runtime (>=1.9.48)"  and apparently giving the ERROR :- "This program is written in gambas."

---

### Post by monkeybrain2012 on 2013-06-22
It looks like outrec has not been maintained for quite some time, so I think it is abandoned. gambas2 is needed for outrec but Ubuntu has switched to gambas3. However you can still install it in 13.04 by grabbing the gambas 2 dependencies from quantal's repository. 

The dependencies are, from outrec's website
 > gambas2-gb-gui, gambas2-runtime, gambas2-gb-form, gambas2-gb-desktop

For 64 bits download the debs here[URL="https://launchpad.net/ubuntu/quantal/amd64/gambas2-runtime/2.23.1-1ubuntu3"]

https://launchpad.net/ubuntu/quantal/amd64/gambas2-runtime/2.23.1-1ubuntu3[/URL]
[https://launchpad.net/ubuntu/quantal/amd64/gambas2-gb-gui/2.23.1-1ubuntu3](https://launchpad.net/ubuntu/quantal/amd64/gambas2-gb-gui/2.23.1-1ubuntu3) [URL="https://launchpad.net/ubuntu/quantal/amd64/gambas2-gb-form/2.23.1-1ubuntu3"]
https://launchpad.net/ubuntu/quantal/amd64/gambas2-gb-form/2.23.1-1ubuntu3[/URL]  [URL="https://launchpad.net/ubuntu/quantal/amd64/gambas2-gb-desktop/2.23.1-1ubuntu3"]
https://launchpad.net/ubuntu/quantal/amd64/gambas2-gb-desktop/2.23.1-1ubuntu3[/URL]

You can find similar pages for 32 bits

EDITED: to install these you will run into other dependencies problem. Just track down the packages the same way (see screen shot for the debs I got) 

To install all of them at once, put all these into one folder, say, outrec-dep on your desktop, then
```
cd Desktop/outrec-dep
sudo dpkg -i *.deb
```

If you have problem installing from the Software Centre you can download outrec at source forge
[http://sourceforge.net/projects/outrec/files/](http://sourceforge.net/projects/outrec/files/)
As you can see it has no new release since July 2010.

---

### Post by cheapodonuts on 2013-06-23
Thanks for the info MB, I'll upgrade to 13.04 and try it. 

Have a donut or twelve. :)

[IMG]http://i81.photobucket.com/albums/j226/chashugh/donuts-3.jpg[/IMG]

---

### Post by SeijiSensei on 2013-06-23
I tried compiling outrec from source but had numerous problems with the gambas2 dependencies.  I finally gave up.  The 10.04 deb on the website installed fine in 12.04 because the gambas3 dependencies had not yet kicked in.  It's really a shame development ended on outrec because it is the only simple solution to grabbing audio output I've found.

---

### Post by monkeybrain2012 on 2013-06-23
> **SeijiSensei said:**
> I tried compiling outrec from source but had numerous problems with the gambas2 dependencies.  I finally gave up.  The 10.04 deb on the website installed fine in 12.04 because the gambas3 dependencies had not yet kicked in.  It's really a shame development ended on outrec because it is the only simple solution to grabbing audio output I've found.

hI,

How would you compile outrec from source? In Fedora the gambas2 requirement is satisfied, but there is no outrec rpm. So I grabbed the tar ball and tried to compile it but I don't even know where to start, it is not a typical "./configure make make install" deal and there is no instruction in the tar ball.

---

### Post by SeijiSensei on 2013-06-23
Hmm, I don't recall to be honest.  I got so tired of trying to navigate "dependency hell," that I just gave up.

I looked again at the source tree.  I think you are supposed to run ./outrec_EN.gambas which sets up some environment variables then has an executable.  With no documentation anywhere, I was left just to browse the offered files and make guesses.

---

### Post by mc4man on 2013-06-23
If really inclined you can run outrec in 13.04, probably better to build then use the 12.04 .deb, just install some basic build packages, inc. debhelper & fakeroot. (takes all of 15 secs to build.

I guess it works ok, never really used so don't know if it uses gst-0.10, if so then that's only partially installed in 13.04. Here just installed sox & a couple of sox packages, seemed to do the trick.

Package list for amd64, i386 would be the same except for using the i386 packages (all.debs are i386
location of all but libqt3-mt
i386
[https://launchpad.net/ubuntu/+source/gambas2/2.23.1-1ubuntu3/+build/2989123](https://launchpad.net/ubuntu/+source/gambas2/2.23.1-1ubuntu3/+build/2989123)
amd64
[https://launchpad.net/ubuntu/+source/gambas2/2.23.1-1ubuntu3/+build/2989120](https://launchpad.net/ubuntu/+source/gambas2/2.23.1-1ubuntu3/+build/2989120)

> gambas2-dev_2.23.1-1ubuntu3_amd64.deb         
gambas2-gb-gui_2.23.1-1ubuntu3_amd64.deb
gambas2-gb-db_2.23.1-1ubuntu3_amd64.deb      
gambas2-gb-qt_2.23.1-1ubuntu3_amd64.deb
gambas2-gb-db-form_2.23.1-1ubuntu3_all.deb    
gambas2-gb-qt-ext_2.23.1-1ubuntu3_amd64.deb
gambas2-gb-desktop_2.23.1-1ubuntu3_amd64.deb  
gambas2-gb-settings_2.23.1-1ubuntu3_all.deb
gambas2-gb-form_2.23.1-1ubuntu3_all.deb       
gambas2-runtime_2.23.1-1ubuntu3_amd64.deb
gambas2-gb-gtk_2.23.1-1ubuntu3_amd64.deb      
libqt3-mt_3.3.8-b-8ubuntu3_amd64.deb
gambas2-gb-gtk-ext_2.23.1-1ubuntu3_amd64.deb

The source has a debian folder so just this at source prompt
fakeroot debian/rules binary

Ex.
> ~/Downloads/test1/outrec-0.0.3.orig$ fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean -k
dh_clean: dh_clean -k is deprecated; use dh_prep instead
dh_installdirs
touch install-stamp
dh_testdir -i
dh_testroot -i
dh_installdocs -i
dh_installchangelogs -i
dh_install -i
dh_installmenu
dh_compress -i
dh_fixperms -i
dh_installdeb -i
dh_gencontrol -i
dh_md5sums -i
dh_builddeb -i
dpkg-deb: building package `outrec' in `../outrec_0.0.3-1_all.deb'.
dh_testdir


I'd use [audio-recorder instead]("https://launchpad.net/~osmoma/+archive/audio-recorder"), by default simple to use, can be configured to a fair extent

(The outrec.desktop needs a %<letter>  on the Exec= line to show up properly in Dash & launcher, %f is ok
```
Exec=/usr/bin/outrec.gambas %f
```

---

### Post by cheapodonuts on 2013-06-24
Argh! It's all looking a bit complex for my one cell brain! :confused:  Hehe, ok, thanx mc4, I'll try audio recorder. :D

---

