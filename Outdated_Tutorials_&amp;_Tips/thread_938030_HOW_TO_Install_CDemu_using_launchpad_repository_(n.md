---
title: "HOW TO: Install CDemu using launchpad repository (no compiling!) on Hardy Heron 8.04"
date: 2008-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by fermulator on 2008-10-04
**_Introduction_**

_____________________________________________________________________
EDIT: CDemu isn't officially supported on Ubuntu Hardy, however it is supported on later releases.  At the time of this edit, this includes Ubuntu 8.10 Intrepid and Ubuntu 9.04 Jaunty.  The PPA site for CDemu ([https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)) has details on how to get this up and running.  I've tried it, and it works quite well! ;-0
_____________________________________________________________________

I've been on the search for an equivalent ISO mounting program as simple as [daemon tools]("http://www.daemon-tools.cc/") (which only runs on Windows) for some time now.  Finally, [cdemu]("http://cdemu.sourceforge.net/") is ready for the challenge, and has been for some time now.

There are numerous posts on how to [compile CDemu]("http://ubuntuforums.org/showthread.php?t=276743&highlight=cdemu") for Ubuntu and some [outdated posts]("http://ubuntuforums.org/showthread.php?t=69530").  It might be better to use an actual deb package directly from the launchpad repository - [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu).

**_How to Install CDemu_**

 1. Add the CDemu launchpad list repository:
```
sudo echo "deb http://ppa.launchpad.net/cdemu/ubuntu hardy main" > /etc/apt/sources.list.d/cdemu.list
```
 2. Update your package database
```
sudo apt-get update
```
 3. Install CDemu
```
sudo apt-get install cdemu-daemon gcdemu
```

The installation will create a CDemu daemon (/etc/init.d/cdemu-daemon) for CDemu system daemon, as well as create a session autostartup entry for your user account (~/.config/autostart/cdemu-daemon.desktop).  You can see this by viewing **System --> Preferences --> Sessions (Startup Programs Tab)** or by running **gnome-session-properties**.

 4. Start CDemu:  We have two options, either:
 - Restart your computer:
```
reboot
```
OR
 - Manually start CDemu for the first time:
```
sudo /etc/init.d/cdemu-daemon start
cdemud-session &
```

 5. Add the CDemu GUI applet
[LIST]
[*] Right click on your panel and select 'Add to Panel ...'
[*] Search for 'cdemu', and select "gCDEmu Applet" and choose "Add"
[*] For additional details see [Adding an Object to a Panel]("http://library.gnome.org/users/user-guide/stable/panels-addobject.html.en")
[/LIST]

**_Footnotes_**
This was tested on 2008-10-04 running Ubuntu Hardy Heron (8.04).

**_Credits_**
[LIST]
[*] Eddy Mulyono - [http://eddymulyono.livejournal.com/tag/tech](http://eddymulyono.livejournal.com/tag/tech)
[/LIST]

**_[COLOR="Red"]BROKEN:_**  I'm having some trouble with the auto starting of cdemud-session[/COLOR] (run by ~/.config/autostart/cdemu-daemon.desktop), so I need to manually run
```
cdemud-session &
```
for now.  (Any tips on why this isn't working?)

---

### Post by bedhead75 on 2008-10-05
I'm also running Hardy Heron 8.04, but after following your instructions and rebooting, CDemu fails to start.  It is also not listed at all in the items that I can add to the panel.  When I manually start it in the terminal by typing "cdemud-session", I get this...

Starting CDEmu daemon
Starting daemon in local mode with following parameters:
 - num devices: 2
 - ctl device: /dev/vhba_ctl
 - audio driver: default
 - bus type: session

...but I don't see any GUI or anything appear.  There is supposed to be a user interface right?  Am I missing something here?

---

### Post by fermulator on 2008-10-05
> **bedhead75 said:**
> I'm also running Hardy Heron 8.04, but after following your instructions and rebooting, CDemu fails to start.  It is also not listed at all in the items that I can add to the panel.  When I manually start it in the terminal by typing "cdemud-session", I get this...

Starting CDEmu daemon
Starting daemon in local mode with following parameters:
 - num devices: 2
 - ctl device: /dev/vhba_ctl
 - audio driver: default
 - bus type: session

...but I don't see any GUI or anything appear.  There is supposed to be a user interface right?  Am I missing something here?

did you skip step #5?

---

### Post by action09 on 2008-10-11
HI, thanks for details of installation first.
Anyway i'have problems.

1/ step 3: First note, there is no file "~/.config/autostart/cdemu-daemon.desktop" but in gnome-session-properties, a session autostartup entry is created anyway, detail: "CDEmu daemon session launcher" launching "cdemud-session" command.

Do i have to create and personnalize a file "~/.config/autostart/cdemu-daemon.desktop"  ? I'm going to search in documentation.

2/ step 5: Add the CDemu GUI applet, If i try to add it i have an error "OAFIID:GNOME_gCDEmu_Applet" problem with the gnome panel, do you want to delet this applet from your configuration ?

Maybe because the cdemu-daemon was not correcly launched at statup... that's the last note :)

---

### Post by fermulator on 2008-10-13
> **action09 said:**
> 
1/ step 3: First note, there is no file "~/.config/autostart/cdemu-daemon.desktop" but in gnome-session-properties, a session autostartup entry is created anyway, detail: "CDEmu daemon session launcher" launching "cdemud-session" command.

Do i have to create and personnalize a file "~/.config/autostart/cdemu-daemon.desktop"  ? I'm going to search in documentation.


 - Interesting point - I had to open the session properties for CDEmu, make some change (uncheck then check again the enabled option for example), then click close.  Then the entry was created for me.
 - EDIT: Wait, I just fiddled a little more, it appears that the cdemu-daemon.desktop item ONLY exists if the session entry is disabled? - Can someone please confirm this?

> **action09 said:**
> 2/ step 5: Add the CDemu GUI applet, If i try to add it i have an error "OAFIID:GNOME_gCDEmu_Applet" problem with the gnome panel, do you want to delet this applet from your configuration ?

 - This is weird.  I've never seen this one before.  Is it actually a problem with the CDEmu gApplet? ... or something corrupt with your panel?  Curious if anyone else gets this, because I've tried these instructions on several systems and not seen this error yet.

---

### Post by Aritomo on 2008-10-19
When I try to install CDemu this way, or through Synaptic, I get the following error:
```
(Reading database ... 182064 files and directories currently installed.)
Unpacking gcdemu (from .../gcdemu_1.1.0-0ubuntu1_all.deb) ...
Setting up cdemu-daemon (1.1.0-0ubuntu1) ...
 * Starting CDEmu daemon                                                         * Inserting vhba kernel module...                                       [fail] 
                                                                         [fail]
invoke-rc.d: initscript cdemu-daemon, action "start" failed.
dpkg: error processing cdemu-daemon (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gcdemu:
 gcdemu depends on cdemu-daemon (>= 1.1.0); however:
  Package cdemu-daemon is not configured yet.
dpkg: error processing gcdemu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cdemu-daemon
 gcdemu
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I'm using Ubuntu Studio 8.04, kernel 2.6.24-21-rt
So, like... help, please?

---

### Post by Aritomo on 2008-10-19
Sorry, solved this one. It just requires a little bit more rebooting on rt-kernels, I guess.
So, if anyone else gets errors like that - reboot once so that vhba installs correctly, then it'll be a good idea to reinstall the daemon, reboot once again, and then reinstall the gui

As for it not autoloading, when you run sudo /etc/init.d/cdemu-daemon start it states there, that it's sort of "currently not configured to load on system start"... whatever that means.

---

### Post by lucianct on 2008-10-19
how can i change the number of devices that are emulated?

cdemu has also broken my sound...

later edit: i fixed the sound by deleting the pulse-audio lines from /etc/init.d/cdemu-daemon, uninstalling pulseaudio (i was using ALSA anyway) and then unmuting the global sound.

later edit #2: to set the number of devices edit /etc/default/cdemu-daemon

---

### Post by fermulator on 2009-05-16
TIP:  CDEMU isn't officially supported on Hardy, but it is on later releases.  An upgrade to your distro is recommended.

[https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)

---

