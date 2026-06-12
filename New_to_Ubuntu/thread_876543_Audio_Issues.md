---
title: "Audio Issues"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by gustasonfrever on 2008-07-31
I can't figure out why ubuntu frequently will play sound for only one application depending on which one I start listening to first. Today I turned on my computer and started watching a video with VLC and now when I went to firefox to listen to music, I can't get audio. VLC's sound still works but can't get firefox to play anything. Rythmbox works and shows up when i go to pulse audio volume control as well as VLC. However when I play something on firefox I can see it flickering in the panel but it won't stay in the list along with rythmbox and VLC. Whats wrong? I've noticed that the same thing will also happen if I use mozilla first, then VLC won't play or show up in the pulse audio volume control.

---

### Post by tuxxy on 2008-07-31
Are you using ALSA in your system > prefs > sound

---

### Post by Superkoop on 2008-07-31
If you have paprefs installed, you can use that, and check the check box in the "Simultaneous Output" tab. This let me listen to audio from multiple devices.

---

### Post by gustasonfrever on 2008-07-31
In what field do I use ALSA? I have it for sound capture but everything else is auto detect.

What is paprefs?

---

### Post by tuxxy on 2008-07-31
select ALSA for sound playback / movies & vids

---

### Post by Superkoop on 2008-07-31
It's the PulseAudio prefrences editor.

To install it:

```
sudo apt-get install
```

Then run it:

```
paprefs
```

---

### Post by gustasonfrever on 2008-07-31
Neither of these suggestions have led to the problem being fixed. I restarted and now I still can't hear volume from firefox. Any further suggestions

---

