---
title: "Rhythmbox won't play songs"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by chimerical_brio on 2008-04-25
I did a fresh install of Hardy, and when I tried to use Rhythmbox, I got a codec problem, so I did the whole Medibuntu restricted-extras update. But now when I try to play music, the song doesn't start; it just hangs at 0:00. What should I do? Thanks.

---

### Post by joshua neff on 2008-04-26
I'm having the same problem with Rhythmbox since my upgrade to Hardy. It just hangs and won't play songs. I'd love to hear a solution (if there is one).

UPDATE: I'm not sure what did it, but it's fixed for me. I installed the Medibuntu repositories and keyring--maybe that's what did it? But Rhythmbox plays fine for me now.

---

### Post by chimerical_brio on 2008-04-27
...bump.

---

### Post by zalberico on 2008-04-27
Is it isolated to rhythmbox?  I'd try a different manager 

sudo apt-get banshee

If that doesn't work we know its a system problem rather than an erratic program.

Thanks

---

### Post by chimerical_brio on 2008-04-27
Well...a weird thing happened. I tried Banshee, wiht no luck, and just for good measure, I tried, VLC, too, and VLC wouldn't work with any media files, even a movie I had watched this morning. So I restarted, and suddenly, Rhythmbox worked. The weirdest part is that I've restarted multiple times since this problem started.

---

### Post by snkiz on 2008-04-27
You could be have trouble with pulseaudio. For some, (Myself included) It does not connect to the sound card driver correctly. there may be a solution to this, I havn't had time to find out. But in the meantime going to your sound propities -system-Administeration-sound Propities and change it to use alsa. Be sure to check any program that needs sound is using gconf settings or alsa.

---

