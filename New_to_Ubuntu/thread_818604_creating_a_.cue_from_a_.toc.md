---
title: "creating a .cue from a .toc"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Barky on 2008-06-04
hey all,

I downloaded cuetools to try and convert a .toc to a .cue but I get an error message when running cueconvert that says "invalid character '#'" on a bunch of lines. 

the image was made using brasero. The cd is an old game that plays music on the cd. If I could just make one that would be good too. If there's another, easier program I could use that would be great too. If you guys could maybe just make one for me that would be good too. Here are the contents of the .toc file.

CD_ROM


// Track 1
TRACK MODE1_RAW
NO COPY
DATAFILE "/home/barky/SOR.bin" 28:55:69 // length in bytes: 306216288


// Track 2
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
SILENCE 00:02:00
FILE "/home/barky/SOR.bin" #306216288 0 02:18:31
START 00:02:00


// Track 3
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 02:18:31 01:25:04
START 00:01:73


// Track 4
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 03:43:35 02:31:18
START 00:01:73


// Track 5
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 06:14:53 02:09:12
START 00:01:73


// Track 6
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 08:23:65 02:51:57
START 00:01:73


// Track 7
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 11:15:47 02:12:41
START 00:01:73


// Track 8
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 13:28:13 02:41:53
START 00:01:73


// Track 9
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 16:09:66 02:14:24
START 00:01:73


// Track 10
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 18:24:15 02:44:74
START 00:01:73


// Track 11
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 21:09:14 02:24:66
START 00:01:73


// Track 12
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 23:34:05 02:00:22
START 00:01:73


// Track 13
TRACK AUDIO
NO COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
FILE "/home/barky/SOR.bin" #306216288 25:34:27 02:50:63
START 00:01:73


thanks guys

---

### Post by Barky on 2008-06-04
well, I got it to work kind of using cdrdao. But when the music tries to play all I get is static. please help!

---

