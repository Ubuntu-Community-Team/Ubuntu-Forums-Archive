---
title: "Sound Converter Plugin"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by ray9 on 2014-08-09
When I try to use "Sound Converter" I get this error:  Python (v2.7) requires to install plugins to play media files of the following type: H.264 decoder.   What do I need to make it work?  I'm using Ubuntu 14.04LTS.  I'd like to convert all mp3/mp4 files to wma.  I can get any of my automobile stereos to recognize anything but wma.

---

### Post by Whoopie on 2014-08-10
Do you have gstreamer0.10-plugins-ugly installed? If not, install it and try again.

---

### Post by 3rdalbum on 2014-08-10
> **ray9 said:**
> When I try to use "Sound Converter" I get this error:  Python (v2.7) requires to install plugins to play media files of the following type: H.264 decoder.   What do I need to make it work?  I'm using Ubuntu 14.04LTS.  I'd like to convert all mp3/mp4 files to wma.  I can get any of my automobile stereos to recognize anything but wma.

I don't think you can convert to WMA format on Ubuntu. You can convert from WMA to something else, but you can't convert to WMA.

Every single car stereo that supports WMA also supports MP3. If it's not recognising the MP3s then you should check what settings you are using to create the CD or encode the MP3s.

---

### Post by Rob Sayer on 2014-08-10
I think winff can convert to .wma but I never tried it with that or soundconverter.

*Why* you'd want to convert to wma or wmv in a linux environment is what I have trouble with.  Even when I used to use windows regularly I avoided those formats whenever possible.  It's been years since I used WMP except by accident.

One thing you should do anyway if you haven't before is install proprietary codecs not included with the default ubuntu install.  Do this in terminal:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

which is one of the first things to do after a ubuntu install really.  Soundconverter needs it to output to mp3 properly because it includes the LAME encoder.

---

### Post by ray9 on 2014-08-10
Thanks for the replies.  I stayed up for hours last night trying to get you-tube videos  I downloaded  onto my Sanza Fuse.  None of them would  show up on it, and was using the horrible Win 8.  I couldn't get Ubuntu to put downloaded you-tube videos on Sanza either.  I have in the past but not now.  I formated Sanza to clear all the old music off to start a new list and when I drag the songs over they won't hook up.  They used too but some of them would not play in my auto devices.  Are some coded so that they can't be recorded?  What type of file will work in auto head ends?  Mp3, WAV or what?  The thumb drives I've recorded on have blank spots where some files aren't recognised.

---

### Post by andrew.46 on 2014-11-04
> **3rdalbum said:**
> I don't think you can convert to WMA format on Ubuntu. You can convert from WMA to something else, but you can't convert to WMA.

It is a pedantic point but FFmpeg will *encode* to Windows Media Audio 1 & 2:

```

andrew@ilium~$ **[COLOR="#FF0000"]ffmpeg -encoders 2>/dev/null | grep wma[/COLOR]**
 A..... wmav1                Windows Media Audio 1
 A..... wmav2                Windows Media Audio 2

```

and *decode* the rest of the family:

```

andrew@ilium~$**[COLOR="#FF0000"] ffmpeg -decoders 2>/dev/null | grep wma[/COLOR]**
 A....D wmalossless          Windows Media Audio Lossless
 A....D wmapro               Windows Media Audio 9 Professional
 A....D wmav1                Windows Media Audio 1
 A....D wmav2                Windows Media Audio 2
 A....D wmavoice             Windows Media Audio Voice

```

Not much help to the OP though...

---

