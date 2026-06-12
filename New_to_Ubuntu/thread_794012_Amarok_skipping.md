---
title: "Amarok skipping"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by pzs on 2008-05-14
I listen to Amarok most of the day. It skips or stutters about once every 3 or 4 songs, which is pretty annoying. This doesn't seem to be affected by what else I'm doing - I can be running simulations in the background and it doesn't skip any more often. 

My machine is a dual core thing with 2GB of memory so this should not be a performance issue. I'm on Hardy Heron.

---

### Post by Cypher on 2008-05-14
Can you see if Trackerd is running? You will see a magnifying glass on the top right in the top panel. If it's running, you might "pause" it for a while and see if the skipping stops.

A dual-core should be plently fast for audio playback, so the HD bandwidth might be a culprit..

---

### Post by KenBW2 on 2008-05-14
Is it skippimg when you switch application or when a dialog opens? Are you running Hardy? If so then the problem is with PulseAudio.

Go to System > Preferences > Sound and change all the "Autodetect" combo boxes to ALSA, restart and hey presto - everything should be fixed
:)

---

### Post by PinkFloyd102489 on 2008-05-14
Mine skips, but it's because I have a Pentium III 450Mhz. :-p

---

### Post by antwerx on 2008-05-15
My audio skips no matter what app I use. Currently listening to Rhythmbox skips, listening to NPR podcasts using a web player skips also.  

I have reset all of my audio prefs to Alsa devices, rebooted and it still skips.  I have stopped trackerd which does not help.

Any more suggestions?

---

### Post by antwerx on 2008-05-15
> **antwerx said:**
> My audio skips no matter what app I use. Currently listening to Rhythmbox skips, listening to NPR podcasts using a web player skips also.  

I have reset all of my audio prefs to Alsa devices, rebooted and it still skips.  I have stopped trackerd which does not help.

Any more suggestions?

UPDATE:  I ran Rhythmbox as root, gksudo rhythmbox, which does not skip.  Try running your audio player of choice as root.

---

### Post by pzs on 2008-06-04
Needing to run as root seems a bit poor. Shouldn't a userspace MP3 player, you know, work?

I haven't had any luck setting everything to ALSA either.

---

### Post by antwerx on 2008-06-04
> **pzs said:**
> Needing to run as root seems a bit poor. Shouldn't a userspace MP3 player, you know, work?

I haven't had any luck setting everything to ALSA either.

I got so feed up with it that I reinstalled gutsy and will wait a bit longer for hardy to get some of the kinks worked out.

---

### Post by michaelzap on 2008-06-05
Mine just started skipping after today's updates (including one for rhythmbox). Even the test sound in the control panel stutters, and I've changed everything to Alsa. I guess I'm not going to listen to music while I work today. :(

---

### Post by psyke83 on 2008-06-11
Hi,

If you are running Hardy and experience skipping, perform this simple test:

1. Ensure your music player is not running
2. Kill the PulseAudio server:
```
$ pkill pulseaudio
```
3. Open your music player, play a song and listen for any skipping

If skipping was eliminated from this simple test, then your problem is with PulseAudio's buffering. See my guide here (Part A & C): [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by jasonsexton on 2008-09-26
I am having a problem somewhat similar to this.  When I play some of my mp3's in Amarok, they skip and some jump to another song.  It sounds as if the mp3 was ripped with another song playing.  Very peculiar.  Anyone heard of this?

---

### Post by Rockin' Moe on 2008-10-12
I'm having what seems like the same issue as **pzs** using amarok-xine, very annoying. I also have a problem where songs' playback starts about .5-1 second into the track when playing through a playlist. Both of these problems have just recently developed after using Amarok with no playback issues for several months.  It seems like some sort of buffering issue, but there doesn't seem to be much in the way of troubleshooting it, I guess because it's very vague. I've tried everything I've seen mentioned here, and just tried reinstalling amarok and the xine librarys, but the problems persist.

Hoping someone might be able to shed some light or point me in the direction of a solution.

---

