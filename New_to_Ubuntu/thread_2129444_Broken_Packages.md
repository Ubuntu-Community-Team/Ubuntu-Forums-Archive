---
title: "Broken Packages"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by jebaearnest on 2013-03-26
Whenever i try to install new packages, I am getting below issue


You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python-aptdaemon.gtk3widgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu5) but 0.43+bzr805-0ubuntu8 is installed
E: Unmet dependencies. Try using -f.



when i execute **sudo apt-get -f install**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-aptdaemon.gtk3widgets
The following packages will be upgraded:
  python-aptdaemon.gtk3widgets
1 upgraded, 0 newly installed, 0 to remove and 463 not upgraded.
22 not fully installed or removed.
Need to get 0 B/14.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up shared-mime-info (1.0-0ubuntu4.1) ...
update-mime-database.real: /usr/local/lib/libxml2.so.2: no version information available (required by update-mime-database.real)
update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg: error processing shared-mime-info (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgtk-3-0:
 libgtk-3-0 depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing libgtk-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblaunchpad-integration-3.0-1:
 liblaunchpad-integration-3.0-1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing liblaunchpad-integration-3.0-1 (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.5-0ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                             gconftool-2: /usr/local/lib/libxml2.so.2: no version information available (required by gconftool-2)
gconftool-2: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol: g_signal_accumulator_first_wins
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 gnome-media depends on liblaunchpad-integration-3.0-1 (>= 0.1.17); however:
  Package liblaunchpad-integration-3.0-1 is not configured yet.
 gnome-media depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of bamfdaemon:
 bamfdaemon depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing bamfdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libbamf0:
 libbamf0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libbamf3-0:
 libbamf3-0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-3-0:
 libgail-3-0 depends on libgtk-3-0 (= 3.4.2-0ubuntu0.4); however:
No apport report written because MaxReports is reached already
                                                                Package libgtk-3-0 is not configured yet.
dpkg: error processing libgail-3-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtksourceview-3.0-0:
 libgtksourceview-3.0-0 depends on libgtk-3-0 (>= 3.4.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtksourceview-3.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 depends on libgtk-3-0 (>= 3.3.18); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gir1.2-gtk-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libgail-3-0 (>= 3.0.0); however:
  Package libgail-3-0 is not configured yet.
 libwebkitgtk-3.0-0 depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gir1.2-webkit-3.0:
 gir1.2-webkit-3.0 depends on gir1.2-gtk-3.0 (>= 3.0.0); however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-webkit-3.0 depends on libwebkitgtk-3.0-0 (>= 1.8.0); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
dpkg: error processing gir1.2-webkit-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-ubuntu-sso-client:
 python-ubuntu-sso-client depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 python-ubuntu-sso-client depends on gir1.2-webkit-3.0; however:
  Package gir1.2-webkit-3.0 is not configured yet.
dpkg: error processing python-ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-sso-client:
 ubuntu-sso-client depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-sso-client-gtk:
 ubuntu-sso-client-gtk depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 ubuntu-sso-client-gtk depends on gir1.2-webkit-3.0; however:
  Package gir1.2-webkit-3.0 is not configured yet.
 ubuntu-sso-client-gtk depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
 ubuntu-sso-client-gtk depends on ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up desktop-file-utils (0.20-0ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_malloc_n
dpkg: error processing desktop-file-utils (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu5); however:
  Version of python-aptdaemon on system is 0.43+bzr805-0ubuntu8.
 python-aptdaemon.gtk3widgets depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-aptdaemon.gtk3widgets (>= 0.40) | synaptic; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
  Package synaptic is not installed.
 update-manager depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 shared-mime-info
 libgtk-3-0
 liblaunchpad-integration-3.0-1
 gconf2
 gnome-media
 bamfdaemon
 libbamf0
 libbamf3-0
 libgail-3-0
 libgtksourceview-3.0-0
 gir1.2-gtk-3.0
 libwebkitgtk-3.0-0
 gir1.2-webkit-3.0
 python-ubuntu-sso-client
 ubuntu-sso-client
 ubuntu-sso-client-gtk
 desktop-file-utils
 libgtk-3-bin
 libreoffice-gnome
 python-aptdaemon.gtk3widgets
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How to fix this issue?

---

### Post by ibjsb4 on 2013-03-26
Have you recently installed GtkUIManager?

---

### Post by schragge on 2013-03-26
> **jebaearnest said:**
> 
Setting up shared-mime-info (1.0-0ubuntu4.1) ...
update-mime-database.real: /usr/[COLOR=#ff0000]local[/COLOR]/lib/libxml2.so.2: no version information available (required by update-mime-database.real)
update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg: error processing shared-mime-info (--configure):
 
A manually installed *libxml2.so.2* in */usr/local/lib/* takes precedence over the standard version installed by the package *libxml2* under */usr/lib/*. The most straigtforward approach would be deleting or renaming */usr/local/lib/libxml2.so.2*.
Alternatively, replace it with the same version as in [precise repository]("http://packages.ubuntu.com/precise-updates/libxml2").

---

### Post by jebaearnest on 2013-03-26
I have moved libxml2.so.2

then executed

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python-aptdaemon.gtk3widgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu5) but 0.43+bzr805-0ubuntu8 is installed
E: Unmet dependencies. Try using -f.
cluster@master:/tmp$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-aptdaemon.gtk3widgets
The following packages will be upgraded:
  python-aptdaemon.gtk3widgets
1 upgraded, 0 newly installed, 0 to remove and 461 not upgraded.
22 not fully installed or removed.
Need to get 0 B/14.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up shared-mime-info (1.0-0ubuntu4.1) ...
update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg: error processing shared-mime-info (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgtk-3-0:
 libgtk-3-0 depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing libgtk-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblaunchpad-integration-3.0-1:
 liblaunchpad-integration-3.0-1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing liblaunchpad-integration-3.0-1 (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.5-0ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                             gconftool-2: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol: g_signal_accumulator_first_wins
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 gnome-media depends on liblaunchpad-integration-3.0-1 (>= 0.1.17); however:
  Package liblaunchpad-integration-3.0-1 is not configured yet.
 gnome-media depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bamfdaemon:
 bamfdaemon depends on libgtk-3-0 (>= 3.0.0); however:No apport report written because MaxReports is reached already

  Package libgtk-3-0 is not configured yet.
dpkg: error processing bamfdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libbamf0:
 libbamf0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libbamf3-0:
 libbamf3-0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-3-0:
 libgail-3-0 depends on libgtk-3-0 (= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.No apport report written because MaxReports is reached already

dpkg: error processing libgail-3-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtksourceview-3.0-0:
 libgtksourceview-3.0-0 depends on libgtk-3-0 (>= 3.4.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtksourceview-3.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 depends on libgtk-3-0 (>= 3.3.18); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gir1.2-gtk-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libgail-3-0 (>= 3.0.0); however:
  Package libgail-3-0 is not configured yet.
 libwebkitgtk-3.0-0 depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gir1.2-webkit-3.0:
 gir1.2-webkit-3.0 depends on gir1.2-gtk-3.0 (>= 3.0.0); however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-webkit-3.0 depends on libwebkitgtk-3.0-0 (>= 1.8.0); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
dpkg: error processing gir1.2-webkit-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-ubuntu-sso-client:
 python-ubuntu-sso-client depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 python-ubuntu-sso-client depends on gir1.2-webkit-3.0; however:
  Package gir1.2-webkit-3.0 is not configured yet.
dpkg: error processing python-ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-sso-client:
 ubuntu-sso-client depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-sso-client-gtk:
 ubuntu-sso-client-gtk depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 ubuntu-sso-client-gtk depends on gir1.2-webkit-3.0; however:
  Package gir1.2-webkit-3.0 is not configured yet.
 ubuntu-sso-client-gtk depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
 ubuntu-sso-client-gtk depends on ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up desktop-file-utils (0.20-0ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_malloc_n
dpkg: error processing desktop-file-utils (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu5); however:
  Version of python-aptdaemon on system is 0.43+bzr805-0ubuntu8.
 python-aptdaemon.gtk3widgets depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-aptdaemon.gtk3widgets (>= 0.40) | synaptic; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
  Package synaptic is not installed.
 update-manager depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 shared-mime-info
 libgtk-3-0
 liblaunchpad-integration-3.0-1
 gconf2
 gnome-media
 bamfdaemon
 libbamf0
 libbamf3-0
 libgail-3-0
 libgtksourceview-3.0-0
 gir1.2-gtk-3.0
 libwebkitgtk-3.0-0
 gir1.2-webkit-3.0
 python-ubuntu-sso-client
 ubuntu-sso-client
 ubuntu-sso-client-gtk
 desktop-file-utils
 libgtk-3-bin
 libreoffice-gnome
 python-aptdaemon.gtk3widgets
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cortman on 2013-03-26
What if you'd run

```
sudo dpkg --configure -a
```

first?

Also, when you post output or code, please use [CODE] tags. It's the hash mark button in the editing toolbar.

---

### Post by schragge on 2013-03-26
Sorry, forgot to mention you also need to rebuild the linker cache:
```
sudo ldconfig
```

---

### Post by ibjsb4 on 2013-03-26
A tip; use code tags.

```
**sudo apt-get autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
[B]The following packages have unmet dependencies:
 python-aptdaemon.gtk3widgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu5) but 0.43+bzr805-0ubuntu8 is installed
E: Unmet dependencies. Try using -f.[/B]
cluster@master:/tmp$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-aptdaemon.gtk3widgets
The following packages will be upgraded:
  python-aptdaemon.gtk3widgets
1 upgraded, 0 newly installed, 0 to remove and 461 not upgraded.
22 not fully installed or removed.
Need to get 0 B/14.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up shared-mime-info (1.0-0ubuntu4.1) ...
update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg: error processing shared-mime-info (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgtk-3-0:
 libgtk-3-0 depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing libgtk-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblaunchpad-integration-3.0-1:
 liblaunchpad-integration-3.0-1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing liblaunchpad-integration-3.0-1 (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.5-0ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                           No apport report written because the  error message indicates its a followup error from a previous failure.
                                             gconftool-2: symbol lookup  error: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol:  g_signal_accumulator_first_wins
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 gnome-media depends on liblaunchpad-integration-3.0-1 (>= 0.1.17); however:
  Package liblaunchpad-integration-3.0-1 is not configured yet.
 gnome-media depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bamfdaemon:
 bamfdaemon depends on libgtk-3-0 (>= 3.0.0); however:No apport report written because MaxReports is reached already

  Package libgtk-3-0 is not configured yet.
dpkg: error processing bamfdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libbamf0:
 libbamf0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libbamf3-0:
 libbamf3-0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-3-0:
 libgail-3-0 depends on libgtk-3-0 (= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.No apport report written because MaxReports is reached already

dpkg: error processing libgail-3-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of libgtksourceview-3.0-0:
 libgtksourceview-3.0-0 depends on libgtk-3-0 (>= 3.4.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtksourceview-3.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 depends on libgtk-3-0 (>= 3.3.18); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gir1.2-gtk-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libgail-3-0 (>= 3.0.0); however:
  Package libgail-3-0 is not configured yet.
 libwebkitgtk-3.0-0 depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of gir1.2-webkit-3.0:
 gir1.2-webkit-3.0 depends on gir1.2-gtk-3.0 (>= 3.0.0); however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-webkit-3.0 depends on libwebkitgtk-3.0-0 (>= 1.8.0); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
dpkg: error processing gir1.2-webkit-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of python-ubuntu-sso-client:
 python-ubuntu-sso-client depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 python-ubuntu-sso-client depends on gir1.2-webkit-3.0; however:
  Package gir1.2-webkit-3.0 is not configured yet.
dpkg: error processing python-ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of ubuntu-sso-client:
 ubuntu-sso-client depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of ubuntu-sso-client-gtk:
 ubuntu-sso-client-gtk depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 ubuntu-sso-client-gtk depends on gir1.2-webkit-3.0; however:
  Package gir1.2-webkit-3.0 is not configured yet.
 ubuntu-sso-client-gtk depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
 ubuntu-sso-client-gtk depends on ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up desktop-file-utils (0.20-0ubuntu3) ...
No apport report written because MaxReports is reached already
                                                               update-desktop-database: symbol lookup error: update-desktop-database:  undefined symbol: g_malloc_n
dpkg: error processing desktop-file-utils (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                             dpkg: error  processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of  python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu5); however:
  Version of python-aptdaemon on system is 0.43+bzr805-0ubuntu8.
 python-aptdaemon.gtk3widgets depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-aptdaemon.gtk3widgets (>= 0.40) | synaptic; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
  Package synaptic is not installed.
 update-manager depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg:  dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 shared-mime-info
 libgtk-3-0
 liblaunchpad-integration-3.0-1
 gconf2
 gnome-media
 bamfdaemon
 libbamf0
 libbamf3-0
 libgail-3-0
 libgtksourceview-3.0-0
 gir1.2-gtk-3.0
 libwebkitgtk-3.0-0
 gir1.2-webkit-3.0
 python-ubuntu-sso-client
 ubuntu-sso-client
 ubuntu-sso-client-gtk
 desktop-file-utils
 libgtk-3-bin
 libreoffice-gnome
 python-aptdaemon.gtk3widgets
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

[ATTACH=CONFIG]240579[/ATTACH]

---

### Post by jebaearnest on 2013-03-26
```
sudo dpkg --configure -a
Setting up shared-mime-info (1.0-0ubuntu4.1) ...
update-mime-database.real: /usr/local/lib/libxml2.so.2: no version information available (required by update-mime-database.real)
update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg: error processing shared-mime-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up desktop-file-utils (0.20-0ubuntu3) ...
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_malloc_n
dpkg: error processing desktop-file-utils (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu5); however:
  Version of python-aptdaemon on system is 0.43+bzr805-0ubuntu8.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-0:
 libgtk-3-0 depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing libgtk-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bamfdaemon:
 bamfdaemon depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing bamfdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbamf0:
 libbamf0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbamf3-0:
 libbamf3-0 depends on bamfdaemon (= 0.2.118-0ubuntu0.2); however:
  Package bamfdaemon is not configured yet.
dpkg: error processing libbamf3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.5-0ubuntu2) ...
gconftool-2: /usr/local/lib/libxml2.so.2: no version information available (required by gconftool-2)
gconftool-2: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol: g_signal_accumulator_first_wins
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of liblaunchpad-integration-3.0-1:
 liblaunchpad-integration-3.0-1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing liblaunchpad-integration-3.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 depends on libgtk-3-0 (>= 3.3.18); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gir1.2-gtk-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-aptdaemon.gtk3widgets (>= 0.40) | synaptic; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
  Package synaptic is not installed.
 update-manager depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ubuntu-sso-client:
 python-ubuntu-sso-client depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
dpkg: error processing python-ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sso-client-gtk:
 ubuntu-sso-client-gtk depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 ubuntu-sso-client-gtk depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtksourceview-3.0-0:
 libgtksourceview-3.0-0 depends on libgtk-3-0 (>= 3.4.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtksourceview-3.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-3-0:
 libgail-3-0 depends on libgtk-3-0 (= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgail-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libgail-3-0 (>= 3.0.0); however:
  Package libgail-3-0 is not configured yet.
 libwebkitgtk-3.0-0 depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-webkit-3.0:
 gir1.2-webkit-3.0 depends on gir1.2-gtk-3.0 (>= 3.0.0); however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-webkit-3.0 depends on libwebkitgtk-3.0-0 (>= 1.8.0); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
dpkg: error processing gir1.2-webkit-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sso-client:
 ubuntu-sso-client depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu2); however:
  Package python-ubuntu-sso-client is not configured yet.
dpkg: error processing ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 shared-mime-info
 desktop-file-utils
 python-aptdaemon.gtk3widgets
 libgtk-3-0
 bamfdaemon
 gnome-media
 libbamf0
 libbamf3-0
 update-notifier
 libgtk-3-bin
 gconf2
 liblaunchpad-integration-3.0-1
 gir1.2-gtk-3.0
 update-manager
 python-ubuntu-sso-client
 ubuntu-sso-client-gtk
 libgtksourceview-3.0-0
 libgail-3-0
 libwebkitgtk-3.0-0
 gir1.2-webkit-3.0
 libreoffice-gnome
 ubuntu-sso-client
```

---

