---
title: "Jack server"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Hotrock on 2008-04-26
Hi, I AM an absolute beginner to Ubuntu Studio (and all thing Linux) and I am confused. 
I have used Steinberg products since the early 1980's so am well practiced in music creation. However I am at a complete loss as to where to start with Ubuntu Studio. Most of the progs ask for Jack Audio Server. I have various Jack progs but none are 'server'. Forgive my ignorance but is this an external piece of hardware or what? 
Thank you for any help you can provide.

Hotrock

---

### Post by Alehbye on 2008-04-26
I could be completely wrong, but it sounds like you need the jackd application. You can get it from Synaptic by searching for 'jackd'.

> JACK Audio Connection Kit (server and example clients)
Low-latency sound server. JACK allows the connection of multiple applications
to an audio device, as well as allowing them to share audio between
themselves.

I hope this helps you or puts you in the right direction.

---

### Post by horace on 2008-04-26
and try qjackctl if you want a gui interface to jackd.

---

### Post by Hotrock on 2008-04-26
> **Alehbye said:**
> I could be completely wrong, but it sounds like you need the jackd application. You can get it from Synaptic by searching for 'jackd'.



I hope this helps you or puts you in the right direction.

You are a star! I'll look for it immediately. Thank you.

Rob.

---

### Post by Hotrock on 2008-04-26
Hm, I apparently have it installed but Rosegarden et al tells me it is not available. Could you please tell me what I could be missing?
Thanks.
Rob

---

### Post by horace on 2008-04-26
> **Hotrock said:**
> Hm, I apparently have it installed but Rosegarden et al tells me it is not available. Could you please tell me what I could be missing?
Thanks.
Rob

Could be a silly question, but have you started jackd?

---

### Post by Hotrock on 2008-04-26
I have several jack apps but no jackd. I didn't know whether or not it was something that ran in the background. So no. I haven't.
I have jackbeat, jack control. jack eq, jack rack and jack timemachine but that's it, I'm getting just a little jacked off with it. ;(

---

### Post by horace on 2008-04-27
I have only recently started using this, but I installed qjackctl. I run that (menu item JACK control under Apps/Sound and Video) and use it to start the JACK server, then start the editing app (Ardour in my case, but Rosegarden in yours).
hth

---

### Post by Hotrock on 2008-04-27
Thank you Horace. I had jack control running but it appears it has not been responding. It appears ok when I first start it but by the time I load in one of the programs (muse, Ardour etc.) it freezes. 
Grrrr.!
I shall call it teething problems for now (unless you know otherwise.) :)

Thanks for your quick responses sir. They are much appreciated.

Rob.

---

