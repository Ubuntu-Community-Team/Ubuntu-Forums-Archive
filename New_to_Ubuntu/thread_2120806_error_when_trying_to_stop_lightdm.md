---
title: "error when trying to stop lightdm"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-27
Hi all, 

I'm getting error after stopping lightdm: 

BUG: soft lockup - CPU#0 stuck for 22s! [QInotifyFileSys:2249]


I tried both ways: 

# sudo service lightdm stop

or 

# sudo /etc/init.d/lightdm stop

with the same result, unfortunately (don't know maybe there are other ways to stop lightdm). 

Anyway, I must reset my PC to go on working. 

Ubuntu version:

user@ubuntu:~$ cat /etc/issue
Ubuntu 12.10 \n \l


My kernel version: 

user@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


My lightdm version: 

user@ubuntu:~$ dpkg -s lightdm
Package: lightdm
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 452
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Architecture: amd64
Version: 1.4.0-0ubuntu2
Provides: x-display-manager
Depends: debconf (>= 0.5) | debconf-2.0, upstart-job, libc6 (>= 2.14), libglib2.0-0 (>= 2.28.0), libpam0g (>= 0.99.7.1), libxcb1, libxdmcp6, libpam-runtime (>= 0.76-14), libpam-modules, adduser, libglib2.0-bin, dbus
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: xserver-xorg, unity-greeter | lightdm-greeter | lightdm-kde-greeter
Conflicts: liblightdm-gobject-0-0, liblightdm-qt-0-0
Conffiles:
 /etc/apparmor.d/lightdm-guest-session a45e8f463e94787d78fb71606aa9ac28
 /etc/apparmor.d/abstractions/lightdm_chromium-browser 96d3d1257e57ceac6853644eb6ffea91
 /etc/apparmor.d/abstractions/lightdm a5ea7fd18262f09bac1c34f3fe65efbd
 /etc/init/lightdm.conf 85cf974c71fe8ec739f6f8eed6cd0f0e
 /etc/dbus-1/system.d/org.freedesktop.DisplayManager.conf b76b6b45d7f7ff533c51d7fc02be32f4
 /etc/lightdm/users.conf 9365d0d580a33cc9be3b5ad77ce5dcc8
 /etc/pam.d/lightdm-autologin 3d4f9d79e7302b4eff2b7a00e5e4693c
 /etc/pam.d/lightdm-greeter d5f358f26b463252c3365c18b7f38a7f
 /etc/pam.d/lightdm 02d4bd40eb6d8c03d4063da806aaf42c
Description: Display Manager
 LightDM is a X display manager that:
  * Has a lightweight codebase
  * Is standards compliant (PAM, ConsoleKit, etc)
  * Has a well defined interface between the server and user interface
  * Cross-desktop (greeters can be written in any toolkit)
Homepage: [https://launchpad.net/lightdm](https://launchpad.net/lightdm)


Help me solve this problem, please.

---

### Post by deadflowr on 2013-02-27
As per the tag you put on this states, my question would be, are you running Kubuntu?

If you're running Kubuntu, the default dm is kdm.

Unless you reconfigure the display manager, with Kubuntu, kdm would stay as the default.

```
sudo dpkg-reconfigure lightdm
```

Run this to choose which ever display manager you'd like to use as the default.
It'll load after a reboot.

---

### Post by lordievader on 2013-02-27
Since 12.10 Kubuntu uses LightDM, if you upgraded from 12.04 kdm might even be broken.

Is there something hogging the CPU before you issue the command?
Perhaps the syslog or the dmesg log can give you a hint why the CPU is locking up, both are located in /var/log.

-lordievader.

---

### Post by marchelloUA on 2013-02-27
**[[COLOR=#000000]deadflowr[/COLOR]]("http://ubuntuforums.org/member.php?u=1276577"),**

I tried 

# sudo dpkg-reconfigure lightdm

but it didn't change anything (sure I performed reboot). 


**[[COLOR=#000000]lordievader[/COLOR]]("http://ubuntuforums.org/member.php?u=404154"), **

Well, last record before crash was the warning from ddclient. Don't know  if this cause problem, but removed ddclient just for testing. It didn't help... 


Upd: This is really strange, but this helps the best for now: 
#sudo killall lightdm 
I'm sured it's not correct way, but it does work. Will use it untill anyone shed some light... 

UUpd: 
#sudo killall lightdm 
works fine only from Yakuake and causes crash in tty1. Don't know why.

---

