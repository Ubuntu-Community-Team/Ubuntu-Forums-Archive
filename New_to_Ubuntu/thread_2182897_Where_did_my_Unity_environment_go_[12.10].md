---
title: "Where did my Unity environment go? [12.10]"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by ArlieS on 2013-10-22
I had a system running 12.10 Ubuntu, with Unity. It's a bit flaky, for which I'll blame the hardware vendor (lenovo). The flakiness usually manifests as display weirdness, showing up when I dock, undock, boot, or go into any suspended state. (I deal with this by configuring it to never suspend itself when docked, and only undocking when I want to nudge it out of a bad state, and very rarely rebooting.)

Last Friday the system had been running for approx. 60 days, which is about all Ubuntu desktop can handle without needing a reboot. I decided to install all the latest updates, then reboot. 

It came back flaky in a new way - Unity wasn't all there. I had menus on my windows (instead of on top of the screen), and no left-side-of-screen icon/menu bar (=? "dash"). IIRC, screen wasn't working either - no switching to another environment minus the broken GUI.   I managed to get a shell, by right clicking a document and selecting "open with... emacs". I used this to examine the mess, and didn't learn very much. 

Then, in a fit of frustration, I did "sudo apt-get install kubuntu-desktop" and "sudo apt-get install fluxbox" and rebooted. 

I now have a choice of window managers on login - but unity is not among them. The gnome-terminal application gives me a blank screen. Normal X things basically work, except for a lot of pain involving handling of multiple displays - not unusual for my flaky hardware, but kde's xrandr wrapper seems unusually brain damaged. (I got things _almost_ working right under fluxbox.)

What I want to know is where my Unity installation went? Did the "latest updates" involve destroying Unity? Does "apt-get install kubuntu-desktop" include an implied "apt-get remove" of unity? 

Related to this, is there a way I can re-establish unity as one of several choices of desktop environment? I don't much like Unity, but at least it's familiar - and it *had* a correct configuration for my external monitors, which I've so far been unable to create in the other two. At the moment, I'm running Windows on the laptop, and I'm more than a little unhappy about that. Any hints?

---

