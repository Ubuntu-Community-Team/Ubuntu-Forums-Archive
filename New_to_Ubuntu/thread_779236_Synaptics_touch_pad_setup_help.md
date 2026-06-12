---
title: "Synaptics touch pad setup help"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by konradpiskorz on 2008-05-02
Hi, I'm running Ubuntu 7.10, just installed in a little bit ago.

I've managed to get my touchpad (an alps variety) set up almost perfectly.

Theres just two things I need to adjust.

1) Before when using the vertical touch pad scroll moving to the top or bottom corner would cause the scroller to continue scrolling automatically.  Are there settings to make this happen?  What are they?

2) Also tapping the touch pad as a click is extremely sensitive.  A lot of the time just scrolling trough a page I end up clicking on random things.  Is there a way to adjust this?  I've only been able to find ways to completely turning this feature off which i do not wish to do.

Thank you in advance

Konrad

---

### Post by reggie_mac on 2008-05-02
Im also a first time use, and have been playing with Hardy for about a week now, almost have a 'perfect setup' but a couple of nuances to get through, I'm wondering if there is a way to turn the touch pad off when a mouse is installed, i know i can can disable it completely but that turn into an issue if i forget to turn it back on before i unplug my mouse.

installed xserver-xorg-input-synaptics v0.14.7

are there any other packages i need to install?

EDIT

just install gsynaptic package and its given me more options, but not yet what im after.

**Konrad**, i think this is the package you are looking for as it givs a whole bunch of options for setting up a touch pad.

---

### Post by konradpiskorz on 2008-05-02
I'm just looking for straight xorg.conf vars I can toss in under the synaptics touchpad area.  I've tried gsynaptics and it doesn't work properly for me.  From my understanding, the reason is I have an ALPS touch pad, not a synaptics touchpad.  The synaptics drivers work but require manual set up on ALPS touch pads from what I have read.

---

