---
title: "Multiple Speakers Not Working"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by sithpigeon on 2008-06-08
I have a Creative Labs Sound Blaster Live! card installed on my computer that has two speaker jacks. I hooked the two speakers into the jacks and configured the sound preferences to Multichannel Playback. I clicked the test button and sound comes through both speakers. But, when I run any other sound producing program, I only get sound through the main speaker pair. How do I set it up so I can get sound through both speaker pairs. Also, what is a "Digital Out" jack?

---

### Post by Happy_Man on 2008-06-08
You may need to restart your computer for the other applications to start using the multichannel. Try that first, and see if it works out.

---

### Post by acidsolution on 2008-06-08
Try installing alsamixer 
```
sudo apt-get install alsamixer
```

and 
```
sudo apt-get install alsamixergui
```

and than go to Applications->Sound and videos -> alsamixergui

and try configuring your sound system form there and try playing with any music player 

this might solve your problem:)

---

### Post by oldsoundguy on 2008-06-08
Make sure (in Synaptic) that you have Alsa installed. (that is the control program).  It will work great on the 5.1 ANALOG.  Digital out is for driving a separate digital input amplifier.  And it will WORK, but you will have no volume control at present (until a driver update) unless you are using the KDE desktop and install Jack.

---

### Post by sithpigeon on 2008-06-08
Thought I had fixed it but after I restarted my computer again the SB Live! card didn't show up under sound preferences and I had to turn it off and re-secure the card. I turned it back on and it picked it up so I switched from the onboard card to the SB Live! card and tried using the test buttons. I didn't get any sound and the test froze when I tried to quit. Any ideas?

---

### Post by oldsoundguy on 2008-06-08
unless you have a digital amp (stand alone) .. do NOT use the digital out .. re check your connections since you moved some stuff around.

---

### Post by sithpigeon on 2008-06-08
Everything's connected and still nothing works. I get a fuzzy noise coming from the speakers when it boots but nothing else. It finally loads the SB Live! card automatically but I can't get any noise.

---

