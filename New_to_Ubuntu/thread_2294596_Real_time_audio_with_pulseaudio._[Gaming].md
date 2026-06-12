---
title: "Real time audio with pulseaudio. [Gaming]"
date: 2015-09-12
forum: New to Ubuntu
---

### Post by toast3 on 2015-09-12
I'm having a real hard time getting audio to work in real time, i  followed a tutorial that told me to lower the default-fragments and  default-fragment-size-msec that you can see in the screen shot but that  still a 10ms~ delay and wasn't low enough. so i followed something  telling me to install a 'faster' kernel so i installed 'low latency  kenel' and used the realtime-scheduling but it hasn't made a  difference...
  [http://i.imgur.com/fTyePXf.png](http://i.imgur.com/fTyePXf.png)

I checked for realtime kernel in the repo but couldn't find it. I just want real time audio...

---

### Post by HermanAB on 2015-09-12
10ms... what are you complaining about?  There is no way that you can discern a 10 ms lag.

---

### Post by mystics on 2015-09-12
If you're picking up lag on a 10ms delay from PulseAudio, then the problem is with the game. Any delay that much below 100ms, which is around when humans start perceiving delay, won't be discernible.

---

### Post by toast3 on 2015-09-14
"There is no way that you can discern a 10 ms lag."
"Any delay that much below 100ms... won't be discernible."

It's pretty ignorant to say that but to be fair the delay is in the 10-20ms range but is still noticeable. Saying you can't detect latency below 100ms is straight out wrong, it kinda reminds me of people who say 'human ears can't distinguish between 30 and 60fps'.

[http://forums.blurbusters.com/viewtopic.php?f=10&t=1134](http://forums.blurbusters.com/viewtopic.php?f=10&t=1134)

In this thread is a test for distinguishing how much mouse lag you can notice and the baseline is 50ms and people can go much lower.

my reaction time is around 120ms, i own a monitor that is 144hz and a mouse with a 6ms debounce. and i've been using this exact setup to play competitive counter-strike for a year now and when i moved to linux i noticed the sound was off.


Yea, but instead of helping me just tell me I'm wrong.

---

### Post by mystics on 2015-09-14
Telling you that you're looking in the wrong place is an  attempt to help you. We don't want you spending hours trying to minimize  audio delay when the current delay should be acceptable and well within  the range of undetectable.

And consider that in switching to Linux there are a few other potential issues:
-Hardware  may not be as compatible. Just because something works perfectly fine  on Windows doesn't mean it will work perfectly fine on Linux without  some work.
-The game isn't the same. OK, technically, it is the same,  but it isn't like they just took the source code from Windows, pressed a  button, and got it running on Linux as well as it did on Windows. If it  were that easy, we'd have more games. So even if Counter-Strike works  perfect on Windows, there might be some problems, either inherent or  with hardware compatibility, on Linux.

Those are just two, but  there are a few potential others. I'm not going to claim that I know  exactly what the issue is, but I am reasonably certain that it is not  the 10ms audio delay. Sorry that that doesn't automatically fix your  issue, but it won't be fixed if you continue looking in the wrong  places.

But I guess to be more direct:

You've given some  monitor and mouse specs, but you've failed to give us any sound  information. If you post things like sound card information and what  you're using to hear it, then maybe someone here will know of an issue  and how to fix it.

I'm not sure what to do if it is a Counter-Strike problem. Maybe the Steam forums?

---

### Post by tristan16 on 2015-09-14
Could this problem be related to sampling rate by any chance? I remember having an audio sync issue with screen recording, and changing the default sampling rate fixed it. Maybe it's worth a shot here: [http://www.ubuntugeek.com/howto-change-pulseaudio-sample-rate.html](http://www.ubuntugeek.com/howto-change-pulseaudio-sample-rate.html)

Personally I don't think 10ms is anything to complain about, but then again, I played on my mom's laptop for years and thought 15FPS was great.

---

### Post by sandyd on 2015-09-14
If you want real time audio that you can actually adjust...

A few things:
[LIST]
[*]For applications with no direct pulseaudio support, but only alsa support, sound goes something like ALSA (Input) -> PulseAudio -> ALSA (Output). I find that's the main reason for latency that people describe.
[*]Try **stopping/disabling** (but not removing) pulseaudio, and switching to direct alsa output. If it fixes the problem, its the issue above. Note that **one** application can play at a time unless you enable dmix.
[*]Despite the fact that PulseAudio is geared towards a desktop sound system, so latency is expected, the latency will not be fixed by changing to JACK2 unless the game has support for jack2 audio output. It will simply travel the same path as pulseaudio, and despite the fact that JACK2 is optimized for low latency, the fact that it travels like that kills off a lot of optimization. That being said: Lots of pain, little gain, and the chance that you might spend a few hours to tune jack2 via qjackctl, and get it to work with alsa applications.
[/LIST]

---

### Post by kuazar on 2015-11-12
> **toast3 said:**
> I'm having a real hard time getting audio to work in real time, i  followed a tutorial that told me to lower the default-fragments and  default-fragment-size-msec that you can see in the screen shot but that  still a 10ms~ delay and wasn't low enough. so i followed something  telling me to install a 'faster' kernel so i installed 'low latency  kenel' and used the realtime-scheduling but it hasn't made a  difference...
  [http://i.imgur.com/fTyePXf.png](http://i.imgur.com/fTyePXf.png)

I checked for realtime kernel in the repo but couldn't find it. I just want real time audio...


[https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&es_th=1&ie=UTF-8#q=adjusting%20pulse%20audio%20real-time%20scheduling%20for%20gaming&es_th=1](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&es_th=1&ie=UTF-8#q=adjusting%20pulse%20audio%20real-time%20scheduling%20for%20gaming&es_th=1)

Hi, I googled the above and got a bunch of different situations to your question, maybe if it doesn't help you, it might at least point you in the right direction. I went through a few really interesting ones, but you will know which one will interest you by going through the links. I'm sorry I could not be of more help to you, and understand your frustration. I would really be interested and would appreciate it if you would post your findings if you happen to get anywhere with it.
Respect-
Kuazar

---

