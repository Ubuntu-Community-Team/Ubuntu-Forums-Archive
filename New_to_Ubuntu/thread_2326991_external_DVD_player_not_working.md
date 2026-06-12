---
title: "external DVD player not working"
date: 2016-06-06
forum: New to Ubuntu
---

### Post by Marina_Dubini on 2016-06-06
hi everybody,
I am new to the forum, I have kubuntu 14 and my laptop is an ASUS [COLOR=#444444][FONT=MMTextWeb-Bold]F302LJ-FN024T[/FONT][/COLOR]. I just bought an external dvd writer/player: it's a Samsung SE-208, but it's not working properly. I connected it to my laptop and my laptop recognises it, but when I insert a CD it looks as if the audio folder is empty and I can't play the songs.
I would be really thankful if anybody could help.
cheers, 
:)

---

### Post by X-RED_Tech on 2016-06-06
Does the CD work on other computers?
What is it exactly? The "audio folder" suggests it isn't a CD Audio. It could be anything else. Please give details.

---

### Post by leunam12 on 2016-06-07
Are you sure you don't need another connection? Many external DVD players use two USB ports, one for power and the other one for data.

---

### Post by Marina_Dubini on 2016-06-07
hi thanks to both of you for your answer,
I't an audio CD I am trying to play and the player works on my friend's macbook with with no need of installation or additional cable.

---

### Post by X-RED_Tech on 2016-06-07
An Audio CD has no "audio folder" or any other folder and is not intended to be opened in a file manager. If it's a CD-ROM with audio files (mp3 or otherwise), then you need to have a matching codec already installed. Please check. A CD-ROM with mp3 (or other) files is NOT and audio CD, it's a DATA CD.
An audio CD should be always correctly recognized in Ubuntu. How exactly does it shows? A screenshoot would help.

---

### Post by mc4man on 2016-06-08
> **X-RED_Tech said:**
> An Audio CD has no "audio folder" or any other folder and is not intended to be opened in a file manager. If it's a CD-ROM with audio files (mp3 or otherwise), then you need to have a matching codec already installed. Please check. A CD-ROM with mp3 (or other) files is NOT and audio CD, it's a DATA CD.
An audio CD should be always correctly recognized in Ubuntu. How exactly does it shows? A screenshoot would help.
Not really, most if not all file managers will represent the tracks on an audio cd in a folder, in nautilus that would be a location of cdda://sr[COLOR="#0000CD"]X[/COLOR]/ as in screen

Sounds more like a kubuntu thing which I haven't used in many years. The little time I did it seemed to do so things regarding audio cds like set up ripping/encoded possibilities  to 'folders' & such. 
Maybe see if you can see the audio cd in Amarok, otherwise search specific to kubuntu & audio cd

You may also want to check what /dev the drive is getting, with any disk in the drive run this in a konsole, look in the *-cdrom section & note the various logical name: entries
```
sudo lshw -c disk
```

---

### Post by X-RED_Tech on 2016-06-08
Indeed. In a folder as in a root folder, not inside some other folder. DVD-Video on the other hand typically is organized in a "video" and an "audio" folder, the latter usually empty.

I wasn't aware of any special "weirdness" regarding audio CDs in Kubuntu but you may be into something. Of course, assuming it really is an audio CD and I'm still not convinced it is, not at all.

---

### Post by mc4man on 2016-06-08
> **X-RED_Tech said:**
> 

I wasn't aware of any special "weirdness" regarding audio CDs in Kubuntu but you may be into something. Of course, assuming it really is an audio CD and I'm still not convinced it is, not at all.
It's been at least 5 yr's for kubuntu here but I remember you could browse or do something where the audio cd 'appeared' to be ripped to .mp3 or .flac,  ect.  Really don't quite remember though.

---

