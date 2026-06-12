---
title: "still need recording help"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by cartisdm on 2008-07-15
I'm giving up on my past attempts and I'm starting from ground zero.  I need to find a way to record audio at a certain pre-set time.  It doesn't need to be high quality or complicated.  I'm using kAlarm to launch a browser that will play audio.  Now I just need a way to record it.

---

### Post by cartisdm on 2008-07-15
It looks like Audacity has a timer recording option but I am having problems with the Audio playback.  Visually stuff is moving around but no sound comes from my speakers.  I've found similar posts but none of the solutions seem to work:-?

---

### Post by tonychar on 2008-08-10
I hope you're still hoping for replies, anf that this helps.  It got Sound Recorder working flawlessly...

I couldn't get Sound Recorder to save playable clips.  It appeared to record and save a clip ok, in any format I chose.  Any player I chose would appear to play it, the progress bar would rack up the time, but I got no sounds.

Now I'm sure there is another way to do this, but from in Sound Recorder, going to << File \ Change Device >> and select << HDA Nvidia ( ALSA Mixer) >>  then when you select << File \ Open Volume Control >> it lets you play with the ALSA settings.  

Go to << Switches >> and tick << IEC958 >> << Mix >> and < Stereo Downmix >>  

Then go to << Edit \ Preferences >> and tick every box, wether you'll use them or not.

On the << Playback >> tab, ensure the volume is full on all options EXCEPT << MIC Boost >>, as this distorts horribly.  Set this about three quarters.  

On the << Recording >> tab, open the volume on << Capture >> and << Digital >> to about a quarter.

Close this box, and from the main screen in Sound Recorder, you can select either << Capture >> or << Digital >> as the << Record from Input >> source.

Test this until you get the volume controls right, in the recording vulume section.  How you set that to start recording is beyond me though!

Good luck!

---

