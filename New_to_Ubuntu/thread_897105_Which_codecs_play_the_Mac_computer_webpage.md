---
title: "Which codecs play the Mac computer webpage"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-08-21
I adore the Mac versus PC tv adverts. I found that Apple has them all online. 

[http://www.apple.com/getamac/ads/](http://www.apple.com/getamac/ads/)

When I enter that URL, I get the Apple page, and a window within it shows something loading, but I never see the adverts.

Which codecs play inside Firefox? Or what does it take to get to see these videos?

---

### Post by Locutus_of_Borg on 2008-08-21
probably quicktime or some such crap

maybe try the mplayer plug-in for firefox

---

### Post by meanburrito920 on 2008-08-21
Install all the Gstreamer plugins through add/remove. That should work for fixing the apple site + many other sites.

---

### Post by SunnyRabbiera on 2008-08-21
yeh works for me too, I got all the codecs and junk.

---

### Post by niteshifter on 2008-08-21
Hi,

Thanks for the link!

They are QT (.mov) files, and play in FF with this codec: libtotem-narrowspace-plugin.so which is part of the Totem plugins 2.20.0 package.

Check what plugins you have in FF typing "about:plugins" (without quotes) into the address bar of FF.

---

### Post by linuxguymarshall on 2008-08-21
Im not sure what codec it is but I was just watching them earlier today. All I have if flashplayer-nonfree and vlc

---

### Post by Mark_in_Hollywood on 2008-08-22
> **meanburrito920 said:**
> Install all the Gstreamer plugins through add/remove. That should work for fixing the apple site + many other sites.

I find that GStreamer and 3 or 4 Gstreamer plug-ins are already installed.

---

### Post by Mark_in_Hollywood on 2008-08-22
> **niteshifter said:**
> Hi,

Thanks for the link!

They are QT (.mov) files, and play in FF with this codec: libtotem-narrowspace-plugin.so which is part of the Totem plugins 2.20.0 package.


This is what I find in about:plugins

QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	   Description 	   Suffixes 	   Enabled
video/quicktime    QuickTime video mov 	           Yes
video/mp4 	   MPEG-4 video    mp4 	           Yes
image/x-macpaint   MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image	pict, pict1, pict2 	Yes
video/x-m4v 	   MPEG-4 video    m4v 	            Yes

---

### Post by Mark_in_Hollywood on 2008-08-22
> **linuxguymarshall said:**
> Im not sure what codec it is but I was just watching them earlier today. All I have if flashplayer-nonfree and vlc

How does flashplayer and vlc "play" inside Firefox?

---

