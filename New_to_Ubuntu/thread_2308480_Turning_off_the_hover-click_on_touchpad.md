---
title: "Turning off the hover-click on touchpad"
date: 2016-01-03
forum: New to Ubuntu
---

### Post by Kari_Leppanen on 2016-01-03
Hi,

I am re-posting this because the old solution: [http://ubuntuforums.org/showthread.php?t=1186015](http://ubuntuforums.org/showthread.php?t=1186015) doesn't work in newer Ubuntu versions. I am using Ubuntu 14.04 on Acer Aspire laptop.

Problem was that when placing a cursor on a panel, it started to create clicks even when nothing was over the touchpad, very annoying. Turning menus on and off rapidly or opening several items of an application at once when clicking on them. (Strangely this only occurred on panels, not on desktop or on links in a browser.)

The solution was to edit: ```
sudo gedit /etc/X11/xorg.conf
``` and add a line: ```
Option "TapButton1" "0"

```
The problem with that solution is that the xorg.conf doesn't exist anymore!

After doing some research I finally found the solution: Edit the file at: ```
sudo gedit /usr/share/X11/xorg.conf.d/50-vmmouse.conf
``` and add that same line: ```
Option "TapButton1" "0" 
```to the section "Inputclass'

After making this change and placing a cursor on a panel item, it still flickers, but doesn't cause multiple clicks. Now I am able to use "tap to click" again on touchpad.

Hope this helps if anyone else is facing this same problem.

Kari

---

### Post by DuckHook on 2016-01-03
```
sudo -H gedit
```you must us the -H flag or```
sudo nano
```Invoking graphical apps like *gedit* with *sudo* alone will lead to big problems.

---

### Post by Kari_Leppanen on 2016-01-03
Not so quickly! The problem is back! 

How do you change the status of a post back from a <SOLVED> state?

I did log off and then back again. I suppose that rebooting isn't necessary and just by logging on would cause the configuration files to be re-read.

Any help, please!

---

### Post by DuckHook on 2016-01-03
> **Kari_Leppanen said:**
> Not so quickly! The problem is back! 

How do you change the status of a post back from a <SOLVED> state?

I did log off and then back again. I suppose that rebooting isn't necessary and just by logging on would cause the configuration files to be re-read.

Any help, please!Even though xorg.conf is no longer needed and is not created by default, you can still create one manually and it will override all initial settings. Ergo, try the old fix. It should still work.

---

### Post by Kari_Leppanen on 2016-01-03
Rebooted to a recovery mode: ran command ```
X -configure
``` in a root shell. Got an error: "could not create lock file in /tmp/.tx0-lock", hence xorg.conf.new was not created into the /root folder. What now? How to create the xorg.conf file into the /etc/X11 directory?

Is this (touchpad) a hardware problem? This is a new laptop ACER Aspire. I didn't have this problem in my old Acer Extensa laptop. And I only used Windows on this laptop to partition the hard drive and burn Ubuntu to a DVD and install it. Are there drivers available for Ubuntu for this touchpad anywhere?

Oh, btw I am running Gnome classic desktop, gnome-session-fallback.

Feeling frustrated #-o

Kari

P.S. Just double checked, there was no /tmp/.tx0-lock file in there when running that X -configure command in recovery mode. Also, booted to Windows. No problems with touchpad there. So this must be a problem with Linux drivers or the gnome panels.

---

