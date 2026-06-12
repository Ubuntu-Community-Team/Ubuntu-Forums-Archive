---
title: "Ubuntu 12.04 Debian packaging problem"
date: 2013-03-24
forum: Programming Talk
---

### Post by alenn on 2013-03-24
Hello
I have problems with packaging Qt5 application. When I package it using debuild on my local machine everything is fine but when I submitt it to Launchpad I get dependency problems. Here is complete log: [http://pastebin.com/JLVeWCH3](http://pastebin.com/JLVeWCH3)
Please help me.

---

### Post by schragge on 2013-03-24
The buldd in Launchpad tries to build it for *precise*. Qt5 packages only exist for *raring*, so naturally it fails.

---

### Post by alenn on 2013-03-24
> **schragge said:**
> The buldd in Launchpad tries to build it for *precise*. Qt5 packages only exist for *raring*, so naturally it fails.

Well, I'm using 12.04 and installed Qt5 using official PPA, if I could install it then why shouldn't Launchpad.

---

### Post by schragge on 2013-03-24
From the [official Launchpad documentation](https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage):
> If you want Launchpad to satisfy your package dependencies using one or more other PPAs, follow the Edit dependencies link on [your PPA]("https://launchpad.net/people/+me/+archive") or the team's overview page.

---

