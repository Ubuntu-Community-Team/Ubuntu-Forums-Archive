---
title: "Another sound issue"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by azizzle on 2008-05-31
This morning, I had sound in all of my programs. I had one issue, though, not being able to watch videos online while rhythmbox was playing. I searched around, and found [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739).
So after I followed those instructions, my sound went out in rhythmbox, vlc and in system>preferencces>sound when I press the 'Test' button, there is no sound, but in all my other apps sound works just fine.

The weird thing, though, is when I'm running these apps, with PulseAudio volume meter open, it shows that both rythmbox, vlc and the sound test are producing sound. PA volume meter shows no reading when my other apps are playing, when sound is actually coming out of my speakers. So something is backwards somewhere, any body have this happen?

btw: This is what I get when I start pulseaudio from the terminal:
$ pulseaudio
W: pid.c: Stale PID file, overwriting.
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL front:0
W: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL front:1
W: alsa-util.c: Cannot find fallback mixer control "PCM".
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL front:1

At this point I've messed with all of my settings so much I think I should just tear down all drivers and start from scratch. Anybody know how I should go about doing this?

---

### Post by azizzle on 2008-05-31
Bump

Is there something wrong with my alsa? Is that why pulse can't find CTL and PCM?

---

### Post by CloudFX on 2008-05-31
Have you had a look at this guide?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by azizzle on 2008-05-31
Yeah I've looked at that guide. I did the fresh alsa install to no avail. I'm really disappointed and I think I'm going to have to do a fresh install :(

---

### Post by azizzle on 2008-05-31
I just don't understand what to do next. Here's the info I have right now:

*MPlayer and Totem work fine. Sound and everything. On MPlayer pulseaudio is selected as the driver. Totem I can't find.

*The GDM sound, login sound, Rhythmbox, VLC and the rest of the system sounds don't work. 

*VLC doesn't have sound, but it doesn't have an option for Pulseaudio in the output. I can't find how to change that.

*Rhythmbox, I've found out uses gstreamer. I have gstreamer-pulse plugin, but when I open gstreamer properties there is an option for pulse, but it says that it's unsupported.

*When I kill the pulse audio process and start it in terminal I'm still getting the output that I indicated in the OP. 

* I've removed and recompiled alsa twice using the Comprehensive Sound Problem thread. 

* When I open the volume meter in Pulseaudio applet, it shows that signal is being produced by both VLC and Rhythmbox, but not MPlayer and totem. But I guess that's because it says "Showing signal levels of ALSA PCM on Front:0 (CA0106) via DMA".

Can somebody please advise?

---

### Post by markbuntu on 2008-06-01
Try getting the alsa plugin for pulseaudio from the repos and switching everything to alsa, especially your Sound preferences because they do not seem to be working on automatic. Then set the default alsa sound to your sound card instead of pulseaudio.

That's what worked for me.

---

