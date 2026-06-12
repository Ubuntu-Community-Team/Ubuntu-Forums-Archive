---
title: "Headphones acting weird: 16.04.1, Dell XPS 9550"
date: 2016-08-22
forum: New to Ubuntu
---

### Post by derek.x.kwan on 2016-08-22
To start, I'm aware of [this thread]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1575078") and may end up adding to that thread if I can't come up with a solution...

It seems lately that I've only been able to get sound through my headphones on my XPS 9550 if I don't plug in my headphones all the way. I can tell **pulseaudio** is detecting when my headphones are plugged in or not (via **pavucontrol**) and when the headphones are plugged in, I can't get sound through them and when they aren't, I can. This usually requires some fiddling around in **alsamixer** to make sure my speakers are muted and my headphones aren't. I've done some digging and have made sure that in /usr/share/pulseaudio/alsa-mixer/paths, **analog-output-headphones.conf** has this:
```
[Element Speaker]
switch = on
volume = ignore
```
And the end of my **alsa-base.conf** in /etc/modprobe.d looks like this:

```
options snd-usb-audio index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-headset-multi
options snd-hda-intel position_fix=0 enable=yes
```

I'm not sure if that's the correct model, it used to be dell-m6-amid which didn't work and led me to change it, I've also tried position_fix=1 with no dice. I'm on a Dell XPS 9550 with a newly upgraded BIOS, 4.4.0-34-generic kernel, and on Ubuntu Studio 16.04.1. I've also done the ol' compressed air in the headphone jack with no help (pulseaudio is detecting the headphones correctly anyways so it probably wasn't an issue in the first place). Thoughts? Maybe this is a hardware issue?

Thanks!

---

