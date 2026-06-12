---
title: "HOW TO: Use VLC to capture video from your webcam to a file"
date: 2006-03-13
forum: Outdated Tutorials &amp; Tips
---

### Post by anil_robo on 2006-03-13
I tried the VLC wizard tonight on Ubuntu Dapper Flight 5 and I was able to capture the webcam video to a file. 

Do this:

Connect your webcam.

Open VLC
File--> OPen capture  device
Go to Video4Linux tab
Specify your video device name (mine was /dev/video0)
(My webcam audio doesn't work, so I left audio device as it is)
Norm: Automatic

Check "stream output" box
Click settings
Specify a filename (make sure you have write permissions there - usually a file on desktop or home directory is the best bet)
Unselect "dump raw input" (it must reamain empty)
Encapsulation method: MPEG1
Video codec: mp1v
Audio codec: mpga
"select all elementary streams" should remain empty.

Press OK

Press OK

Now press PLAY button on VLC.
The video should start recording. You can check this while VLC is recording video by right clicking on the recording file and selecting properties (it will show increasing file size).

Notes:
1. You can do an HTTP streaming by a similar method you are able to capture to a file.
2. Powerusers:
Media resource locator:
v4l:// :v4l-vdev="/dev/video0" :v4l-adev="/dev/dsp" :v4l-norm=3 :v4l-frequency=-1 
Destination target:
:sout=#transcode{vcodec=mp1v,vb=1024,scale=1}:duplicate{dst=std{access=file,mux=mpeg1,url="FULL PATH NAME HERE"}}

========================================
Keywords: VLC, Video, Capture, Record, Encode, Save, V4L, Video for Linux, Streaming

---

### Post by s57nev on 2006-09-08
Works fine ...but still you can't see yourself while recording and that's not acceptable. We need such application !

---

### Post by cvmostert on 2006-10-14
> **s57nev said:**
> Works fine ...but still you can't see yourself while recording and that's not acceptable. We need such application !

I totally agree with you... I need to see how stupid i look while recording... and what i am doing... and where to position myself.

Cheers.

edit: thanx anyway... a step in the right direction.

---

### Post by insub2 on 2006-10-29
i tried this and got the sound recorded but video is just a blue screen.  though i am using a pci card with a vcr hooked up trying to record from a tape.  any suggestions?

---

### Post by insub2 on 2006-10-30
> **insub2 said:**
> i tried this and got the sound recorded but video is just a blue screen.  though i am using a pci card with a vcr hooked up trying to record from a tape.  any suggestions?
 figured out that it has to do with my video capture card not working nicely with VLC (and this may be related to not working well with xawtv, also)  but this method would work otherwise.  thanks for the tip.

---

### Post by insub2 on 2006-10-30
SOLUTION!
for video capture card (as opposed to the webcam) set to NTSC (as opposed to NORM)


BUT the recorded quality isn't quite as good as the regular play quality.  any  thoughts?

---

### Post by stateq2 on 2006-11-03
Thanks!  I've been trying this w/ mplayer, but the video output kinda fades away after a few seconds....but vlc worked perfect w/ better video quality.

---

### Post by kowal on 2007-08-06
> **s57nev said:**
> Works fine ...but still you can't see yourself while recording and that's not acceptable. We need such application !

You should try Freej

---

### Post by skanchi on 2007-08-24
you can also select "play locally"  in the outputs section. This enables both recording and viewing simultaneously

---

### Post by raphinou on 2007-08-30
I have posted a howto about recording a webcam stream with vlc at [http://blog.raphinou.com/2007/08/building-webcam-recorder-with-vlc-ion.html](http://blog.raphinou.com/2007/08/building-webcam-recorder-with-vlc-ion.html)

---

### Post by ekravche on 2007-09-01
I'm recording but the video size is too small is there a way to change the size?

---

### Post by ozzyprv on 2007-09-01
Is there any way to confirm that my webcam is actually "/dev/video0"?

I followed the instruccion, but I cannot get the video recorded.

---

### Post by isecore on 2008-04-20
This was exactly what I was looking for. Works fine. The only problem is that my video is horribly distorted.

I'm running a Logitech Quickcam Web (with built-in microphone) on Ubuntu Hardy running on AMD64, current as of 08/04/20. Camera works fine in everything else, but recording here is just noise.

Any input (no pun intended) would be appreciated :)

update: I fixed it. I had to manually specify the resolution in the advanced settings, then the image became normal.

---

### Post by Scormen on 2008-04-21
Hi all,

I'm getting this error message when I try to open a capture device:
> v4l demuxer error: cannot get channel infos

Any idea what's going wrong?

Thanks,
Kris

---

### Post by Metaleks on 2008-04-22
If your webcam is integrated into your laptop, where would the device be located?  I can't for the life of me figure out.

---

### Post by pwn on 2008-05-23
I guess it depends on the driver. I have a Sony Vaio AR590E with an integrated camera. I installed the Ricoh Webcam driver and I got it to work with Mplayer, but couldnt get it to work with VLC. The driver is v4l2.

The device is /dev/video0

---

### Post by akaname on 2008-10-06
Some cameras need v4l2, but VLC Version 0.8.6 supplied by Ubuntu Hardy doesn't support that. Ubuntu Intrepid (end of october) will supply VLC Version 0.9.3 and solve this problem.

---

### Post by OnlyWhisky on 2008-12-28
It doesn't work with Logitech Communicate STX under Ubuntu 8.10.

---

### Post by johnjohn2 on 2009-02-15
thanks

---

### Post by danielsk on 2009-04-09
Hi, I'm trying to record the video with my laptop built in camera and mic. I followed the tips and here is where I am now.

First, I'm using 8.10 AMD 64 on a HP DV5160 Pavilion laptop.

I can use VLC to record video and audio, BUT not both at once. If I set up in the VLC "video for linux" tab it records the audio, if I use the video for linux 2 tab it only records video.

I can setup both at once and try to sync video and audio later, but anyone has an idea of how to make them work together?

Thanks

Daniel

---

### Post by seetchoo on 2009-05-25
I have almost exactly the same problem as danielsk has but I cannot capture audio even if I use "video for linux". Is there anybody out there who has any idea that what could be the solution?

---

### Post by danielsk on 2009-05-26
@seetchoo, just to be sure, can you record audio in any other program?

---

### Post by ephigy on 2009-06-14
I can record sound an video using ffmpeg (doesn't synch properly though)but using VLC I can't seem to record sound with my vid. I don't have mp4 listed though, I'm trying to do it with ogg. Am I missing a codec for mp4 (searched but didn't find any mp4 codecs).

---

### Post by executorvs on 2009-09-09
did you ever find a solution to the lack of audio?

---

### Post by nawi2010 on 2009-10-30
is there any update for best alternate webcam video recording software for ubuntu instead vlc?

---

### Post by soni1770 on 2009-11-02
cheese is ok

sudo aptget cheese
i thiink

---

### Post by kssworld93 on 2010-08-09
```
sudo apt-get install cheese
```

---

### Post by kushelmex on 2010-08-17
Work perfect, tnks!!

---

### Post by wojtek.wurzenberger on 2011-03-04
> **nawi2010 said:**
> is there any update for best alternate webcam video recording software for ubuntu instead vlc?

I just installed guvcnew and it works perfect. 

VLC is to complicated for me and I cannot configure it to stream and see the screen despite the option "Display locally" activated.
Although it streams, I do not see either the controls or panel!

Cheesy works too, but is slow and shatters the videos 

My environment Ubuntu 10.10 (Maverick) amd64 runing from SDHC card with 3GB persistence casper file, Toshiba Satellite T115D (4GB RAM, 2Core AMD Vision 64 bit , built in webcam)

---

### Post by executorvs on 2011-03-16
I've been using Kdenlive with great success for a fair bit now.

---

