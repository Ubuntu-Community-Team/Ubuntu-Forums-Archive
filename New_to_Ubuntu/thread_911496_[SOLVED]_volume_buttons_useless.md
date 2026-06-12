---
title: "[SOLVED] volume buttons useless"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by ZOOstation on 2008-09-05
Hokay, so...
I was trying to get my plug-in microphone to work and in the prosess I messed something up. I was tinkering in the sound settings -- the only places I remember doing anything were the Volume Control and Preferences>>Sound, but that doesn't mean that's all I did. But when I got the mic working, a new quirk had appeared: the volume buttons on my keyboard (it's a laptop, that's where they are) don't effectively do anything.

When I use those buttons to turn the volume up or down, the typical transparent volume splash icon appears, and the bar moves up and down (left or right, technically) accordingly. But it makes no change in the actual sound coming through the speakers. When I use those buttons while the Volume Control window is open, the only sliders that move are under Line-In. I can adjust the actual loudness of sounds by adjusting the Master or PCM sliders in Volume Control.

Also, the internal sounds have been activated, or unmuted, or something. They're audibly there now.

Anybody know how I can find the source of these problems and/or how to fix them?

---

### Post by Dejavou42 on 2008-09-05
Settings > Preferences > Keyboard shortcuts 

select the volume up shortcut (right hand side) and press the volume up button on your keyboard. Do the same with volume down.

That should do it.

---

### Post by ZOOstation on 2008-09-05
Nope.

---

### Post by anotherdisciple on 2008-09-05
+1

Dejavou42 has it covered. Ubuntu uses GNOME... and GNOME makes this REALLY easy to set up.

---

### Post by anotherdisciple on 2008-09-05
> **ZOOstation said:**
> Nope.

hmmm... maybe it just needs clarification.

The volume up option should have a field to the right that says something strange... like 0XA... something something...

Double click on that right field... it will change and you just push the button that you actually want to be volume up.

---

### Post by anotherdisciple on 2008-09-05
> **ZOOstation said:**
> Hokay, so...
I was trying to get my plug-in microphone to work and in the prosess I messed something up. I was tinkering in the sound settings -- the only places I remember doing anything were the Volume Control and Preferences>>Sound, but that doesn't mean that's all I did. But when I got the mic working, a new quirk had appeared: the volume buttons on my keyboard (it's a laptop, that's where they are) don't effectively do anything.

When I use those buttons to turn the volume up or down, the typical transparent volume splash icon appears, and the bar moves up and down (left or right, technically) accordingly. But it makes no change in the actual sound coming through the speakers. When I use those buttons while the Volume Control window is open, the only sliders that move are under Line-In. I can adjust the actual loudness of sounds by adjusting the Master or PCM sliders in Volume Control.

Also, the internal sounds have been activated, or unmuted, or something. They're audibly there now.

Anybody know how I can find the source of these problems and/or how to fix them?

Okay... never mind... I know what you did... what do you have selected to playback sound... ALSA?

Whatever that is needs to match your volume control. Make sure that you have a Volume Control applet on one of your panels. The, right-click that and choose the volume settings (Not sure what it's titled, but you'll know what I mean). There should be an option to choose what volume to control... ex) ALSA.... make sure that matches what we looked at earlier.

The option may be under one of the dropdown menus

---

### Post by ZOOstation on 2008-09-05
Close! That selection was in Preferences>>Sound, not in the Volume Control. But that did the trick.

For reasons I don't understand, this seems to have also killed the internal sound I was complaining of hearing. If I'm wrong, I'll ask again.

---

### Post by ZOOstation on 2008-09-06
I was wrong. About the internal sound, that is -- the volume buttons are still fine. In case I'm using the wrong term, the sounds I'm referring to are beeps that occur when I hold a button past its usefulness, like if I'm erasing text and continue to hold backspace after there is no more text to erase, or continuing to hold the up or down key when I reach the end of a drop-down list. This sound never used to occur until I messed with the audio to try to make my microphone work. How can I make it go away again?

---

