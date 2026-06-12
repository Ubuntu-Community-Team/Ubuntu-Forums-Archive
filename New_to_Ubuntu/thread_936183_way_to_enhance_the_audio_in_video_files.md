---
title: "way to enhance the audio in video files?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-10-02
sometimes i get video files that have very low volume

usually either .avi or .mkv format


i turn the volume all the way up on both the media player and for ubuntu itself but it is still so low that i can barely hear it

this does not happen with all .avi and .mkv (only sometimes)


if i burn the media to a dvd and play it on my tv the volume sounds normal


so my question is there any way to enhance the volume on these type of files ? (that way i dont need to burn them to dvd just to watch them)

---

### Post by H.Callahan on 2008-10-02
I do a lot of playing with video files, mostly under Windows as I have not found equivilents of all the stuff I generally use when editting video.

Under Windows, the VirtualDubMod program will allow you to do select the audio stream from an .avi file, adjust the volume, and then save it back to an .avi file.  I have not found a Linux equivilent to that program.

---

### Post by mindoms on 2008-10-03
Im not sure about that.
but maybe those low volume video files might have an ac-3 audio stream, and your soundcard decodes them in hardware, but the volume for those lanes is set soo low.

just open the mixer and play on the lanes, while a low-volume movie is running. maybe it helps...
to make all lanes appear, choose (in gnome-volume-control)
Edit -> Preferences
and check those lanes that seem right

---

### Post by billgoldberg on 2008-10-03
> **H.Callahan said:**
> I do a lot of playing with video files, mostly under Windows as I have not found equivilents of all the stuff I generally use when editting video.

Under Windows, the VirtualDubMod program will allow you to do select the audio stream from an .avi file, adjust the volume, and then save it back to an .avi file.  I have not found a Linux equivilent to that program.

Yeah buddy, this isn't a windows help forum.

--

I don't know anything about video/audio editors.

You will get better answers if post it in the right forum (not absolute beginners talk).

---

### Post by falkTX on 2008-10-03
Some video players have an option to "normalize volume".
I know VLC and SMplayer can do it.

This also works when a video starts with low volume and then suddently BOOM...

You should try it

---

### Post by bhadotia on 2008-10-03
> **tjwoosta said:**
> sometimes i get video files that have very low volume

usually either .avi or .mkv format


i turn the volume all the way up on both the media player and for ubuntu itself but it is still so low that i can barely hear it

this does not happen with all .avi and .mkv (only sometimes)


if i burn the media to a dvd and play it on my tv the volume sounds normal


so my question is there any way to enhance the volume on these type of files ? (that way i dont need to burn them to dvd just to watch them)

I usually come across these files. I play them in vlc with extened gui . In the extened gui, on the equilizer tab, I enable the equilizer and increase the volume to the fullest. This lets me hear the sound but I sometimes have problems with sound quality.

---

### Post by H.Callahan on 2008-10-03
> **billgoldberg said:**
> Yeah buddy, this isn't a windows help forum.

Sorry if I offended you.  I was trying to tell him that he might want to look for a video editing program that was capable of adjusting the audio and that such things are possible, but I had not found one yet under Ubuntu.

---

### Post by sleepingdragon on 2008-10-03
Take a look at [Avidemux]("http://avidemux.berlios.de/"), it's in the repos. It'll happily convert .avi into another format of your choosing, and will handle audio volume changes in a nice friendly manner.

---

