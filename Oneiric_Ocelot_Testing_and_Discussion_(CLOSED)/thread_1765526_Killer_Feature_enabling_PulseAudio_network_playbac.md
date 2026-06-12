---
title: "Killer Feature: enabling PulseAudio network playback"
date: 2011-05-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by crispy_chunks on 2011-05-23
I have added this comment to [bug #273742]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/273742"):

> No need for me to add anything to this bug as we all know it exists. Wifi is laggy, cable good.

I would just like to add that this network sound is a killer feature of pulseaudio, and therefore also of ubuntu. There are so many use cases where this feature is useable by non-technical end users. Most people have a stationary computer connected to their stereo and use a laptop or other device around the area. Sending sound output to the stereo is in many cases a great convenience. I propose that this feature is a reason for many people who don't see a reason to shift from Windows or OSX to consider ubuntu, but as the situation is now there are a few issues that needs to be addressed:

1) Stability. For some reason my 10.04 installation stopped being able to play back sound it recieves from network. I believe this to be fixed with later installations.
2) Lag. Sound needs to play instantly, or almost instantly. I know that this an inherent design limitation of doing this over wireless, but there is a lag of more than what the latency of the network can account for. Sometimes 1-10 seconds.
3) Integration into the desktop. If issue 1 and 2 gets fixed to a point where it would be considered acceptable by end-users desktop integration should be addressed. For example, people need to be aware of this feature. It needs to be integrated into applications that ship with ubuntu. For example Totem could have a feature to compensate for the network lag if it was aware that it was redirecting sound over the network. Banshee could have a button next to the volume which could be pressed and sound would play over the network instead leaving other applications sounds still playing on the local sound card, for example system sounds, totem video, flash plugin etc.


I really believe that putting some effort into this already existing feature we could develop it into a killer feature. I would work on it myself, but alas, no skills :(

---

### Post by hugmenot on 2011-05-23
What would improve audio tunnels in Pulseaudio a lot would be compression using Celt/Opus codec. They used to have this on their roadmap. Sending uncompressed PCM is just too much for WLAN.

Celt is low-latency and high quality at low bitrates:
[http://listening-tests.hydrogenaudio.org/igorc/results.html](http://listening-tests.hydrogenaudio.org/igorc/results.html)

Recent discussion of this topic:
[http://article.gmane.org/gmane.comp.audio.pulseaudio.general/9639/match=celt+pulseaudio](http://article.gmane.org/gmane.comp.audio.pulseaudio.general/9639/match=celt+pulseaudio)

---

### Post by crispy_chunks on 2011-05-25
Other codecs sound like a good plan, however, I have no idea of how PulseAudio actually works, just what it does and can do. I guess now theres already a quality loss associated with playing over network?

---

### Post by hugmenot on 2011-05-25
Now? No. They send uncompressed audio over the line, which does not work so well over wireless.

---

### Post by LSenf on 2011-07-08
paprefs is some kind of a first step, offering easy network access to the local pa-server.

however, the client-side program i used so far for connecting to the server (padevchooser) is not included in oneiric anymore, as its development is not continued.

The mentioned alternative, pavucontrol, is apparently not able to connect to a different pa-server. Any ideas for an alternative?

---

### Post by hugmenot on 2011-07-08
There are two ways to stream audio in PA, the first is 

```
client &#8594; network &#8594; pa server
```

the second one is 

```
client &#8594; local PA server &#8594; network &#8594; remote PA server
```

the second is using so called tunneled sinks. you can auto-discover network sinks with both pavucontrol and the ubuntu sound indicator.

---

### Post by LSenf on 2011-07-08
Thanks a lot, tunneled sinks are a far better solution for my purpose! :D

After entering

```
pacmd load-module module-tunnel-sink server=myip
```I can use the sound indicator for switching.

Still, entering this command will not make this the killer feature the thread starter mentioned...
So, is there a convenient GUI way to create this tunnel? Of course, if sharing / accessing sound cards via network was possible from the indicator's sound settings menu, we'd have our killer feature! :popcorn:

---

### Post by hugmenot on 2011-07-08
> **LSenf said:**
> So, is there a convenient GUI way to create this tunnel?

Yes, it&#8217;s automatic. Just tick it.

[IMG]http://i.imgur.com/GyK30.png[/IMG]

And on the server:
[IMG]http://i.imgur.com/gof58.png[/IMG]

---

