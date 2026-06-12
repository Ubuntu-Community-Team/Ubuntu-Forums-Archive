---
title: "No Sound, worked previously"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by goldenbough on 2008-05-28
I am running 8.04 (Hardy) and am having some difficulties with the sound operation.  The sound has worked before through this OS yet not now; I don't know what I did to get to this point!  When I switch over to Windows the sound works without any issue.

---

### Post by sayakb on 2008-05-28
At a terminal:
```
sudo apt-get install linux-backports-modules
```

---

### Post by goldenbough on 2008-05-28
No dice.  That command did not work through the terminal.  I went through the synaptic package manager, and supposedly I installed through there, yet I still am not getting sound.

---

### Post by markbuntu on 2008-05-28
Try going to System/Preferences/Sound and changing everything to ALSA instead of automatic.

---

### Post by goldenbough on 2008-05-28
Nothing, with that change.

---

### Post by iaculallad on 2008-05-28
> **goldenbough said:**
> I am running 8.04 (Hardy) and am having some difficulties with the sound operation.  The sound has worked before through this OS yet not now; I don't know what I did to get to this point!  When I switch over to Windows the sound works without any issue.

What audio card are you using?

Code:

```
lspci
```

---

### Post by Maestro23 on 2008-05-28
Might want to check alsamixer. In terminal:

> alsamixer

Make sure nothing is turned down or muted.

---

### Post by goldenbough on 2008-05-28
Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

---

### Post by markbuntu on 2008-05-28
Ok, try this, go to System/Preferences/Sound and just fool around with the settings until something works.

There are also a few other things that can make this problem. If you downloaded any pulseaudio or xmms dependent packages they will use those managers to take over control of your sound card. The solution to that is to open synaptic and search alsa and get the wrappers for pulseaudio and xmms and anything else you think you need so they all use alsa. If you have hydrogen or any DJ or mixing tool they probably use jack so you need to get jackcontrol and set it to use alsa or jack will shut out everything else semi permanently since jack does not always close when you close the app.

If you are live DJing or realtime mixing or recording you should use jack connected directly to the sound card to reduce latency. You can kill jack with jackcontrol when you are finished.


The problem here is that linux offers a zillion ways to use your sound card and they all will take complete control and shut out the others and make apps that depend on them unable to use the sound card and fail. 

The solution is to decide on one sound manager to control the sound card and make all the others go through that one. So far I have found that ALSA is the only sound manager that all the others will play with. Pulseaudio and xmms and jack will all go through alsa if they are told to.

Only flash will not play with others, it will not share the sound card with newcomers but will share with apps already using it. For example, if I am playing a stream in rythmbox and start a flash video, they will both come through my speakers but if flash is playing and I try to start a stream in rythmbox it will give me an error. 

I have not found a solution to that yet.

Good luck and let us know how you make out.

PS. you probably should get alasmixergui or gnomeALSAmixer etc so you can have a mixer in your menus just a click away.

---

