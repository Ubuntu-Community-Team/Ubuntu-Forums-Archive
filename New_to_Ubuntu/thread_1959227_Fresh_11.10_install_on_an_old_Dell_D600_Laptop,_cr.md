---
title: "Fresh 11.10 install on an old Dell D600 Laptop, cruddy video playback"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by seaders on 2012-04-15
So, I've been using an old laptop of mine (a Dell D600, running Windows XP) as a media player with XBMC connected to the TV for the last while.  There were only a few things that were keeping me tied to Windows, but because all of them have recently released versions that sounded like they're all good on Linux too now, I decided to check out the most recent stable Ubuntu and play around with it a bit.

Now, the laptop is quite old, but I mainly used it for watching videos and the performance was pretty much perfect, so long as I didn't try to play a 1080p mkv at it.  Unfortunately I haven't been able to get any sort of decent performance from any program I've tried (VLC, mplayer, Banshee, XBMC), with every one of them having extremely choppy playback, for all types of files, even low quality ones.  Max FPS would be about 15, but it generally looks less than 10.

One of the options I'd read about was to start mplayer with command
> mplayer -ao alsa -vo vdpau -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,ffodivx, foo.avi
but when I do that, mplayer doesn't actually pop up at all, in fact, it doesn't pop up if I start it with just "-vo vdpau", which might be part of the problem, I think?

Anyone any notions?  Am I going to be able to get any joy with this, or am I wasting my time?

---

### Post by cogier on 2012-04-15
I suggest you try Ubuntu 10.04LTS which is available [here]("http://www.ubuntu.com/download/ubuntu/download") until late April (just click on the dropdown box with Ubuntu 11.10 to select 10.04).

I think this might suit your hardware better than Ubuntu 11.10.

I trust you have installed Medibuntu see the "how to"[here]("http://medibuntu.org/repository.php")

---

### Post by seaders on 2012-04-16
Thanks for the reply cogier, I might do alright, aye.

After posting this thread, I did a bit more digging and found
[http://ubuntuforums.org/showthread.php?t=1381370](http://ubuntuforums.org/showthread.php?t=1381370)
and 
[http://ubuntuforums.org/showthread.php?t=1095102](http://ubuntuforums.org/showthread.php?t=1095102)

They both had problems with the D600's funky chipset (Radeon Mobility FireGL M9000), but that seemed to be for more intense stuff like 3D gaming, not just video playback.  I was getting about 30FPS with glxgears and it seemed to be running smooth enough too, but I'm absolutely no expert.

and from XBMC
[http://forum.xbmc.org/showthread.php?tid=49844](http://forum.xbmc.org/showthread.php?tid=49844)

There seems to be an old ATI driver that I can only have when on 8.04 (which I obviously didn't know about before!), but the guys on XBMC were saying they got decent performance, but with Xubuntu on, not Ubuntu.

I have (now) installed Medibuntu, but after that, which video player should I try and use?  Again, I've tried the ones I listed above, but it doesn't look like there's been any improvements.

Whaddaya think, 10.04, even older with a version of 8, or try Xubuntu?

---

### Post by Mark Phelps on 2012-04-16
Your old 8.04-era ATI driver won't work on any Ubuntu version newer than 8.10.  So, don't bother even trying to install it.

The open-source Radeon driver is installed by default and that is what you have available currently.

---

### Post by seaders on 2012-04-16
> **Mark Phelps said:**
> Your old 8.04-era ATI driver won't work on any Ubuntu version newer than 8.10.  So, don't bother even trying to install it.

The open-source Radeon driver is installed by default and that is what you have available currently.
I was actually talking about installing 8.04 not just the driver, the entire system to check that driver.

---

