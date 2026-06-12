---
title: "can you help me undo this command?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by xerxes651 on 2008-07-24
I did the command
sudo dpkg-reconfigure -phigh xserver-xorg
from where i saw it posted in another thread where someone said it would fix their "undefined video mode number 31f" now it gives me "undefined video mode number 31b" and my compiz will not work, do any of you know how i can undo that command so at least my compiz will work again?

---

### Post by overdrank on 2008-07-24
> **xerxes651 said:**
> I did the command
sudo dpkg-reconfigure -phigh xserver-xorg
from where i saw it posted in another thread where someone said it would fix their "undefined video mode number 31f" now it gives me "undefined video mode number 31b" and my compiz will not work, do any of you know how i can undo that command so at least my compiz will work again?

HI and welcome, could you give us some system specs, like graphics and memory? The command you used has worked for some users in the past and if you are using Hardy 8.04 there are other ways of correcting graphics issues.

---

### Post by hyper_ch on 2008-07-24
what's the output of

```

sudo ls -al /etc/X11

```

and when did you run the other command?

---

### Post by m_ad on 2008-07-24
overdrank, shouldn't there be a backup of his old xorg.conf file that he could replace the new one with?

---

### Post by xerxes651 on 2008-07-24
> **overdrank said:**
> HI and welcome, could you give us some system specs, like graphics and memory? The command you used has worked for some users in the past and if you are using Hardy 8.04 there are other ways of correcting graphics issues.

let me see, hardy 8.04, AMD Turion(tm) 64 X2 Mobile Technology TL-50 800 mhz 882 mbs of ram, 128 mbs ati integrated graphics radeon express 1100

---

### Post by xerxes651 on 2008-07-24
> **hyper_ch said:**
> what's the output of

```

sudo ls -al /etc/X11

```

and when did you run the other command?


total 96
drwxr-xr-x  10 root root  4096 2008-07-24 08:22 .
drwxr-xr-x 141 root root 12288 2008-07-24 08:25 ..
drwxr-xr-x   2 root root  4096 2008-04-22 14:03 app-defaults
drwxr-xr-x   2 root root  4096 2008-06-18 19:31 cursors
-rw-r--r--   1 root root    14 2008-04-22 14:02 default-display-manager
drwxr-xr-x   6 root root  4096 2008-04-22 13:54 fonts
-rw-r--r--   1 root root 17394 2007-11-19 10:15 rgb.txt
lrwxrwxrwx   1 root root    13 2008-06-18 15:59 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2008-04-22 13:59 xinit
drwxr-xr-x   2 root root  4096 2008-04-22 13:49 xkb
-rw-r--r--   1 root root  1475 2008-07-24 08:22 xorg.conf
-rw-r--r--   1 root root  1548 2008-07-24 08:22 xorg.conf.20080724082257
drwxr-xr-x   2 root root  4096 2008-07-06 17:39 Xresources
drwxr-xr-x   2 root root  4096 2008-06-18 17:15 xserver
-rwxr-xr-x   1 root root  3730 2008-03-13 11:10 Xsession
drwxr-xr-x   2 root root  4096 2008-07-06 17:39 Xsession.d
-rw-r--r--   1 root root   265 2007-11-19 10:15 Xsession.options
-rw-r--r--   1 root root    13 2007-07-24 05:59 XvMCConfig
-rw-------   1 root root   614 2008-04-22 13:51 Xwrapper.config


and i did the command about 5 mins ago

---

### Post by hyper_ch on 2008-07-24
then run

```

sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf.20080724082257 /etc/X11/xorg.conf

```

Log out and back in again (or reboot) and you have your old settings there again ;)

And when posting output from a command or content of a file use [noparse][code][/nocode][/noparse] brackets around it.

---

### Post by xerxes651 on 2008-07-24
> **hyper_ch said:**
> then run

```

sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf.20080724082257 /etc/X11/xorg.conf

```

Log out and back in again (or reboot) and you have your old settings there again ;)

And when posting output from a command or content of a file use [noparse][code][/nocode][/noparse] brackets around it.

adam@adam-laptop:~$ sudo rm /etc/X11/xorg.conf
[sudo] password for adam:
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
adam@adam-laptop:~$ sudo mv /etc/X11/xorg.conf.20080724082257 /etc/X11/xorg.conf
mv: cannot stat `/etc/X11/xorg.conf.20080724082257': No such file or directory
adam@adam-laptop:~$

and it didnt work, still no compiz, now my touchpad's scroll button thing is messed up and acting like a right click

---

### Post by xerxes651 on 2008-07-24
seems now i cant even get advanced graphics settings to work, if i cant get this resolved by noon today ill have to reinstall :(

---

### Post by m_ad on 2008-07-24
Reassure that /etc/X11/xorg.conf exists. I don't know how it wouldn't, but bash is telling you it doesn't.

do 'sudo ls /etc/X11' again, and see if xorg.conf exists.

if it doesn't, just rename xorg.conf.20080724082257 to xorg.conf.

---

### Post by xerxes651 on 2008-07-24
> **m_ad said:**
> Reassure that /etc/X11/xorg.conf exists. I don't know how it wouldn't, but bash is telling you it doesn't.

do 'sudo ls /etc/X11' again, and see if xorg.conf exists.

if it doesn't, just rename xorg.conf.20080724082257 to xorg.conf.

app-defaults             fonts    xinit       xserver     Xsession.options
cursors                  rgb.txt  xkb         Xsession    XvMCConfig
default-display-manager  X        Xresources  Xsession.d  Xwrapper.config

is what that pulled up, btw what do i have to do to rename xorg.conf? Im fairly decent with running linux but im not all that great with terminal codes sorry for being a noob

---

### Post by m_ad on 2008-07-24
something happened to your xorg.conf file. what happened since the post when you had two xorg.conf files?

---

### Post by xerxes651 on 2008-07-24
> **m_ad said:**
> something happened to your xorg.conf file. what happened since the post when you had two xorg.conf files?

i have no idea, the only thing i did since i screwed it up from the first command i posted about was uninstall and reinstall compiz, changed the resolution back to what it was b4 the screw up and the code i was told to put it, the first time i added that code it didnt bring up any text or confirmation of doing anything, so then i rebooted, didnt fix it, tried again, then it brought up that "does not exist" error

---

### Post by m_ad on 2008-07-24
I have no idea how you couldn't have an xorg.conf file. I'm still a noob also so, hopefully an expert will come across and help you solve this. Sorry I can't be of anymore help.

---

