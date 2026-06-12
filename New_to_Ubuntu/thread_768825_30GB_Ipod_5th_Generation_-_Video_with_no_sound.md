---
title: "30GB Ipod 5th Generation - Video with no sound"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by BurningFury on 2008-04-26
Hello there to all Ubuntu users.
I just recently bought a 5th Generation Ipod Video, and i must say that
i love the little thing. It can play music just perfect but it has some
problems with the video side.

Now, I've read countless posts about video conversion to ipod here, and all
point to the same place: scripts, tools, etc.
I've used Vive, ThinLiquidFilm, WinFF, Multimedia Converter, etc...
and countles variations of scripts, with the same result.
My videos encode fine on the PC, in fact, the sound is crisp and live when
played, but when i transfer them to the ipod I only get the video to display but there's no audio to hear.

I also thought of changing the sample rate to: 441000 instead of the accostumed: 448000, and in either scenario i get the same results.
It lead me to belive that the audio codec was to blame: FACC.
I've tried using the NeroAAC encoder, but as you can see, I don't know
the right commands to produce compliant audio streams for ipods.
(If anyone can provide a good command to convert audio with NeroAAC I'll be 
forever in your debt)

Now, a bit of background about my Ipod:
30GB Ipod Video [5th Generation]
Version Firmware: 1.3

If anyone knows a workaround to this problem, please be kind to post
any help. As you see, it is a bit frustrating that us Linux users can't
fully utilize our devices to the limit.

Thanks for all the good work you guys do. Much appreciated.

---

### Post by BurningFury on 2008-04-27
Sorry for the double post, but isn't a kind soul out there to help me out?

Thanks in advance.

---

### Post by BurningFury on 2008-04-28
I had to search earth, sea and heaven for the answer, but i found it.

It seems that Ipods can't play audio streams that aren't encoded with
the AAC_LC profile. So after discovering the problem, I made several tests
and i found a way to make complaint .mp4 files for ipod.

I will share this with everyone else, since I know before hand how frustrating it is to be stuck. Anyhow, let's begin.
* I won't go into details here, I'll just give an overlook of the process*

1- First we'll have to separate our video and audio streams.
   We'll accomplish this by using FFMPEG and this command:

> ffmpeg -i Input.* -vn Output.wav

* Note that it will produce a raw PCM audio file.
* Also note that for our input file we could use: .avi, mpeg, mp4, etc.
  as long as FFMPEG is properly compiled to handle such formats.

2- After we obtained our Audio, we proceed to encode it with NeroAacEnc.
   I used NeroAacEnc since it gives better results, and to be honest...
   FAAC sucks.

> neroAacEnc -br 30000 -2pass -lc -if Audio.wav -of Audio.m4a

* That will encode our RAW Audio into a AAC_LC complaint stream.
* Also note that i used 30000 as the bitrate, it gives me good audio
  quality and small file size, but feel free to mess with the bitrate.
* Remember that the file extension for our audio has to be .m4a

3- Muxing everything back with MP4Box:

> MP4Box -add video.mp4 -add audio.m4a Output.mp4

* This will mux everything back together, and now we can load it up
  into our iPod.

4- You can move the final video to the iPod using GtkPodAac or
   ThinLiquidFilm.

That's it. Note that before hand I prepared my video to fit the aspect ratio of the iPod screen using Avidemux. 
It's a good thing to prepare the video, since it will just be more easy to deal with.

Have fun folks =)

---

