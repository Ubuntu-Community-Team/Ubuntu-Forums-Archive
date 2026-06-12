---
title: "Some sound issues (new user)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Extraneous on 2008-04-25
[b]Edit: SOLVED

Needed to set the default Alsa device to my headset. Took many hours of trying every possible solution under the sun before I found out how to do this. Thanks to all who helped.[/b]

OK well I finally got around to installing Ubuntu (Dual-booting with Vista) and all seems to be fine and dandy, bar a couple of things.

It *is* possible for me to get sound, sometimes. The tests in System > Preferences > Sound work, after I've set it to my audio device (I have a USB headset). Rhythmbox will also play my music fine. However despite many fiddling with options, I can't get VLC to play sound (Audio or Video files), or Amarok.

I also can only get video, not sound for flash videos in FireFox (e.g. YouTube).

I've looked around the forums and tried a few things, but nothing seems to have any effect. So far as Flash goes trying to install flashplugin-nonfree just tells me I have the latest version already.

I'm using Hardy Heron (8.04) 64-bit.

I'd really appreciate a hand as I've spent a good couple of hours on this to no avail!

---

### Post by PeterJS on 2008-04-25
The flash problem is a known issue with the 64 bit flash hacks and pulse audio. You can install libflashsupport to try and make flash work with pulse audio, but it is *very* unstable on 64 bit systems, hence the reason it was made optional during the betas.

For amarok and vlc you might try running them under OSS emulation:
```

padsp vlc

```
```

padsp amarok

```

---

### Post by Extraneous on 2008-04-25
> **PeterJS said:**
> The flash problem is a known issue with the 64 bit flash hacks and pulse audio. You can install libflashsupport to try and make flash work with pulse audio, but it is *very* unstable on 64 bit systems, hence the reason it was made optional during the betas.

For amarok and vlc you might try running them under OSS emulation:
```

padsp vlc

```
```

padsp amarok

```

Ah, so there's no way to watch Flash videos? Damn.

Also, is that the only way I can get VLC and Amarok to work? It seems to be fine for other people, only me having trouble.. I can see video in VLC, just not get any sound. Same with Amarok :(.

---

### Post by hermes0710 on 2008-04-25
Reinstall pulseaudio and libflashsupport and reboot:

```
sudo apt-get install --reinstall pulseaudio
```

```
sudo apt-get install libflashsupport
```

---

### Post by Extraneous on 2008-04-25
> **hermes0710 said:**
> Reinstall pulseaudio and libflashsupport and reboot:

```
sudo apt-get install --reinstall pulseaudio
```

```
sudo apt-get install libflashsupport
```

No dice, nothing's changed.

I'm sure it's probably just some simple setting I'm missing (other than flash)..

---

### Post by hermes0710 on 2008-04-25
> **Extraneous said:**
> No dice, nothing's changed.

I'm sure it's probably just some simple setting I'm missing (other than flash)..

The suggestion had to do with flash and mp3 playback together. Is this working?

---

### Post by Extraneous on 2008-04-25
> **hermes0710 said:**
> The suggestion had to do with flash and mp3 playback together. Is this working?

Alas, no.. It re-installed Pulseaudio and installed libflashsupport, I rebooted and the exact same problems remain. Thanks for the suggestion though! At least it feels like I'm trying :).

---

### Post by Extraneous on 2008-04-25
Any ideas? I can live without Flash but I'd like to be able to play videos without having to boot into Vista..

---

### Post by PeterJS on 2008-04-25
> **Extraneous said:**
> Any ideas? I can live without Flash but I'd like to be able to play videos without having to boot into Vista..

Have you tried OSS emulation?

For VLC do you have the package **vlc-plugin-pulse** installed and none of the other vlc-plugin-* packages installed?

For Amarok it looks like the Pulse Audio output plugin is in the **libxine1-misc-plugins** plugins package.

---

### Post by Extraneous on 2008-04-25
Already have the vlc-plugin-pulse package.. How do I check if I have the other vlc-plugin-* packages installed? And I get "E: Couldn't find package" for the Amarok package.

OSS emulation didn't work either

---

### Post by PeterJS on 2008-04-25
> **Extraneous said:**
> Already have the vlc-plugin-pulse package.. How do I check if I have the other vlc-plugin-* packages installed? And I get "E: Couldn't find package" for the Amarok package.

OSS emulation didn't work either

For the Amarok package it's entirely possible that I got the package name wrong in that post, but either way here's the official package page for it:
[http://packages.ubuntu.com/hardy/libxine1-misc-plugins](http://packages.ubuntu.com/hardy/libxine1-misc-plugins)
You can download the deb package at the bottom of the page.

To check on the VLC plugins, it' probably be easiest to open synaptic and search for *vlc-plugin-*

---

### Post by Extraneous on 2008-04-25
I did have one other vlc-plugin installed, so I removed that but, alas, still no luck. I suppose I'll have to continue with Vista for my video-viewing needs..

Thanks for being so patient with helping me.

Edit: AHA! I fixed it. As I suspected it were something simple. My default audio device in Alsa was set to my onboard sound, which I thought was the problem. I had set my sound preferences to my USB headset and while the default audio and movie players for Ubuntu were smart enough to figure it out and play sound, stuff like VLC and FireFox wasn't. After much searching I found how to set my headset to be the default Alsa device, set my sound preferences to Alsa and hey presto! Everything works perfectly :D.

Thanks again to all those who helped. Sorry for troubling you.

---

