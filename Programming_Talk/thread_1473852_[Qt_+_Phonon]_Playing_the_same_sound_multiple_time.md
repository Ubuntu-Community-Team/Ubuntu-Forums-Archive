---
title: "[Qt + Phonon] Playing the same sound multiple times"
date: 2010-05-05
forum: Programming Talk
---

### Post by benskiedra on 2010-05-05
Hello,

I'm using Qt 4.6.2 (+ phonon library) and I wanted to ask if it is possible to play the same sound multiple times without it being stopped? What I mean is, for example, to play "another" hit.mp3 which is, lets say, 2 seconds in length, exactly after playing one second of the previous "hit.mp3". I understand that this can be achieved by using multiple instances of MediaObject(s), but it is not what I'm trying to achieve.
The real-world example of my situation would be a pool game. Lets say it's the beginning of the game, you hit the cue ball and it hits a playable ball which hits other balls they correspondingly hit other ones and so on... After each hit event a sound "hit" should be played.

Is this possible without using multiple MediaObjects?

---

### Post by stefanadelbert on 2010-11-29
I'm, in effect, trying to do something similar. For my app I have a number of sounds that are triggered by certain events. I would like to have one Phonon::AudioOutput as a sink for all sounds so that one Phonon::VolumeSlider controls the volume of all sounds that the application makes.

For example, imagine an electronic drum kit - click a drum and it plays the relevant sample. If you were quick you could click one drum and then click a cymbal and the two should play simultaneously.

I've tried to create a number of Phonon::MediaObjects, one for each sound, and connect each MediaObject (using Phonon::createPath) to a single AudioOutput. This doesn't work though. Only one of the sounds plays, which suggests to me that multiple paths to an AudioOutput doesn't work. Only the last created path seems to work.

Ideally, if one sound is triggered while one is already playing, they should both play simultaneously, i.e. the sounds should be mixed in layering one sound on top of another. This is why I went for multiple MediaObjects.

This [article]("http://vir.homelinux.org/blog/archives/45-Phonon-Trolltech.html") mentions a Phonon Mixer class that could be inserted into a graph, but it's the only mention of something like that. I also says that implicit mixing of multiple MediaObjects connected to one AudioOutput does not work "anymore".

I would be very interested in hearing if anyone has achieved something like this.

---

