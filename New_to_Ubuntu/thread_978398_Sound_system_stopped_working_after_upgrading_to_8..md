---
title: "Sound system stopped working after upgrading to 8.10"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-11
Hi
Thank you for reading my post
My sound system stopped working after I upgrade to 8.10

Explanation of what test i have performed so far:

1- restart the system several time and apply all updates
2- open System> Preferences>Sound and Tried all available options like OSS, Pulse Audio Server, ALSA, HDA Intel Analog and digital result:

- selecting OSS and HDA Analog and pressing test result in the following error :

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

```
while other items shows a **Testing Pipeline** windows with a progress bar and no sound in the spearker yet.

3- Amarok shows that it play something even the equlizer moves but no sound in the speaker.


Now, would you please let me know which sound system I should select between all those sound system and what other tests I should perform to find the root cause of this problem?

Thanks

---

### Post by rhuea on 2008-11-11
Hi, i had the same problem that you had now. Luckily someone answered me and now its fixed. here is the linked he gave me.

[http://ubuntuforums.org/showthread.p...audio+intrepid](http://ubuntuforums.org/showthread.p...audio+intrepid)

I have never performed the optional steps, 1a and 1b

---

### Post by legolas_w on 2008-11-11
Any comment?
I performed all steps mentioned in [http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid](http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid) with no luck.

Thanks.

---

### Post by mapes12 on 2008-11-11
Can you get to ```
Alsamixer
``` from Terminal?

---

### Post by legolas_w on 2008-11-11
Yes,

 and it shows only one bar for playback and one bar for capture :-o
I remember that in 8.04 there was several bar for controlling the voice but now there is only one.

Thanks.

---

### Post by legolas_w on 2008-11-11
And I have a bit of more information :

when I execute ```
sudo alsa reload
``` command I get the following output:



```

legolas@NEEPER:~$ sudo alsa reload
[sudo] password for legolas: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/legolas/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5738(pulseaudio) 5866(mixer_applet2). 
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.


```

---

