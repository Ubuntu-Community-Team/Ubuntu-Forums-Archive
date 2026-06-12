---
title: "Cinnamon installed in Gnome Ubuntu?"
date: 2018-08-22
forum: New to Ubuntu
---

### Post by ubantunovice2 on 2018-08-22
I'm exploring my new Ubuntu installation to learn.

What I have is the standard Ubuntu 18.04.1 with Gnome 3. So, when I explored the installed software I notice a lot of Cinnamon related software (see screenshot). Are these redundent since I'm using Gnome not Cinnamon?

Are there Gnome equivalents?

---

### Post by Frogs Hair on 2018-08-22
There are some alternatives including Gnote and Tomboy notes for the desktop. Gnome offers a number of extension to add features to the gnome-shell. Some extensions are available in the repository. To install from the terminal use the following. Open gnome-tweaks an look under extensions.

```
sudo apt install gnome-tweaks 
``` ```
sudo apt install gnome-shell-extensions
```




   [https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by ajgreeny on 2018-08-22
Did you clean install the 18.04 version or was it an upgrade from either 16.04 or 17.10 in which you knowingly had cinnamon installed?

I am not aware of any need for any of those packages in a normal installation of Ubuntu with the default gnome desktop but I don't use gnome and therefore could be wrong so wait for other answers before removing them, or if you do remove them, make sure you are aware of any other packages that are removed with them so you can restore everything if needed.

---

### Post by deadflowr on 2018-08-22
Seems like some inadvertent package installs.
What did you install post-install?

---

### Post by ubantunovice2 on 2018-08-22
Thank you all. This is a fresh install. Not an upgrade. That's why I was surprised. Does Ubuntu keep a log of what is installed and when? That would give me a clue if it was inadvertently installed by me without my knowing what I was doing.

Is there a way to do what windows calls an 'image backup'? That way I could remove these packages and have the option of restoring the system if I break something.

---

### Post by deadflowr on 2018-08-22
>  Does Ubuntu keep a log of what is installed and when?
Yep
look at the history.log file in /var/log/apt.

---

### Post by ajgreeny on 2018-08-22
You can also run command ```
grep " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all packages installed in date order and see what was installed when those cinnamon packages were added.

---

### Post by ubantunovice2 on 2018-08-23
Thank you both. It's tough not knowing which way is up or down....
I am attaching the history file. You can probably figure it out better than me.

---

### Post by deadflowr on 2018-08-23
Don't you have an updated history.log?
You posted an older archived log.
logs get rotated after X amount of time. ( i think this log is set to rotate once a month)
(the log posted is from last month)

So when time comes the old log get archived as a .gz archive file, as denoted,
and a new log file is created.
The new log file should just be name history.log, without anything else (no .1.log, nor any .gz extensions)

Anyway, nothing in the posted log shows cinnamon.
So we know nothing cinnamon related was installed last month.
But we also don't know if anything cinnamon related was installed this month

You might be able to tweak ajgreeny's command a little and specify cinnamon it should show what cinnamon packages have been installed recently:
like
```
grep " cinnamon " /var/log/dpkg.log.1 /var/log/dpkg.log
```
I would think that would be small enough an output to just copy and paste without the need to post an attachment.

---

### Post by ubantunovice2 on 2018-08-24
Thank you again for helping.

```
jeff@jeff-VirtualBox:~$ grep " cinnamon " /var/log/dpkg.log.1 /var/log/dpkg.log
```
       I got no result

```
jeff@jeff-VirtualBox:~$ grep " install cinnamon " /var/log/dpkg.log.1 /var/log/dpkg.log 
```
      I tried this, but again no result

```
jeff@jeff-VirtualBox:~$ grep " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```
      This one worked and I selected the parts that contained cinnamon plus a little extra to see if something else installed it because it needed it.

Because Ubuntu is installed in a vm if I don't need cinnamon I would like to get rid of it since I'm not using it now. I'm learning one thing at a time plus the command line as I go along. But I'm really a newbie at any linux.
<earliest entries. When Ubuntu was first installed. 2018-07-25>

```
/var/log/dpkg.log.1:2018-07-25 03:03:55 install base-passwd:amd64 <none> 3.5.44
/var/log/dpkg.log.1:2018-07-25 03:03:56 install base-files:amd64 <none> 10.1ubuntu2
/var/log/dpkg.log.1:2018-07-25 03:03:56 install libc6:amd64 <none> 2.27-3ubuntu1

<snip>
```

<beginning of cinnamon appearances. 2018-08-04
not sure what else may have installed cinnamon>

```
/var/log/dpkg.log:2018-08-04 15:54:48 install python:amd64 <none> 2.7.15~rc1-1
/var/log/dpkg.log:2018-08-04 15:54:48 install sgml-base:all <none> 1.29
/var/log/dpkg.log:2018-08-04 15:54:48 install cinnamon-desktop-data:all <none> 3.6.2-2
/var/log/dpkg.log:2018-08-04 15:54:49 install libcinnamon-desktop4:amd64 <none> 3.6.2-2
/var/log/dpkg.log:2018-08-04 15:54:49 install gir1.2-cinnamondesktop-3.0:amd64 <none> 3.6.2-2
/var/log/dpkg.log:2018-08-04 15:54:49 install gir1.2-cogl-1.0:amd64 <none> 1.22.2-3
/var/log/dpkg.log:2018-08-04 15:54:49 install gir1.2-coglpango-1.0:amd64 <none> 1.22.2-3
/var/log/dpkg.log:2018-08-04 15:54:50 install gir1.2-clutter-1.0:amd64 <none> 1.26.2+dfsg-4
/var/log/dpkg.log:2018-08-04 15:54:50 install muffin-common:all <none> 3.6.0-1
/var/log/dpkg.log:2018-08-04 15:54:52 install libmuffin0:amd64 <none> 3.6.0-1
/var/log/dpkg.log:2018-08-04 15:54:54 install gir1.2-meta-muffin-0.0:amd64 <none> 3.6.0-1
/var/log/dpkg.log:2018-08-04 15:54:56 install python-pil:amd64 <none> 5.1.0-1
/var/log/dpkg.log:2018-08-04 15:54:57 install cinnamon-common:all <none> 3.6.7-8ubuntu1
/var/log/dpkg.log:2018-08-04 15:54:59 install cinnamon-control-center-data:all <none> 3.6.5-2
/var/log/dpkg.log:2018-08-04 15:54:59 install libcvc0:amd64 <none> 3.6.2-2
/var/log/dpkg.log:2018-08-04 15:55:00 install gir1.2-cvc-1.0:amd64 <none> 3.6.2-2
/var/log/dpkg.log:2018-08-04 15:55:00 install cinnamon-settings-daemon:amd64 <none> 3.6.2-1
/var/log/dpkg.log:2018-08-04 15:55:00 install libcinnamon-control-center1:amd64 <none> 3.6.5-2
/var/log/dpkg.log:2018-08-04 15:55:01 install libcinnamon-menu-3-0:amd64 <none> 3.6.0-1
/var/log/dpkg.log:2018-08-04 15:55:01 install cinnamon-control-center:amd64 <none> 3.6.5-2
/var/log/dpkg.log:2018-08-04 15:55:01 install gir1.2-xkl-1.0:amd64 <none> 5.4-3
/var/log/dpkg.log:2018-08-04 15:55:01 install gir1.2-gkbd-3.0:amd64 <none> 3.26.0-3
/var/log/dpkg.log:2018-08-04 15:55:01 install xapps-common:all <none> 1.0.4-2fakesync1
/var/log/dpkg.log:2018-08-04 15:55:02 install libxapp1:amd64 <none> 1.0.4-2fakesync1
/var/log/dpkg.log:2018-08-04 15:55:02 install gir1.2-xapp-1.0:amd64 <none> 1.0.4-2fakesync1
/var/log/dpkg.log:2018-08-04 15:55:02 install iso-flags-png-320x240:all <none> 1.0.1-1
/var/log/dpkg.log:2018-08-04 15:55:03 install libcscreensaver0:amd64 <none> 3.6.1-2
/var/log/dpkg.log:2018-08-04 15:55:03 install python3-setproctitle:amd64 <none> 1.1.10-1build2
/var/log/dpkg.log:2018-08-04 15:55:03 install python3-psutil:amd64 <none> 5.4.2-1
/var/log/dpkg.log:2018-08-04 15:55:03 install python3-xapp:all <none> 1.0.1-1
/var/log/dpkg.log:2018-08-04 15:55:04 install python3-xlib:all <none> 0.20-3
/var/log/dpkg.log:2018-08-04 15:55:04 install cinnamon-screensaver:amd64 <none> 3.6.1-2
/var/log/dpkg.log:2018-08-04 15:55:04 install cinnamon-session-common:all <none> 3.6.1-1
/var/log/dpkg.log:2018-08-04 15:55:04 install cinnamon-session:amd64 <none> 3.6.1-1
/var/log/dpkg.log:2018-08-04 15:55:05 install libmozjs-38-0:amd64 <none> 38.8.0~repack1-0ubuntu4
/var/log/dpkg.log:2018-08-04 15:55:05 install libcjs0:amd64 <none> 3.6.1-0ubuntu1
/var/log/dpkg.log:2018-08-04 15:55:05 install cjs:amd64 <none> 3.6.1-0ubuntu1
/var/log/dpkg.log:2018-08-04 15:55:05 install libcaribou-common:all <none> 0.4.21-5
/var/log/dpkg.log:2018-08-04 15:55:05 install libcaribou0:amd64 <none> 0.4.21-5
/var/log/dpkg.log:2018-08-04 15:55:06 install gir1.2-caribou-1.0:amd64 <none> 0.4.21-5
/var/log/dpkg.log:2018-08-04 15:55:06 install gir1.2-cmenu-3.0:amd64 <none> 3.6.0-1
/var/log/dpkg.log:2018-08-04 15:55:06 install gir1.2-gtkclutter-1.0:amd64 <none> 1.8.4-3
/var/log/dpkg.log:2018-08-04 15:55:06 install libkeybinder-3.0-0:amd64 <none> 0.3.2-1
/var/log/dpkg.log:2018-08-04 15:55:06 install gir1.2-keybinder-3.0:amd64 <none> 0.3.2-1
/var/log/dpkg.log:2018-08-04 15:55:06 install gnome-backgrounds:all <none> 3.28.0-1
/var/log/dpkg.log:2018-08-04 15:55:08 install mesa-utils:amd64 <none> 8.4.0-1
/var/log/dpkg.log:2018-08-04 15:55:08 install muffin:amd64 <none> 3.6.0-1
/var/log/dpkg.log:2018-08-04 15:55:08 install libnemo-extension1:amd64 <none> 3.6.5-1
/var/log/dpkg.log:2018-08-04 15:55:08 install nemo-data:all <none> 3.6.5-1
/var/log/dpkg.log:2018-08-04 15:55:09 install nemo:amd64 <none> 3.6.5-1
/var/log/dpkg.log:2018-08-04 15:55:09 install policykit-1-gnome:amd64 <none> 0.105-6ubuntu2
/var/log/dpkg.log:2018-08-04 15:55:09 install python-dbus:amd64 <none> 1.2.6-1
/var/log/dpkg.log:2018-08-04 15:55:10 install python-gi:amd64 <none> 3.26.1-2
/var/log/dpkg.log:2018-08-04 15:55:10 install python-cairo:amd64 <none> 1.16.2-1
/var/log/dpkg.log:2018-08-04 15:55:10 install python-gi-cairo:amd64 <none> 3.26.1-2
/var/log/dpkg.log:2018-08-04 15:55:10 install python-lxml:amd64 <none> 4.2.1-1
/var/log/dpkg.log:2018-08-04 15:55:11 install python-pam:amd64 <none> 0.4.2-13.2ubuntu4
/var/log/dpkg.log:2018-08-04 15:55:11 install python-ptyprocess:all <none> 0.5.2-1
/var/log/dpkg.log:2018-08-04 15:55:11 install python-pexpect:all <none> 4.2.1-1
/var/log/dpkg.log:2018-08-04 15:55:11 install python-pyinotify:all <none> 0.9.6-1
/var/log/dpkg.log:2018-08-04 15:55:11 install cinnamon:amd64 <none> 3.6.7-8ubuntu1
/var/log/dpkg.log:2018-08-04 15:55:12 install gnome-icon-theme:all <none> 3.12.0-3
/var/log/dpkg.log:2018-08-04 15:55:17 install gir1.2-appindicator3-0.1:amd64 <none> 12.10.1+18.04.20180322.1-0ubuntu1
/var/log/dpkg.log:2018-08-04 15:55:18 install blueman:amd64 <none> 2.0.5-1ubuntu1
/var/log/dpkg.log:2018-08-04 15:55:19 install cinnamon-l10n:all <none> 3.6.4-1
/var/log/dpkg.log:2018-08-04 15:55:21 install xscreensaver-data:amd64 <none> 5.36-1ubuntu1
/var/log/dpkg.log:2018-08-04 15:55:21 install cinnamon-screensaver-x-plugin:all <none> 3.6.1-2
/var/log/dpkg.log:2018-08-04 15:55:21 install rubygems-integration:all <none> 1.11
/var/log/dpkg.log:2018-08-04 15:55:22 install rake:all <none> 12.3.1-1
/var/log/dpkg.log:2018-08-04 15:55:22 install ruby-did-you-mean:all <none> 1.2.0-2
/var/log/dpkg.log:2018-08-04 15:55:22 install ruby-minitest:all <none> 5.10.3-1
```

---

### Post by deadflowr on 2018-08-24
Did you perchance try installing the nemo file manager?

---

### Post by ubantunovice2 on 2018-08-24
I decided to go ahead and remove cinnamon as a learning activity.
I found this thread [https://ubuntuforums.org/showthread.php?t=1987942](https://ubuntuforums.org/showthread.php?t=1987942)
and did
sudo apt-get remove cinnamon
sudo apt-get autoremoveI'll see if anything breaks.

---

### Post by ubantunovice2 on 2018-08-24
> **deadflowr said:**
> Did you perchance try installing the nemo file manager?
You win!

Yes I found I had it installed. Don't remember doing so!

I will remove it. If I am learning correctly, the command I need is:
sudo apt-get remove nemo
(If not I'll go gui......)

---

### Post by ajgreeny on 2018-08-26
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by ubantunovice2 on 2018-08-26
It's all a learning process for me. I did not realize that I have to be careful to read which flavor a tool comes from. When I installed Nemo I did not realize that it came from the cinnamon desktop which it therefore apparently installed. I now know to read that part of the _description_ **and also** the part when it pauses before the installation to tell me what it plans to install and _waits for me to agree_. 

Seems obvious now, but for a newbie it is part of the learning process. Thank you for helping.

---

