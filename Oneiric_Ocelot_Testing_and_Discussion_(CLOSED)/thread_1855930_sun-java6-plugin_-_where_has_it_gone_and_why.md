---
title: "sun-java6-plugin - where has it gone and why?"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nicolasdiogo on 2011-10-07
hello,

i have some applications that require to be run as applet using the original sun-java

i am not sure why this package is no longer available - any idea which repository i would find this now?


thanks,

---

### Post by effenberg0x0 on 2011-10-07
It looks like they're at their usual place. Maybe it just took a bathroom break when you searched.

```
[08:29 ][al:AL-DESK:~]
$ sudo apt-get install sun-java6-plugin
[sudo] password for al: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
[08:30 ][al:AL-DESK:~]

``````

[08:32 ][al:AL-DESK:~]
$ sudo apt-cache show sun-java6-plugin
Package: sun-java6-plugin
Source: sun-java6
Priority: optional
Section: web
Installed-Size: 60
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 6.26-1natty1
Depends: libasound2, libx11-6, libxext6, libxi6, libxt6, libxtst6, sun-java6-bin (>= 6.26-1natty1), firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | moblin-web-browser | xulrunner | xulrunner-1.9 | konqueror | chromium-browser | midori | google-chrome
Filename: pool/partner/s/sun-java6/sun-java6-plugin_6.26-1natty1_amd64.deb
Size: 1866
MD5sum: b03a724187ed16305bc301ae13d1428d
SHA1: ef9a5fc1772090bace33f51b6b873bf580f3ff93
Description: Java(TM) Plug-in, Java SE 6
 Java Plug-in enables applets written to the Java Platform 6
 specification to be run in Mozilla and other web browsers.
 Java Plug-in comes with the Java Runtime Environment (JRE).
 .
 This is a metapackage containing dependencies for running Java in
 various browsers.
Npp-Mimetype: application/x-java-vm, application/x-java-applet, application/x-java-applet;version=1.1, application/x-java-applet;version=1.1.1, application/x-java-applet;version=1.1.2, application/x-java-applet;version=1.1.3, application/x-java-applet;version=1.2, application/x-java-applet;version=1.2.1, application/x-java-applet;version=1.2.2, application/x-java-applet;version=1.3, application/x-java-applet;version=1.3.1, application/x-java-applet;version=1.4, application/x-java-applet;version=1.4.1, application/x-java-applet;version=1.4.2, application/x-java-applet;version=1.5, application/x-java-applet;version=1.6, application/x-java-applet;jpi-version=1.6.0_07, application/x-java-bean, application/x-java-bean;version=1.1, application/x-java-bean;version=1.1.1, application/x-java-bean;version=1.1.2, application/x-java-bean;version=1.1.3, application/x-java-bean;version=1.2, application/x-java-bean;version=1.2.1, application/x-java-bean;version=1.2.2, application/x-java-bean;version=1.3, application/x-java-bean;version=1.3.1, application/x-java-bean;version=1.4, application/x-java-bean;version=1.4.1, application/x-java-bean;version=1.4.2, application/x-java-bean;version=1.5, application/x-java-bean;version=1.6, application/x-java-bean;jpi-version=1.6.0_07
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a
Npp-Name: The Java(TM) Plug-in, Java SE 6


[08:32 ][al:AL-DESK:~]

```Regards,
Effenberg

---

### Post by dino99 on 2011-10-07
> **nicolasdiogo said:**
> hello,

i have some applications that require to be run as applet using the original sun-java

i am not sure why this package is no longer available - any idea which repository i would find this now?


thanks,

look at synaptic : canonical repo partner might be activated, then update
but icedtea6-plugin is replacing it

---

### Post by thatguruguy on 2011-10-07
You may want to read [this thread]("http://ubuntuforums.org/showthread.php?t=1855292").

---

### Post by ronacc on 2011-10-07
> **dino99 said:**
> look at synaptic : canonical repo partner might be activated, then update
but icedtea6-plugin is replacing it

it may replace it but some prgs/web sites don't work with iced tea but do with the actual sun-java .

---

### Post by nicolasdiogo on 2011-10-07
thanks for the link

this thread.

---

