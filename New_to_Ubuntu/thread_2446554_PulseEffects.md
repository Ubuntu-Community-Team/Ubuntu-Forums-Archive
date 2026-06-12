---
title: "PulseEffects"
date: 2020-07-02
forum: New to Ubuntu
---

### Post by nixpix76 on 2020-07-02
Hi!

[COLOR=#ff0000][SIZE=4]EDIT. Nevermind. After a reboot it works :) I thought reboots were a thing of the past, moving from MS to Linux :D[/SIZE][/COLOR]

I'm not sure if this is the correct forum to ask, but I have to start somewhere :) I am completely new to Linux, been running it for a few days and liking it so far. I am running Kubuntu 20.04. I am having issues getting the equalizer working in PulseEffects. It simply wont activate. All other filters are working. I checked the [https://github.com/wwmm/pulseeffects](https://github.com/wwmm/pulseeffects) for requirements to run all the filters. I think I have all stuff needed correctly installed, but since I am new, its a bit confusing still ;) Googling the issue points to "Linux Studio Plugins" being the one specifically needed for the equalizer. I have these installed:

lsp-plugins-doc/focal,focal 1.1.15-1~focal1 all
lsp-plugins-jack/focal,now 1.1.15-1~focal1 amd64 [installed,automatic]
lsp-plugins-ladspa/focal,now 1.1.15-1~focal1 amd64 [installed,automatic]
lsp-plugins-lv2/focal,now 1.1.15-1~focal1 amd64 [installed,automatic]
lsp-plugins-vst/focal,now 1.1.15-1~focal1 amd64 [installed,automatic]
lsp-plugins/focal,focal,now 1.1.15-1~focal1 all [installed]

What I have done so far is: Installed PulseEffects through Discover. Installed what I think is the correct "dependancys" through Muon Package Manager. And I also added the repo "[COLOR=#333333][FONT=Monaco]ppa:mikhailnov/pulseeffects",[/FONT][/COLOR] and did an update/upgrade. But the EQ refuses to activate. Anybody out there that can help me please?

[COLOR=#333333][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by uninvolved on 2020-07-02
You possibly could have avoided the reboot by stopping and restarting pulseaudio.

---

