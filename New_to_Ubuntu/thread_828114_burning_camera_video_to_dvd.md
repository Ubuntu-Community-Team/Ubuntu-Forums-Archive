---
title: "burning camera video to dvd"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-06-13
Ok, so I have some family videos that I would like to burn to a dvd so I can watch them on my tv. How to I burn the video files to a dvd?

---

### Post by sdowney717 on 2008-06-13
perhaps dvdstyler
[http://www.dvdstyler.de/](http://www.dvdstyler.de/)
[http://www.bookpool.com/ct/177](http://www.bookpool.com/ct/177)

devede is in synaptic

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

k3b lets you write dvd's

---

### Post by bumanie on 2008-06-13
If the camera has firewire support try kino. It is meant to be very good (never used it, so can't offer personal opinion). > sudo apt-get install kino I do know you have to add IEEE 1394 to modprobe to get it working with firewire - read the kino site or google for instructions.

---

### Post by sam_delta on 2008-06-13
install devede, you can use synaptic or ```
sudo apt-get install devede
``` you can include more than 1 video, and you can add a simple menu to select which video to see, im sure that there are also some tutorials out there

this program will code your videos into dvd format and create an ***.iso file, which you can burn with your preferred burning application to your cd

sam

---

### Post by sdowney717 on 2008-06-13
[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

I just found and installed qdvdauthor which is a front end for dvdauthor.

download version 1.20
terminal into the directory where you extract it.
type in ./configure
it will open a screen to let you make and compile.

qdvdauthor requires videotrans which is in synaptic.
pay attention to the log if you get any errors for clues

I found I had to use mencoder instead of videotrans. videotrans kept altering the fps with the sound speeding it up 20%. It would say my video file was 25fps and it was converting it to 29 fps and therefore the sound would be recorded at 120%.

mencoder worked perfectly fine keeping the video and sound playing at the right speed.

Does anyone have any thoughts on this?

---

### Post by timcredible on 2008-06-13
some programs you can use:

devede
qdvdauthor
dvdstyler

if you want to convert pictures to video with music added:

digikam
devede
avidemux

if you have the videos on minidv tape and have a firewire connection on the camcorder, use kino to get the video off the tape.

I've used all of the above, i prefer devede, digikam, and kino - just my personal opinion.  i think they're all in synaptic

---

### Post by sdowney717 on 2008-06-13
So far only mencoder works 
I tried transcoder and get video and no audio,

WARN: audio sector out of range: -50721 (vobu #775, pts 454.824)

---

### Post by producer on 2008-06-18
I am also working on this.  Kino does the capturing very well.  You just have to make sure that your user is in the group that matches the group for /dev/raw1394 and that the group has r/w permission on the device.  k3b writes data DVDs and will burn an .iso image, but it will not, ( I don't think it will), create the iso image from a video.  You have to be careful of the format and compression ratios of the video and use the right tools to set everything up.  You also have to have the right codecs.  I'm not further than that today and I do have a requirement.
I editted a 444 or 45 minute video the other day and notived that it was many gigabytes long.  Even when I changed the format it came out 7.6 Gigabytes.  Still too long for a DVD.  How do the pros get full movies on the DVDs?  Are they using MPEG4 formats and compression, and what does that for us?  There has to be a proceedure.

---

### Post by crjackson on 2008-06-18
> **producer said:**
> I am also working on this.  Kino does the capturing very well.  You just have to make sure that your user is in the group that matches the group for /dev/raw1394 and that the group has r/w permission on the device.  k3b writes data DVDs and will burn an .iso image, but it will not, ( I don't think it will), create the iso image from a video.  You have to be careful of the format and compression ratios of the video and use the right tools to set everything up.  You also have to have the right codecs.  I'm not further than that today and I do have a requirement.
I editted a 444 or 45 minute video the other day and notived that it was many gigabytes long.  Even when I changed the format it came out 7.6 Gigabytes.  Still too long for a DVD.  How do the pros get full movies on the DVDs?  Are they using MPEG4 formats and compression, and what does that for us?  There has to be a proceedure.

I haven't used kino (still using windows for video) but it sounds like kino is an NLE only.  You need to compress the file using mpeg2 format for DVD content using some other application I would guess.

---

### Post by producer on 2008-06-18
Yeah Kino I have only used for capture, although it can do some basin editing, but no fancy wipes or effects. I believe a DVD authoring tool is necessary and then when you have the VIDEO_TS and the AUDIO_TS files you can use k3b to actually burn the disc.  That's what I've found out so far, anyway.  I can't say it's 100% accurate, but that seems to be the gist of it.  People seem to say QDvdAuthor is a good program to use.  I haven't seen it yet and I'm not going to do more tonight.  Tommorrow is another day and I hope to have more time for it then.  k3b seems to actually be much more powerful than I first imagined, though.

---

### Post by sdowney717 on 2008-06-21
you can shrink down a video file using 
Convertit
I uploaded the .deb because it is hard to find

or possibly winff

---

