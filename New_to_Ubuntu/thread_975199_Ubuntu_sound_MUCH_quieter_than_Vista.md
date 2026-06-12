---
title: "Ubuntu sound MUCH quieter than Vista"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by ubername on 2008-11-08
Following on from this thread, with the somewhat unhelpful title of 'please help the Noob'

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5822850](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5822850)

In Vista, my sound is clear and great,  - I can't put the volume control much above halfway before walls start to shake etc.

However in Ubuntu Intrepid, I need to have the sound practically all the way up to have it audible. I have tried messing with various settings (using volume control, alsamixer, making sure the volume control is using the corrrect channel ('front' in my case)) but I cant seem to get the basic sound right. Any helpful hints, or things I should post to help work this out? Does anyone else have this as well?

I am using a built in sound card on an intel pentium D setup.

---

### Post by ubername on 2008-11-08
Something which may be relevant: My alsamixer only shows one channel called master, which is turned all the way up, with the 'card' identified as PulseAudio, but my volume control shows several channels (Master, PCM, front etc.) with the device identified as HDA Intel (ALSA mixer).

---

### Post by shifty_powers on 2008-11-08
```
alsamixer
```

in a terminal and make sure it is turned up :D

---

### Post by ubername on 2008-11-08
> **shifty_powers said:**
> ```
alsamixer
```

in a terminal and make sure it is turned up :D

Thanks, I've done that, see my previous post about alsamixer channels v. volume control channels.

---

### Post by ubername on 2008-11-08
Another thing I should mention - I have headphones which boost the bass sound if it is running above a certain level. In Vista this works but in Ubuntu it does not because the sound is so quiet.

TIA for any help.

---

### Post by kansasnoob on 2008-11-08
Try installing gnome-alsamixer:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video, note the toggles in mine:

[ATTACH]91724[/ATTACH]

[ATTACH]91725[/ATTACH]

---

### Post by ubername on 2008-11-09
> **kansasnoob said:**
> Try installing gnome-alsamixer:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video, note the toggles in mine:

[ATTACH]91724[/ATTACH]

[ATTACH]91725[/ATTACH]

Thanks, the gnome gui is a bonus, (better than 'volume control') but what do you mean by 'note the toggles in mine'? Sorry to be dumb. I've looked at your 'tick boxes' but I have  a different card to you (I think) so I don't have the same options.

---

### Post by ubername on 2008-11-22
Hmm. It seems this is no longer the case, because (sob) the sound has gone really quiet in vista now as well! This is not the way I wanted to go!

---

### Post by Periswell on 2008-11-22
are you sure you're not playing a really quiet song? =]

on a serious note have you tried in terminal gnome-volume-control and put the 'front' ones up to maximum?

---

### Post by insane_alien on 2008-11-22
if that doesn't work out, go to alsamixer(terminal and type in 'alsamixer') and experiment there.

---

### Post by ubername on 2008-11-22
From alsamixer at the prompt:

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused

Could this be it?

Also starting Pulseaudio device chooser from applications>sound & video menu creates a 'starting' icon(?) in the task bar but then just goes away.

---

### Post by Martje_001 on 2008-11-22
Does it work when you turn off Pulseaudio and choose ALSA instead?

System --> Preferences --> Sound

---

### Post by ubername on 2008-11-22
> **Martje_001 said:**
> Does it work when you turn off Pulseaudio and choose ALSA instead?

System --> Preferences --> Sound

Sorry, getting a bit confused here: what exactly should I do?

Trying to test this, if I set 

System --> Preferences --> Sound (playback options) to ALSA or Pulse audio (rather than Autodetect) I get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

In fact now I have tried a bit further I get the same thing even after 'sudo alsa force-relaod' for autodetect

---

### Post by Martje_001 on 2008-11-22
You could also try removing pulseaudio altogether (make sure you reboot after it).

---

### Post by Onesimus on 2008-11-22
I found that I had quiet sound until I turned up PCM.  To do this, right click on the volume control in the top right hand corner of screen.

Select 'Open volume control'

Increase on PCM.  (Not sure what PCM is, but it worked for me)

---

### Post by ubername on 2008-11-23
I found [url]http://forums.techguy.org/
windows-vista/
699808-sound-really-quiet.html
[/url] fixed it in Vista.

Perhaps I am wrong, but there is still something odd about ubuntu /8.10 / pulseaudio / alsa setup.

You can see how I have nailed down the problem! (Not)


I'm now geting the 'plug headphones in and sound fades' scenario again [http://ubuntuforums.org/showthread.php?t=913328](http://ubuntuforums.org/showthread.php?t=913328)

---

### Post by sportscrazed2 on 2008-11-23
are you using vlc?  the sound is usually louder in vlc for me

---

### Post by Tom--d on 2008-11-23
First thing is remove Pulseaudio in Synpatic Package manager. (Search for pulseaudio and remove it).

Then in Sound make everything ALSA.

Reboot

Then go into alsamixer and then make everything 100%

---

### Post by kansasnoob on 2008-11-23
> **ubername said:**
> Hmm. It seems this is no longer the case, because (sob) the sound has gone really quiet in vista now as well! This is not the way I wanted to go!

That sounds like a hardware issue!

Is the sound working right in Vista now?

---

### Post by ubername on 2008-11-23
> **kansasnoob said:**
> That sounds like a hardware issue!

Is the sound working right in Vista now?

yup,  good in vista;  not in ubuntu (when headphones plugged in)

---

### Post by kansasnoob on 2008-11-23
> **ubername said:**
> yup,  good in vista;  not in ubuntu (when headphones plugged in)

Try installing gnome-alsamixer! It's in synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in the apps menu under Sound & Video. Lot's of toggles! Look at mine:

[ATTACH]93908[/ATTACH]

[ATTACH]93909[/ATTACH]

---

### Post by ubername on 2008-11-23
Hhmm...

All getting a bit strange now. Forgetting the Vista bit which seems sorted, I am now in the position where everything works fine sound-wise when I boot. Speakers work, and when I plug headphones in, they work too. I unplug them and voilà, there is the sound from the speakers. Lovely... I plug in the headphones again and, oh dear, the sound starts fading until it has gone (Unplug. No sound from speakers). Any further help gratefully received.

---

### Post by Snappo on 2008-11-23
I've noticed this as well with my laptop... oh well my ipod headphones are getting some use. :)

---

### Post by ubername on 2008-11-24
Yup, it's definitely the unplugging then re-plugging the headphones which causes the sound to fade. I I do
sudo alsa force-reload
with the headphones in then they work fine.

---

### Post by sprince09 on 2008-12-29
I seem to be having the exact same problem (headphones cause sound to fade, sudo alsa force-reload temporarily fixes it)... any updates on this?

Intel HDA soundcard for me.

---

### Post by 11lettenJ on 2009-01-01
I didnt have a problem with fading but my sound was just plain quiet. I could barely hear it through the headphones or speakers. I did install the alsamixer. I turned PCM, front, master, and some others all the way up but most importantly, I changed everything from autodetect to ALSA. works great, I nearly went deaf the first time I turned on Benny Benassi vs. Public Enemy- Bring the Noise with my headphones in.

---

### Post by ubername on 2009-01-02
> **11lettenJ said:**
> I didnt have a problem with fading but my sound was just plain quiet. I could barely hear it through the headphones or speakers. I did install the alsamixer. I turned PCM, front, master, and some others all the way up but most importantly, I changed everything from autodetect to ALSA. works great, I nearly went deaf the first time I turned on Benny Benassi vs. Public Enemy- Bring the Noise with my headphones in.

Doesn't make any difference for me, but thanks for joining in, and welcome to the community!

---

