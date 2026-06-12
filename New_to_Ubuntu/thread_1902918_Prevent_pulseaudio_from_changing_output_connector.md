---
title: "Prevent pulseaudio from changing output connector?"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by rectec794613 on 2012-01-01
Hi I already posted about this, but received no response with several bumps over several days. Basically, if I re-insert my headphones into the jack, PulseAudio changes the output connector to "Analog Headphones" which produces no sound. So it forces me to manually change it back to "Analog Speakers" through the sound settings to get the audio working properly. This is a real nuisance. Any help is *greatly* appreciated. I'm sick of that feeling of dread the moment I accidentally disconnect my headphones. Please help!

P.S. Hundredth post! That cheers me up. : )

---

### Post by lechien73 on 2012-01-01
When you change the settings back to "Analog Output", do the headphones work, and are the speakers muted?

You can change the switching mechanism, by adjusting the paths in /usr/share/pulseaudio/alsa-mixer/paths. The files you probably want to be researching are analog-output-headphones.conf and analog-output.conf (the comments in analog-output.conf.common are helpful too).

However, to see what we might need to change, could you please post the output of:

```
aplay --list-devices
```

Thanks

---

### Post by rectec794613 on 2012-01-01
Hello and thanks for the response. Sorry for the delay. I got into the analog-output-headphones.conf file and investigated, however I'm unsure what to do next. Here's the output of that command:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I figure the automatic output switching that pulseaudio does is a feature. I don't believe I need it, as my sound card(?) already manages that for me. So it should be as simple as disabling that feature. I don't recall having this problem before with pulse on this computer, so it could've been from an update.

---

### Post by lechien73 on 2012-01-02
Hi and thanks for your reply,

Could you try opening a terminal window and typing:

```
alsamixer
```

Check that the Headphones level doesn't have "MM" beneath it. If it does, then use the arrow keys to highlight Headphones, and then press M to unmute.

Rather than try to disable the auto-switch, it might be a better idea to see if we can fix PulseAudio so that it switches properly.

---

### Post by rectec794613 on 2012-01-03
I ran alsamixer. The headphones level has '00' under it and I can't change it. Pressing M changes '00' to 'MM'.

---

### Post by Viybel on 2012-01-03
I have exactly the same problem on a fresh Kubuntu 11.10 installed on an Asus N73S laptop.

Here is the output of "aplay --list-devices", in case you need it:

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC269VB Digital [ALC269VB Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```In alsamixer, the Headphone column is unmuted (i.e. 00) but there is no sound level bar on top of the [00] so the sound level cannot be adjusted (whether the headphones are plugged in or not).

If I max out the volume in any music player, I get a very faint signal of the music in the headphones.

I reported this in [bug #911331 ]("https://bugs.launchpad.net/ubuntu/+bug/911331"), which might be a duplicate of [bug #909348]("https://bugs.launchpad.net/ubuntu/+bug/909348") and [bug #817943]("https://bugs.launchpad.net/ubuntu/+bug/817943"), but not exactly like [bug #829843]("https://bugs.launchpad.net/ubuntu/+bug/829843").

It looks like [bug #817943]("https://bugs.launchpad.net/ubuntu/+bug/817943") is the culprit here.

It's quite annoying and we don't know when it's going to be resolved, so it would be nice if someone could explain how we can disable the automatic switching mechanism in the meantime (I didn't understand much of the documentation in analog-output.conf.common). We don't need this feature anyway because, as rectec794613 mentioned, the speaker muting is already managed (somehow) when the headphones are plugged in, even if the output connector is set back to "Analog Speakers".


Thanks in advance for your help.

Vianney

---

### Post by lechien73 on 2012-01-03
Yes, I'm starting to become convinced that we need to add options to alsa-base.conf in the /etc/modprobe.d directory. I'm just not sure which ones :)

I'll keep looking, though, in case someone with more experience than me doesn't solve it in the meantime!

---

### Post by rectec794613 on 2012-01-03
> **Viybel said:**
> I have exactly the same problem on a fresh Kubuntu 11.10 installed on an Asus N73S laptop.

Here is the output of "aplay --list-devices", in case you need it:

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC269VB Digital [ALC269VB Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```In alsamixer, the Headphone column is unmuted (i.e. 00) but there is no sound level bar on top of the [00] so the sound level cannot be adjusted (whether the headphones are plugged in or not).

If I max out the volume in any music player, I get a very faint signal of the music in the headphones.

I reported this in [bug #911331 ]("https://bugs.launchpad.net/ubuntu/+bug/911331"), which might be a duplicate of [bug #909348]("https://bugs.launchpad.net/ubuntu/+bug/909348") and [bug #817943]("https://bugs.launchpad.net/ubuntu/+bug/817943"), but not exactly like [bug #829843]("https://bugs.launchpad.net/ubuntu/+bug/829843").

It looks like [bug #817943]("https://bugs.launchpad.net/ubuntu/+bug/817943") is the culprit here.

It's quite annoying and we don't know when it's going to be resolved, so it would be nice if someone could explain how we can disable the automatic switching mechanism in the meantime (I didn't understand much of the documentation in analog-output.conf.common). We don't need this feature anyway because, as rectec794613 mentioned, the speaker muting is already managed (somehow) when the headphones are plugged in, even if the output connector is set back to "Analog Speakers".


Thanks in advance for your help.

Vianney
Exactly. Glad to see I'm not the only one who has this problem. And thanks for that bug report. I have no clue how to submit one. Output switching seems to be a basic hardware level mechanism that's been around for a while. I don't know much about it, but I'll get back if I find some info.

---

### Post by rectec794613 on 2012-01-07
I recently set up Arch as a secondary OS and installed X11, Gnome-Shell, Pulse... all the goodies. I found that I don't get this problem with that particular install of PA, so I figure it must be something that Ubuntu does with Pulse's settings that makes it behave this way.

---

### Post by Viybel on 2012-01-08
I did this [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules) and it solved my problem.

In some similar bug reports, other people solved their problem with this: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I have to say this was really painful for me: I had to search for a dozen hours before finally being able to use my headphones on a very common computer (Asus N73S).

Vianney

---

### Post by rectec794613 on 2012-01-08
[IMG]http://media.steampowered.com/steamcommunity/public/images/avatars/63/63dba418aa1b4201e96f0dc0a591db4a6dd00c4d.jpg[/IMG]
It worked. I installed the package and rebooted. Then I opened up sound settings and plugged in my headphones. It changed to headphones which worried me, but then I turned on some music and I could hear it! No more hassle now.

Thank you both for your hard work. Hopefully this will help solve people's problems in the future. If anyone still needs help, feel free to post. Otherwise, I'll go ahead and mark this thread as solved.

---

### Post by lechien73 on 2012-01-08
Good stuff...glad it's finally working for you.

You're probably better marking the thread as [SOLVED], and letting others start their own threads. You'll be delighted by the satisfying feeling it gives you ;)

---

### Post by Viybel on 2012-01-22
This bug is back, even after installing Alsa Driver Modules ([https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)).

Adding this PPA solves it:

sudo add-apt-repository ppa:diwic/jack-detection

Vianney

---

### Post by rectec794613 on 2012-01-22
> **Viybel said:**
> This bug is back, even after installing Alsa Driver Modules ([https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)).

Adding this PPA solves it:

sudo add-apt-repository ppa:diwic/jack-detection

Vianney
Well I haven't had any problems yet. I'm holding off on installing the kernel update and the ALSA module update, though. Thanks for sharing this ppa. Hopefully it'll come in handy if something goes wrong.

---

### Post by rectec794613 on 2012-01-25
So I updated the alsa modules and to kernel-15 and the problem's back. So I added that repo and apt-get updated. But before I upgrade, should I remove the repo for the old modules? What about the modules themself? I'll hold off on upgrading the modules until I get more info. Thanks.

---

### Post by Viybel on 2012-01-26
No, that's what apt is here for.

---

### Post by rectec794613 on 2012-01-26
> **Viybel said:**
> No, that's what apt is here for.
Could you please clarify?

---

### Post by rectec794613 on 2012-02-04
Ok I installed the new pulseaudio packages and restarted.

My audio didn't work afterwards. I fixed it by removing .pulse and restarting. I'll make a how-to and post the link here later.

---

