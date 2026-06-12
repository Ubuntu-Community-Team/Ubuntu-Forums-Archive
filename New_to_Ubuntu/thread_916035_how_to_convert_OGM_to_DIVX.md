---
title: "how to convert OGM to DIVX ?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by medya on 2008-09-10
I have some videos in OGM format I need to convert them to DIVX ,

is there any tool to do that in Linux ?

---

### Post by shirilover on 2008-09-10
Avidemux will do what you need.

---

### Post by Vivaldi Gloria on 2008-09-10
> **shirilover said:**
> Avidemux will do what you need.

Avidemux can make xvid but can it make divx? AFAIK xvid is an open format but divx is proprietary.

---

### Post by medya on 2008-09-11
nice program but I dont see DIVX name in the format to choose,
btw I just need to convert to a format that my home DVD player can read it .
(it cant read OGM) whats ur suggestion .

---

### Post by lovinglinux on 2008-09-11
What you call format name is the file extension. In the video realm, the file extension is also called container. A container is "like" a zip file for videos. Inside a container you can find audio files, video files, subtitles and other stuff, depending on the container features. 

Examples:

DivX container - mymovie.divx
AVI container - mymovie.avi
MP4 container - mymovie.mp4
Matroska container - mymovie.mkv
Ogg container -mymovie.ogv

So, inside the video container you will find a video stream and at least an audio stream. These streams are compressed (encoded) to fit a single CD or DVD using a special codecs. There are several types of encoders/codecs and to watch a video created with one type you need a player with the corresponding decoder.

Examples: DX5, Xvid, H.264

DivX is a proprietary container/codec, but you can use the open source xvid codec to encode a video and save it in an AVI container. Since your player is capable of playing DivX it will probably play an AVI file encoded with Xvid.

Convert your OGG files using Avidemux using Xvid encoder and save them as AVI. Put them on a DVD and try to play it. If this doesn't work, try renaming the avi extensions to divx. For example, rename "mymovie.avi" to "mymovie.divx". I'm not sure if this will work in the player, but it works in the computer.

---

### Post by medya on 2008-09-11
lovinglinux since you know this program is there any way to Batch Convert my files to Xvid ?

let say I have 20 OGM files, and I wanna batch convert them (probably a command in terminal) .

is it possible?

---

### Post by lovinglinux on 2008-09-11
With WinFF you just have to add all files you want and it will batch convert them. You don't even need the command line, is all GUI. Very easy.

---

