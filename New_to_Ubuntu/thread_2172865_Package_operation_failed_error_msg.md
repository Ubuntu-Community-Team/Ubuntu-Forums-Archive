---
title: "Package operation failed error msg"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by atulrajan9 on 2013-09-06
```
installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package nautilus-open-terminal.
(Reading database ... 
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
(Reading database ... 193067 files and directories currently installed.)
Unpacking nautilus-open-terminal (from .../nautilus-open-terminal_0.20-1_amd64.deb) ...
Processing triggers for gconf2 ...


(gconftool-2:10599): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
Setting up crossplatformui (2.1.2) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart


Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop acpid ; start acpid. The restart(8) utility is also available.
acpid stop/waiting
acpid start/running, process 10619
package libqtgui4 exist
QT_VERSION = 4
make -C /lib/modules/3.8.0-30-generic/build M=/usr/local/bin/ztemtApp/zteusbserial/below2.6.27 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-30-generic'
  CC [M]  /usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.o
/usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.c:34:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.o] Error 1
make[1]: *** [_module_/usr/local/bin/ztemtApp/zteusbserial/below2.6.27] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-30-generic'
make: *** [modules] Error 2
dpkg: error processing crossplatformui (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up nautilus-open-terminal (0.20-1) ...
Errors were encountered while processing:
 crossplatformui
Setting up crossplatformui (2.1.2) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart


Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop acpid ; start acpid. The restart(8) utility is also available.
acpid stop/waiting
acpid start/running, process 10877
package libqtgui4 exist
QT_VERSION = 4
make -C /lib/modules/3.8.0-30-generic/build M=/usr/local/bin/ztemtApp/zteusbserial/below2.6.27 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-30-generic'
  CC [M]  /usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.o
/usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.c:34:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.o] Error 1
make[1]: *** [_module_/usr/local/bin/ztemtApp/zteusbserial/below2.6.27] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-30-generic'
make: *** [modules] Error 2
dpkg: error processing crossplatformui (--configure):
 subprocess installed post-installation script returned error exit status 2 
```






im getting this while installing any package.. the package installs but error msg pops up
how do i fix this?

---

### Post by mörgæs on 2013-09-08
Moved as this is not specific for Dell.

---

