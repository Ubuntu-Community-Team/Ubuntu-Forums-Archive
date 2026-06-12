---
title: "Speaker problems"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by hollandmc on 2008-05-17
For some reason, my speakers (which have always worked fine) won't play any sound all of a sudden. They're just generic Dells (came with my Demension 2400)... It was odd: even though sound worked fine with Banshee and Totem, it wouldn't with any movie or sound editors (I'd always get an "audio device not detected" thing or "unknown audio problem") and it would play sans sound. Yesterday, in an attempt to get a video editor to work (I need to know what's being said in the videos to properly edit them and no video editor seemed to recognize the speakers), I unplugged my speakers and plugged in a different set. The computer didn't recognize them at all and I couldn't play any sound. I put the Dells back in... Now they won't work at all. Banshee and Totem both stay silent while playing and I can't for the life of me figure out why. The speakers themselves are fine -- they're plugged in and they've always worked well -- but the computer refuses to recognize them. Help? 

(Sorry if I didn't give enough information or if it seems unclear... it's 3 AM and I'm not entirely sure what I'm talking about, anyway.)

Also, I'm using Hardy Heron on a Dell Dimension 2400.

(Thanks in advance. You guys are always great)

---

### Post by Xiong Chiamiov on 2008-05-17
I've done quite my share of late-night/early-morning sound troubleshooting, so I feel for ya.

[This sticky]("http://ubuntuforums.org/showthread.php?t=205449") from the multimedia forum is quite exhaustive, so try looking through there first.

---

### Post by hollandmc on 2008-05-17
I tried everything on the guide but to no avail... Ubuntu detects my sound card and speakers, but they just won't work. I re-installed alsa, downloaded all the drivers available (the speakers are supported; Intel --> ICH southbridge AC97 audio --> ICH4), restarted my computer, and nada. I did everything else applicable and it didn't work... I can re-install Hardy Heron if need be (my documents are all backed up), but I'd prefer not to if at all possible. 

When I go into terminal and use ```
sudo alsa reload
``` (I have no idea what that does but I assumed it would just jumpstart alsa), it says ```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marcus/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5699(pulseaudio). 
Unloading ALSA sound driver modules: snd-atiixp-modem snd-via82xx-modem snd-intel8x0m snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-intel8x0 snd-ac97-codec snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-atiixp-modem snd-via82xx-modem snd-intel8x0m snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
```

I then tried ending pulseaudio via System Monitor to see if it was causing problems, but it didn't do anything... I vaguely recall ending a process with a name that had "audio" or "sound" in yesterday while trying to kill LiVES (it was freezing up my computer); could that have anything to do with it?

Oh, and when I go to System --> Preferences --> Sound, everything is set to autodetect (as it was when my speakers were working), but it just won't work. I've also tried it by changing everything to the speakers themselves (I'm given the options "Intel 82801DB-ICH4" and "Intel 82801DB-ICH4 IEC958") and OSS. Nothing helps.

Any suggestions? I'm really at a loss here... 

I know enough to know how to make sure I don't destroy my computer through sudo, so I should be alright there, but other than that I've got no idea what I'm going.

---

