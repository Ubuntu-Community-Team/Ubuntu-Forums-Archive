---
title: "Ubuntu's sound problem"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-01
The one where when you're playing a media player (Banshee, in my case), but then all other programs lose their sound. Has anyone figured out to fix this, or if it's even possible?

This is what my volume control looks like:
[IMG]http://img104.imageshack.us/img104/5639/screenshotgo6.png[/IMG]
And I have the device set to 'Playback: ALSA PCM on Front: 0 (VIA 8233A) via DMA (PulseAudio Mixer)

I've search uncountable amounts of threads, but none of them fix it.

---

### Post by sayakb on 2008-06-01
Change the device to HDA Intel (ALSA Mixer) or OSS mixer.

---

### Post by adobrakic on 2008-06-01
I don't have either of those exactly. I have VIA 8332A (ALSA Mixer)
[IMG]http://img141.imageshack.us/img141/715/screenshotvolumecontrolrd1.png[/IMG]

---

### Post by sayakb on 2008-06-01
Does ALSA mixer work for you?

---

### Post by adobrakic on 2008-06-01
No, I still have no sounds in programs, other than Banshee. Unless I close Banshee, of course.

---

### Post by kansasnoob on 2008-06-01
I've found gnome-alsamixer to work better sometimes. Especially with Realtek.

Just install gnome-alsamixer from synaptic. It may not work but it also won't break anything.

---

### Post by kansasnoob on 2008-06-01
Hmmmmm, maybe I'm misunderstanding some of the sound complaints. Is it that you're playing audio in one program, let's say you're playing tunes from your ipod with Banshee, and you're surfing the net and start a Youtube video and you expect Ubuntu's audio to sort that out?

As I read more and more of these audio complaints I'm just not sure I understand what the complaint is??????????????????????? :confused:

---

### Post by adobrakic on 2008-06-01
Maybe I'm misunderstanding your post. Are you trying to be sarcastic, but failing at it? And yes, I do expect Ubuntu to be able to play sound from Youtube and sound from Banshee at the same time.

Your confusion gone yet? Or do you still need some explaining?

---

