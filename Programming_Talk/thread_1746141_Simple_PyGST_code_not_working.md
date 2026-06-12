---
title: "Simple PyGST code not working"
date: 2011-05-01
forum: Programming Talk
---

### Post by Tahakki on 2011-05-01
Can anyone see what's wrong with the following PyGST code? It's fairly simple - it simply records webcam/microphone into an Ogg video:

```
cPipe = gst.Pipeline("capturepipe")
            cCam = gst.element_factory_make("v4l2src", "camera")
            cCam.set_property("device", "/dev/video0")
            cCamCaps = gst.Caps("video/x-raw-yuv,width=640,height=480,framerate=30/1")
            cCamCapsFilt = gst.element_factory_make("capsfilter", "cCamCapsFilt")
            cCamCapsFilt.set_property("caps", cCamCaps)
            #Feed branch
            cFeedQ = gst.element_factory_make("queue", "cFeedQ")
            cFeed = gst.element_factory_make("xvimagesink", "sink")
            #Vid branch
            cVidQ = gst.element_factory_make("queue", "cVidQ")
            cVidRate = gst.element_factory_make("videorate", "videorate")
            cVidRateCaps = gst.Caps("video/x-raw-yuv,framerate=30/1")
            cVidRateCapsFilt = gst.element_factory_make("capsfilter", "cVidRateCapsFilt")
            cVidRateCapsFilt.set_property("caps", cVidRateCaps)
            cVidTheora = gst.element_factory_make("theoraenc", "theoraenc")
            cVidQ2 = gst.element_factory_make("queue", "cVidQ2")
            #Sound branch
            cMic = gst.element_factory_make("alsasrc", "mic")
            cMic.set_property("device", "plughw:0,0")
            cMicCaps = gst.Caps("audio/x-raw-int,rate=48000,channels=2,depth=16")
            cMicCapsFilt = gst.element_factory_make("capsfilter", "cMicCapsFilt")
            cMicCapsFilt.set_property("caps", cMicCaps)
            cMicQ = gst.element_factory_make("queue", "cMicQ")
            cAudCon = gst.element_factory_make("audioconvert", "audioconvert")
            cAudQ = gst.element_factory_make("queue", "cAudQ")
            cVorbEnc = gst.element_factory_make("vorbisenc", "vorbisenc")
            cVorbQ = gst.element_factory_make("queue", "cVorbQ")
            #End
            cOggM = gst.element_factory_make("oggmux", "oggmux")
            cFileS = gst.element_factory_make("filesink", "filesink")
            cFileS.set_property("location", "output.mp4")

            #Add all elements
            cPipe.add(cCam, cCamCapsFilt, cFeedQ, cFeed, cVidQ, cVidRate, cVidRateCapsFilt, cVidTheora, cVidQ2, cMic, cMicCapsFilt, cMicQ, cAudCon, cAudQ, cVorbEnc, cVorbQ, cOggM, cFileS)
            #Link Feed branch
            gst.element_link_many(cCam, cCamCapsFilt, cFeedQ, cFeed)
            #Link Vid branch
            gst.element_link_many(cVidQ, cVidRate, cVidRateCapsFilt, cVidTheora, cVidQ2, cOggM, cFileS)
            #Link Sound branch
            gst.element_link_many(cMic, cMicCapsFilt, cMicQ, cAudCon, cAudQ, cVorbEnc, cVorbQ, cOggM)

            cPipe.set_state(gst.STATE_PLAYING)
```

The code gives no errors, and the xvimagesink appears, but seems to be stuck on the first frame - it doesn't update. The .ogg file contains no data. Here's the command-line thing I'm using, which works fins:

```
gst-launch v4l2src ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! \
tee name=t_vid ! queue ! xvimagesink sync=false t_vid. ! queue ! videorate ! \
video/x-raw-yuv,framerate=30/1 ! theoraenc ! queue ! mux. \
alsasrc device=plughw:0,0 ! audio/x-raw-int,rate=48000,channels=2,depth=16 ! \
queue ! audioconvert ! queue ! vorbisenc ! queue ! mux. \
oggmux name=mux ! filesink location=output.ogg
```

Can anyone spot what's wrong? Thanks!

---

### Post by Tahakki on 2011-05-01
Didn't realise you had to actually create a Tee element! All sorted now. Here's the updated code if anyone's interested:

```
            cPipe = gst.Pipeline("capturepipe")
            cCam = gst.element_factory_make("v4l2src", "camera")
            cCam.set_property("device", "/dev/video0")
            cCamCaps = gst.Caps("video/x-raw-yuv,width=640,height=480,framerate=30/1")
            cCamCapsFilt = gst.element_factory_make("capsfilter", "cCamCapsFilt")
            cCamCapsFilt.set_property("caps", cCamCaps)
            cCamTee = gst.element_factory_make("tee", "cCamTee")
            #Feed branch
            cFeedQ = gst.element_factory_make("queue", "cFeedQ")
            cFeed = gst.element_factory_make("xvimagesink", "sink")
            #Vid branch
            cVidQ = gst.element_factory_make("queue", "cVidQ")
            cVidRate = gst.element_factory_make("videorate", "videorate")
            cVidRateCaps = gst.Caps("video/x-raw-yuv,framerate=30/1")
            cVidRateCapsFilt = gst.element_factory_make("capsfilter", "cVidRateCapsFilt")
            cVidRateCapsFilt.set_property("caps", cVidRateCaps)
            cVidTheora = gst.element_factory_make("theoraenc", "theoraenc")
            cVidQ2 = gst.element_factory_make("queue", "cVidQ2")
            #Sound branch
            cMic = gst.element_factory_make("alsasrc", "mic")
            cMic.set_property("device", "plughw:0,0")
            cMicCaps = gst.Caps("audio/x-raw-int,rate=48000,channels=2,depth=16")
            cMicCapsFilt = gst.element_factory_make("capsfilter", "cMicCapsFilt")
            cMicCapsFilt.set_property("caps", cMicCaps)
            cMicQ = gst.element_factory_make("queue", "cMicQ")
            cAudCon = gst.element_factory_make("audioconvert", "audioconvert")
            cAudQ = gst.element_factory_make("queue", "cAudQ")
            cVorbEnc = gst.element_factory_make("vorbisenc", "vorbisenc")
            cVorbQ = gst.element_factory_make("queue", "cVorbQ")
            #End
            cOggM = gst.element_factory_make("oggmux", "oggmux")
            cFileS = gst.element_factory_make("filesink", "filesink")
            cFileS.set_property("location", "output.mp4")

            #Add all elements
            cPipe.add(cCam, cCamCapsFilt, cCamTee, cFeedQ, cFeed, cVidQ, cVidRate, cVidRateCapsFilt, cVidTheora, cVidQ2, cMic, cMicCapsFilt, cMicQ, cAudCon, cAudQ, cVorbEnc, cVorbQ, cOggM, cFileS)
            #Link Feed branch
            gst.element_link_many(cCam, cCamCapsFilt, cCamTee, cFeedQ, cFeed)
            #Link Vid branch
            gst.element_link_many(cCamTee, cVidQ, cVidRate, cVidRateCapsFilt, cVidTheora, cVidQ2, cOggM, cFileS)
            #Link Sound branch
            gst.element_link_many(cMic, cMicCapsFilt, cMicQ, cAudCon, cAudQ, cVorbEnc, cVorbQ, cOggM)

            cPipe.set_state(gst.STATE_PLAYING)
```

---

