---
title: "I'm having trouble installing Unrevoked3 on Ubuntu 14.04"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by courtneyking1990 on 2014-05-14
I'm trying to use Unrevoked 3 to root my HTC EVO 4G phone.  I've never been able to start the rooting process since Unrevoked doesn't open. I've been googling around and these are the steps I've found that I've been using:

[COLOR=#000000][FONT=verdana]1. Download latest unrevoked for linux[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]2. extract to desktop[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]3. set phone settings to: USB Charge only [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana](menu>settings>connect to pc>default connection type>charge only) [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]4. enable phone settings to USB debugging (menu>settings>applications>development>USB debugging-check)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]5. connect phone to computer[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]6. open a terminal[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]7. type in terminal: cd /home/username/Desktop (hit enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana](Use your own "username" above. The prompt in terminal will begin with username@computername.)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]8. type in terminal: chmod +x reflash (hit enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]9.type in terminal: sudo ./reflash (hit enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana](it will ask for your administrative password, enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]10. Wait for the rooting process to finish.

After step 9, I always get this error and I don't get the prompt to put in my password:
[/FONT][/COLOR]./reflash: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I tried to install whatever the lib in the error is but I get told it doesn't exist or whatever. I'm at a lost for what to do. I expected this to be a simple process and the frustrates the hell out of me.

---

### Post by lisati on 2014-05-14
*Thread moved to **Absolute Beginners Section**.*

---

### Post by courtneyking1990 on 2014-05-16
I'm just bumping this thread for answers.

---

### Post by courtneyking1990 on 2014-05-18
Just another bump. Please help me *crying face*

---

### Post by coldcritter64 on 2014-05-18
On older versions that library seemed to be related to ia32-libs-gtk. One google result mentions installing it to fix the problem in 12.10. However with multiarch in newer releases I'm not sure it even exists and can't accurately check (I'm on Debian at the moment, it is installed here actually but may not necessarily even be available for you on Ubuntu ... I really don't know the extent of recent Ubuntu changes w.r.t. multiarch packages/ia32 libraries).

1st check to see if the package is available, open a terminal (ctrl + alt + t), and copy/paste the command

```
apt-cache policy ia32-libs-gtk
```IF it is available, try installing it and rerun the process you were attempting. To install (if available)
```
sudo apt-get install ia32-libs-gtk
``` Obviously this code will only work IF there is an installation candidate for the package.

Hopefully, someone with a better knowledge of Ubuntu and multiarch/ia32 packages etc will chime in and point the way for you, if this doesn't work out. Regards, coldcritter64.

---

### Post by courtneyking1990 on 2014-05-19
Thanks coldcritter64, it didn't do anything I'm afraid. Oh well, doesn't look like it's gonna happen?

---

