---
title: "Public key problem"
date: 2010-11-04
forum: Philippine Team
---

### Post by tykmo on 2010-11-04
Mga ser at maám makikisuyo naman po.


may ganito po ako error: W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 80E7349A06ED541C.

Hindi ko po maintindihan kung paano ko po nakuha ang ganitong error.

salamat

---

### Post by yiannis66 on 2010-11-04
try something like:

gksudo -- wget -O - "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x ([http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035)80E7349A06ED541C](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035)80E7349A06ED541C) (http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035)" | apt-key add - then

gksudo -- wget -O - "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x ([http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035)9AA38DCD55BE302B](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035)9AA38DCD55BE302B) (http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035)" | apt-key add - and finally...

sudo apt-get update && sudo apt-get upgradeNot sure exactly if it will work, though. I've been having bad luck accessing the keyserver, lately. :?
696f6e6963

---

### Post by Script Warlock on 2010-11-04
baka may na install ka na galing sa ppa...

---

### Post by tykmo on 2010-11-05
medyo ok na nawala yung public key error. Uncheck ko lang yung mga disabled repositories sa synaptic manager. Kaso meron pang naiwang problema: 


------------------------------------------------------------
Setting up libutempter0 (1.1.5-3) ...
Creating utempter group...
groupadd: cannot lock /etc/gshadow; try again later.
addgroup: `/usr/sbin/groupadd -g 123 utempter' returned error code 10. Exiting.
dpkg: error processing libutempter0 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libkpty4:
 libkpty4 depends on libutempter0 (>= 1.1.5); however:
  Package libutempter0 is not configured yet.
dpkg: error processing libkpty4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdesu5:
 libkdesu5 depends on libkpty4 (= 4:4.5.1-0ubuntu7); however:
  Package libkpty4 is not configured yet.
dpkg: error processing libkdesu5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime:
 kdebase-runtime depends on libkdesu5 (>= 4:4.5); however:
  Package libkdesu5 is not configured yet.
 kdebase-runtime depends on libkpty4 (>= 4:4.5); however:
  PackaNo apport report written because the error message indicates its a followup error from a previous failure.
          No apport report written because the error message indicates its a followup error from a previous failure.
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                                                                                                No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                                                                                                 No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
               ge libkpty4 is not configured yet.
dpkg: error processing kdebase-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kdebase-runtime; however:
  Package kdebase-runtime is not configured yet.
dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on kdebase-runtime; however:
  Package kdebase-runtime is not configured yet.
 python-kde4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.
 python-kde4 depends on libkpty4 (>= 4:4.5); however:
  Package libkpty4 is not configured yet.
dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdesudo:
 kdesudo depends on kdebase-runtime; however:
  Package kdebase-runtime is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
                                                                                   No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
 dpkg: error processing kdesudo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi-kde:
 gdebi-kde depends on python-kde4 (>= 3.16.0-0ubuntu11); however:
  Package python-kde4 is not configured yet.
 gdebi-kde depends on kdesudo; however:
  Package kdesudo is not configured yet.
dpkg: error processing gdebi-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkde3support4:
 libkde3support4 depends on libkpty4 (= 4:4.5.1-0ubuntu7); however:
  Package libkpty4 is not configured yet.
dpkg: error processing libkde3support4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5:
 kdelibs5 depends on libkde3support4 (= 4:4.5.1-0ubuntu7); however:
  Package libkde3support4 is not configured yet.
 kdelibs5 depends on libkdesu5 (= 4:4.5.1-0ubuntu7); however:
  Package libkdesu5 is not configured yet.
 kdelibs5 depends on libkpty4 (= 4:4.5.1-0ubuntu7); however:
  Package libkpty4 is not configured yet.
dpkg: error processing kdelibs5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5-dev:
 kdelibs5-dev depends on libkde3support4 (= 4:4.5.1-0ubuntu7); however:
  Package libkde3support4 is not configured yet.
 kdelibs5-dev depends on libkpty4 (= 4:4.5.1-0ubuntu7); however:
  Package libkpty4 is not configured yet.
 kdelibs5-dev depends on libkdesu5 (= 4:4.5.1-0ubuntu7); however:
  Package libkdesu5 is not configured yet.
dpkg: error processing kdelibs5-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepimlibs5-dev:
 kdepimlibs5-dev depends on kdelibs5-dev (>= 4:4.5.1); however:
  Package kdelibs5-dev is not configured yet.
dpkg: error processing kdepimlibs5-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qapt-batch:
 qapt-batch depends on kdebase-runtime; however:
  Package kdebase-runtime is not configured yet.
dpkg: error processing qapt-batch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kdebase-runtime; however:
  Package kdebase-runtime is not configured yet.
 kubuntu-debug-installer depends on qapt-batch; however:
  Package qapt-batch is not configured yet.
dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 software-properties-kde depends on qapt-batch; however:
  Package qapt-batch is not configured yet.
dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xterm:
 xterm depends on libutempter0 (>= 1.1.5); however:
  Package libutempter0 is not configured yet.
dpkg: error processing xterm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on xterm; however:
  Package xterm is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-kde:
 update-manager-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 update-manager-kde depends on kdesudo; however:
  Package kdesudo is not configured yet.
dpkg: error processing update-manager-kde (--configure):
 dependency problems - leaving unconfigured
Setting up winbind (2:3.5.4~dfsg-1ubuntu8) ...
groupadd: cannot lock /etc/gshadow; try again later.
addgroup: `/usr/sbin/groupadd -g 123 winbindd_priv' returned error code 10. Exiting.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of polkit-kde-1:
 polkit-kde-1 depends on kdebase-runtime; however:
  Package kdebase-runtime is not configured yet.
dpkg: error processing polkit-kde-1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                     Errors were encountered while processing:
 libutempter0
 libkpty4
 libkdesu5
 kdebase-runtime
 kdepim-runtime
 python-kde4
 kdesudo
 gdebi-kde
 libkde3support4
 kdelibs5
 kdelibs5-dev
 kdepimlibs5-dev
 qapt-batch
 kubuntu-debug-installer
 software-properties-kde
 xterm
 ubuntu-desktop
 update-manager-kde
 winbind
 polkit-kde-1
E: Sub-process /usr/bin/dpkg returned an error code (1)


---------------------------------------------------------------

Makikisuyo naman po. Ang naalala ko lang po eh may naconfigure ako sa kopete noon pero tinanggal ko na. Ano po kaya ang diagnostic niyo po.

salamat

---

### Post by Script Warlock on 2010-11-05
baka may maitulong to try mo lang..

sudo dpkg --configure -a

---

