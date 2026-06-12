---
title: "Gnome 3 is not compatible with ATI Catalyst Drivers"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by jasonwatkins on 2011-11-01
There, I said it :)

Well considering i've been trying for about 6 months to get the last few incarnations of the ATI Catalyst Drivers to work with *any* incarnation of Gnome 3 - and failing - then it stands to reason that Gnome 3 simply cannot be compatible with the Catalyst drivers.

Usually what will happen is that i'll install the distro - for the sake of this post, let's say i've installed this ..

[http://ubuntu-gs-remix.sourceforge.net/p/download/](http://ubuntu-gs-remix.sourceforge.net/p/download/)

The "remix" of 11.10 featuring the Gnome 3 environment as standard.

So i'll use the additional hardware wizard to find the drivers, it'll install them, i'll reboot and the top menu bar will completely glitch out and be unreadable - the text is replaced by graphical blocks.

So i'll remove the driver and try the other one (post release or something).  Then, the whole screen will just be a mess of graphical glitches.

So i'll re-install.  I'll download the 'official' catalyst drivers from the ATI website and install them.  I'll reboot and .. Gnome 3 will fail to load.  So i'll set the resolution for my monitor, I'll flip the "fallback mode" switch so that the next time it attempts to use the 'full gnome 3 experience'.  

But next time .. it doesn't.  It's locked into fallback mode.

You can repeat this general sequence of events for Fedora and OpenSuse as well.

It's only because I take a shadow image copy of my Windows installation that I can be bothered to keep trying these distros.

And before anyone thinks to ask, no i really don't want to use unity, the original gnome shell or KDE either.

I've googled for the various methods of installation for the ATI drivers and tried them all - nothing works. 

I've bought a brand new VGA to DVI lead for my monitor, which works perfectly (and has even improved the overall clarity of picture) and still nothing works.

So I can safely say, Gnome 3 is not compatible with the ATI Catalyst Drivers.

Rant over :)

---

### Post by verymadpip on 2011-11-01
Try the open source drivers.
No problems with them here.

---

### Post by jasonwatkins on 2011-11-01
I've never been able to find these mythical "open source drivers" or, for that matter, any instructions on how to actually configure them for use.

I'd gladly give them a punt if i could ..

---

### Post by gandaran on 2011-11-01
read this thread
[http://ubuntuforums.org/showthread.php?t=1859626](http://ubuntuforums.org/showthread.php?t=1859626)

---

### Post by coffeecat on 2011-11-01
> **jasonwatkins said:**
> I've never been able to find these mythical "open source drivers" or, for that matter, any instructions on how to actually configure them for use.

I'd gladly give them a punt if i could ..

Nothing mythical about them at all. They are what comes as default. I'm posting from an Oneiric system in a machine with an ATI Radeon HD5450 GPU using the default open source driver. Unity 3d/compiz works just fine, gnome shell (gnome 3) works just fine and gnome-session-fallback works just fine.

---

### Post by jasonwatkins on 2011-11-01
Hhmm .. i'm sceptical but i'm willing to give them a punt later on.  We'll see :)

Thanks for the information

---

### Post by jasonwatkins on 2011-11-01
Well what do you know .. it actually worked :)

I'm currently running full Gnome 3 with full 1440x900 desktop with the official ATI drivers.

Problem is though, it's glitching regularly enough to become a bit annoying. I'm currently playing some music with Clementine, as an example, and whenever the track changes the screen will screw up and graphically go all over the place for a second then it'll be ok again.

Sometimes it'll go to a point where the menu essentially crashes and re-starts as well.

But the very fact it's actually working with the drivers in *any* form is a bloody miracle :)

Anyway, i'll give it a re-install and remember not to tick "download non free updates" or whatever it's called so I can properly get the open source drivers installed and see where we go from there.

Thanks for the information again, I'm happy to have been proven wrong :)

---

### Post by cbowman57 on 2011-11-01
Try this from the command line, if it works add it to your ~/.profile
```
export CLUTTER_VBLANK=none
```

---

### Post by linuxaspirer on 2011-11-01
I have one question , I have ATI Catalyast installed, I have hooked my cpu to the HDTV. I am oin the highest resolution. But On the highest resolution there is a part of screen on vertically cut off.

I guess in windows we can increase the size of screen, but I could not find that in the ATI catalyst, can anybody help me regards to this.

Linux Aspirer

---

### Post by coffeecat on 2011-11-02
> **linuxaspirer said:**
> can anybody help me regards to this.


@linuxaspirer, please start your own thread and not tag onto another.

---

### Post by jasonwatkins on 2011-11-02
> **cbowman57 said:**
> Try this from the command line, if it works add it to your ~/.profile
```
export CLUTTER_VBLANK=none
```

Nice one, will do.  Thankyou.  I'm just going to have a go re-installing it with the OS drivers and see what happens but i'll certainly go back to what I did last night and try your suggestion as well.

---

### Post by cbowman57 on 2011-11-02
I'll be curious to know if you notice a difference.

Don't know what refresh rate your monitor runs at but you can edit the tweener.js to match it.
```
ClutterFrameTicker.prototype = {
    FRAME_RATE : 85,
``` (Default is 60)

---

### Post by jasonwatkins on 2011-11-02
Ok, i re-installed and tried to get the open source drivers working but couldn't quite figure out what I was doing - tried one method and still didn't have any way of forcing the 1440x900 resolution for my monitor.

so I used these commands ..

```
sudo /usr/share/ati/fglrx-uninstall.sh # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

from here ..

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577/comments/22](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577/comments/22)

and then installed the new ATI 11.10 Drivers from their website.

Added "export CLUTTER_VBLANK=none" to /etc/environment and rebooted.  Still saw some glitching, albeit not as much as last night.  So I enabled "tear free" mode in the catalyst control center and, as it stands at the moment, it seems to have completely eliminated the problem.

I'm just trying to replicate what I did last night for 10 minutes or so to see if it really has worked, but it's looking good so far.

---

### Post by cbowman57 on 2011-11-02
Try the export CLUTTER... in a terminal.  

There was a bug some months back that kept it from being read from environment, probably swatted by now but just in case.   If it helps & the bug still exists you can put it in .profile or .bashrc

Otherwise it sounds  like you've solved your problem, congrats. :)

---

### Post by jasonwatkins on 2011-11-02
> **cbowman57 said:**
> Otherwise it sounds  like you've solved your problem, congrats. :)

Thankyou.  You would not believe the grief i've had trying to get Gnome3 to work in all of these various distros.  

I did check the environment with "env" when I rebooted and CLUTTER is there and properly set.

I did just manually click on a song in Clementine though and the screen just went mad - looked like it threw up all over itself!.  That could just be a clementine thing or even a corrupted MP3 file because I tried manually clicking on a few others and nothing happened.

I'm going to play around with it for one more night and try some more things before i'm completely happy.  If i get to later on tonight with no problems then I'll make the big switch (again) and move over from Windows full time.

---

### Post by cbowman57 on 2011-11-02
Super, also good to know that bug is dead. :)

thanks

---

