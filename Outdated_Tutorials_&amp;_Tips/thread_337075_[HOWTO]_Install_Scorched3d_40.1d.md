---
title: "[HOWTO] Install Scorched3d 40.1d"
date: 2007-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ilbozo on 2007-01-12
So, this is my first howto. I wanted to play online with scorched3d and the version in ubuntu repositories is too old to connect to more recent servers. Hope it helps and hope it's the right place in the forum! ;) 

**1St: Download the rpm package **[URL="http://prdownloads.sourceforge.net/scorched3d/Scorched3D-40.1d-i386.rpm?download"][COLOR="Lime"]here[/COLOR]
[/URL]
**2nd: Install the libgtk1.2 libs and alien (rpm to deb converter)**
```
sudo apt-get install libgtk1.2 alien
```

**3rd: Convert rpm to deb**
```
sudo alien Scorched3D-40.1d-i386.rpm
```

**4th: Remove the older version**
```
sudo apt-get remove scorched3d scorched3d-data scorched3d-doc
```

**5th: Install Scorched3d deb**
```
sudo dpkg -i scorched3d_40.1d-2_i386.deb
```

---

### Post by kandza on 2008-01-05
Where can i get libgtk1.2

---

