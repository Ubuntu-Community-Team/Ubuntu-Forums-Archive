---
title: "Real VNC will not install or launch"
date: 2018-03-15
forum: New to Ubuntu
---

### Post by skitter on 2018-03-15
I downloaded Real VNC from here:

[https://www.realvnc.com/en/connect/download/viewer/linux/](https://www.realvnc.com/en/connect/download/viewer/linux/)

I put it on my desk top and set it to be executable.  ls command looks like this:

~/Desktop$ ls -l VNC-Viewer-6.17.1113-Linux-x64.deb 
-rwxrwx--x 1 skitter skitter 3557258 Mar 15 21:22 VNC-Viewer-6.17.1113-Linux-x64.deb

When I attempt to run it from the command line, I'm receiving this message:

~/Desktop$ ./VNC.deb
./VNC.deb: line 1: syntax error near unexpected token `newline'
./VNC.deb: line 1: `!<arch>'


The reason I'm trying to run it from the command line is when I try to open it in the package manager, it just flashes for a moment, then does nothing.  When I check /var/log/syslog after trying the package manager, I see the data below.  Any assistance is appreciated. 


Mar 15 22:19:43 skitterBox gnome-session[2011]: (gnome-software:2310): GLib-GIO-CRITICAL **: g_file_get_path: assertion 'G_IS_FILE (file)' failed
Mar 15 22:19:43 skitterBox gnome-session[2011]: (gnome-software:2310): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed
Mar 15 22:19:43 skitterBox dbus[1195]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 22:19:43 skitterBox AptDaemon: INFO: Initializing daemon
Mar 15 22:19:43 skitterBox org.debian.apt[1195]: 22:19:43 AptDaemon [INFO]: Initializing daemon
Mar 15 22:19:43 skitterBox dbus[1195]: [system] Successfully activated service 'org.debian.apt'
Mar 15 22:19:43 skitterBox AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Mar 15 22:19:43 skitterBox org.debian.apt[1195]: /usr/lib/python3/dist-packages/aptdaemon/worker/pkworker.py:35: PyGIWarning: PackageKitGlib was imported without specifying a version first. Use gi.require_version('PackageKitGlib', '1.0') before import to ensure that the right version gets loaded.
Mar 15 22:19:43 skitterBox org.debian.apt[1195]:   from gi.repository import PackageKitGlib as pk
Mar 15 22:19:43 skitterBox org.debian.apt[1195]: 22:19:43 AptDaemon.PackageKit [INFO]: Initializing PackageKit compat layer
Mar 15 22:19:43 skitterBox AptDaemon: INFO: InstallFile() was called: [Invalid UTF-8]
Mar 15 22:19:43 skitterBox org.debian.apt[1195]: 22:19:43 AptDaemon [INFO]: InstallFile() was called: [Invalid UTF-8]
Mar 15 22:19:43 skitterBox gnome-session[2011]: (gnome-software:2310): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed
Mar 15 22:19:43 skitterBox AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/738e021160144243bff663cec0ec134f
Mar 15 22:19:43 skitterBox org.debian.apt[1195]: 22:19:43 AptDaemon.Trans [INFO]: Queuing transaction /org/debian/apt/transaction/738e021160144243bff663cec0ec134f
Mar 15 22:19:43 skitterBox AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/738e021160144243bff663cec0ec134f
Mar 15 22:19:43 skitterBox org.debian.apt[1195]: 22:19:43 AptDaemon.Worker [INFO]: Simulating trans: /org/debian/apt/transaction/738e021160144243bff663cec0ec134f
Mar 15 22:19:44 skitterBox AptDaemon.Worker: INFO: Installing local package file: [Invalid UTF-8]
Mar 15 22:19:44 skitterBox org.debian.apt[1195]: 22:19:44 AptDaemon.Worker [INFO]: Installing local package file: [Invalid UTF-8]
Mar 15 22:19:44 skitterBox gnome-session[2011]: (gnome-software:2310): Gs-WARNING **: failed to call gs_plugin_app_install on apt: GDBus.Error:org.debian.apt.TransactionFailed: error-unreadable-package-file: [Invalid UTF-8]
Mar 15 22:19:44 skitterBox gnome-session[2011]: (gnome-software:2310): Gs-WARNING **: not saving error for (null): GDBus.Error:org.debian.apt.TransactionFailed: error-unreadable-package-file: [Invalid UTF-8]

---

### Post by kerry_s on 2018-03-15
a deb you install. just click on it, it should open in software center, then just click install
also it says it only works on 16.04, are you using ubuntu 16.04?

---

### Post by skitter on 2018-03-15
Thanks, yes I'm sure I'm 16.04.  When I try launching the file and  running it in the software center it just flashes for a moment and  doesn't install- software center loads, I click install then nothing happens.  The errors in the first post are what shows up in  syslog when I try to use the software center. 

O/S Version:
~/Desktop$ lsb_release -a
LSB  Version:     core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

---

### Post by kerry_s on 2018-03-15
[https://askubuntu.com/questions/899072/vnc-viewer-not-installing-in-ubuntu](https://askubuntu.com/questions/899072/vnc-viewer-not-installing-in-ubuntu)

---

