---
title: "PLEASE HELP!!! How to play videos in MTS format?"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by 2Bblondie on 2012-01-31
Hi guys, pleaaaase, I need your help!!
I am quite a beginner with Ubuntu and blond... :D and I tried to find an answer to this, but unsuccesfully :confused:
**How to play videos in MTS format? DO I REALLY HAVE TO CONVERT THE VIDEOS INTO OTHER FORMAT?** Isn't there another way??? I have a Sony HD camera with loooads of videos from holidays and cannot imagine converting theml..
I have Ubuntu 10.04 Lucid Lynx, I have  SMPlayer, VLC... but the videos are jamming..and just impossible to see what's there...

Thank you!!!:P

---

### Post by sffvba[e0rt on 2012-01-31
A quick search brought me this post on the forum - [http://ubuntuforums.org/showpost.php?p=11150126&postcount=9](http://ubuntuforums.org/showpost.php?p=11150126&postcount=9)

Seems with smplayer you will be able to view the format.


404

---

### Post by papibe on 2012-01-31
SMPlayer will decode it and play it.

However, my guess is that you have an HD video that would only play fine by using video hardware acceleration.

In 10.04 the easiest way is using the vdpau over an Nvidia card. It may be possible to add vaapi functionality to VLC (on ATI or some Intel integrated graphics) by adding some ppa's and upgrading.

Could you open the video with VLC and paste what it says on Tools -> Codec Information?

Hope it helps,
Regards.

---

### Post by 2Bblondie on 2012-02-01
Thanks guys, well..SMPlayer simply does not play it :(

And sorry, but what does vdpau over an Nvidia card mean?? and vaapi functionality and ppa's .... :( I am completely lost..:confused:
Well true is that there is some codec problem.. probably..
the codec of the video is for sound: a52 and for video: h264 but what should I do with that???

---

### Post by Carborundum on 2012-02-01
> **2Bblondie said:**
> Thanks guys, well..SMPlayer simply does not play it :(

And sorry, but what does vdpau over an Nvidia card mean?? and vaapi functionality and ppa's .... :( I am completely lost..:confused:
Well true is that there is some codec problem.. probably..
the codec of the video is for sound: a52 and for video: h264 but what should I do with that???
A52 and H264 are both very common codecs. SMplayer should have no problem with them.

Try downloading the latest build of mplayer (for which SMplayer is a GUI) by running these commands from a terminal:

```
sudo add-apt-repository ppa:motumedia/mplayer-daily
sudo apt-get update
sudo apt-get install mplayer
```Then try opening the MTS file from terminal using mplayer:

```
mplayer path/to/file.MTS
```Where path/to/file.MTS should of course be replaced with the actual path to the file.

Hopefully mplayer will be able to play it. If not it will give you an error message to post here.

---

### Post by Jerry N on 2012-02-01
I have some experience with this!  My Canon camcorder also creates .mts (h.264 I think) files and I have had a great deal of trouble with this in Ubuntu.  Initially, I was using an Athlon 3800+ (dual core, 2ghz) and getting nothing but jerky and broken images with VLC.  It should be noted that the Win 7 Media Player played those videos perfectly on that machine.  I am now using a Phenom II 965 (3.4ghz quad core) and VLC plays the videos OK BUT if I move the progress slider forward or backward the image breaks up and I have to stop VLC and start again.  This computer will be dedicated to an HDMI port on a large screen TV and I want to be able to control things with only a wireless mouse.  

Movie player plays the video OK (with the 3.4 ghz processor) but if I touch the slider, everything stops.  Smplayer is jerky and broken up - completely unsatisfactory.  Kaffiene won't play the .mts or .m2tc videos at all.  

In my searches, I have seen it suggested playing that playing .mts files with Linux requires a really fast CPU and a powerful graphics card does not help.  My experience agrees with this.  

My primary OS is Windows 7 but I wanted to use Linux on this media machine.  Since I want to be able to move forward or back in the video using only the mouse, it looks like I will be installing Windows 7 and using the Media Player.  VLC has gobs of options and allows a great deal of configurability but the Win 7 Media Player just works.

If you want to play your .mts files on your computer, it looks like you will probably need 3 ghz or more (or install Windows 7).  I think that VLC and the other Linux media players need work.

Jerry

---

### Post by papibe on 2012-02-01
> **Jerry N said:**
> In my searches, I have seen it suggested playing that playing .mts files with Linux requires a really fast CPU and a powerful graphics card does not help.  My experience agrees with this.

I have a different experience. For example, I have a m2ts with this details (from mediainfo):
```
Video
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.0
Bit rate mode                            : Variable
Bit rate                                 : 3 512 Kbps
Maximum bit rate                         : 25.0 Mbps
[B]Width                                    : 1 920 pixels
Height                                   : 1 080 pixels[/B]
Frame rate                               : 24.000 fps

Audio
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy

```
Note that this is is full HD video. My brother can play it smoothly on his HTPC with a atom processor and a Nvidia ION. I can also play it with a 2006's pentium D, and a Nvidia 9500GT. 

@2Bblondie: Could you tell us a little but about your hardware, specially your graphic card?

Regards.

---

### Post by Jerry N on 2012-02-01
papibe:  I don't have mediainfo but my HD videos have a frame rate of 30.  Could this be the difference?  I tried VLC on a P4 with Mint 11 and all I got was a lockup.  I don't have Win 7 on that P4 so I can't make a comparison with Windows Media Player.  

On the 3.4ghz Phenom, I am using a GTX 9800 video board with the recommended drivers installed.  Like I said, on that machine VLC plays smoothly until I try move ahead or back in the video and then it all goes to pot.

Jerry

---

### Post by papibe on 2012-02-02
@Jerry N:

I think I haven't try to play any 30fps video on my machine. It sounds like an interesting test. If you care to share one of those videos, I could share my experience with it.

Just an idea.
Regards.

---

### Post by Bartender on 2012-02-02
AVCHD (shows up as .mts) is thinly supported in Linux.  I have a Sony AVCHD camcorder.  I haven't really burned the midnite oil on this problem, but can tell you that I've found no super-easy solutions for importing nor editing.

---

### Post by Dumbestcrayon on 2012-02-02
I haven't tried this, but it may be worth a try in VLC:

[Credit]("http://www.robotastic.com/2010/avchdmts-performance-in-vlc/")

> Go to Tools > Preferences
In the lower left of the box click the checkbox *Show settings All*
Then go to Input & Codecs > Other Codecs > FFmpeg and look for the option called *Skip the loop filter for H.264 decoding*
Change it from *none* to *all*
Restart VLC

---

### Post by Jerry N on 2012-02-02
> **papibe said:**
> @Jerry N:

I think I haven't try to play any 30fps video on my machine. It sounds like an interesting test. If you care to share one of those videos, I could share my experience with it.

Just an idea.
Regards.

I see another difference.  I am recording at 8 gigabytes per hour.  This calculates to a bit rate of nearly 18 megabits per second.  I would suspect that if I were recording at 2 or 4 gigabytes per hour the playback situation would be much different.

Jerry

Correction:  The bit rate on my videos is 16363 kilobits per second or 16.363 megabits per second

---

### Post by Jerry N on 2012-02-02
> **Dumbestcrayon said:**
> I haven't tried this, but it may be worth a try in VLC:

[Credit]("http://www.robotastic.com/2010/avchdmts-performance-in-vlc/")

Thanks for the tip but my version of VLC doesn't have the "Other Codecs" option!
This is version 1.1.12 compiled on October 20, 2011.
Possibly the guy you quoted is using an earlier version of VLC.  There seem to be thousands of options in VLC, almost none of which I understand!  

Jerry

---

### Post by 2Bblondie on 2012-02-04
@2Bblondie: Could you tell us a little but about your hardware, specially your graphic card?


Hi, so it looks like it doesn't have a simple solution :)
My netbook is Acer Aspire ONE D257, 
 
**Processor**  Intel Atom N455 / 1.66 GHz [LEFT]L2 cache - 1MB
Intel Graphics Media Accelerator 3150
[/LEFT]
RAM up to 2GB
HDD up to 500GB

SMPlayer doesn't work at all, just the sound of the video.. with VLC PLayer I can see just few pictures, messed up..sound is poor..

Thanks so much for trying..

---

### Post by cotcot on 2012-02-04
I play mine sometimes with VLC. 
But most of the time I first convert them.

---

### Post by papibe on 2012-02-04
> **2Bblondie said:**
> 
**Processor**  Intel Atom N455 / 1.66 GHz [LEFT]L2 cache - 1MB
Intel Graphics Media Accelerator 3150
[/LEFT]
I'm afraid with that hardware you won't be able to reproduce HD video. In order to play it smoothly, you would need to convert it to SD, and even to a less CPU intensive codec like Xvid or DivX.

Regards.

---

### Post by 2Bblondie on 2012-02-12
> **papibe said:**
> I'm afraid with that hardware you won't be able to reproduce HD video. In order to play it smoothly, you would need to convert it to SD, and even to a less CPU intensive codec like Xvid or DivX.

Regards.

Oh Ok. Thanks. so the only solutiion at the end will be getting Windows... :cry:

---

### Post by papibe on 2012-02-12
> **2Bblondie said:**
> Oh Ok. Thanks. so the only solutiion at the end will be getting Windows... :cry:
I almost pretty sure that that netbook won't be able to reproduce HD video regardless of what OS you install on it.

If you really need to see those videos on that hardware, I think your best bet is to convert them.

Regards.

---

### Post by 2Bblondie on 2012-02-13
> **papibe said:**
> I almost pretty sure that that netbook won't be able to reproduce HD video regardless of what OS you install on it.

If you really need to see those videos on that hardware, I think your best bet is to convert them.

Regards.


right.. I iwsh I knew I was buying such a sh**** computer then.. well thanks for your help!

---

