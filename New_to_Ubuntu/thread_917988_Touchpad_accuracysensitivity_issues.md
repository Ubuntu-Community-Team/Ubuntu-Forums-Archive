---
title: "Touchpad accuracy/sensitivity issues"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Meetloaf13 on 2008-09-12
Hello all,

I have been fighting w/ my touchpad since I installed Ubuntu 8.04 x64.

I wish it would just work like it does in Vista or XP, but as long as I can configure it properly, I will be happy as a clam.

My biggest beef, when trying to make small precise movements, it get's really jumpy. I have tried messing with the touch sensitivity of the touch pad (how sensitive it is the pressure you apply), and the normal sensitivity option, as well as the acceleration...to no avail.

Another problem I have that is probably related, is that sometimes the touchpad doesn't respond to my 'touch'...is it giving me the silent treatment? :)

I am running a Dell Vostro, if anyone with a similar setup could send me your xorg.conf (I think that's where they reside) settings or provide any suggestions, I will be most grateful.

Thanks!

---

### Post by Tyler H on 2008-09-12
What model of the Vostro. I'm running the 1000 series with 8.04 and everything works flawless.

---

### Post by Meetloaf13 on 2008-09-12
I've got the Vostro 1500...I think the only difference b/t mine and yours is yours has the AMD chipset as opposed to the Intel.

Would you mind posting the contents of your xorg.conf relating to pointing devices?

---

### Post by k33bz on 2008-09-12
sudo gedit /etc/X11/xorg.conf


ADD THESE LINES BELOW THE MOUSE SECTION:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
EndSection


ADD THIS LINE IN THE SERVERLAYOUT SECTION:

InputDevice "Synaptics Touchpad"

---

### Post by bobnutfield on 2008-09-12
If your touchpad is listed in xorg.conf as a Synaptics driver, then there is a GUI app that you can adjust you touchpad with called GSynaptics and it is in the repos.  You can install with:

> sudo apt-get install gsynaptics

---

### Post by chip616 on 2008-09-18
k33bz:

The touchpad on two of my machines are just WAY too sensitive, sending the cursor off into another portion of a document while I am typing if I happen to even brush the touchpad with my thumb.

I struggled with this for over 6 months with Fedora 8.  In Fedora 8 there is no touchpad section in xorg.conf.  I tried adding a touchpad section into xorg.conf on Fedora 8, and it was ignored.  I never did find a solution in Fedora 8.

I am now running Kubuntu 8.04, and this worked just fine on both my daughter's Vostro 1700, and my Vostro 1710.  On both machines, all I had to do was add the shmconfig option (everything else was already there), and install gsynaptics (there appears to be no KDE equivalent to the Gnome app).  As we both run KDE, I added gsynaptics to the menu structure as well.

So, I can confirm that this solution works, and this terribly annoying oversensitive touchpad is now much more dormant.

Frank.

---

### Post by sporkubus on 2008-09-28
I installed gsynaptics as suggested, adjusted the sensitivity and disabled clicks, and it worked great. Except that at some point in my session, all of these settings randomly revert to the way they were before and I have ultra-sensitive mouse clicks again that make it almost impossible to type.

---

### Post by gazazello on 2010-08-11
gsynaptics worked as a sharp! 

Thanks guys!

---

