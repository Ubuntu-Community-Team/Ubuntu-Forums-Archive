---
title: "Amarok14 on 10.04"
date: 2010-04-30
forum: Packaging and Compiling Programs
---

### Post by joshuarowley42 on 2010-04-30
I have just been having issues installing Amarok 1.4 on my recently upgraded Lucid. I was repeatedly getting the following error message:
amarok14: Depends: libmysqlclient15off (>= 5.0.27-1) but it is not installable
The following actions will resolve these dependencies:

To solve this you need to install the package manually, ([http://security.debian.org/debian-setch12_i386.deb](http://security.debian.org/debian-setch12_i386.deb)) I am not entirely sure why and found this information on a German Ubuntu forum and in such take no credit, just though I would post an english version. 

([http://forum.ubuntuusers.de/topic/lucyd-lynx-amarok-1-4-libmysqlclient15off/#post-2458395](http://forum.ubuntuusers.de/topic/lucyd-lynx-amarok-1-4-libmysqlclient15off/#post-2458395))

LX

---

### Post by koshari on 2010-05-03
aye, and for 64bit ubuntu you need this file...


> [http://security.debian.org/debian-security/pool/updates/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.32-7etch12_amd64.deb](http://security.debian.org/debian-security/pool/updates/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.32-7etch12_amd64.deb)

---

### Post by DougieFresh4U on 2010-05-03
> **koshari said:**
> aye, and for 64bit ubuntu you need this file...

Thank you very much

---

### Post by Freaky#Funga on 2010-05-14
Thanks for this.
Link to 32-bit version is dead, here is actual one:
[http://security.debian.org/debian-security/pool/updates/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.32-7etch12_i386.deb]("http://security.debian.org/debian-security/pool/updates/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.32-7etch12_i386.deb")

---

### Post by krupintupple on 2010-05-16
excellent stuff! i'd been looking for this for a while. it's really hard to believe that the same people who made amarok 1.4 also made amarok 2, sadly.

---

### Post by karhulitos on 2010-07-12
My god it was difficult to simply create a playlist to wife's iPod Nano and transfer the songs & the list. 2.3.1 Amarok, Rhythmbox, ATunes, gtkpod, you name it. All freezed or simply couldn't do it.

I knew I had done it a year ago. It was Amarok 1.4.

---

### Post by cong06 on 2010-08-23
for amd64: [https://launchpad.net/ubuntu/lucid/amd64/libmysqlclient15off](https://launchpad.net/ubuntu/lucid/amd64/libmysqlclient15off)

---

