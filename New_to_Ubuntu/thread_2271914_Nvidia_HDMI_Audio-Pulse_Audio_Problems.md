---
title: "Nvidia HDMI Audio-Pulse Audio Problems"
date: 2015-04-02
forum: New to Ubuntu
---

### Post by enzodad on 2015-04-02
Hello, okay im a noob at this so im sorry for any confusion

I have a Nvidia GT 610 GPU i just installed because linux hates my radeon hd6450 lol anyway---

Driver install with lost of swearing :) 

BUt no DTS-HD Dolby TrueHD passthrough in Kodi.....so i uninstalled Pulseaudio and BAM it works.. WOOT but now i can not get audio to work outside of Kodi i skimmed through about 3HRS worht command lines forums and i can not get audio...inside Kodi all audio works...outside nothing.

Is there guide for dummies to get this to work....
i installed everything i could find for alsa lol and nothing works at a loss here about to go back to horrible windows

---

### Post by dino99 on 2015-04-03
pulseaudio is what ubuntu use; so if you have removed it you mostly break the sound system

---

### Post by SeijiSensei on 2015-04-03
If you restore PulseAudio, install the **pavucontrol** package as well.  If you enter the command "pavucontrol &" in a terminal window, you should have complete control over all audio inputs and outputs.

---

### Post by enzodad on 2015-04-16
did that- seems Linux hates Radeon HD 6450 & Gforce GT610----how many graphics cards do i have to go through lol

Not sure why i cant use ASLA and not pulse.....Seriously im stuck using windows because this stuff..i use PC for one thing--Media---
HD/BluRay movie rips and watching streams online/Kodi

---

### Post by Vladlenin5000 on 2015-04-16
I never had any issue with any GT6xx in any combination with the nvidia drivers.

---

### Post by enzodad on 2015-04-16
well im happy for you. but that dosent help, is your card integrated or not. How is it configured etc what settings. NEW user here i can disable Pulse but then i have no sound out side of a program Like Kodi that allows passthrough

---

### Post by Geoffrey_Arndt on 2015-04-16
Sometimes sound problems can be traced back to user and file permissions.   My knowledge of Unity is somewhat limited, but I know in KDE and other DE's in Ubuntu, you can access the user and ID which groups he belongs to (e.g., audio and pulse), and also what apps are linked to group permissions.    Probably a way to do this via CLI but am not familiar with it, perhaps someone with more experience or knowledge can advise.

---

### Post by Geoffrey_Arndt on 2015-04-16
Sorry - network glitch . . duplicate post.

---

