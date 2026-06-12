---
title: "VLC stuttering"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by cartisdm on 2008-05-03
I installed VLC because I'm not a big fan of totem or the other media players (and I just gave up on trying to get them to work).  I'm trying to play a DVD  in VLC and it plays the menus etc. but it keeps stuttering.  Video is there, audio is there....just acting retarded.  I've done the guides and walkthroughs online but nothing seems to be helping me out (in Totem I still get that annoying plugin error message)

---

### Post by Canis familiaris on 2008-05-03
If you haven't installed your ATi graphics driver, then install it now.
If you have installed it then diable Compiz if it is not disabled already.

---

### Post by cartisdm on 2008-05-03
> **Anurag_panda said:**
> If you haven't installed your ATi graphics driver, then install it now.
If you have installed it then diable Compiz if it is not disabled already.

1. Installed
2. Not running :(

---

### Post by treggmo on 2008-05-03
cartisdm,
Start the DVD in VLC then click on Video > Deinterlace and choose X at the bottom.

---

### Post by opendevlite on 2008-05-03
This is my fix for audio on playing VCD on VLC, just try this out, it migth work for DVD's also

In VLC go to Settings->Preferences->Audio->Output Modules

Click on "Advanced Options" to view "Audio Output Modules"

in Audio Output Modules, select "ALSA audio output"

Click on "Save"

---

### Post by cartisdm on 2008-05-03
> **treggmo said:**
> cartisdm,
Start the DVD in VLC then click on Video > Deinterlace and choose X at the bottom.


Awesoooooooooooome.  Worked like a chart, thanks man.  Strange I couldn't find a simple fix like that searching through google

---

### Post by treggmo on 2008-05-03
You're welcome. I found the fix by trial and error myself. I tried setting "X" as default in Preferences > Video > Filters > Deinterlace > Save, but it doesn't stick.

---

### Post by kerti on 2008-06-09
I've managed to play VCDs on VLC, with ALSA as recommended. It works fine, but I notice that VLC simply "freezes" playback when the disc is a bit worn off and thus the file is slightly corrupted. I notice my hard disk light was on during the entire time VLC freezes. Is this normal?

When I play the VCD on Windows, it's also a pain due to poor disc condition, but the player simply skips damaged parts and resumes playback. Also, my hard disk isn't spinning all the time. Is this something to be fixed in VLC?

Another thing, when I play a VCD fullscreen and switch back to windowed, the audio plays but the video wont show. Any hints?

---

### Post by Gyrotwister on 2008-06-09
> In VLC go to Settings->Preferences->Audio->Output Modules
Click on "Advanced Options" to view "Audio Output Modules"
in Audio Output Modules, select "ALSA audio output"
Click on "Save" 

Fixed my VLC DVD play back sound problem. Thankyou opendevlite.

---

### Post by coolnezz on 2009-09-23
ugh... nothing worked for me on VLC.
MPlayer is working fine though.

---

### Post by coolbrook on 2009-09-23
You're bumping a really old thread here.  Anyways, FWIW VLC was updated today.  The new version is 1.02 (for Jaunty anyway) and since it's an upgrade then it's worth a look.

---

### Post by RandyNose on 2012-03-11
I found that by deleting my .pulse dir in my home dir cleared up my audio issue that I was having with VLC. 

Use Nautilus to open your home folder, and check the View Hidden files option under the View menu, then delete the .pulse folder and reboot. This creates a new default config file for pulse audio, and it worked for me. :D

---

### Post by coffeecat on 2012-03-11
Old thread - closed.

---

