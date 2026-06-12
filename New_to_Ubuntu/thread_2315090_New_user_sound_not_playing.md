---
title: "New user sound not playing"
date: 2016-02-26
forum: New to Ubuntu
---

### Post by kali3 on 2016-02-26
Lubuntu: 15.10
Speakers/soundcard
Sound card: m-audio audiophile 24/96

can  anyone explain to a complete lubuntu novice how to get sound, recently  installed lubuntu 15.10 but cannot get  any sound working

---

### Post by trag on 2016-03-07
Install Ubuntu Restricted Extras, Pulseaudio Volume Control
good luck
Trag

---

### Post by sandyd on 2016-03-07
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1110830](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1110830)

Seems to be dead through pulseaudio, may still work through ALSA.

---

### Post by trag on 2016-03-08
Question: do you have "gstreamer" installed on your machine? I copy/pasted this from another help forum. 

[COLOR=#111111][FONT=Ubuntu]Lubuntu shares many components with XFCE. My suggestion would be to use the XFCE4-Mixer. This still gives you a lightweight solution compatible with the lxde ethos.[/FONT][/COLOR]
[h=3]to install[/h]sudo apt-get install xfce4-mixer gstreamer0.10-alsa
[COLOR=#111111][FONT=Ubuntu]This installs the following limited number of xfce packages:[/FONT][/COLOR]
exo-utils libgarcon-1-0 libgarcon-common libwnck-common libwnck22 libxres1 xfce4-mixer xfce4-panel
[h=3]to run[/h][COLOR=#111111][FONT=Ubuntu]Type xfce4-mixer in a lxterminal. In Options, in the Auto-Mute Mode drop-down menu, select "Disabled."

might be useful 
good luck
tragic

[/FONT][/COLOR]

---

