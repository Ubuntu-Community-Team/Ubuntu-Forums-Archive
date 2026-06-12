---
title: "upgrade error"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by sujit_das on 2014-07-27
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/1,849 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package libqt5gui5:i386 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of libqt5widgets5:i386:
 libqt5widgets5:i386 depends on libqt5gui5 (>= 5.2.0) | libqt5gui5-gles (>= 5.2.0); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.


dpkg: error processing package libqt5widgets5:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5opengl5:i386:
 libqt5opengl5:i386 depends on libqt5gui5 (>= 5.2.0) | libqt5gui5-gles (>= 5.2.0); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5opengl5:i386 depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:i386 is not configured yet.


dpkg: error processing package libqt5opengl5:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5printsupport5:i386:
 libqt5printsupport5:i386 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gNo apport report written because the error message indicates its a followup error from a previous failure.
                   No apport report written because the error message indicates its a followup error from a previous failure.
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         les (>= 5.0.2); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5printsupport5:i386 depends on libqt5widgets5 (>= 5.2.0); however:
  Package libqt5widgets5:i386 is not configured yet.


dpkg: error processing package libqt5printsupport5:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5quick5:i386:
 libqt5quick5:i386 depends on libqt5gui5 (>= 5.2.0); however:
  Package libqt5gui5:i386 is not configured yet.


dpkg: error processing package libqt5quick5:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-privatewidgets-plugin:i386:
 qtdeclarative5-privatewidgets-plugin:i386 depends on libqt5gui5 (>= 5.2.0) | libqt5gui5-gles (>= 5.2.0); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 qtdeclarative5-privatewidgets-plugin:i386 depends on No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                  No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:i386 is not configured yet.
  Package libqt5quick5-gles is not installed.
 qtdeclarative5-privatewidgets-plugin:i386 depends on libqt5widgets5 (>= 5.2.0); however:
  Package libqt5widgets5:i386 is not configured yet.


dpkg: error processing package qtdeclarative5-privatewidgets-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-dialogs-plugin:i386:
 qtdeclarative5-dialogs-plugin:i386 depends on qtdeclarative5-privatewidgets-plugin; however:
  Package qtdeclarative5-privatewidgets-plugin:i386 is not configured yet.
 qtdeclarative5-dialogs-plugin:i386 depends on libqt5gui5 (>= 5.2.0) | libqt5gui5-gles (>= 5.2.0); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 qtdeclarative5-dialogs-plugin:i386 depends on libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:i386 is not configured yet.
  Package libqt5quick5-gles is not installed.


dpkg: error processing package qtdeclarative5-dialogs-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-qtquick2-plugin:i386:
 qtdeclarative5-qtquick2-plugin:i386 depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:i386 is not configured yet.
  Package libqt5quick5-gles is not installed.


dpkg: error processing package qtdeclarative5-qtquick2-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-window-plugin:i386:
 qtdeclarative5-window-plugin:i386 depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:i386 is not configured yet.
  Package libqt5quick5-gles is not installed.


dpkg: error processing package qtdeclarative5-window-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hud:
 hud depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 hud depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:i386 is not configured yet.


dpkg: error processing package hud (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liboxideqtcore0:i386:
 liboxideqtcore0:i386 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.


dpkg: error processing package liboxideqtcore0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liboxideqt-qmlplugin:i386:
 liboxideqt-qmlplugin:i386 depends on liboxideqtcore0 (= 1.0.4-0ubuntu0.14.04.1); however:
  Package liboxideqtcore0:i386 is not configured yet.
 liboxideqt-qmlplugin:i386 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 liboxideqt-qmlplugin:i386 depends on libqt5quick5 (>= 5.2.0~rc1) | libqt5quick5-gles (>= 5.2.0~rc1); however:
  Package libqt5quick5:i386 is not configured yet.
  Package libqt5quick5-gles is not installed.


dpkg: error processing package liboxideqt-qmlplugin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386:
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 depends on liboxideqt-qmlplugin; however:
  Package liboxideqt-qmlplugin:i386 is not configured yet.
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:i386 is not configured yet.
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 depends on qtdeclarative5-window-plugin; however:
  Package qtdeclarative5-window-plugin:i386 is not configured yet.


dpkg: error processing package qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of webbrowser-app:
 webbrowser-app depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 webbrowser-app depends on libqt5quick5 (>= 5.2.0~rc1) | libqt5quick5-gles (>= 5.2.0~rc1); however:
  Package libqt5quick5:i386 is not configured yet.
  Package libqt5quick5-gles is not installed.
 webbrowser-app depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:i386 is not configured yet.
 webbrowser-app depends on liboxideqt-qmlplugin (>= 1.0.0~bzr490); however:
  Package liboxideqt-qmlplugin:i386 is not configured yet.
 webbrowser-app depends on qtdeclarative5-dialogs-plugin; however:
  Package qtdeclarative5-dialogs-plugin:i386 is not configured yet.
 webbrowser-app depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:i386 is not configured yet.
 webbrowser-app depends on qtdeclarative5-ubuntu-ui-extras-br
dpkg: error processing package webbrowser-app (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of webapp-container:
 webapp-container depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:i386 is not configured yet.
  Package libqt5gui5-gles is not installed.
 webapp-container depends on libqt5quick5 (>= 5.2.0~rc1) | libqt5quick5-gles (>= 5.2.0~rc1); however:
  Package libqt5quick5:i386 is not configured yet.
  Package libqt5quick5-gles is not installed.
 webapp-container depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:i386 is not configured yet.
 webapp-container depends on webbrowser-app (= 0.23+14.04.20140428-0ubuntu1); however:
  Package webbrowser-app is not configured yet.


dpkg: error processing package webapp-container (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt5gui5:i386
 libqt5widgets5:i386
 libqt5opengl5:i386
 libqt5printsupport5:i386
 libqt5quick5:i386
 qtdeclarative5-privatewidgets-plugin:i386
 qtdeclarative5-dialogs-plugin:i386
 qtdeclarative5-qtquick2-plugin:i386
 qtdeclarative5-window-plugin:i386
 hud
 liboxideqtcore0:i386
 liboxideqt-qmlplugin:i386
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386
 webbrowser-app
 webapp-container
E: Sub-process /usr/bin/dpkg returned an error code (1)
suzz@suzz-System-Product-Name:~$
```

---

### Post by bapoumba on 2014-07-27
Well, some context would be nice. Which ubuntu flavor are you running ? What did you do/install prior to getting that upgrade error ?
Please also post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

