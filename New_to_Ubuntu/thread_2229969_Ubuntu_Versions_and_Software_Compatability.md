---
title: "Ubuntu Versions and Software Compatability"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by david228 on 2014-06-16
I'm a new user of Ubuntu and I have just installed Version 14.04

I have been looking in the Ubuntu Apps Directory ([https://apps.ubuntu.com/cat/](https://apps.ubuntu.com/cat/)) but I find that most of the available software seems to disapear when I click on the 14.04 tab.

Does this mean that I won't be able to utilise these programmes with my 14.04 and will have to wait for upgrades?

Or do I need to install an earlier version like 13.10 that seems to appear for most programmes.

I specifically want the Arduino IDE from the Electronics tab but it disapears in the 14.04 tab (but happily shows on 13.10).

---

### Post by LastDino on 2014-06-16
That is not yet available for 14.04, if you really really want that program and would downgrade for it, go for 12.04 LTS rather than 13.10. As 13.10 has almost reached it's end of life. 12.04 is long term supported version, just like 14.04, so you should be good till maybe support for 14.04 comes out, if ever, or 12.04 runs into EOL, whichever happens first.

---

### Post by Rob Sayer on 2014-06-16
That usually just means it hasn't been fully beta tested yet.

Before downgrading to 13.10 I'd try downloading the package from Aruino's site.

And if you do so, DON'T install the daily build or testing.  Get the stable version.

Generally I would recommend new linux users to stick to the official repos.  You can introduce problems with unsupported ppa's.  But in this case, where it was in the 13.10 repos, I'd make an exception.

---

### Post by grahammechanical on 2014-06-16
Arduino IDE is in the 14.04 software centre. It may not be the latest version but it is there.

Regards.

---

### Post by kansasnoob on 2014-06-16
> **grahammechanical said:**
> Arduino IDE is in the 14.04 software centre. It may not be the latest version but it is there.

Regards.

+1!

```
lance@lance-desktop:~$ apt-cache show arduino
Package: arduino
Priority: optional
Section: universe/electronics
Installed-Size: 1687
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Scott Howard <showard@debian.org>
Architecture: all
Version: 1:1.0.5+dfsg2-2
Depends: default-jre | java6-runtime, libjna-java, librxtx-java (>= 2.2pre2-3), arduino-core (= 1:1.0.5+dfsg2-2)
Recommends: extra-xdg-menus, policykit-1
Filename: pool/universe/a/arduino/arduino_1.0.5+dfsg2-2_all.deb
Size: 1164058
MD5sum: 1c49d26126aee347d8dbe7bb5ad63310
SHA1: bfc32edd8a7d9d77cc2f3494fdd8800218bba13f
SHA256: 6119224929dc0577199c1b32cc3a65b0c3a7c10339fa9f51237e1192dff6c49e
Description-en: AVR development board IDE and built-in libraries
 Arduino is an open-source electronics prototyping platform based on
 flexible, easy-to-use hardware and software. It's intended for artists,
 designers, hobbyists, and anyone interested in creating interactive
 objects or environments.
 .
 This package will install the integrated development environment that
 allows for program writing, code verfication, compiling, and uploading
 to the Arduino development board. Libraries and example code will also
 be installed.
Description-md5: 60f8f72e8783c6b5a72254120b680cdb
Homepage: http://www.arduino.cc
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

---

### Post by LastDino on 2014-06-16
> **grahammechanical said:**
> Arduino IDE is in the 14.04 software centre. It may not be the latest version but it is there.

Regards.
I can confirm this.
Forget about my previous post as I referred to that list instead of going into software center myself. Looks like that list hasn't been updated.:P

It is there in 14.04
Version is: arduino 1:1.0.5+dfsg2-2

Good luck!

---

### Post by david228 on 2014-06-16
> **grahammechanical said:**
> Arduino IDE is in the 14.04 software centre. It may not be the latest version but it is there.

Regards.

Thanks for the replies, however I remain a little bemused. I'm not sure what I am doing wrong but when I look at: [https://apps.ubuntu.com/cat/applications/arduino/](https://apps.ubuntu.com/cat/applications/arduino/) 
I do not see a 14.04, only 13.10 and earlier.

Neither do I see a "**Version is: arduino 1:1.0.5+dfsg2-2**" but a:
[TABLE]
[TR]
[TH]Version:
[/TH]
[TD]1.0.5+dfsg2
[/TD]
[/TR]
[/TABLE]

Are we looking at the same site/thing?   :confused:

---

### Post by david228 on 2014-06-16
And I am also at work right now using their antiquated Windows system, so I am unable to check the Arduino site which lists a: Linux: [32 bit]("http://arduino.googlecode.com/files/arduino-1.0.5-linux32.tgz"), [64 bit]("http://arduino.googlecode.com/files/arduino-1.0.5-linux64.tgz") 
without actually downloading the file to see which version it is.

---

### Post by LastDino on 2014-06-16
We are looking into Ubuntu software center. Which is default package manager in Ubuntu, you will see that once you install Ubuntu 14.04.

---

### Post by monkeybrain20122 on 2014-06-16
> **david228 said:**
> Thanks for the replies, however I remain a little bemused. I'm not sure what I am doing wrong but when I look at: [https://apps.ubuntu.com/cat/applications/arduino/](https://apps.ubuntu.com/cat/applications/arduino/) 
I do not see a 14.04, only 13.10 and earlier.

Neither do I see a "**Version is: arduino 1:1.0.5+dfsg2-2**" but a:
[TABLE]
[TR]
[TH]Version:[/TH]
[TD]1.0.5+dfsg2[/TD]
[/TR]
[/TABLE]

Are we looking at the same site/thing?   :confused:

Maybe that page is not up to date?

[https://launchpad.net/ubuntu/+source/arduino](https://launchpad.net/ubuntu/+source/arduino)
The package version in 14.04 is 1.0.5, which is the latest.

---

### Post by david228 on 2014-06-16
> **LastDino said:**
> We are looking into Ubuntu software center. Which is default package manager in Ubuntu, you will see that once you install Ubuntu 14.04.

There is a Software Centre tag on my 14.04 home system which I'll have a look at when I get home. Perhaps looking from the work computer is the problem.

---

### Post by david228 on 2014-06-16
> **monkeybrain20122 said:**
> Maybe that page is not up to date?

[https://launchpad.net/ubuntu/+source/arduino](https://launchpad.net/ubuntu/+source/arduino)
The package version in 14.04 is 1.0.5, which is the latest.

Thank you. Yes, the link you've supplied does show what I am after, however, being at work right now I can't do much with it (there is a lot of internet blocking done by my employer). I'll have a proper look from home later.

---

