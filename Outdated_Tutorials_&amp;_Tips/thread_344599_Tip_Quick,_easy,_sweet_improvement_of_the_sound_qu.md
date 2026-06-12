---
title: "Tip: Quick, easy, sweet improvement of the sound quality"
date: 2007-01-23
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperDindon on 2007-01-23
Something most users ignore is that the default Dmix's resampling to 48khz quite screws up 44.1khz sound. The Dmix behaviour might change in the future, but for now this isn't the right behaviour for most users.. If you have a standard usage of your desktop, you would like the best sound quality from music and movies and, on the other hand, *while listening music* you might do other stuff requiring sound ( watching Web videos, gaming, voip, .. ). Almost all music is 44.1khz material, so the first right thing to do is to set Dmix default samplerate to 44.1khz.. :
```
#Into /etc/asound.conf

pcm.!default {
   type plug
   slave.pcm {
       type dmix
       ipc_key 1024
       slave {
           pcm "hw:0,0"
           rate 44100
       }
   }
}
```
..in such a way you can enjoy Dmix ( the "default" pseudo-device ) in your music players without quality loss. And if you want to avoid 48khz->44.1khz resampling in movies either, setup your movies players to use the "plughw:0,0" device ( for mono/stereo ), taking into account that no other sound will be played when watching movies ( which may be what you want :) )

Also **from Feisty**, there will be the "samplerate" plugin available in official packages. Once you will have upgraded ( not before ), install the "libasound2-plugins" package and add this line at the top of /etc/asound.conf :
```
defaults.pcm.rate_converter "samplerate"
```
Dmix will then employ a much better resampling algorithm than the default one, and some apps such as Skype(32khz) will greatly benefit from it.


**NOTE 1 :**
My tip doesn't take into account arts, esound, and other sound servers, which may "replace" Dmix and hide your configuration. Note that there's always [a way to get rid of them]("http://ubuntuforums.org/showthread.php?t=384535") - at least for non-too-exotic software.

**NOTE 2 :**
There are others resampling algorithms in the libasound2-plugins package :
> samplerate_best
samplerate_linear
samplerate_medium
samplerate_order
IMO (just) "samplerate" is the best load/quality compromise, but if you're interested in testing also the others simply replace "samplerate" in the asound.conf file by one of the above.

**_NOTE 3 :_**
A specific case is for soundcards doing resampling everything to **48khz** themselves : AC'97 onboard chipsets, all Creative Live and Audigy series, Hercules Fortissimo I/II/III ( not the IV ). Due to their limited power and flexibility, they perform quite crappy resampling on non-48khz material. On Windows this is avoided because kmixer resample everything by default to 48khz ( and certainely perform some other nasty destructive voodoo.. ). We might want something like this in that case : 
```
defaults.pcm.rate_converter "samplerate"  # from Feisty only

pcm.!default {
   type plug
   slave.pcm {
       type dmix
       ipc_key 1024
       slave {
           pcm "hw:0,0"
           rate [COLOR="Red"]48000[/COLOR]
       }
   }
}
```
Same than above except the rate set to 48000. This is the default Dmix configuration, but Dmix is not enabled by default on soundcards featuring "hardware" mixing. Software mixing instead of hardware mixing increases of course the CPU load, but it's negligible on all modern machines, and the difference in sound quality is **really** worth it.

Et voilà!   :grin:

---

### Post by hugmenot on 2007-02-12
And the CPU load? How&#8217;s it affected?

---

### Post by hugmenot on 2007-02-14
[COLOR="Red"]Pay attention that you listen to this with headphones and low volume first. This sample contains inaudible high frequency content at full intensity[/COLOR] and may fry your tweeters.

Listening to udial.wav I still get bad sirening artifatcs with only "samplerate". EDIT: bah, stupid me, I named th file .asound.conf instead of .asoundrc. Now sampelrate alone works well. Thanks!

obsolete &#8595;

How about you? If you don&#8217;t know it udial can reveal low quality resampling cards. Normally you shouldn&#8217;t hear any weird alien-like noises.

---

### Post by Jonie on 2007-11-23
I know this is an old thread, but if anyone still reads it... I tried the suggestions on Feisty, featuring the Audigy SE. The value versions of those cards come without hardware mixing, and here comes dmix, mixing everything to 48k.

As suggested in Note3:

```
defaults.pcm.rate_converter "samplerate" ....
```

putting this in .asoundrc doesn't change anything from the default setup.

using


```
defaults.pcm.rate_converter "samplerate_best" ....
```

improves slightly treble reproduction (removes "aliasing"), however CPU usage while playing mp3 file with Rhythmbox jumps from default 7% to a whooping 25%. Measured on Ahtlon 64 3200+, Feisty running Compiz. 1 GHz or so CPU would hardly avoid skipping with this setting.

---

### Post by SuperDindon on 2007-12-18
> **Jonie said:**
> As suggested in Note3:

```
defaults.pcm.rate_converter "samplerate" ....
```

putting this in .asoundrc doesn't change anything from the default setup.

As the time I was writing this topic Dmix's default resampling algorithm was an internal algorithm, not "samplerate", and this likely hasn't changed yet since I can't find any line in the changelog and "samplerate" is still part of the alsa-plugins package ( "samplerate***" are actually plugins taking advantage of libsamplerate, i.e an external library not really closely related to ALSA )

---

### Post by DShroud on 2008-01-21
I'm using the on-board sound on my motherboard which uses the Realtek ALC850.  I was experiencing bad sound quality, popping, crackling, and major distortion of any loud really low or high frequency sounds.

After reading through all the guides in this thread, none helped, but I did notice a trend, most said to lower the volume.  After further inspection, I noticed alsamixer provides the user with the measure of adjustment to the dB gain, to all channels.

My fix was to lower the PCM level so that the dB gain shown at the top left hand corner in alsamixer was equal to zero.  Any higher or lower than that would lead to major distortion of sound.

---

### Post by hugmenot on 2008-01-21
Yeah, for some strange reason the PCM slider is set to amplify above 0dB. Of course this leads to clipping of the audio. The General slider should be safe to put to the max, though.

---

