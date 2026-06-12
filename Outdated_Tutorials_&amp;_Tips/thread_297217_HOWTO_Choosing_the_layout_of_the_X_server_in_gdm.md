---
title: "HOWTO: Choosing the layout of the X server in gdm"
date: 2006-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by canard on 2006-11-10
**Introduction**
I have been trying since a long time to use my laptop with my LCD/CRT screen at work the easiest way, that is to say (ok i already regret to write this) as under MS windows. 

**Warning**
This How-to uses different scripts which i did not write myself, so all the credit for them should go to Alexander Zimmermann who has published them under the GPL Licence (I have just modified one of them to use Xorg, since they were designed for Xfree86). 

**[SIZE="4"]1. Assumption[/SIZE]**
I suppose that you have already set different layouts in your xorg.conf, that is to say you have different working configurations, for your laptop screen only and your laptop screen plus an external LCD screen for example.
that is to say you have defined two or more 
```
Section "ServerLayout"
        *your options*
EndSection
```
You should also define a default layout like this
```
Section "ServerFlags"
	Option		"DefaultServerLayout" "thelayoutyouwantasdefault"
EndSection
```

**[SIZE="4"]2. How it works[/SIZE]**
 - We are using a wrapper for the X server that will look for a layout name in the file /tmp/.xlayout and that will start the default X server with that layout option. If the file does not exist the default layout option will be used.
 - We are using the external program *xautolock* and launch it at gdm startup. *xautolock* launches an action when you leave the mouse for one second into one of the corners.
 - In that case an xterm window appears and launches a script that scans your xorg.conf file for ServerLayouts and let the user select one if it.
 - This selection is written to /tmp/.xlayout and the X server gets killed and is restarted afterwards from gdm with the new layout option.
 - As the user is logged in gdm kills *xautolock*

**[SIZE="4"]3. Software install[/SIZE]**
We need to install a few things, like xautolock, perl and xterm.
```
sudo apt-get install xautolock perl xterm
```

**[SIZE="4"]4. GDM config file patch[/SIZE]**
In order to use it we need to replace the default X server that is launched by gdm by the wrapper script. We need to edit the file gdm.conf
```
sudo gedit /etc/gdm/gdm.conf
```
replace the following lines
```

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true

```
by
```

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/local/bin/XLayoutSet -audit 0
flexible=true
```

**[SIZE="4"]5. The scripts[/SIZE]**
You will need four different scripts
```
    
    * /usr/local/bin/XLayoutChooser
    * /usr/local/bin/XLayoutSet
    * /etc/gdm/PostLogin/Default
    * /etc/gdm/Init/:0

```
you will find them in attachment.
```

tar xvzf /path/to/file/layoutchooser.tar.gz
cd layoutchooser
sudo cp XLayout* /usr/local/bin/
sudo cp Default /etc/gdm/PostLogin/
sudo cp :0 /etc/gdm/Init/

```
Now give root the execution permission on these files
```

sudo chmod u+x /usr/local/bin/XLayout*
sudo chmod u+x /etc/gdm/PostLogin/Default
sudo chmod u+x /etc/gdm/Init/:0

```

**[SIZE="4"]6. Test[/SIZE]**
Restart GDM by using another TTY or CTRL+ALT+BACKSPACE
when you see the login window put your mouse cursor in a corner of the screen for more than one second. A xterm window asks you to choose the layout and restarts gdm with it.

[SIZE="3"]*Enjoy*[/SIZE]:cool:

---

### Post by Dr. Moe on 2008-08-02
@Canard:

THANKS !!
EVER SO MUCH !!
This is by far the most elegant solution I've come across to the old issue of using a laptop in both single and dual monitor setup !!
The scripts are straightforward and efficient, _plus_ part of the beauty of it is that the scripts WILL adapt to any new server layout you'd want to define in xorg.conf.
In other words, once it's set up, it should be once and for all ; just add a new 'ServerLayout' section to xorg when you need to use different hardware, restart gdm, and that's it !

Just for info, have you posted this in a French forum as well for our fellow countrymen to enjoy ?

---

