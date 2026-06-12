---
title: "Using MIDI in JACK"
date: 2009-12-31
forum: Programming Talk
---

### Post by Envergure on 2009-12-31
I'm having trouble using JACK for MIDI connections.  I'm using QJackCtrl to make connections.  All available inputs and outputs are divided into Audio and MIDI tabs in QJackCtrl, **but nothing ever appears under MIDI.  Even my computer's physical MIDI ports aren't recognized.**  The MIDI ports of all software and hardware always appear under a third tab called ALSA.  So now I have this half-finished synth with JACK MIDI ports, which appear under the MIDI tab, but I have nothing to connect them to.

Do I have to use ALSA for my MIDI and JACK for my audio in order to be compatible with all the other software and hardware? 
Is there a way to get JACK to list my physical MIDI ports so I don't have to mix sound libraries?
Does QJackCtrl handle ALSA Sequencer, Alsa RawMidi, or both types?  What's the difference between the two?


For now I'll just try adding ALSA RawMIDI ports too, since I'm trying to finish it before 2010 starts in an hour :)

Thanks
- Chris

---

### Post by Envergure on 2009-12-31
Nevermind, I figured it out:
1)  Click "Setup..." on the QJackCtrl main window
2)  In the window that opens, change "MIDI Driver" (bottom-left) to "seq".
3)  Go back to the "Connections" window.  All the ALSA MIDI ports should now be listed under a client called "alsa_pcm"

---

### Post by LeifAndersen on 2010-01-01
I would like to take this moment to state how much I envy you.  I have spent not hours, but days on end, (possibly >70 total), trying to get Jack to work for me (with rosegarden), to no avail.  Good job.

---

### Post by blackone86 on 2011-10-11
figured id comment on this instead of a new thread... I am having the same problem as the OP. However i did what he recommended and everything is still under ALSA. I have nothing under Midi or Audio. My midi controller/keyboard seems to be recongnized but with no sound for the synth apps. If i open Hydrogen i can get sound but only from the last 2 keys on the keyboard and thats it. Im soooo confused

---

