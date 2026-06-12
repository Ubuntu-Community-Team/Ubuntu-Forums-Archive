---
title: "Synaptic settings don't work in Intrepid"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by GreenVoid on 2008-11-12
Hello everyone,

In Synaptic -> Settings -> Preferences -> General I ried to set 'Reloading outdated package information' to 'Automatically' instead of 'Always ask', which was the default setting after a fresh install.

Synaptic simply froze. I force-quit it and tried again. And again. And again... Every time the same freeze.

Then I tried to find the relevant config file but I couldn't.

So does anyone have any suggestions?
The best would obviously be to solve it in Synaptic, but a config trick would do, too.

---

### Post by laket on 2008-11-19
I have the "same" problem with unsetting the network proxy in preferences in synaptic. after pressing apply synaptic freezes. even waited an hour to see if it comes back to live, but no chance, one has to kill the application.
searching forums and google.com/linux didn't help either.

for anybody with the same or similar problem to synaptic freeze or crash:
there is a synaptic.conf file in /root/.synaptic/ which u can only access with root (no sudo here!) here u can manually configure ur synaptic preferences! once saving it u have the preferences set the way u would have done it with the gui.

---

