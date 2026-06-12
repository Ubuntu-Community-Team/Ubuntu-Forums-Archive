---
title: "XConfManager application!"
date: 2007-02-04
forum: Programming Talk
---

### Post by WakkiTabakki on 2007-02-04
Hello everyone!
The XConfManager is a tool written in python for managing xorg.conf-files, it also has some basic editing capabilities.

The idea behind the XConfManager is this:
I use my laptop for a lot of different things, as a work computer, for presentations, as media player etc... 
So X is sometimes configured with TV-out, sometimes cloned display with a projector or with an external monitor (sometimes left and sometimes right of the lcd), I also have a few different keyboards and mice depending on where I am. 
Now, setting up X for each situation is a bit of a hazzle, right.
Enter the XConfigManager.

First, ofcourse, an xorg.conf need to be created for each of the different configurations. 
The application then helps managing those configurations. It does so by splitting the xorg.conf into two parts, one with the sections that are common to all configurations (such as module loading, fonts etc) and one with the sections specific for each configuration.

On the first start, XConfManager imports and splits the current xorg.conf and makes it the default configuration.

Current features (version 0.2)
* Basic editing capabilities 
* Automatic import of default xorg.conf
* Applying a configuration and automatic restart of X (optional)

Planned features:
* Bootup menu allowing to choose the X-setup during boot
* Scheduling configurations, e.g if starting the computer on a workday around 9 choose the work configuration
* Figure how to save a gnome session and be able to completely restore session after restart
* Test a configuration by starting a new X-server on a different VT


Note, this app is mainly aimed at easing management of multiple X-configurations on a computer. It's not intended as afull-fledged xorg-editing application, for that, look here:
[http://ubuntuforums.org/showthread.php?t=156243]("http://ubuntuforums.org/showthread.php?t=156243")


Please, try it and post any comments and remember, the app is still in its infancy so any input is appreciated! 

/N

---

### Post by Sokraates on 2007-02-06
This looks promising. Just what some of the more professional users need (at least the lucky ones, who can use Ubuntu at work). Thank you very much.

I will give it a try this weekend and post the results.

---

### Post by slimdog360 on 2007-02-06
It would be good for a usb install so people can use ubuntu (or whatever) on different computers.

---

