---
title: "Run arduino from GUI"
date: 2022-01-30
forum: New to Ubuntu
---

### Post by baskaran-86 on 2022-01-30
Hi guys, I am new to Ubuntu ,I installed Arduino in Ubuntu. to run the program every time I have to go to the installed folder and I have to run the script file manually in order to start the arduino. Is there a way to done it in GUI
         Thanks in advance

---

### Post by yetimon_64 on 2022-01-30
You don't mention how, or from where, you installed it or what release you are on. However [[COLOR=#0000ff]--this guide--[/COLOR]]("https://linuxconfig.org/how-to-install-arduino-ide-on-ubuntu-20-04-focal-fossa") (clickable link) shows how to install arduino on ubuntu 20.04 using a snap package. From my reading of the linked site it appears a GUI interface is supplied that can be started from a launcher in the activities menu.

I should mention I've never installed or used arduino so am not sure how the debian package in the repository works. I just googled "Arduino in Ubuntu" and found that link. **Edit**: I just installed arduino here on Xubuntu 20.04 from the repositories (.deb version not the snap I link to above) and an arduino launcher is supplied. If you are on Ubuntu (standard release) then open the activities menu and type in "arduino" in the search box and a launcher should show up there to launch the program in a GUI, good luck.

Regards, yeti.

---

### Post by him610 on 2022-02-01
I did not know what *arduino* was, other than a single board computer. I set out to find out what I could about it. It is in the repository. For any others who may be curious, here is what I found...
```

apt show arduino
Package: arduino
Version: 2:1.0.5+dfsg2-4.1
Priority: optional
Section: universe/electronics
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Scott Howard <showard@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,657 kB
Depends: default-jre | java6-runtime, libjna-java, librxtx-java (>= 2.2pre2-3), arduino-core (= 2:1.0.5+dfsg2-4.1)
Recommends: extra-xdg-menus, policykit-1
Homepage: http://www.arduino.cc
Download-Size: 1,165 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: AVR development board IDE and built-in libraries
 Arduino is an open-source electronics prototyping platform based on
 flexible, easy-to-use hardware and software. It's intended for artists,
 designers, hobbyists, and anyone interested in creating interactive
 objects or environments.
 .
 This package will install the integrated development environment that
 allows for program writing, code verfication, compiling, and uploading
 to the Arduino development board. Libraries and example code will also
 be installed.

```

---

