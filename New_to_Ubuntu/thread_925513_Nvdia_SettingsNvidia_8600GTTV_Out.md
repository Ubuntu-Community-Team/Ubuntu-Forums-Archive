---
title: "Nvdia Settings/Nvidia 8600GT/TV Out"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Tumpster on 2008-09-20
Hey there, I need assistance in setting this up as I see I should be able to get my tv acting as a secondary monitor. I just want to be able to stream some movies across and music and what not but I need assistance in doing so. I'm utilizing the tv/s-video out on my card and a cable to match but I'm having troubles setting it all up. Anyone up for helping me out? Thanks!!! :)

---

### Post by graben3 on 2008-09-20
Go in synaptic package mamager and search for envy.

Check Envyng-Core, Envyng-gtk

Click the apply button

Then go in Application -> System -> EnvyNG

Click auto detect the nvidia driver for you...

Install

Then, once this is finished, reboot and go into 
Applications -> System -> NvidiaXServer Settings

And ...then its pretty simple, just activate your TV.

If you want the changes to be permanent (ie still there after reboot) youll have to edit your menu item for NvidiaXServer Settings and add "gksudo " before the actual command. To do that, lauch System -> Preferences -> Main menu

And find the item corresponding to nvidia, edit it and add the "gksudo " just before.

---

### Post by Tumpster on 2008-09-20
I've seen this here but don't see an option to select my tv. I've installed my drivers though Envy and have the settings tool setup but don't see the way to add it under listed monitors. I look under the "nvidiaxserver settings" and tell it to to detect but I get nothing but my main LCD monitor when I do. Any ideas?

---

### Post by willca on 2008-09-23
try installing nvidia-settings via apt-get and try it from the command line.

---

