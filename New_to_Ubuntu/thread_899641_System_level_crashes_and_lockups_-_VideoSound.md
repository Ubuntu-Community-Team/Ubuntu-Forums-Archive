---
title: "System level crashes and lockups - Video/Sound"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Phlimm on 2008-08-24
Hi I am running a dual boot Hardy Heron 8.04 / Win2K system with:

Soundblaster Live 5.1 Sound card

An MSI KM400A MB with VT8237 Unichrome integrated video

I did a lot of trial and error trying to get this stuff working.  

Currently, I am using this setup for sound:

Sound events
[LIST]
[*]Sound Playback: ADC Capture/Standard PCM Playback
[/LIST]

Music and Movies
[LIST]
[*]Sound Playback: ALSA
[/LIST]

Audio Conferencing
[LIST]
[*]Sound Playback: Multichannel Capture/PT Playback
[*]Sound Capture: Multichannel Capture/PT Playback
[/LIST]

Default Mixer Tracks:
[LIST]
[*]Device: SB Live 5.1 (Alsa mixer)
[/LIST]

With this I was able to get my microphone working and embedded videos functional as well.  What I am encountering is this - When playing embedded videos, on occasion the entire system will lock up completely.  No mouse, no keyboard, Firefox 3 totally locked up, entire system crashed.  Forced to do a system reset.

I get this with Win2K and tried Ubuntu as an alternative, but it is happening almost as much here as there.  Seriously doubt there is any system wide hardware issue such as a RAM or HD problem as I have already done diagnostics in those areas in Win2K.

In addition, Firefox bookmark lists are extremely slow to load and sometimes lock up Firefox forcing a crash of the program via Xfce Task Manager.

Any advice on drivers or configurations that I can get / use / set to avoid things like this and also increase video effects?


Also is there a way to show active apps on the toolbar when minimized?

TIA

Phlimm

---

### Post by srt4play on 2008-08-27
> **Phlimm said:**
> I get this with Win2K and tried Ubuntu as an alternative, but it is happening almost as much here as there.  Seriously doubt there is any system wide hardware issue such as a RAM or HD problem as I have already done diagnostics in those areas in Win2K.

Since the problem is happening in both Windows and Ubuntu I definitely would focus on hardware. Let memtest run overnight to eliminate the RAM and run your HDD manufacturer's diagnostics on the drive.

---

