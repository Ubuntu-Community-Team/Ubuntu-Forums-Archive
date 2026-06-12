---
title: "[SOLVED] Audio drivers question"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by mindpulse on 2008-07-30
Hey, I just recently started using ubuntu this week. So far I've gotten over the initial hurdles (especially connecting to my school through vpnc) and now I'm starting to do some refinement. I've noticed that when playing back media, I'm tending to get some crackling in the sound. Was wondering if this could be due to the audio drivers initially used by ubuntu, and if this was the case, where I could look for better drivers (no real luck so far, or found stuff that I wasn't sure if it'd be a good idea to install ^^;;  ). Thanks!

---

### Post by sstvinc2 on 2008-07-30
What's the source of the audio that you're trying to play?  Is it everything, or just, for instance, flash media?  The reason I ask is that sometimes the problem is actually with the hardware driver, but sometimes it's with codecs or plugins.

---

### Post by mindpulse on 2008-07-30
so far it's been just with vlc. haven't had time to install any other players yet. as far as the types of files, I'm using various avis. some of them work with minimal cracking, some with more, but it's always there. You can pretty much consider my installation of ubuntu a fresh copy with the basic updates it asks you to do from the server

---

### Post by sstvinc2 on 2008-07-30
Just to clarify, you're not having this problem with any kind of mp3s or wavs or anything else?  Just avis?

Do you have 'gstreamer ffmpeg' and 'gstreamer extra plugins' installed?  Both can be found in Applications->Add/Remove.

---

### Post by mindpulse on 2008-07-30
oi sorry for the delay, in a place where my windows laptop is getting internet but my linux one isn't, will have to wait till tomorrow when I can get to a better hotspot again, thank you for the suggestion though will be testing it tomorrow!

---

### Post by mindpulse on 2008-07-31
ok, just tried installing both of those. still is clipping the sound. tried mp3s too, same problem

---

### Post by sstvinc2 on 2008-07-31
Well, on the plus side, you should be able to play pretty much any multimedia file now.  But of course, that doesn't really solve your problem.

For now, I'd do two things: first, check out these two posts:
[http://ubuntuforums.org/showthread.php?t=662043&highlight=crackling+playback]("http://ubuntuforums.org/showthread.php?t=662043&highlight=crackling+playback")
[http://ubuntuforums.org/showthread.php?t=508448&highlight=crackling+playback]("http://ubuntuforums.org/showthread.php?t=508448&highlight=crackling+playback")

Also, so someone more savvy than myself can help you out if none of those solutions work, post the output of > aplay -l here so we can see what kind of hardware you're working with.

---

### Post by sstvinc2 on 2008-07-31
Actually, a better command to post the output of might be > lspci | grep -i audio

Should be a little more concise.

---

### Post by mindpulse on 2008-07-31
results for lspci|grep -i audio:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

results for aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

also tried those thread solutions. none of them have worked (still have to try the alsa reinstall) so far, though I seem to have a different problem. It's not really cracking I'm getting, more like brief halts in the sound

---

### Post by mindpulse on 2008-07-31
FIXED! :DDDDDDD

had to go into system->preferences->sound preferences and set sound events off of autodetect. right now it's on Conexant Digital and seems to work just find :) thanks for the help though!

---

### Post by sstvinc2 on 2008-07-31
Well, can't say that's what I expected, but I'm glad that it works now.

---

