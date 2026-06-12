---
title: "[SOLVED] .mkv to .avi"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by expatCM on 2008-10-17
How do you convert .mkv files to .avi format please?

---

### Post by ezramorris on 2008-10-17
> **expatCM said:**
> How do you convert .mkv files to .avi format please?

Hi, firstly, avi is only a audio/video wrapper, so there are actually many codecs you could use for your video. As an example, I'll use MPEG4.

You can use a command line application encoder called MEncoder, which is derived from the media player [MPlayer]("http://www.mplayerhq.hu/").

This is available on Ubuntu's multiverse repository. To enable this, go to System>Administration>Software Sources. On the "Ubuntu Software" tab, make sure "Software restricted by copyright or legal issues (multiverse)" is checked. Click close, then reload when asked to.

Next, install mencoder. System>Administration>Synaptic Package Manager. Click search, then search for mencoder in Name. Right-click on mencoder, and click 'mark for installation'. Click apply, then apply again on the confirmation box.

OK, now we can start encoding. Open up a terminal from Applications>Accessories>Terminal.

A basic command is:
```
mencoder "inputfile.mkv" -o "outputfile.avi" -oac copy -ovc lavc -lavcopts vcodec=mpeg4
```
[LIST]
[*]You will need to change inputfile.mkv and outputfile.avi to your actual files.
[*]-oac copy specifies that we don't want to change the audio codec.
[*]-ovc lavc specifies that we want to use the avcodecs library to convert the video.
[*]-lavcopts specifies that the next item will be an option for lavc.
[*]vcodec=mpeg4 specifies that we want to use the MPEG4 codec.
[/LIST]
You can find more options, etc. by typing man mencoder, but it is a very large and detailed manual.

Hope this helps.

---

### Post by expatCM on 2008-10-17
Your help is appreciated ... thank you.

The command will run but only to a point.....  I have a single file of 1.5GB to convert and what happens is that only the first say 20 seconds of the intro are converted and the process then stops.  What is converted can be played though.

I have no idea why this happens.

I then explored a bit and found mkvmerge which basically is a gui allowing you to select the file and then change the output file to an avi.
[http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)
Sadly .. this program does exactly the same thing.

So I am missing something along the way.

Does anything leap out as being an obvious oversight?

---

### Post by nhasian on 2008-10-17
you can can change containers like mkv to avi with Avidemux.  there's an older version in the repo, or you can get the most recent version 2.4.3 from:

[http://www.getdeb.net/app/Avidemux](http://www.getdeb.net/app/Avidemux)

---

### Post by ezramorris on 2008-10-18
> **expatCM said:**
> Your help is appreciated ... thank you.

The command will run but only to a point.....  I have a single file of 1.5GB to convert and what happens is that only the first say 20 seconds of the intro are converted and the process then stops.  What is converted can be played though.

I have no idea why this happens.

I then explored a bit and found mkvmerge which basically is a gui allowing you to select the file and then change the output file to an avi.
[http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)
Sadly .. this program does exactly the same thing.

So I am missing something along the way.

Does anything leap out as being an obvious oversight?

Hi,
I spoke to some people on the IRC channel, and they suggested playing it with mplayer, and seeing if it plays for more than 20 seconds. If it doesn't, it is likely the original file is corrupt in some way.
```
mplayer -vo x11 "inputfile.mkv"
```
Also try fast forwarding and rewinding with the left and right arrow keys. It should jump 5 seconds or so, if not, it probably has a corrupt index.

---

### Post by expatCM on 2008-10-18
Well thank you for your continued efforts ....

I just ran the media with the mplayer command and the same thing happens so I guess your second comment that the media may well be corrupted must apply so I will stop at this point.

Thank you for all your time ....  I feel that I have learned quite a bit.

---

### Post by tsx2424 on 2010-09-19
I had tried to convert video from mp4 to avi as using menconder command.It's work as well.although the video quality is not good.the result is very blurring.How Can I get the good quality from that command? Thank you for helping.

---

### Post by Paqman on 2010-09-19
The Ubuntu repos now contain a really good simple video transcoder called Arista. Well worth a look IMO, and much simpler than fiddling about with the command line.

---

### Post by tsx2424 on 2010-09-19
I will try it.Thank you!

---

### Post by MooPi on 2010-09-19
I use mencoder and get quality conversions. Try this code for mencoder:

```
mencoder **.mpg -o movie.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=5000 -oac mp3lame -lameopts mode=2:cbr:br=128:vol=5
```
 The video or vbitrate an be adjusted as well as lames bitrate, vb. adjust to your needs. You can even specify scale with this command ```
-vf scale=352:240
```
Insert this command right after the video portion.

---

### Post by tsx2424 on 2010-09-20
It's working.Thank you for help.

---

