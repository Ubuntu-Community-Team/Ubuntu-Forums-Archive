---
title: "Just reinstalled. Need help getting back audio loopback with no delay."
date: 2012-08-06
forum: New to Ubuntu
---

### Post by Uikri on 2012-08-06
I've been using Ubuntu for less than a year anyway. So, I know how to get audio loopback. [http://thelinuxexperiment.com/guinea-pigs/jon-f/pulseaudio-monitoring-your-line-in-interface/](http://thelinuxexperiment.com/guinea-pigs/jon-f/pulseaudio-monitoring-your-line-in-interface/) But apparently that's not going to fly if I want it to have no delay [http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-pulseaudio-loopback-delay/](http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-pulseaudio-loopback-delay/) Nobody has answered my thread in *General Help*, and this is technically different, so I'll try here. Please, help me out. I just want to reacquire my audio loopback, and be able to use it with my consoles without delay. If there's an easier way to do it than described in those guides, then tell me, as I don't really know what I'm doing.

---

### Post by tartalo on 2012-08-06
I don't really understand your problem, but since no one else answers...

If you are trying to do anything serious with audio, you probably need to get rid of PulseAudio.

Also, have a look at Jack: [http://jackaudio.org/](http://jackaudio.org/)

---

### Post by Uikri on 2012-08-06
> **tartalo said:**
> I don't really understand your problem, but since no one else answers...

If you are trying to do anything serious with audio, you probably need to get rid of PulseAudio.

Also, have a look at Jack: [http://jackaudio.org/](http://jackaudio.org/)

Thank you for your reply!

So you're saying I need to *get rid* of Pulse? What would I use then, and how would I manage it? Will take a look at Jack.

*Edit: So, in laymen's terms, JACK just makes it where all audio programs can work with each other? Or am I getting it wrong?*

---

### Post by tartalo on 2012-08-07
I'm no expert but I've heard that Pulseaudio causes latency and other problems, and as far as I know, people working with audio completely remove it. If you remove it your system will be using ALSA for audio output.

Anyway, before messing with your system you might want to ask to someone that knows more about sound in Linux. Have a look here, they mention a couple of forums: [http://linux-audio.com/](http://linux-audio.com/)

EDIT: No, I don't think that Jack allow ANY program to work with each other, there's a list here: [http://jackaudio.org/applications](http://jackaudio.org/applications)

---

### Post by Uikri on 2012-08-09
> **tartalo said:**
> I'm no expert but I've heard that Pulseaudio causes latency and other problems, and as far as I know, people working with audio completely remove it. If you remove it your system will be using ALSA for audio output.

Anyway, before messing with your system you might want to ask to someone that knows more about sound in Linux. Have a look here, they mention a couple of forums: [http://linux-audio.com/](http://linux-audio.com/)

EDIT: No, I don't think that Jack allow ANY program to work with each other, there's a list here: [http://jackaudio.org/applications](http://jackaudio.org/applications)

So then Jack replaces things like Pulse and ALSA?

---

### Post by tartalo on 2012-08-10
> **Uikri said:**
> So then Jack replaces things like Pulse and ALSA?

No.

ALSA is part of the Linux Kernel and allows the output through the sound card. OSS is part of the Kernel too and does more or less the same, you can only use one of these and you are using ALSA for sure (there are two for historical reasons).

ALSA (and OSS) offer few features beyond sound output, so other software has been writen on top to fill the gap.

Two of these are JACK and PulseAudio. They serve different purposes and you might even have both connected toghether. 

But PulseAudio is known to cause a huge latency, therefore if latency is a problem, as it seems it is, Pulseaudio is probably better avoided. 

More on the Linux sound labirynth : 
[http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)

EDIT: It's not exactly right that OSS and ALSA are exclusive, the article explains it better

---

### Post by tartalo on 2012-08-10
Uikri, check this forum:

[http://www.linuxmusicians.com/](http://www.linuxmusicians.com/)

---

