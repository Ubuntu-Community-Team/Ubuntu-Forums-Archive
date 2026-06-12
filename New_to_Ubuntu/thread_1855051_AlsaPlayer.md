---
title: "AlsaPlayer"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by mdavis1231 on 2011-10-05
Does anyone know of any way to get AlsaPlayer to play through a USB headset?  I'm not seeing anywhere where you can change the output settings.

[B]Mark in Cincinnati
*"It's great to be free from Windoze...YIPPEE!!!" ):P*
[/B]

---

### Post by Bucky Ball on 2011-10-05
What release of Ubuntu are you running? Do you see anything like 'Alsamixer' in your sound applications?

---

### Post by Lisiano on 2011-10-05
Ahh. I though we covered that, you can change everything in Pavucontrol and Gnome Volume Control, just make sure AlsaPlayer is playing something first.

---

### Post by mdavis1231 on 2011-10-07
> **Bucky Ball said:**
> What release of Ubuntu are you running? Do you see anything like 'Alsamixer' in your sound applications?

I'm running Ubuntu 10.04 LTS.  I do not have PulseAudio installed because I don't like it at all.  I do have ALSAMIXER installed.

Even though I'm now using Audacious, I would still like to know if there's a way to play AlsaPlayer through a USB headset.

---

### Post by mdavis1231 on 2011-10-07
> **Lisiano said:**
> Ahh. I though we covered that, you can change everything in Pavucontrol and Gnome Volume Control, just make sure AlsaPlayer is playing something first.

I reinstalled PulseAudio after speaking with you, as well as Pavucontrol.  I could not find in Ubuntu 10.04 LTS where it would allow me to choose individual devices to modify input/output.

I gave up on Amarok.  I now have Audacious installed.  It allowed me to not only choose the output device that I wanted it to play through, but it also has no problem whatsoever playing _**any**_ CD's beautifully.

---

### Post by Lisiano on 2011-10-08
```
pavucontrol
```
Just type that or the way with padevchooser.

As for AudioCDs, it's due to some migration (Forgot from what) so in a sense, blame KDE. All Gnome apps should play AudioCDs perfectly as they utilize GVFS.
Audacious depends on GTK -> Gnome app -> GVFS -> Perfect AudioCD support.

Sorry for the long delays in my PMs. Playing the Battlefield 3 Beta. Tooooo good. Can't resist it. Must buy the Limited Edition.

---

### Post by mdavis1231 on 2011-10-15
> **Lisiano said:**
> ```
pavucontrol
```Just type that or the way with padevchooser.

As for AudioCDs, it's due to some migration (Forgot from what) so in a sense, blame KDE. All Gnome apps should play AudioCDs perfectly as they utilize GVFS.
Audacious depends on GTK -> Gnome app -> GVFS -> Perfect AudioCD support.

Sorry for the long delays in my PMs. Playing the Battlefield 3 Beta. Tooooo good. Can't resist it. Must buy the Limited Edition.

Well, since I like Amarok so well, at this point I've just resorted to the terminal mount and play commands to get Amarok 2.4 to play Audio CD's.  I guess at this point I'll just have to be happy with that.  Maybe they'll have this corrected in Amarok 2.4.3 "Berlin".

---

