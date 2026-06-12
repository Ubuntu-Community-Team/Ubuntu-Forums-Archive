---
title: "Sheet music composer?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-06-07
Where can I find a sheet music composer for Linux that can play back what you've written?

---

### Post by tonymoloney on 2008-06-07
Have you tried NoteEdit?

---

### Post by Bölvaður on 2008-06-07
TuxGuitar

---

### Post by linkmaster03 on 2008-06-07
NoteEdit: Sound doesn't work, error shows on terminal: ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

TuxGuitar: This shows:

```
/usr/bin/tuxguitar: 21: /usr/lib/jvm/java-6-sun-1.6.0.06/bin/java/jre/bin/java: not found
```

---

### Post by lisati on 2008-06-07
the only one I've used regularly is a Windows program (haven't tried it in Wine yet): Noteworthy Composer

---

### Post by loell on 2008-06-07
try [nted]("apt:nted") music editor , you'll most likely need [timidity]("apt:timidity") .

---

### Post by stmiller on 2008-06-07
Here are some main ones:

[http://muse-sequencer.org/](http://muse-sequencer.org/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

[http://lilypond.org/](http://lilypond.org/)

[http://mscore.sourceforge.net](http://mscore.sourceforge.net) (most like Sibelius)

---

### Post by linkmaster03 on 2008-06-07
loell: Sound doesn't play on it, no errors. Sound works on Youtube and everything else though. :S

stmiller: 

Muse: Couldn't load Jack, the audio module.

Rosegarden: See Muse

MuseScore: Works, but I really hate the controls. Very unintuitive.

---

### Post by loell on 2008-06-07
this is probably because, most of these editors use **ALSA** for sound output. :(  ,  if you are in hardy heron, set your sound output to alsa instead of the default pulseaudio.

---

### Post by linkmaster03 on 2008-06-08
I use HDA Intel ALSA mixer and it works for other things, but when I change it from Autodetect to ALSA, this shows.

[img]http://img361.imageshack.us/img361/7050/sunjun081046yt6.png[/img]

---

### Post by loell on 2008-06-08
try restarting, the in the sound configuration instead of **master** select **PCM** then change all playbacks to alsa, i think this is more or less what i did to regain nted's sound , oh btw, you did select **timidity** in nted's **configure MIDI** did you?

---

### Post by linkmaster03 on 2008-06-08
I selected Timidity, and it worked! Thank you!

---

### Post by loell on 2008-06-08
I won't just accept a simple thank you ;)

I'd like to listen to what you've come up in your composition. :guitar:

drop me a message when its finished..   j/k  :)

---

### Post by linkmaster03 on 2008-06-08
Transposed piano music:

[http://youtube.com/watch?v=xT6GSOuxWXg](http://youtube.com/watch?v=xT6GSOuxWXg)

For trumpet:

[img]http://img386.imageshack.us/img386/3705/roostaf2.png[/img]

---

