---
title: "Streaming all Ubuntu-audio to Android Phone"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by KrijnR on 2013-03-30
I am completely lost.

I have searched all of the internet for a simple app that could stream all my audio-output to my Android-device. 

Every app that I tried either failed or just streamed jukebox or any other audio file. I don't care if it connects via bluetooth or wifi.
Why is this such a hard thing to do?

If someone could point me in the right direction, I'd be very gratefull.

---

### Post by tgalati4 on 2013-03-30
So you want to turn your smartphone into a bluetooth headset?  You would need a network-aware audio framework for that.  Pulseaudio comes to mind.  A little searching:

[http://arunraghavan.net/2012/04/pulseaudio-on-android-part-2/](http://arunraghavan.net/2012/04/pulseaudio-on-android-part-2/)

[http://www.freedesktop.org/wiki/Software/PulseAudio/Ports/Android](http://www.freedesktop.org/wiki/Software/PulseAudio/Ports/Android)

Another person had luck with: [http://www.subsonic.org/pages/index.jsp](http://www.subsonic.org/pages/index.jsp)

---

### Post by KrijnR on 2013-03-30
Yeah, that's what I tried at first. But I couldn't get that to work :(

So now I'm trying to set up an Icecast-server, which is quite new to me, but nonetheless enjoyable.

---

### Post by tgalati4 on 2013-03-30
What phone, what version of Android?  What was preventing you from getting the previous methods to work?  I have a Samsung Galaxy SIII with 4.1.1 and I was going to try a couple of methods.  I use DNLAplay which works with my freenas server.  Not the same use case, but it works.

---

### Post by KrijnR on 2013-03-30
I've got an Galaxy Nexus S with 4.1.2

I don't get how Subsonic is supposed to run on Ubuntu. When I installed it I got a message that said "bad installation". Also, it seems as if Subsonic only streams a playlist, I'd like to stream all of my audio.

---

### Post by KrijnR on 2013-03-31
Ah, I've got it working now. For those interested:

Download Soundwire here:

[http://georgielabs.99k.org/](http://georgielabs.99k.org/)

Download the app for Android: 

[https://play.google.com/store/apps/details?id=com.georgie.SoundWireFree](https://play.google.com/store/apps/details?id=com.georgie.SoundWireFree)

Connect them and fiddle with the settings on your pc. It has some delay but you can change that in the Android-app-settings.

---

