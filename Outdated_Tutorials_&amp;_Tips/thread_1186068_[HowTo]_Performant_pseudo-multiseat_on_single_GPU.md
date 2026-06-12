---
title: "[HowTo] Performant pseudo-multiseat on single GPU"
date: 2009-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by bryonak on 2009-06-13
**[size="3"]HowTo: A well performing, full eye-candy, accelerated pseudo-multiseat setup on a single dualhead GPU.[/size]**

[b][color="blue"]
1. Introduction
2. Hardware specs
3. Goals
4. xorg.conf
5. Bugfixing (known issues)
6. Display Environment
7. Mouse Switching
8. VNC
9. Remote Control
10. Thoughts
[/color][/b]


**[size="3"][color="blue"]1. Introduction[/color][/size]**

Over the past weeks, I've tried to set up a multiseat configuration for my surf-station/beamer and have come across many hurdles and problems, which I've been able to resolve since then.
This guide tries to make it easy for my fellow humans to achieve a better understanding of multiseat techniques.
However it is not "newbie-friendly", but rather targeted at seasoned users (or determined newbies ;)) because it requires experience with the command line and the X server.
It is meant as a collection of knowledge you can adapt to suit your needs.

Hopefully someone will find time to implement automatisations of the whole process.


**[size="3"][color="blue"]2. Hardware Specs[/color][/size]**

A server/surfstation/media-center:
Athlon X2 (dualcore) CPU, 2GB RAM
GeForce 8400GS two-headed video card (DVI+VGA)
One 15'' LCD (1024x768 ) for surfing
One HD-ready beamer (1280x720)

Ubuntu 9.04 64bit Desktop


**[size="3"][color="blue"]3. Goals[/color][/size]**

The goal is to have a server that uses a LCD to act as a surf station, while at the same time powering a beamer in order to act as a theater.
All this in "native" performance, which means full 3D/OpenGL acceleration and Compiz turned on on the surf station, to impress on casual visitors ;)
Because there is no input separation like with true multiseating, I added the "pseudo" in the title. More about that later.

True multiseating, which means completely independant sets of monitors, keyboards and mice using one computer, is much easier to achieve with two graphics adapters, because you can start two distinct X servers on each video card.
Having one card that presents two adapters to the system (lspci) also works well.
This is however out of the scope of this HowTo, since my card only presents one adapter.

Many multiseat setups today are realised with Xephyr, a "nested" X server on top of an already running one. While being quite easy to setup and powerful in terms of features, the abstraction has one major drawback: performance.
I've tried Xephyr for my purpose, but HD movies were unwatchable with my hardware because of stuttering and tearing.

I have to add that this guide is written for GNOME, but most things should apply to other window managers aswell.
It is also written for a Nvidia GPU, but apart from the fine tuning parameters in xorg.conf's Device section, everything should be portable.


**[size="3"][color="blue"]4. xorg.conf[/color][/size]**

Attach both monitors to your computer and boot it.
Download my xorg.conf from the attachment and try to adapt as much as possible. Obviously you might have to change the driver, the PCI BusID (see *lcpci* for that), the meta modes and monitor resolutions to match your hardware.
Save the changes and restart X. After logging in, both monitors should show a desktop.

The most important part in the xorg.conf is the ServerLayout
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1025 0
EndSection
```
My Screen0 has a width of 1024 pixels. Screen1 is right of it, but not accessible with the mouse, because Screen1 starts with an offset of 1025 pixels: there is a "1-pixel barrier" which the mouse can't cross.
Set the x-offset of Screen1 to 1024 (or whatever the width of your Screen0 is) and restart X. Now you should be able to move the mouse over the right edge to the other screen.
We will work with that setup for now, but revert to the pixel barrier later.


**[size="3"][color="blue"]5. Bugfixing (known issues)[/color][/size]**

There are two bugs with Ubuntu 9.04 Jaunty which will hopefully be resolved in 9.10.

If you use Compiz and your Screen1 has a bigger resolution than Screen0, you will notice that the desktop on the second monitor is capped to the resolution of the first.
This glitch can be resolved with the gconf-editor:
apps -> compiz -> general -> screen1 -> options
Create a boolean called "detect_outputs" and set to FALSE
Create a list called "outputs" and make this entry: 1280x720+0+0
The "outputs" list entry should match the resolution of your second monitor.
Restart X.

The second bug is with the gnome-panel, which seems to get confused when launching applications from the second screen.
Visit the [bug report]("https://bugs.launchpad.net/gnome-panel/+bug/256041") and download Andreas Moog's patched version of gnome-panel from the comments.

Another tricky point:
When playing high-resolution videos on the second monitor, you want to get the maximum performance.
Especially when using [Moovida]("http://www.moovida.com/"), Compiz may cause little slowdowns or stuttering, so I recommend to turn it off on the second screen.
It's not needed anyway since Moovida is fullscreen and provides enough eye candy itself.
Do this by saving this into a script file and making it executable:
```
#!/bin/bash
sleep 3 && compiz --replace --sm-disable --only-current-screen --display :0.0 && sleep 2 && killall gnome-panel &
```
Then add it to your startup applications and restart X.
The second screen should fall back to Metacity, the sleep is there so that Compiz doesn't get replaced by something loading after it.
The problem with this solution is that the gnome-panel might behave a bit strangely: for me, it's not possible to minimise applications by clicking on their panel entry in the second screen. Minimise by window button or keyboard shortcut works well, and everything else too.

Besides, you can delete all gnome-panels on Screen1 and use something else instead, be it another panel or Cairo-Dock, AWN, ...


**[size="3"][color="blue"]6. Display Environment[/color][/size]**

When you start applications from the gnome-panel on both monitors, they will land in the first monitor. It happens because the panel thinks it's on Screen0, which is true because there is only one process instance of the panel and it originates there.

With the *env* command, you will see that the DISPLAY variable is in the format :X.Y, where X is the video adapter and Y the screen. Executing *env* on your first monitor will show :0.0, the second will show :0.1.
In order to get a terminal on the second monitor, type this into a shell:
```

DISPLAY=:0.1
gnome-terminal

```
You can also move the mouse to the second screen and press Alt+F2.

Since this is too cumbersome to do every time, we'll make some launchers on the second screen (for example, right click on the panel and "add to panel" an application launcher).
Applications that support a display option can be forced on the second screen by adding "--display=:0.1" to the launcher command. These include gnome-terminal and the file managers PCManFM and Thunar (Nautilus might have some issues because it manages both desktops at the same time).

For all other applications, we'll have to cheat a bit and use a tool that sends the applications to the second screen:```
sudo aptitude install dtach
```
Then save this script as /usr/bin/forcescreen1 and make it executable:
```
#!/bin/bash
DISPLAY=:0.1
dtach -n /tmp/dtach$1 $1
```
Now you can prefix your launchers with this, for example "forcescreen1 rhythmbox".


**[size="3"][color="blue"]7. Mouse Switching[/color][/size]**

Now set the x-offset in the xorg.conf back to 1025 (or your corresponding value) in order to reintroduce the mouse barrier.
You can skip this step if you are happy with the wrapping, but I like to hit an edge when I expect it, so we need a way to assign the mouse to one screen or another.

Download the dualscreen-mouse-utils-0.5.tar.gz from [David Mohr's page]("http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils") and compile the mouse_switchscreen.c (just type make).
You will have to have at least the following packages installed: xserver-xorg-dev, libx11-dev, libxtst-dev.
Then assign it to a keyboard shortcut -> now you can happily switch between the two monitors.


**[size="3"][color="blue"]8. VNC[/color][/size]**

Controlling the beamer from a notebook you have on your lap is much more comfy than having to go to the server's keyboard/mouse.
I recommend autostarting x11vnc with the following options:
```
x11vnc -forever -nofb -display :0.1
```
The nofb option will turn off the graphic transfer and only transmit mouse/keyboard data. You can remove it and enable frame transfer, but then I strongly suggest reading the x11vnc man page for performance optimisation techniques.

Connect to the VNC server with Vinagre (GNOME's default VNC viewer) or the vncviewer terminal app. The address should be "yourserverIP:0".
x11vnc will show you the second screen, but send the keyboard/mouse input initially to :0.0, so you have to use your mouse switching shortcut inside the VNC session.

Note that one can not control Screen0 (the LCD in my case) and Screen1 (the beamer via VNC) at the same time, hence the "pseudo-multiseat".
But it's perfectly possible to switch control at any time (start a movie on Screen1 and then give control to Screen0).

If you really want independant VNC, start Xephyr on Screen1. It will then be available as :1.0.
If you want an independant VNC *and* good performance, I can only recommend buying a second video card.


**[size="3"][color="blue"]9. Remote Control[/color][/size]**

For those who don't to use a laptop, there's another alternative: your HID capable bluetooth cell phone.
These include most Sony Ericssons and lot's of others (can't tell exactly though because I have mainly SE phones to test).

All you need is to plug a USB bluetooth dongle (quite cheap nowadays) into the computer and...

1. Edit the Local device class section in your /etc/bluetooth/hcid.conf to look like this***:
```
        # Local device class
        class 0x520204;
```
2. Restart bluetooth with ```
sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start
("restart" didn't work for me)
```
3. Select "always visible" in the bluetooth preferences (System -> Preferences -> Bluetooth)
4. Search for your phone and connect to it in order to set a mutual passkey.
5. On your mobile phone, select the "bluetooth remote control" option (either in Organiser or Entertainment), choose the device name (which you set in the bluetooth preferences of your computer) and confirm the request on the PC.

*** If you have no hcid.conf, take the one from the attachment.


I have not yet found a way to force bluetoothd to send instructions only to Screen1, so the same control limitations as with the VNC apply.
Suggestions on how to do this are very welcome!

You can use an infrared remote control via LIRC as well, but I can't elaborate on that since I don't have a receiver.
Another option is to use bluetooth control plugins for various media players (remoteJ or anyremote for example), but keep in mind that those often require installation of java applets to the phone.


**[size="3"][color="blue"]10. Thoughts[/color][/size]**

This HowTo is a summary of my personal solution, and I hope someone finds it useful.
It isn't true multiseating in the traditional sense, but allows for more or less independant use of the screens.
If I could get the bluetooth server (bluetoothd) to send instructions only to the beamer, it would almost qualify as a true multiseat system since you could use the mouse for surfing independantly from the remote control for playing movies.

As discussed in another thread, there might be a better (more like true multiseat) setup using the ratpoison window manager. A Belgian enterprise sells such systems and claims full video performance, which implies that they achieve input separation by launching Gnome within, as seen in a comment reply, ratpoison instead of Xephyr.

What I would really like to see is some organised effort to improve the multiseat setup on Ubuntu!

---

### Post by bryonak on 2009-06-13
Slightly improved the general wording and expanded sections 9 and 10 a bit.

---

### Post by Sugi on 2009-06-27
Great howto.  Thanks.  To anyone out there that is reading this thread with a dual-monitor setup.  The mouse-switchscreen is a MUST.  

Starcraft + mouse-switchscreen + dual-mointors = Not a problem

Sugi

---

### Post by freakalad on 2009-06-30
very nice!

I've been looking at [doing something similar myself]("http://ubuntuforums.org/showpost.php?p=7098005"), but throwing in remote ssh-X to a KVM VM client in the mix

Hope this'll become a standard feature in a future release (since it's a VERY powerful feature to be had by altering a couple of lines)

---

### Post by bigalanisfan on 2009-07-28
Is it absolutely impossible to create a real multiseat system with a videocard presenting only one adapter? I think that overlay limitations of the card can make it harder. But impossible?

---

### Post by kacperpl1 on 2009-09-18
The problem is to get one gpu multiseat with acceleration because when u create something like host X session and split it into two xephyrs or xnests only host session has dri and glx enabled. Its a problem that everyone tries to overcome and for now i think the only one who did that doesnt want to share his knowledge for free...(see multiseat channel on youtube, multiseat.be)

---

