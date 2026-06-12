---
title: "File locaitons when compiling Samba from souce"
date: 2011-03-09
forum: Packaging and Compiling Programs
---

### Post by vaspenil on 2011-03-09
Hello all
 
When compiling and installing samba from souce, I realized that files ends up in different directories then when I install samba from deb packages.
 
My question is:
What configure parameters are used when the deb package are prepared?
Shall I use those, or is it better to keep to the default file locations that the samba installer provides?

---

### Post by gmargo on 2011-03-10
The configure parameters used should be contained in the source packages.

Run "apt-get source samba" to get the samba source files.  Check the **debian/rules** file for the configuration used.

Or see it online here: [http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/maverick/samba/maverick-updates/view/head:/debian/rules]("http://bazaar.launchpad.net/%7Eubuntu-branches/ubuntu/maverick/samba/maverick-updates/view/head:/debian/rules")

---

