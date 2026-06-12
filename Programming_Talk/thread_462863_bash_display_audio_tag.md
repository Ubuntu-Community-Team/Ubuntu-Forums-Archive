---
title: "bash display audio tag"
date: 2007-06-03
forum: Programming Talk
---

### Post by jovial on 2007-06-03
Hello 

I've a list of audio file  ogg and mp3 format.
And i want to display info tag in a zenity frame
Iknow some external tool like infotag oggnfo, but using these tools create dependency in my script
In native Fiesty with the codec installed i can show info audio in nautilus propriety.
which process gnome use ,to display the audio's informations?
is it possible to call them by a bash script or a line commands?

---

### Post by duff on 2007-06-03
nautilus uses gstreamer to identify the tags.  You can use gst-launch to do the same.

```
 # gst-launch-0.10 filesrc location=/path/to/mymusic.mp3 ! id3demux ! fakesink -t
```

will dump out more than you want, but some simple grep- and awk-ing will clean it up.

---

### Post by jovial on 2007-06-08
The solution is totem-video-indexe

totem-video-indexer "/home/jovial/Musique/Camille/Le fil/03 - Assise.mp3"
give:

TOTEM_INFO_TITLE=Assise
TOTEM_INFO_ARTIST=Camille
TOTEM_INFO_YEAR=2005
TOTEM_INFO_ALBUM=Le fil
TOTEM_INFO_DURATION=136
TOTEM_INFO_TRACK_NUMBER=3
TOTEM_INFO_HAS_VIDEO=False
TOTEM_INFO_HAS_AUDIO=True
TOTEM_INFO_AUDIO_BITRATE=128
TOTEM_INFO_AUDIO_CODEC=MPEG-1 layer 3
TOTEM_INFO_AUDIO_SAMPLE_RATE=44100
TOTEM_INFO_AUDIO_CHANNELS=2

totem-video-indexer "/home/jovial/Musique/Camille/Le fil/03 - Assise.mp3" | grep ARTIST | sed -e 's/TOTEM_INFO_ARTIST=//'
give:
  Camille


Thanks to  Ritesh Khadgaray who give me this solution .
tested on Fiesty

Bye

jean-Luc

Bye

Jean-luc

---

