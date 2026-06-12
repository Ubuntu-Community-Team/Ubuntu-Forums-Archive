---
title: "Screensaver problem (XScreenSaver vs Gnome)"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-18
Hi,

The screensaver seems to have issues.

```
The GNOME screensaver daemon appears to be running.
It must be stopped for XScreenSaver to work properly.
Stop the GNOME screen saver daemon now?
```

Once I press OK, I get this:

```
The XScreenSaver daemon doesn't seem to be running
on display ":0".  Launch it now?
```

However this doesn't seem to solve it.

I have found this thread here from 2006:

[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

Not sure if its still the case after 6 years.

Any comments?

Thanks,

---

### Post by mutap on 2012-05-18
Default, Gnome screensaver is activated.
You installed XScreenSaver, and you tried to start it.
Before that, Gnome screensaver must be stopped.
And then you lauched XScreenSaver.

So there is no issue, this is correct behaviour. 

If you want to remove Gnome screensaver(in order to start XScreenSaver at boot time) to this

> sudo apt-get remove gnome-screensaver

After that go to startup aplications and add
> xscreensaver –nosplash

---

### Post by Houmie on 2012-05-18
> **mutap said:**
> Default, Gnome screensaver is activated.
You installed XScreenSaver, and you tried to start it.
Before that, Gnome screensaver must be stopped.
And then you lauched XScreenSaver.

So there is no issue, this is correct behaviour. 

If you want to remove Gnome screensaver(in order to start XScreenSaver at boot time) to this



After that go to startup aplications and add

Thanks for your reply. Which one is better to keep? Gnome or XScreenSaver?

Thank you

---

### Post by mutap on 2012-05-18
Well, I like XScreenSaver and I use it, but it is just a matter of taste.
Try Gnome screensaver, try X, and choose what you like better. ;)

---

### Post by Houmie on 2012-05-18
> **mutap said:**
> Well, I like XScreenSaver and I use it, but it is just a matter of taste.
Try Gnome screensaver, try X, and choose what you like better. ;)

It seems to me, I can't set the gnome screensaver. All it does is just blanking the screen.  I think thats why everyone is going for X-Screensaver. :-\

---

### Post by 1976MrEMan on 2012-08-04
I've uninstalled the gnome screensaver daemon, and added xscreensaver to the startup applications, but i still have to manually start xscreensaver upon boot. i've followed instructions from multiple forums and pages, and most can't be done due to error messages, the rest just don't work. I have even tried the steps listed in this thread with no results. Does anybody know what's going on here?

---

### Post by Toz on 2012-08-04
> **1976MrEMan said:**
> I've uninstalled the gnome screensaver daemon, and added xscreensaver to the startup applications, but i still have to manually start xscreensaver upon boot. i've followed instructions from multiple forums and pages, and most can't be done due to error messages, the rest just don't work. I have even tried the steps listed in this thread with no results. Does anybody know what's going on here?

The command is actually:
```
xscreensaver -no-splash
```
...(there's a typo earlier in this thread).

If that still doesn't work, have a look at the .xsession-errors log file in your home directory (the file is a hidden file) for some information on what may have gone wrong.

---

### Post by 1976MrEMan on 2012-08-04
I got it, and yes, it was a typo. Everyone note the space between xscreensaver, and -nosplash. Thanks, Toz

---

### Post by Psil0cybin on 2013-04-19
Thanks helped me today!

---

### Post by alecz20 on 2013-06-13
> **Houmie said:**
> It seems to me, I can't set the gnome screensaver. All it does is just blanking the screen.  I think thats why everyone is going for X-Screensaver. :-\

On some systems Gnome screensaver fails to turn off the display, at most it will blank the screen, but it will not turn it off.
I think there is a bug somewhere but I can't find it now.

XScreensaver does not suffer from this bug because it is using **xset **and **DPMS **and such.

---

### Post by GTiBanshee on 2013-07-17
This is my very first post in a forum and my very first post in the Ubuntu forums, plus I am working on my very first installation of a Linux system.  So you can see I'm breaking some some new ground on many fronts here so any help or advice for someone like me, even outside my question, would be much appreciated!

Here's my question, I have been trying, and failing to activate the screen saver on my Ubuntu 13.04 distro for the past few days, installed just a few days ago.  A little history... I've built two desktop computers, both with Windows, I have two laptop Macs, My wife and I have iPhones, and I have been studying EE.  I know it's not vital to have a screen saver but it's nice if I walk a way from my computer there's pretty things dancing around my screen instead of just black.  That's what is happening now just black...  If I go into system tools I can find a there is a section for appearance, but no screen saver.  Brightness & Lock has the settings for screen off and lock but again no screen saver.  Nowhere ells is there a setting that should contain a screen saver, I looked anyway.  I searched for it using the Ubuntu search, I tried looking for it in the Ubuntu Software Center.  Then I found this forum posting, and I searched the Ubuntu Software Center for the xscreen saver, and found it... but wouldn't you know it I couldn't download it and install it.  So I thought I've used the sudo apt-get command before I know it's safe (I realized as I was tying this safe is a relative term, I know that the command "sudo" can get me into allot of trouble if not used properly), and I know the xscreen-saver is not a malicious program b/c I saw it in the USC, so I tried that, I went to my terminal and typed in sudo apt-get xscreen-saver, this is what I got:

[COLOR=#ff0000]sudo: unable to open /var/lib/sudo/*********/0: read-only file system
E: invalid operation xscreen-saver

[/COLOR]
So then I thought maybe I needed to be signed in as root so I typed in sudo su, and repeated to processes and again it didn't work.  My next thought was that I might not need the "-" so I took that out and tried again, but that still didn't work.  I'm not to picky with my screen saver, I don't even know what gnome, xscreen-saver, or the default Ubuntu 13.04 (if one exists) has to offer.  I would just like to hae something to start off with, and then later on I can get more picky about which one I want.


GTiBanshee

I'm running:
Intell i7 Quad Core 3.2 Ghz
EVGA X58 Motherboard
EVGA Nvida GTx480
WD 2TB
Intell 128 SSD

---

### Post by alecz20 on 2013-07-17
The correct syntax would be:

```

sudo apt-get install xscreensaver

```

Alternatively, you can use Synaptic Package Manager to search for individual packages and install them. I find it much easier to find package names like that (compared to Software Center)

Although on later Ubuntu releases, I think you first need to install Synaptic (:-&)

---

### Post by GrouchyGaijin on 2013-07-17
Hi Guys,

I've been using xscreensaver for a long time, but yesterday I noticed that the xscreensaver is not starting a boot.

This is despite having 

```
xscreensaver -no-splash
```

in my list of start-up applications.

Has anyone else had this happen?
I'm on Ubuntu 12.04

---

### Post by Buntu Bunny on 2013-07-18
> **alecz20 said:**
> 
Although on later Ubuntu releases, I think you first need to install Synaptic (:-&)

That's correct. Happily it's in the Software Center.

---

