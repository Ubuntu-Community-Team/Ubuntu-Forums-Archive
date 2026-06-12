---
title: "Console Text Displayed on Shutdown/Logoff"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by Landen on 2014-07-25
Hi,

Instead of a nice high-res Ubuntu logo for a shutdown animation, I am greeted with this ugly console text that flashes ever so briefly before shutting down. This does nothing to impact performance, but it is annoying. Anyone have any idea how to fix this?

---

### Post by grahammechanical on 2014-07-25
No.

What your are seeing is Linux after the desktop environment has been shut down. Things might change by the release of Ubuntu 16.04 when Ubuntu will have replaced the Xserver with the Mir display server. Which will also replace Plymouth, LightDM and Compiz. But we just have to wait and see.

This is what we get when using a free (as in not paid for) open source operating system made up of many different software projects written by different programmers and all stitched together in some remarkable fashion. It is a wonder it works at all. Well, no. It is all down to a lot of hard work by many people.

Regards.

---

### Post by Landen on 2014-07-25
I have since figured out that it's a problem with my drivers.

After switching from my NVIDIA binary driver - version 331.38 from nvidia-331 to X.org X server -- Nouveau display driver from xserver-xorg video-nouveau, everything worked fine. 

...Any solution at all?

---

### Post by kira-yamato-2008 on 2014-07-26
Post your system specs, and get a more up-to-date NVIDIA binary driver. You may wanna check out my thread on my video flicker and tearing issue [here]("http://ubuntuforums.org/showthread.php?t=2236278"). Some of the links and info you may find useful. I've had no end of trouble trying to get the Nvidia binary drivers functioning properly on my machine.

---

### Post by Rob Sayer on 2014-07-26
Even if there are no problems with drivers it's quite likely you'll still get text messages on shutdown.  As post #2 said, a linux system will revert to text bases mode when powering down because it shuts down the GUI program before final halt.  The DE gui is just another app to linux.

As long as there aren't any error messages there you have no problems.  Relax.

---

### Post by Landen on 2014-07-26
After a night of updating and switching drivers, I got back on my Nvidia driver with a regular shutdown and startup screen. Woo!
Only problem is, the resolution is 640x480 and my 1920x1080p screen isn't supported. So, looks like I'm stuck with this low res image of the Ubuntu logo. On the upside, startup and shutdown is fast... So I don't have to look at it's ugliness for long.
Is this the end of the road?

---

