---
title: "SMplayer and Diablo 3...sound cuts out"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by venom104 on 2012-08-23
Ok here is my story. I play diablo 3 quite a bit and it works great...the problem is whenever I am playing something in smplayer and open Diablo 3...the entire sound goes out. I don't understand why this happens. It ONLY happens with smplayer and Diablo 3.

What do I do to solve the problem?

---

### Post by Perfect Storm on 2012-08-23
It's properly something to do with wine have difficulties with pulseaudio. If you're running Diablo3 with wine 1.4.x try wine 1.5.x instead. I have read it should fix its pulseaudio problems.

---

### Post by venom104 on 2012-08-24
> **Artificial Intelligence said:**
> It's properly something to do with wine have difficulties with pulseaudio. If you're running Diablo3 with wine 1.4.x try wine 1.5.x instead. I have read it should fix its pulseaudio problems.


I appreciate the response, but I'm using wine 1.5.10 (guild wars 2 is coming soon).

---

### Post by SeijiSensei on 2012-08-24
In SMPlayer, check Options > Preferences > Audio and see what driver is selected.  If SMPlayer is using pulse, try setting it to use alsa directly instead.  I'd try to solve this on the SMPlayer side since mplayer comes with quite an array of audio drivers.  One of them might coexist successfully with wine+Diablo.

---

### Post by venom104 on 2012-08-24
> **SeijiSensei said:**
> In SMPlayer, check Options > Preferences > Audio and see what driver is selected.  If SMPlayer is using pulse, try setting it to use alsa directly instead.  I'd try to solve this on the SMPlayer side since mplayer comes with quite an array of audio drivers.  One of them might coexist successfully with wine+Diablo.

I checked...oddly enough there are like 5 versions of alsa in there...anyway I picked the one without any extra parameters and sound came out. Same problem though...strangely enough, VLC uses alsa, but doesn't have the same problem?

---

