---
title: "Pulseaudio needs more work, SQ is subpar, really ..."
date: 2011-05-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xeizo on 2011-05-25
When comparing SQ in Pulseaudio with KDE/Phonon using VLC as backend the quality of sound in Pulse is laughable.
 
KDE/Phonon/VLC sounds pretty much transparent ie as bare ALSA.
 
Pulse/Gstreamer has two modes; without tweaking levels the sound is powerful but usually quite heavily distorted(distorsion occurs inside Pulse)
 
The other mode is when tweaking the level of the inputted audiostream, distorsion can be almost elliminated but then the sound appears weak and without body. Probably because of a significant amount of resolved bits lost when tweaking the level.
 
KDE/Phonon/VLC manages to sound both undistorted and with full body ie no lost bits.
 
"Someone" needs to give Pulse a serious overhaul so that it can manage input streams without distorting them. In it's current state Pulse is unusable for anyone requiring  "HiFi"-sound.

---

### Post by seeker5528 on 2011-05-26
> **xeizo said:**
> "Someone" needs to give Pulse a serious overhaul so that it can manage input streams without distorting them. In it's current state Pulse is unusable for anyone requiring  "HiFi"-sound.

Pulseaudio wasn't designed for high quality/low latency of sound, it was designed to provide convenience of features with "good enough" sound.

If you use Pulseaudio there is going to be a trade off in quality or latency or both depending on the options used, that's a design decision based on the idea that it's not really necessary for the desktop and for the applications that need low latency there is jackd that is designed for low latency.

From the standpoint of the Ubuntu devs what's best is in the middle somewhere, not too much of a performance drag on older machines, not too bad of sound quality on newer machines. Whether Ubuntu uses the best options by default may be a question and if the quality seems *that* bad you might want to look at the configuration.

I only keep the pulseaudio stuff that dependencies require, so I can't really help you with how you would go about changing the configuration.

Later, Seeker

---

### Post by xeizo on 2011-05-27
I have done as yourself and removed all Pulse except dependencies. How could I not. The sound is excellent when using only Alsa.

What bothers me about Pulse is that it is the default and less knowing people may think that Ubuntu in itself have bad sound quality.

One possibility is to do like the KDE-team have done in Phonon, to provide an option to select "hardware only without any conversions" in the sound control panel when using ALSA(the option only appears when Pulse is removed from the system, so it may be a bug which is a feature). 

It works/sounds excellent, while still maintaining a large part of the sound server functionality ie apps do not lock the soundcard.

---

### Post by hugmenot on 2011-05-28
What you&#8217;re going on about here is bordering on what would get you reprimanded or banned on some digital audio related forums (i.e., making unsubstantiated claims about the quality of sound).

Anyhow, the one and only quality-related module in Pulseaudio is the resampling algorithm used, and the Ubuntu package chooses a fast one to avoid having Pulseaudio use several percent of CPU while streams are playing.

Check resample-method in /etc/pulse/daemon.conf. If you don&#8217;t mind burning a some CPU cycles you can make it use a higher quality resampler

doc:
```
       resample-method=  The resampling algorithm to use. Use one of src-sinc-best-
       quality,  src-sinc-medium-quality,  src-sinc-fastest,   src-zero-order-hold,
       src-linear,  trivial, speex-float-N, speex-fixed-N, ffmpeg. See the documen&#8208;
       tation of libsamplerate and speex for explanations of the different src- and
       speex- methods, respectively. The method trivial is the most basic algorithm
       implemented. If you're tight on CPU consider using this. On the  other  hand
       it  has  the worst quality of them all. The Speex resamplers take an integer
       quality setting in the range 0..10 (bad...good). They exist in two flavours:
       fixed  and  float. The former uses fixed point numbers, the latter relies on
       floating point numbers. On most desktop CPUs the float point resampler is  a
       lot  faster,  and  it also offers slightly better quality. See the output of
       dump-resample-methods for a  complete  list  of  all  available  resamplers.
       Defaults  to  speex-float-3. The --resample-method command line option takes
       precedence. Note that some modules overwrite or  allow  overwriting  of  the
       resampler to use.
```

---

### Post by hugmenot on 2011-05-28
I see you are talking about levels too.

While looking at daemon.conf you can also try to toggle on flat-volumes setting, which always attenuates the physical DAC before it touches software mixer volume, i.e., it merges hardware and software volumes and staggers them. You can watch alsamixer -c0 to see this happen. No bits lost whatsoever.

[IMG]http://i.imgur.com/WWJaG.gif[/IMG]

---

### Post by Harry33 on 2011-05-29
> **hugmenot said:**
> 
...
Check resample-method in /etc/pulse/daemon.conf. If you don’t mind burning a some CPU cycles you can make it use a higher quality resampler

doc:
```
       resample-method=  The resampling algorithm to use. Use one of src-sinc-best-
       quality,  src-sinc-medium-quality,  src-sinc-fastest,   src-zero-order-hold,
       src-linear,  trivial, speex-float-N, speex-fixed-N, ffmpeg. See the documen&#8208;
       tation of libsamplerate and speex for explanations of the different src- and
       speex- methods, respectively. The method trivial is the most basic algorithm
       implemented. If you're tight on CPU consider using this. On the  other  hand
       it  has  the worst quality of them all. The Speex resamplers take an integer
       quality setting in the range 0..10 (bad...good). They exist in two flavours:
       fixed  and  float. The former uses fixed point numbers, the latter relies on
       floating point numbers. On most desktop CPUs the float point resampler is  a
       lot  faster,  and  it also offers slightly better quality. See the output of
       dump-resample-methods for a  complete  list  of  all  available  resamplers.
       Defaults  to  speex-float-3. The --resample-method command line option takes
       precedence. Note that some modules overwrite or  allow  overwriting  of  the
       resampler to use.
```

The default resample-method is speex-float-1 ATM (the latest pulse-audio package).

---

### Post by xeizo on 2011-05-29
As hugmenot says it may be simple matter of configuration, I'm more concerned about the symptoms and not an expert on what causes them. The problem in itself is easy to hear for anyone not toally deaf I guess.

It's possible that the lowly SPEEX resampling algorithm introduces distorsion in such amount as my ears mistakes it for saturation. I'll try the best algorihtm the next time I use pulse, however, I'm not in a hurry reinstalling it.

Cpu-usage shouldn't be an issue on anything Core2 and above. 

If it it's just configuration **I would suggest putting a Sound Quality-button into Pavucontrol, in ie 5 steps from best to worst**. People are used to these quality-steps when they convert audiofiles, so there should be no confusion.

---

### Post by hugmenot on 2011-05-29
Since you posted in the Testing and Development forum for Ubuntu+1 I would think trying it out and systematically comparing results would be worthwhile. Post a bug on Launchpad with your findings.

Otherwise your post is ineffective.

---

### Post by xeizo on 2011-05-29
> **hugmenot said:**
> Since you posted in the Testing and Development forum for Ubuntu+1 I would think trying it out and systematically comparing results would be worthwhile. Post a bug on Launchpad with your findings.

Otherwise your post is ineffective.

That's true, since I seem to be the only one caring a bit about SQ I guess I'll have to push it myself. Mabe past Launchpad and directly to the original Pavu-developers.

Even if the problem is easy to fix through a configuration file, that's not the Ubuntu-spirit because if we just wanted to edit text-files to get things done there wouldn't be any need for a Ubuntu-desktop in the first place.

---

### Post by ssam on 2011-05-30
maybe your issue is related to this
[http://www.pulseaudio.org/wiki/PulseAudioStoleMyVolumes](http://www.pulseaudio.org/wiki/PulseAudioStoleMyVolumes)


also, from the PA website
"2010-02-12: Canonical are hiring a sound software engineer. More details can be found at [http://webapps.ubuntu.com/employment/canonical_UDSE/](http://webapps.ubuntu.com/employment/canonical_UDSE/) "
i can't see the ad any more so i guess the got someone.

---

