---
title: "[SOLVED] MIDI not working, other sounds working"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-15
Title says it all.

---

### Post by markbuntu on 2008-08-15
Well, it does and it doesn't. 

What exactly are you trying to do?
If you want specific answers to your problems, you need to post more specific questions and provide some information.
Like: 
Which application are you trying to use and what are you trying to do with it and how have you configured it?
What sound card do you have?
Are you using jack or alsa or something else?
What have you tried already?
Have you done a search?

---

### Post by SZ07 on 2008-08-16
The poster above is right in that next time you should provide more info. The more specifics you can provide, the easier it will be for others to solve your problems.

Anyway, I just recently setup midi on a fresh ubuntu install. I tried several media players and midi did not work with any of them. After searching I found out that getting midi to work depends on hardware. If you have a dedicated sound card (e.g. soundblaster) then you should search in the forums since there are a few guides explaining how to solve the issue.

If, however, you have an onboard sound card (i.e. motherboard does the sound processing) as do most people, then you have to get ubuntu to synthesize the midi sound. The following guide explains how to do this, and by following it, I got midi playback within minutes.

[http://www.funnestra.org/ubuntu/hardy/#timidity](http://www.funnestra.org/ubuntu/hardy/#timidity)

---

### Post by zzzonked on 2008-08-16
Sorry about the vagueness of the problem guys. I was using Kguitar and couldn't get the tab to play itself. But I've just installed TiMidity from Synaptic, and it's working fine now.

---

