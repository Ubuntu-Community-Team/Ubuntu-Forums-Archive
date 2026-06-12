---
title: "Use of a virtual combined sound device in PulseAudio"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by samwisgg on 2008-06-01
OK,
after reading the PulseAudio wiki & checking all pages on PulseAudio.org I finally decided to seek help on this forum.
Here's my sound setup :
1) internal sound card from which the sound output is connected to the speakers built in in my monitor
2) external sound card hooked up via USB and feeding via optical interface to a set of high-end audio speakers.

Both sound devices are recognized in ALSA and PulseAudio. Pulse Audio Sound server is using default the internal card.

1st problem : whenever I login, the login sound coming from my internal card (thus via monitor speakers) is very loud.

2nd problem : I've defined a virtual sound device that combines the internal and external sound card. I selected that device also for my media player (exaile) but what I really want to do is to ouput sound from exaile only via my external sound card. So what I do is in PulseAudio Volume control set the volume of the virtual stream of the internal card to zero so that I have only the sound from my high-end speakers. This works ... until you stop the sound stream from exaile. When you reclick play afterwards sound is again at full 100% volume output on both internal and external sound card :(. How to fix this ? Is there a way under PulseAudio to remember it's volume controls ? Or if that is not possible how can I get exaile to play only via the external sound card ?

Thanks for any help.

---

### Post by kyphi on 2008-06-01
I suspect that what you have currently is an internal sound chip (not a card) on your motherboard as well as an external sound card.

If that is the case, go into your BIOS and disable your onboard sound.  You only need one sound device.

---

### Post by samwisgg on 2008-06-02
Kyphi,

I indeed have an internal sound chip from Intel and an external sound card from M-audio on the other.
It is not a matter of not using the internal chip anymore. What I would like to do is route the sound from mediaplayers (exaile, totem) to the external sound card while all other 'beeps' (login, notification sounds and so one) should be routed to the intel. So my question is : how do you do this in PulseAudio ?

---

### Post by kyphi on 2008-06-03
As far as I know, you can only specify one sound device.

---

