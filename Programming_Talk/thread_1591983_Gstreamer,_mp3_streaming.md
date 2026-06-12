---
title: "Gstreamer, mp3 streaming"
date: 2010-10-10
forum: Programming Talk
---

### Post by vik_2010 on 2010-10-10
I've been messing around with gstreamer for a few days, and it's been . . . awkward. I feel like I'm just trying to memorize a bunch of different names (all of them really strange) . . . and memorization isn't really my thing. I think I really need to learn the low-level programming that goes into multimedia work if i'm every going to get a firm grasp on this.

Anyways, I've been trying to stream an mp3 over my lo address using gstreamer using rtp-over-udp [I hope i've got that right], and don't know what's up. Can any one help me?

My server's launch code is:
[PHP]gst-launch filesrc location="Music/test.mp3" ! mpegtsmux ! rtpmp2tpay ! udpsink port=4444 host=127.0.0.1[/PHP]The error I get says:

ERROR: from element /GstPipeline:pipeline0/MpegTsMux:mpegtsmux0: Could not create handler for stream
Additional debug info:
mpegtsmux.c(561): mpegtsmux_create_streams (): /GstPipeline:pipeline0/MpegTsMux:mpegtsmux0

Does anyone know how I should correct this? Also, what's the best way to learn this stuff? (and digital media in general?)

Thanks.

EDIT: Also, if anyone can help me make sense of h.261/h.263/h.264/the mp3/mpeg/mpg/any-other-names-that-begin-with-m, I would appreciate it.

---

### Post by PaulM1985 on 2010-10-10
Hi

Unfortunately I can't give any advice to solve your problem but maybe the following will help:

I had a similar sort of problem recently. I was trying to use gstreamer to stream music and videos from one computer to another.  After not really getting anywhere and struggling with the documentation, I decided to put all the files I wanted to play on a web server and then play them through gstreamer.

I downloaded apache tomcat and set it to point at my directory and got it running, then used gstreamer to play the files.  I found that gstreamer was ok for music, but was lacking on playing videos (frames were quite jumpy, sound often got out of sync with audio).

I replaced gstreamer with xine and I have been using that and found it has been very good.  This is a library which is for C/C++.

If xine is not appropriate you could still try out gstreamer with the tomcat route.  I know this is not actually a solution to your problem but will hopefully be a good alternative if you don't manage to get further.

Paul

---

### Post by vik_2010 on 2010-10-10
I tried a new approach: wireshark now says that data is being transferred and received ( I know this because there are green-colored bands that appear in wireshark's data-packet capturing window when there isn't a process listening on the port to which data is being sent), but I still get no sound:

my streamer's code is :
[PHP]gst-launch filesrc location="Music/test.mp3" ! audio/mpeg, mpegversion=1, layer=3! ffdec_mp3 ! audioconvert ! rtpL16pay ! udpsink port=4445 host=127.0.0[/PHP]By receiver's code is :
[PHP]
gst-launch udpsrc -vvv port=4445 ! gstrtpbin ! rtpL16depay !  audioconvert ! audioresample ! volume volume=1 ! alsasink
[/PHP]What I'm trying to do is stream music from the former to the latter.

This might help:

When I try to stream the music straight to a file, the file's size stays as 0 bytes.

---

### Post by SledgeHammer_999 on 2010-10-10
Try using "mad" instead of "ffdec_mp3".

---

### Post by vik_2010 on 2010-10-10
Didn't work . . . did it work for you?

When i changed it to mad, i was required to also specify the channel and rate variables. I just chose 44100Hz for the rate, and 2 for channel - these were what came up when i ran the file in mplayer - but I'm not sure what I should choose. How would these affect the output?


EDIT: OK, so it HAS to do with the udpsink/udpsrc pads. If I run:

[PHP]gst-launch filesrc location="Music/test.mp3" ! audio/mpeg, mpegversion=1, layer=3 ! mad [OR ffdec_mp3, doesn't matter] ! rtpL16pay ! rtpL16depay ! audioconvert ! audioresample ! alsasink[/PHP]

..it's plays beautifully. But if I do:

[PHP]gst-launch filesrc location="Music/test.mp3" ! audio/mpeg,  mpegversion=1, layer=3 ! ffdec_mp3  ! audioconvert ! rtpL16pay ! udpsink port=4444 udpsrc port =4444 ! rtpL16depay ! audioconvert ! audioresample ! alsasink[/PHP]

..then it just sits there saying 
"Setting pipeline to playing ...
New clock: GSTSystemClock"

Any suggestions?

---

### Post by SledgeHammer_999 on 2010-10-10
No. I suggested "mad" because it has a higher "rank" than ffdec_mp3. You should try asking in the gstreamer mailing list. There are many people there who can help.

---

