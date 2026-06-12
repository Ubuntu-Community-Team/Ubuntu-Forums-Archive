---
title: "ubuntu will not install samba"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by th3fa7kid on 2012-04-03
i have an older, failing gateway laptop with ubuntu on it. i am trying to get all the info off of it (40-50GB) using a windows network/machine or via FTP. have tried many things including attempting to install samba but to no avail. i keep getting the following message:


installArchives() failed: (Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 263146 files and directories currently installed.)
Preparing to replace empathy-common 2.32.1-0ubuntu1.1 (using .../empathy-common_2.34.0-0ubuntu3.2_all.deb) ...
Unpacking replacement empathy-common ...
dpkg: ../../src/archives.c:968: tarobject: Assertion `r == stab.st_size' failed.
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on empathy-common (= 2.34.0-0ubuntu3.2); however:
  Package empathy-common is not installed.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-iconaigure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstreamanalyzer0:
 libstreamanalyzer0 depends on libexiv2-10; however:
  Package libexiv2-10 is not installed.
dpkg: error processing libstreamanalyzer0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-ubuntuone-music-store:
 rhythmbox-ubuntuone-music-store depends on rhythmbox-plugins (>= 0.13.3); however:
  Version of rhythmbox-plugins on system is 0.13.1-0ubuntu6.1.
dpkg: error processing rhythmbox-ubuntuone-music-store (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkio5:
 libkio5 depends on libstreamanalyzer0 (>= 0.7.2); however:
  Package libstreamanalyzer0 is not configured yet.
dpkg: error processing libkio5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotifyconfig4:
 libknotifyconfig4 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknotifyconfig4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-scriptengine-declarative:
 plasma-scriptengine-declarative depends on libkio5 (>= 4:4.5.2-0ubuntu1); however:
  Package libkio5 is not configured yet.
dpkg: error processing plasma-scriptengine-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff3-4:
 libknewstuff3-4 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknewstuff3-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkparts4:
 libkparts4 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkparts4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
 libplasma3 depends on libknewstuff3-4 (= 4:4.6.2-0ubuntu4); however:
  Package libknewstuff3-4 is not configured yet.
dpkg: error processing libplasma3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktexteditor4:
 libktexteditor4 depends on libkparts4 (= 4:4.6.2-0ubuntu4); however:
  Package libkparts4 is not configured yet.
dpkg: error processing libktexteditor4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkhtml5:
 libkhtml5 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
 libkhtml5 depends on libkparts4 (= 4:4.6.2-0ubuntu4); however:
  Package libkparts4 is not configured yet.
 libkhtml5 depends on libktexteditor4 (= 4:4.6.2-0ubuntu4); however:
  Package libktexteditor4 is not configured yet.
dpkg: error processing libkhtml5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-config-cron:
 kde-config-cron depends on libkio5 (>= 4:4.3.4); however:
  Package libkio5 is not configured yet.
dpkg: error processing kde-config-cron (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkatepartinterfaces4:
 libkatepartinterfaces4 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
 libkatepartinterfaces4 depends on libkparts4 (= 4:4.6.2-0ubuntu4); however:
  Package libkparts4 is not configured yet.
 libkatepartinterfaces4 depends on libktexteditor4 (= 4:4.6.2-0ubuntu4); however:
  Package libktexteditor4 is not configured yet.
dpkg: error processing libkatepartinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-scriptengine-javascript:
 plasma-scriptengine-javascript depends on libkio5 (>= 4:4.5.2-0ubuntu1); however:
  Package libkio5 is not configured yet.
 plasma-scriptengine-javascript depends on libplasma3 (>= 4:4.5.80); however:
  Package libplasma3 is not configured yet.
dpkg: error processing plasma-scriptengine-javascript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkemoticons4:
 libkemoticons4 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkemoticons4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkfile4:
 libkfile4 depends on libkio5 (= 4:4.6.2-0ubuntu4); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkfile4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on libkatepartinterfaces4 (= 4:4.6.2-0ubuntu4); however:




If you can help me, it would be greatly appreciated.

---

### Post by gordintoronto on 2012-04-04
It might be relevant to mention what version of Ubuntu is on the machine.

I *think* Linux Mint includes Samba in the LiveCD, so booting from that might help you.

Otherwise, perhaps you could remove the hard drive from the computer, and mount it in a USB enclosure.

---

