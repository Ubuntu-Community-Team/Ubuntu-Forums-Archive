---
title: "Audacity + TuxGuitar"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Bölvaður on 2008-05-20
I am wanting to record a song I wrote down in TuxGuitar. I would do that by playing the song in TuxGuitar and be recording with Audacity from mic input (or line in).

That I am unable to do because of the known error that OSS wants to be the only one ;)
I thought it wouldn't be a problem because of PulseAudio.

It doesn't look undo able, so I'll continue to try, but any help is welcomed

---

### Post by FuturePilot on 2008-05-20
Audacity has some problems with PulseAudio still. Try starting Audacity like this
```
padsp audacity
```
That starts it with a type of compatibility layer with PulseAudio.

---

