---
title: "Pulseaudio vs ALSA"
date: 2011-07-01
forum: Recurring Discussions
---

### Post by marin123 on 2011-07-01
Using Ubuntu for over a year now and i'm beginning to wonder, why is pulseaudio used over alsa?
alsa has better latency and better sound and whenever i can, i tell my apps to use alsa.
so, why does ubuntu use pulseaudio? why is it better than alsa? if alsamixer had nice gui, it could be easy to use just like pulseaudio (if we are going that way in ubuntu - gui everything)...

---

### Post by alphacrucis2 on 2011-07-01
> **marin123 said:**
> Using Ubuntu for over a year now and i'm beginning to wonder, why is pulseaudio used over alsa?
alsa has better latency and better sound and whenever i can, i tell my apps to use alsa.
so, why does ubuntu use pulseaudio? why is it better than alsa? if alsamixer had nice gui, it could be easy to use just like pulseaudio (if we are going that way in ubuntu - gui everything)...

Pulseaudio is a sound server which allows multiple sound sources to be fed through to one or more sinks. AFAIK Alsa only works with one source at a time.... Actually I think that is wrong and Alsa does support multiple concurrent sources.

Found this diagram showing what it does:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Pulseaudio-diagram.svg/1000px-Pulseaudio-diagram.svg.png[/IMG]

Appears that pulseaudio is as well as, rather than instead of alsa.

---

### Post by Aquix on 2011-07-01
It's not down to an easy choice between pulse and alsa. I once read a lenghty article about linux sound and it can leave you confused. Someone could write a book about it. What's needed is a cleanup but I'm not sure how that would end up.

---

### Post by twipley on 2011-07-12
> **marin123 said:**
> alsa has better latency and better sound and whenever i can, i tell my apps to use alsa.
thanks, i've just solved an "audio sync" problem i had, using alsa instead of pulseaudio.

---

### Post by Erik1984 on 2011-07-13
What I find strange when looking to that diagram: PulseAudio depends on ALSA to get the sound to the sound card. When I let mpd (music player daemon) output to ALSA other programs cannot play sound. When I send the ouput to pulse they can. However it is still directed to ALSA only via pulse. So the same multiple sound sources still end up being played with ALSA.

---

### Post by marin123 on 2011-07-14
i guess pulseaudio handles multiple sources, does the mixing and then sends one signal to alsa which passes it to sound card.

---

### Post by 3rdalbum on 2011-07-16
Pulseaudio can do things smarter. It does per-application volume controls (for instance, turn Empathy down when listening to DVDs), supports switching of sound sources on the fly as they get plugged in and unplugged, streams your computer audio across a network, And cleans up the "audio blocking" problems that used to exist on Linux.

Pulseaudio, as far as I know, can support multiple OSes. Alsa is Linux-only. An application developer can target Pulseaudio and the program will compile for BSD and Solaris as well as Linux.

---

### Post by HoKaze on 2011-07-16
The Linux sound system is a strange, complex and potentially conflicted place to be.
Personally, I would prefer it if OSS4 got more development and more distros supported it (or at least stopped removing OSS support from their kernels) as at the moment OSS4 is a tad bit less user-friendly to use and can be hard to install, but does support a lot of applications (directly or through ALSA emulation of sorts), allows for multiple sources and generally doesn't have the issues Pulse does.

Of course, OSS4 is still lacking in a few areas, especially regarding some drivers (especially when it comes to recording sound) and application support can sometimes be a pain, but it is supported across multiple *nixes, not just Linux.
Ideally if more work could be done on OSS4 (better integration, easier to install, more support, better/more drivers, automatically changing from speaker output to headphones when they are plugged in, etc) I think the audio problem could be solved in a simpler, more efficient way.

I may be very much wrong in my view and perhaps there are some good reasons why we continue to struggle with ALSA and ALSA+Pulseaudio beyond "OSS3 was replaced by ALSA a long time ago due to license issues".
Any thoughts?

---

### Post by buzzmandt on 2011-07-16
several releases ago after ubuntu went pulseaudio but kubuntu had not yet, installing pulseaudio was the only way i could get my sound to work with usb sound speakers and firefox.  

also i was using teamspeak linux client, which ONLY had OSS support, when it was running it took control of the sound card and nothing else could have sound.  Pulseaudio fixed this by running as the sound server making teamspeak linux client only think it had control of the card when in fact it was pulseaudio.  ever since teampeak linux client will run with the sound of everything else running along with it.

Ive been very happy with the decision to use pulsaudio myself... when something better comes along I'll be all for it, but until then....  hey! this is linux, install what you want/need  :)

---

### Post by weasel fierce on 2011-07-17
by and large pulseaudio works though some games aren't keen on it

---

### Post by Spice Weasel on 2011-07-17
PulseAudio is a complete pain and is only adding to the mess which is currently audio in Linux.

---

### Post by miklcct on 2011-07-20
I install PulseAudio only because some of my CONSOLE APPLICATIONS need it to work, without it, it need root access to my console.

---

### Post by linuxyogi on 2011-07-27
> **Spice Weasel said:**
> PulseAudio is a complete pain and is only adding to the mess which is currently audio in Linux.

I removed pulse audio & all app sound notifications from Thunderbird to Xchat all stopped working. Installed esound but that didnt work. 

I don't have any issues with pulse. I removed it to see if sound of a game running under wine increase which it didn't.  

The only thing I hate about pulse audio is that it defaults to 2 channels. 

I don't understand the reason. They hate surround sound ? :confused:

---

