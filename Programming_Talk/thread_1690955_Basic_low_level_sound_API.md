---
title: "Basic low level sound API"
date: 2011-02-19
forum: Programming Talk
---

### Post by marking on 2011-02-19
I am currently working on a custom sound mixing engine aimed for large game projects.
It will have a full DSP pipeline, as well as a scripting language with an IDE (wxWidgets) for sound designers, to develop custom sound effects that can be generated in real-time.
This API will do all the sound mixing, and sends the final data stream to a low level OS API that sends this to the soundcard.
For example, in windows, I use the [_waveOut API_]("http://msdn.microsoft.com/en-us/library/aa909811.aspx").

Having only some (end-user)experience in Linux audio, I know there are a lot of different systems (Alsa, OSS, Pulse, openAL, etc..?), but have no idea which are (still) used these days, which are deprecated, etc... 

My initial thought is the (new) PulseAudio API (I like Pulse), but, as I said, I have no idea if pulse would be the best approach for this project.
Just to clarify, I only want to be able to send basic wave/PCM chunks to this API. I do not want to use mixing, nor bothered by drivers. I prefer a reliable API, that I can rely on to be supported in Linux (mainly Ubuntu) for a long while.

Some insight in this would be very helpful :)

Ps. no thank you, I know about FMOD, SFML, etc...

---

### Post by crazyfuturamanoob on 2011-02-19
I haven't used many audio libraries, but I recommend PortAudio. IMO the API is much easier than OpenAL's.

---

### Post by marking on 2011-02-19
> **crazyfuturamanoob said:**
> I haven't used many audio libraries, but I recommend PortAudio. IMO the API is much easier than OpenAL's.
Thanks for your tip, never heard about PortAudio before!
But as far as I understand, PortAudio has a layer around Alsa/Pulse, in which case, I'd be better off using directly anyway.

---

