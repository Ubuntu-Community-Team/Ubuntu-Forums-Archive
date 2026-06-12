---
title: "No sound.  Kind of."
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Me887799 on 2008-06-25
After a fresh install of Ubuntu, I haven't any sound.  Kind of.

When I unplug and plug back in my headset, the ubuntu login sound plays, but nothing else that emits sound does.

I'm using a USB Logitech headset on a realtek HD sound card.  AC886 I believe.  The microphone does not work either.

I am running Ubuntu Hardy Heron

---

### Post by SSDF on 2008-06-25
yeah I had a problem with this ( i was using a  Logitech easy call package), But the only sounds I could hear was testing the sounds in the  sounds preference box... (although i couldn't hear the system sounds when I tested them)

I got help form a guy on a ubuntu chat, and I had to add a line to a certain file, somthing about 

3stack.


But turns out I could just use normal speakers, for w/e reason a usb speaker is hard to set up.

---

### Post by kansasnoob on 2008-06-25
I'd start by installing gnome-alsamixer from synaptic.

You can then go to Sound & Video > Gnome Alsa Mixer and open the gui:

[ATTACH]75349[/ATTACH]

[ATTACH]75350[/ATTACH]

Lots of neat tools right at your hand now!

---

### Post by Me887799 on 2008-06-25
> **kansasnoob said:**
> I'd start by installing gnome-alsamixer from synaptic.

You can then go to Sound & Video > Gnome Alsa Mixer and open the gui:

[ATTACH]75349[/ATTACH]

[ATTACH]75350[/ATTACH]

Lots of neat tools right at your hand now!


My music playback worked... until I had to restart my computer.  No sound again =/ 

I use AC883 instead of AC886.

---

