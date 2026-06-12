---
title: "Intermittent (but frequent) media problems"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Nutopia on 2008-09-23
Hello folks,

I'm having some issues with Ubuntu that have been going on now for some time. Frequently (but not all the time - that makes it fun, huh?) I can't play certain media files - either in my browser or in another application. For example, I cannot play MP3s right now, but I was able to play them early yesterday morning. I've tried multiple different applications (VLC, Amarok, RhythmBox, etc) and I've also tried to play them directly in the Firefox web browser - no luck.
Another example is .mov files on the web. I can see the movie play, but I hear no sound. Again, this doesn't happen all the time - sometimes it works, sometimes it doesn't. 
In both cases, it appears as if the audio is playing - the track progress bar is moving... but nothing is coming out. I know it's not an issue with my hardware because other types of media work 100% of the time - such as youtube videos. 

I have the 'restricted file format' for mp3s downloaded and installed, so that's not the issue. 

Can anyone help me debug what is going on? This is getting rather annoying as I do like to listen to music on my computer a lot!

Thanks!

---

### Post by NT4usB on 2008-09-23
The obvious comes to mind.
Check to see that main and/or PCM are not muted.
I find on my MythTV slave, sometimes simply watching a recoreded program mutes PCM. Unmute and all is well. 
Might have been watching (and listening to) mpegs and avis all night but one visit to Myth mutes it.

---

### Post by markbuntu on 2008-09-23
If you are using flash9, that will cause this problem more than anything else. You need libflashsupport installed to fix that. The most likely problem is that you have System/Preferences/Sound set to autodetect. You should change it to ALSA.

For a more extensive fix, you can read my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Nutopia on 2008-09-23
Thanks for the tips! Nothing was muted, but I did change my Sound preferences to select ALSA and installed the libflashsupport package - I'll see how it works.

---

