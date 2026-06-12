---
title: "Record My Desktop Sound Problems"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-10-21
Sorry if this has already been posted, bu I couldn't find the answer relating to poor sound problems in gtk-RecordMyDesktop.  The only way for me to here sound (in my case music) while recording is to turn the front mic way up.  The only problem is that on my laptop, i believe the mic is located right next to my mousepad causing viewers to hear all the typing and clicking I do.

My question is, is there a way to hear sounds (such as music from my laptop) through the computer (not sure about the correct terminology sorry) without using the mic??  So essentially all you hear is the music instead of my fingers??  Thank You

---

### Post by whitethorn on 2008-10-21
If you have a certain cable (sorry don't know what it's called) the kind you can stick into your headphone jack.  Well you need that kind of connection on both ends of the cable.  Stick one into you headphone jack and one into the mic jack, so you're kindof creating a loop.  I've also read you can also record what you hear using audacity, never worked for me because I use pulse audio and not Alsa.

---

### Post by patrickballeux on 2008-10-21
When I want to record from my sound card (as I do when I broadcast over the web at blogTV), I use JACK and Pulseaudio.

Pulseaudio is installed by default, and you need to install qjackctl and jackeq (useful to manage you different audio source).  Then it's only a matter of "routing" your sound to the desired destination.

Read my wiki page for enable Flash to read from JACK using Pulseaudio: [http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack]("http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack")

You have enough in there to be able to do what you want.  (Flash will be a bonus...)

Good luck!

---

### Post by BigBananaMan on 2009-08-28
> If you have a certain cable (sorry don't know what it's called) the kind you can stick into your headphone jack. Well you need that kind of connection on both ends of the cable. Stick one into you headphone jack and one into the mic jack, so you're kindof creating a loop.
I've tried that but all I get is a steady clicking sound approximately every half second.  How I do it is plug a microphone in and place the microphone next to the speakers for super crappy 1920s quality recording with me coughing, dropping things, and occasionally swearing in the background.

---

