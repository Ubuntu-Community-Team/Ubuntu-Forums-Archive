---
title: "Problem with audio inputs."
date: 2014-07-13
forum: New to Ubuntu
---

### Post by spode2 on 2014-07-13
I am having a problem with the internal microphone on an ASUS X101CH notebook not working. I have had no problems with this until recently and I suspect a recent software update is responsible. The pulse volume window shows no signal until I put a plug in the external microphone socket. The internal microphone then starts working and I can remove the plug. The internal microphone input is selected all the time.

There seems to be no Pulse user manual for muggles, or even a clear description of what Pulse audio is for. I read that it mixes all sources and sends the result to the sound card but this cannot be so because Pulse volume control has input switching. Or does this just switch the level display?

---

### Post by spode2 on 2014-07-18
More information:

I am using Lubuntu 14.04

What appears to be happening here is that the headset microphone is seen as "plugged in" at startup. Inserting and removing a plug prods the system into the correct state. I do not understand how this can happen, since the default input in Pulse Volume is shown as the internal microphone. The fact that the system falsely sees something plugged into the jack overrides the input selection, which begs the question: what use is the input selection? Or, as I asked before, does it just change which source the level indicator is showing, not the actual input source?

The problem is intermittent, so it could just possibly be a hardware fault. How can I disable the headset microphone input in software to prove this?

---

