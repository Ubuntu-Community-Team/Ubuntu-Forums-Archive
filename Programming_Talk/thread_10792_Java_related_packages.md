---
title: "Java related packages?"
date: 2005-01-11
forum: Programming Talk
---

### Post by theBlackDragon on 2005-01-11
How do you guys install java related tools on you Ubuntu system?

After having figured out that there is a repository that distributes debs for the j2sdk I am now wondering if there are any packages for important java development tools, like Ant or the eclipse IDE?

Thanks in advance

---

### Post by jerome bettis on 2005-01-18
hi

this is how i got java 1.5 installed on ubuntu:

wget [http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb](http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb)
sudo apt-get install java-package
sudo apt-get install sun-j2sdk1.5debian
sudo dpkg -i su*.deb

make sure you have multiverse in your sources list first.

as for eclipse, doing apt-get will get you version 2.0 which is pretty beat anymore.  just go download the 3.0 tarball from their site and you should be able to just extract it and run it.

so far my experience with eclipse 3.0 on ubuntu has been 100% error free.  using 2.0 with blackdown java for debian was awful and why i tried switching to ubuntu.

---

### Post by Hikaru79 on 2005-01-18
[QUOTE=jerome bettis]hi

this is how i got java 1.5 installed on ubuntu:

wget [http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb](http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb)
sudo apt-get install java-package
sudo apt-get install sun-j2sdk1.5debian
sudo dpkg -i su*.deb

make sure you have multiverse in your sources list first.

as for eclipse, doing apt-get will get you version 2.0 which is pretty beat anymore.  just go download the 3.0 tarball from their site and you should be able to just extract it and run it.

so far my experience with eclipse 3.0 on ubuntu has been 100% error free.  using 2.0 with blackdown java for debian was awful and why i tried switching to ubuntu.[/QUOTE]
 Both the SDK and Eclipse are extremely simple installs to do manually, compared to most linux apps. There's a very comprehensive HOW-TO on the forum, and the Eclipse IDE is simply extract-and-run. :)

---

