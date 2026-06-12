---
title: "SOS please help!"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by TooFreppaT on 2012-04-15
I turned on my computer and the bars (top and bottom of screen) are gone/missing. the ones with the system tray and menu bars and everything that makes this whole thing work!

I'm using Ubuntu 10.10

the only way I'm able to access my web browser was by clicking on a saved website on my desktop (whew! lucky!)

just added a new tab (I have about a hundred of them open - they open automatically when the web browser starts) and then minimised it ...it just disappeared!
aaahh, but if I "Alt+TAB" - then it becomes accessible again! ...atleast I'm getting somewhere with this!

don't know what to do now :confused:



just remembered that they are called "panels" (I had two of them & don't know what happened to them)

before, whenever something disappeared all I had to do was restart, then it would magically come back again... didn't happen this time - I've restarted enough times to know it ain't gonna fix itself

back on the desktop, the only thing I can do is right-click the background... it gives me the option to change the background, but if I click it, it does nothing... nothing shows up no matter how long I wait

before I thought to click on the saved webpage, I was trying to find the web browser through ¿nautilus? ...I opened up a folder on the desktop, but couldn't remember where to go to open stuff like the web browser that I am now using

screenprint doesn't work either!

I can't see my clock! have no idea what time it is!



...bet everyone who's reading this is going :lolflag:

---

### Post by abyrne on 2012-04-15
Can you get access to a terminal? If so, run the command
```
gnome-panel
```
and post any output.

---

### Post by TooFreppaT on 2012-04-15
is there a way to access terminal by pressing keys on the keyboard?

I pressed "Alt+F2" and nothing happened!

---

### Post by abyrne on 2012-04-15
I believe that either Ctrl-Alt-T or WindowsKey+T should do the trick.

---

### Post by TooFreppaT on 2012-04-15
```
gnome-panel
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel

```

and then I did...

```
sudo apt-get install gnome-panel
[COLOR="Red"]asking_for_password[/COLOR]: [COLOR="Lime"]password_entered[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  evolution-data-server evolution-data-server-common gnome-applets
  gnome-control-center indicator-applet libcamel1.2-14 libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7
  libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13
  libgdata-google1.2-1 libgdata1.2-1
Suggested packages:
  evolution evolution-data-server-dbg gnome-netstatus-applet deskbar-applet
  cpufrequtils epiphany-browser menu-xdg
The following NEW packages will be installed:
  evolution-data-server evolution-data-server-common gnome-applets
  gnome-control-center gnome-panel indicator-applet libcamel1.2-14
  libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8
  libegroupwise1.2-13 libgdata-google1.2-1 libgdata1.2-1
0 upgraded, 17 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,792kB/2,865kB of archives.
After this operation, 9,560kB of additional disk space will be used.
[COLOR="red"]Do you want to continue [Y/n][/COLOR]? [COLOR="Lime"]y[/COLOR]
Get:1 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libedataserver1.2-13 amd64 2.30.3-2ubuntu2.1 [147kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libecal1.2-7 amd64 2.30.3-2ubuntu2.1 [95.5kB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libcamel1.2-14 amd64 2.30.3-2ubuntu2.1 [394kB]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libebook1.2-9 amd64 2.30.3-2ubuntu2.1 [74.4kB]
Get:5 http://archive.ubuntu.com/ubuntu/ maverick-updates/main evolution-data-server-common all 2.30.3-2ubuntu2.1 [99.4kB]
27% [5 evolution-data-server-common 66.9kB/99.4kB 67%]             73.1kB/s 27s^C

```

---

### Post by JC Cheloven on 2012-04-15
First off, you'll want to open a terminal. There is a keyboard shortcut for that (as for many other apps). If you didn't change it, that should be ctrl-alt-F1 or ctrl-alt-T, if memory heps. 
Or you can hit ctrl-alt-F2 to enter commands by one at a time.

Once at a terminal you can try a number of things, for example the path outlined [here]("http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/").

Or perhaps simply reinstalling gnome-panel will do it: 
```
sudo apt-get install --reinstall gnome-panel
```

...  once you get a terminal (and with your web browser, which you have available), you can do a little search if none of the above worked. 

Note: I'm telling by memory as I don't use gnome. I think the above should work... Oh, your panel configurations are stored in ~/.gconf/apps/panel , you may want to save that elsewhere before playing around, if you had a lot of configurations in your panel.
Note2: Until you fix your panels, you can launch everything, for example nautilus, by simply typing "nautilus" at a terminal.

EDIT: oops, a lot of people answered while I tried to remember how things were in gnome, etc. Please forgive any duplicity.

---

### Post by TooFreppaT on 2012-04-15
so I think panels is installed ¿again? (don't know why it wasn't - I saw it only a few hours ago)

but I still can't see them? how do I make them come back again?

---

### Post by JC Cheloven on 2012-04-15
> **TooFreppaT said:**
> so I think panels is installed ¿again? (don't know why it wasn't - I saw it only a few hours ago)
From your previous output, it seems you aborted the installation? If so, please allow it to complete
It's strange anyway, gnome-panel not being already installed. 
> but I still can't see them? how do I make them come back again?
Did you had a look at my previous link?

---

### Post by abyrne on 2012-04-15
> so I think panels is installed ¿again? (don't know why it wasn't - I saw it only a few hours ago)
Could have been some really weird dependency conflict. Hard to say...

[COLOR="Blue"]EDIT: JC Cheloven is right. Were you trying to use Ctrl-C to copy? Ctrl-C is Terminal speak for "stop the currently running program". Run the install command again and allow it to complete.[/COLOR]

> but I still can't see them? how do I make them come back again?
Try rebooting. (Hint: you can do that from the terminal with "sudo reboot")
If that doesn't work, run
```
gnome-panel
```
and tell us if it outputs anything weird.

---

### Post by TooFreppaT on 2012-04-15
okay, so even before I got to see the comments after my last, I clicked on the tab next to the one that this is on ([http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/](http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/))

as soon as I pressed ALT+F2 my computer crashed and died (stuff went a little crazy just inbetween the ALT+F2 and the crashing and dying)

so I pulled the plug (couldn't do anything else)
when I plugged it back in and switched on...

I did this:

```
[COLOR="Red"]#####@user:~$[/COLOR] [COLOR="Lime"]gnome-panel[/COLOR]
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
[COLOR="Red"]#####@user:~$[/COLOR] [COLOR="lime"]sudo apt-get install gnome-panel[/COLOR]
[COLOR="Red"][sudo] password for user:[/COLOR] [COLOR="Lime"]********[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  evolution-data-server evolution-data-server-common gnome-applets
  gnome-control-center indicator-applet libcamel1.2-14 libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7
  libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13
  libgdata-google1.2-1 libgdata1.2-1
Suggested packages:
  evolution evolution-data-server-dbg gnome-netstatus-applet deskbar-applet
  cpufrequtils epiphany-browser menu-xdg
The following NEW packages will be installed:
  evolution-data-server evolution-data-server-common gnome-applets
  gnome-control-center gnome-panel indicator-applet libcamel1.2-14
  libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8
  libegroupwise1.2-13 libgdata-google1.2-1 libgdata1.2-1
0 upgraded, 17 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,081kB/2,865kB of archives.
After this operation, 9,560kB of additional disk space will be used.
[COLOR="Red"]Do you want to continue [Y/n]?[/COLOR] [COLOR="Lime"]y[/COLOR]
Get:1 http://archive.ubuntu.com/ubuntu/ maverick-updates/main evolution-data-server-common all 2.30.3-2ubuntu2.1 [99.4kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libedataserverui1.2-8 amd64 2.30.3-2ubuntu2.1 [96.8kB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick/main gnome-control-center amd64 1:2.32.0-0ubuntu2 [407kB]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick/main gnome-panel amd64 1:2.30.2-1ubuntu3 [441kB]
Get:5 http://archive.ubuntu.com/ubuntu/ maverick/main gnome-applets amd64 2.30.0-3ubuntu3 [191kB]
Get:6 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libebackend1.2-0 amd64 2.30.3-2ubuntu2.1 [17.4kB]
Get:7 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libedata-book1.2-2 amd64 2.30.3-2ubuntu2.1 [44.5kB]
Get:8 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libedata-cal1.2-7 amd64 2.30.3-2ubuntu2.1 [57.9kB]
Get:9 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libgdata1.2-1 amd64 2.30.3-2ubuntu2.1 [89.5kB]
Get:10 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libgdata-google1.2-1 amd64 2.30.3-2ubuntu2.1 [14.2kB]
Get:11 http://archive.ubuntu.com/ubuntu/ maverick-updates/main evolution-data-server amd64 2.30.3-2ubuntu2.1 [595kB]
Get:12 http://archive.ubuntu.com/ubuntu/ maverick/main indicator-applet amd64 0.4.6-0ubuntu1 [27.8kB]
Fetched 2,007kB in 25s (78.1kB/s)                                              
Selecting previously deselected package libedataserver1.2-13.
(Reading database ... 375318 files and directories currently installed.)
Unpacking libedataserver1.2-13 (from .../libedataserver1.2-13_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libecal1.2-7.
Unpacking libecal1.2-7 (from .../libecal1.2-7_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libcamel1.2-14.
Unpacking libcamel1.2-14 (from .../libcamel1.2-14_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libebook1.2-9.
Unpacking libebook1.2-9 (from .../libebook1.2-9_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package evolution-data-server-common.
Unpacking evolution-data-server-common (from .../evolution-data-server-common_2.30.3-2ubuntu2.1_all.deb) ...
Selecting previously deselected package libedataserverui1.2-8.
Unpacking libedataserverui1.2-8 (from .../libedataserverui1.2-8_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package gnome-control-center.
Unpacking gnome-control-center (from .../gnome-control-center_1%3a2.32.0-0ubuntu2_amd64.deb) ...
Selecting previously deselected package gnome-panel.
Unpacking gnome-panel (from .../gnome-panel_1%3a2.30.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package gnome-applets.
Unpacking gnome-applets (from .../gnome-applets_2.30.0-3ubuntu3_amd64.deb) ...
Selecting previously deselected package libebackend1.2-0.
Unpacking libebackend1.2-0 (from .../libebackend1.2-0_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libedata-book1.2-2.
Unpacking libedata-book1.2-2 (from .../libedata-book1.2-2_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libedata-cal1.2-7.
Unpacking libedata-cal1.2-7 (from .../libedata-cal1.2-7_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libegroupwise1.2-13.
Unpacking libegroupwise1.2-13 (from .../libegroupwise1.2-13_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libgdata1.2-1.
Unpacking libgdata1.2-1 (from .../libgdata1.2-1_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libgdata-google1.2-1.
Unpacking libgdata-google1.2-1 (from .../libgdata-google1.2-1_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package evolution-data-server.
Unpacking evolution-data-server (from .../evolution-data-server_2.30.3-2ubuntu2.1_amd64.deb) ...
Selecting previously deselected package indicator-applet.
Unpacking indicator-applet (from .../indicator-applet_0.4.6-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Setting up libedataserver1.2-13 (2.30.3-2ubuntu2.1) ...
Setting up libecal1.2-7 (2.30.3-2ubuntu2.1) ...
Setting up libcamel1.2-14 (2.30.3-2ubuntu2.1) ...
Setting up libebook1.2-9 (2.30.3-2ubuntu2.1) ...
Setting up evolution-data-server-common (2.30.3-2ubuntu2.1) ...
Setting up libedataserverui1.2-8 (2.30.3-2ubuntu2.1) ...
Setting up gnome-control-center (1:2.32.0-0ubuntu2) ...
Setting up gnome-panel (1:2.30.2-1ubuntu3) ...
Setting up gnome-applets (2.30.0-3ubuntu3) ...
Setting up libebackend1.2-0 (2.30.3-2ubuntu2.1) ...
Setting up libedata-book1.2-2 (2.30.3-2ubuntu2.1) ...
Setting up libedata-cal1.2-7 (2.30.3-2ubuntu2.1) ...
Setting up libegroupwise1.2-13 (2.30.3-2ubuntu2.1) ...
Setting up libgdata1.2-1 (2.30.3-2ubuntu2.1) ...
Setting up libgdata-google1.2-1 (2.30.3-2ubuntu2.1) ...
Setting up evolution-data-server (2.30.3-2ubuntu2.1) ...
Setting up indicator-applet (0.4.6-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
[COLOR="Red"]#####@user:~$[/COLOR] [COLOR="lime"]gnome-panel[/COLOR]

** (gnome-panel:2777): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
(null)


  

                            



```

the second time I entered gnome-panel it came up with an error and requested something be deleted, I'm sure I pressed the option to delete but could be wrong (habitually chose the option not to delete for way too long)

at the end I pressed enter 7 times... I'm still waiting for the [COLOR="Red"]#####@user:~$[/COLOR] to show up!

but good news: it's back and it's got everything where I had it before! :guitar:

but I think I chose the delete option so I'm not sure what I'm missing¿ hold on... I think I'm missing the way to shutdown and stuff! anyone know how I can get this back, if I deleted it?

and what do I do with terminal - is it safe to just close it?

---

### Post by pqwoerituytrueiwoq on 2012-04-15
for the [COLOR=Red]#####@user:~$[/COLOR] to show up gnome-panel has to be closed you may want to press [crtl] +[C] and run [FONT=Courier New]gnome-panel &[/FONT]

---

### Post by TooFreppaT on 2012-04-15
thanks! it stayed this time!

all I need now is help getting that thing that was in the upper right corner (where you shutdown and stuff) I right click the panel > add to panel > user switcher but it's not the same¿

Alt+F2 and screenprint run perfectly now also!

from my last terminal session (previous page):
```
** (gnome-panel:2777): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
(null)
```

sooo, how to add FastUserSwitchApplet ...I can't find it in the "add to panel" list¿

---

### Post by TooFreppaT on 2012-04-15
okay so following this: [http://ubuntu-tutorials.com/2007/06/01/fast-user-switching-applet-ubuntu-704/](http://ubuntu-tutorials.com/2007/06/01/fast-user-switching-applet-ubuntu-704/)

I got:
```
[COLOR="red"]#####@user:~$[/COLOR] [COLOR="Lime"]sudo aptitude install fast-user-switch-applet[/COLOR]
[COLOR="Red"][sudo] password for user:[/COLOR] [COLOR="Lime"]********[/COLOR]
sudo: aptitude: command not found
[COLOR="Red"]#####@user:~$[/COLOR] [COLOR="Lime"]sudo apt-get install fast-user-switch-applet[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fast-user-switch-applet is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gdm indicator-applet-session

E: Package 'fast-user-switch-applet' has no installation candidate
[COLOR="Red"]#####@user:~$[/COLOR]

```

tried following the following:
[http://ubuntuforums.org/showthread.php?t=1454603](http://ubuntuforums.org/showthread.php?t=1454603)
[http://ubuntuforums.org/tags.php?tag=fast-user-switch-applet](http://ubuntuforums.org/tags.php?tag=fast-user-switch-applet)
[https://vinci.wordpress.com/2008/11/03/new-ubuntu-and-new-gnome-fast-user-switch-applet/](https://vinci.wordpress.com/2008/11/03/new-ubuntu-and-new-gnome-fast-user-switch-applet/)

but nothing...

---

### Post by Swagman on 2012-04-15
Just looking through my saved TomBoy notes on Top Panel rebuild:

```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

That should still work on Maverick

---

### Post by cmcanulty on 2012-04-15
you can also add it to startup applications

---

### Post by TooFreppaT on 2012-04-15
> you can also add it to startup applications

add what? and how?

I "Solved" this thread and started a new one @ [http://ubuntuforums.org/showthread.php?t=1959677](http://ubuntuforums.org/showthread.php?t=1959677)

---

### Post by JC Cheloven on 2012-04-15
> **Swagman said:**
> Just looking through my saved TomBoy notes on Top Panel rebuild:
```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
That should still work on Maverick

> **JC Cheloven said:**
> (...) Once at a terminal you can try a number of things, for example the path outlined [here]("http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/"). (...)

@the OP:  EDIT: (deleted line) Doesn't matter. Take your own picture.

---

