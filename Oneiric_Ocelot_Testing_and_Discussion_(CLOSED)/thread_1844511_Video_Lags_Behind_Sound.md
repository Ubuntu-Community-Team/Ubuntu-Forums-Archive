---
title: "Video Lags Behind Sound"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by teejay17 on 2011-09-15
I have three test machines running up-to-date 11.10. All three have issues with video in that the video lags way behind the sound. 
When these test machines were running 11.04, 10.10, and 10.04, watching video was not an issue and they could perform the task flawlessly. 
These three test machines are running on board generic Intel graphics, nothing special requiring any sort of special drivers.
Is anyone else suffering from this issue, and can I report this as a bug?

---

### Post by teejay17 on 2011-09-15
> **teejay17 said:**
> I have three test machines running up-to-date 11.10. All three have issues with video in that the video lags way behind the sound. 
When these test machines were running 11.04, 10.10, and 10.04, watching video was not an issue and they could perform the task flawlessly. 
These three test machines are running on board generic Intel graphics, nothing special requiring any sort of special drivers.
Is anyone else suffering from this issue, and can I report this as a bug?
I should also mention that it doesn't matter what video format (.avi, mpeg, Flash), nor what video player (Flash Player, Banshee, VLC, MPLayer), the sound and the video are way out of sync.

---

### Post by lucazade on 2011-09-15
check this bug if it is same issue you get

[URL="https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/825709"]Choppy sound in Oneiric after latest pulseaudio update 
[/URL]

I get this with an Intel hda sound chipset

---

### Post by splicerr on 2011-09-15
Could be Unity that's slowing down your video playback, and therefore lags behind sound. Try logging into a "Ubuntu 2D" desktop and see if the problem persists.

---

### Post by teejay17 on 2011-09-15
> **splicerr said:**
> Could be Unity that's slowing down your video playback, and therefore lags behind sound. Try logging into a "Ubuntu 2D" desktop and see if the problem persists.
I am in Unity 2D on all three systems.

---

### Post by teejay17 on 2011-09-15
> **lucazade said:**
> check this bug if it is same issue you get

[URL="https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/825709"]Choppy sound in Oneiric after latest pulseaudio update 
[/URL]

I get this with an Intel hda sound chipset
No, it isn't choppy. The sound is actually fine. The problem is that the video is about 5-10 seconds behind the sound on every media player, playing any type of video file.

---

### Post by teejay17 on 2011-09-18
Update: I asked about this issue [here ]("https://answers.launchpad.net/ubuntu/+source/unity-2d/+question/171357") and it was suggested I report this as a bug. 
If anyone is interested in looking into this, I have reported the bug here: [https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/852554](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/852554)
Cheers!

---

