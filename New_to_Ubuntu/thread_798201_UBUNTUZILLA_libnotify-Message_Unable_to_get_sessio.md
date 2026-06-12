---
title: "UBUNTUZILLA: libnotify-Message: Unable to get session bus: Did not receive a reply..."
date: 2008-05-18
forum: New to Ubuntu
---

### Post by LeDechaine on 2008-05-18
Looks like ubuntuzilla is broken in my ubuntu (7.10) installation.
In fact, it never worked.. yet.

```
May 18 00:00:02 A99-LeDechaine /USR/SBIN/CRON[23085]: (root) CMD (/usr/local/bin/ubuntuzilla.py -p thunderbird -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUNTUZILLA" -- )
May 18 00:00:02 A99-LeDechaine /USR/SBIN/CRON[23086]: (root) CMD (/usr/local/bin/ubuntuzilla.py -p firefox -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUNTUZILLA" -- )
May 18 00:00:17 A99-LeDechaine UBUNTUZILLA: libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
May 18 00:00:17 A99-LeDechaine UBUNTUZILLA: notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>2.0.0.13</b>. The new release available is <b>2.0.0.14</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatefirefox">detailed update instructions</a>.'
May 18 00:00:17 A99-LeDechaine UBUNTUZILLA: Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
May 18 00:00:17 A99-LeDechaine UBUNTUZILLA: Process returned code 1
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: Latest release version of Firefox : 2.0.0.14
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: Currently installed version of Firefox : 2.0.0.13
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: Traceback (most recent call last):
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 1060, in <module>
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:     bs.start()
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 209, in start
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:     fi.start()
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 246, in start
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:     self.checkforupdateGui()
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 550, in checkforupdateGui
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:     self.updateActionsGui()
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 575, in updateActionsGui
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:     self.util.execSystemCommand(executionstring="notify-send -i '" + iconPath + "' -t 14400000 'Ubuntuzilla: "+self.options.package.capitalize()+" Update Available.' 'A "+self.options.package.capitalize()+" Update is Available. The version you are running is <b>"+self.installedVersion+"</b>. The new release available is <b>"+self.releaseVersion+"</b>. Please refer to these <a href=\""+self.version.url+"#update" + self.options.package + "\">detailed update instructions</a>.'", errormessage="Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.")
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA:     raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: __main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: notify-send -i '/opt/thunderbird/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Thunderbird Update Available.' 'A Thunderbird Update is Available. The version you are running is <b>2.0.0.9</b>. The new release available is <b>2.0.0.14</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatethunderbird">detailed update instructions</a>.'
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
May 18 00:00:20 A99-LeDechaine UBUNTUZILLA: Process returned code 1
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA: Retrieving the version of the latest release of Thunderbird from the Mozilla website...
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA: Latest release version of Thunderbird : 2.0.0.14
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA: Currently installed version of Thunderbird : 2.0.0.9
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA: Traceback (most recent call last):
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 1060, in <module>
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:     bs.start()
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 212, in start
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:     ti.start()
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 246, in start
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:     self.checkforupdateGui()
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 550, in checkforupdateGui
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:     self.updateActionsGui()
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 575, in updateActionsGui
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:     self.util.execSystemCommand(executionstring="notify-send -i '" + iconPath + "' -t 14400000 'Ubuntuzilla: "+self.options.package.capitalize()+" Update Available.' 'A "+self.options.package.capitalize()+" Update is Available. The version you are running is <b>"+self.installedVersion+"</b>. The new release available is <b>"+self.releaseVersion+"</b>. Please refer to these <a href=\""+self.version.url+"#update" + self.options.package + "\">detailed update instructions</a>.'", errormessage="Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.")
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA:     raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
May 18 00:00:21 A99-LeDechaine UBUNTUZILLA: __main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
```

By the way, libnotify-bin **is** installed. So this is not the problem.
Any ideas?

---

### Post by nowshining on 2008-05-18
are you trying to install thunderbird + firefox?

---

### Post by LeDechaine on 2008-05-19
No. Firefox and ubuntuzilla are both in the default ubuntu 7.10 installation LiveCD.
(Well, I don't remember installing ubuntuzilla..)

---

### Post by LeDechaine on 2008-05-19
And weirdly, an update (via firefox) just worked...
It's not even supposed to happen since i'm not running it as root, no?!

---

### Post by nowshining on 2008-05-19
well, if it comes thru the update-manager - then yes it's okay. Firefox B3 is the default browser for HH.

---

### Post by LeDechaine on 2008-07-07
As I said, i'm using Ubuntu 7.10...

Argh, whatever...

---

### Post by nanotube on 2008-07-08
Hi!

this was a problem on gutsy with older versions of ubuntuzilla. if you get the latest, it should work fine. give it a try, and post back here if you run into any more problems.

---

### Post by LeDechaine on 2008-07-08
Actually, according to the deb package manager, i'm using the latest available version, 4.5.0. Never updated this program since i've installed Ubuntu 7.10, thought.

---

### Post by nanotube on 2008-07-08
> **LeDechaine said:**
> Actually, according to the deb package manager, i'm using the latest available version, 4.5.0. Never updated this program since i've installed Ubuntu 7.10, thought.

ubuntuzilla updates itself automatically. :)

so, does this error still happen with the latest ubuntuzilla?

---

### Post by LeDechaine on 2008-07-09
Oh! Nice! :)

..But the error still happens. :P

> Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: 
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: notify-send 'test' -t 1
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: Previous command has failed to complete successfully. Exiting.
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: Process returned code 1
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: notify-send -i '/opt/thunderbird/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Thunderbird Update Available.' 'A Thunderbird Update is Available. The version you are running is <b>2.0.0.9</b>. The new release available is <b>2.0.0.14</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatethunderbird">detailed update instructions</a>.'
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Jul  9 08:00:29 A99-LeDechaine UBUNTUZILLA: Process returned code 1
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA: Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA: Latest release version of Thunderbird : 2.0.0.14
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA: Currently installed version of Thunderbird : 2.0.0.9
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA: Traceback (most recent call last):
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 1090, in <module>
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:     bs.start()
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 212, in start
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:     ti.start()
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 246, in start
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:     self.checkforupdateGui()
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 568, in checkforupdateGui
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:     self.updateActionsGui()
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 597, in updateActionsGui
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:     self.util.execSystemCommand(executionstring="notify-send -i '" + iconPath + "' -t 14400000 'Ubuntuzilla: "+self.options.package.capitalize()+" Update Available.' 'A "+self.options.package.capitalize()+" Update is Available. The version you are running is <b>"+self.installedVersion+"</b>. The new release available is <b>"+self.releaseVersion+"</b>. Please refer to these <a href=\""+self.version.url+"#update" + self.options.package + "\">detailed update instructions</a>.'", errormessage="Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.")
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA:     raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
Jul  9 08:00:30 A99-LeDechaine UBUNTUZILLA: __main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: 
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: notify-send 'test' -t 1
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Previous command has failed to complete successfully. Exiting.
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Process returned code 1
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>2.0.0.15</b>. The new release available is <b>3.0</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatefirefox">detailed update instructions</a>.'
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Process returned code 1
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Latest release version of Firefox : 3.0
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Currently installed version of Firefox : 2.0.0.15
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: Traceback (most recent call last):
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 1090, in <module>
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:     bs.start()
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 209, in start
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:     fi.start()
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 246, in start
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:     self.checkforupdateGui()
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 568, in checkforupdateGui
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:     self.updateActionsGui()
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 597, in updateActionsGui
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:     self.util.execSystemCommand(executionstring="notify-send -i '" + iconPath + "' -t 14400000 'Ubuntuzilla: "+self.options.package.capitalize()+" Update Available.' 'A "+self.options.package.capitalize()+" Update is Available. The version you are running is <b>"+self.installedVersion+"</b>. The new release available is <b>"+self.releaseVersion+"</b>. Please refer to these <a href=\""+self.version.url+"#update" + self.options.package + "\">detailed update instructions</a>.'", errormessage="Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.")
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA:     raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
Jul  9 08:00:31 A99-LeDechaine UBUNTUZILLA: __main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by nanotube on 2008-07-09
well there are a couple of bug threads on launchpad about this issue:

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/139368](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/139368)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)

it appears that installing package "dbus-x11" solves it (might need a reboot?). try it and see if it helps:
```
sudo apt-get install dbus-x11
```

---

### Post by LeDechaine on 2008-07-13
Hmm, already installed here, most recent version.

---

### Post by nanotube on 2008-07-14
> **LeDechaine said:**
> Hmm, already installed here, most recent version.

and i presume the same thing goes for "libnotify-bin"?
how about sending a message manually? do you see a popup if you run command
```
notify-send "bla"
```
?

---

### Post by LeDechaine on 2008-07-15
(Nevermind, double-post, look down :p)

---

### Post by LeDechaine on 2008-07-15
Yeah, same thing for libnotify-bin
And for notify-send, it works, manually and not manually since I even use this little useful command for Gkrellm to notify me when my CPU or HDD temperatures are high. ;) (And it works #1)

The problem seems to be in ubuntuzilla itself =/

---

### Post by philinux on 2008-07-15
To be honest I did use ubuntuzilla in the past, but I fail to see the use now.

The updates come pretty quick to the repo's its' hardly worth the fuss.

---

### Post by nanotube on 2008-07-15
> **philinux said:**
> To be honest I did use ubuntuzilla in the past, but I fail to see the use now.

The updates come pretty quick to the repo's its' hardly worth the fuss.

indeed, if you are using the latest ubuntu, that's true. but all those older versions, which are still stuck on 1.5 or 2.0, that's where it's quite relevant.

---

### Post by nanotube on 2008-07-15
> **LeDechaine said:**
> Yeah, same thing for libnotify-bin
And for notify-send, it works, manually and not manually since I even use this little useful command for Gkrellm to notify me when my CPU or HDD temperatures are high. ;) (And it works #1)

The problem seems to be in ubuntuzilla itself =/

hm well, i'm rather at a loss then... i can't reproduce this bug myself, and nobody else seems to be having it, so it's probably something specific to your config.

---

### Post by philinux on 2008-07-16
> **nanotube said:**
> indeed, if you are using the latest ubuntu, that's true. but all those older versions, which are still stuck on 1.5 or 2.0, that's where it's quite relevant.


Agreed.

What about enabling the backports repo's?

---

### Post by nanotube on 2008-07-16
> **philinux said:**
> Agreed.

What about enabling the backports repo's?

there's no ff2 or ff3 backport for dapper, and no ff3 backport for feisty. don't know about gutsy though...

---

