---
title: "HOWTO: Get VBR Mp3 from Rhythmbox"
date: 2010-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by W3ird_N3rd on 2010-06-01
This guide is written for Ubuntu 9.10 and 10.04. Older/newer versions may also work but have not been tested.

Wouldn't it be nice to rip your favourite CD to high quality VBR Mp3 with Rhythmbox so you can play it on your Mp3 player? I'll tell you how.

First, we need to install some packages containing the required Mp3 encoder. Go to System>Administration and open Synaptic Package Manager. Search for gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse. Right-click on each one and select "Mark for installation". When you're finished, click Apply.

If you can't find those packages, go to Settings>Repositories and make sure Universe and Multiverse are enabled. Don't forget to click reload after enabling!

Now go to Applications>Sound & Video and start Rhythmbox. Go to Edit>Preferences>Music and click the "edit" button next to the preferred format. Select "CD Quality, MP3" and click Edit. Empty the field for "GStreamer pipeline", and paste the following into it:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```
The "2" for VBR-quality can be changed if you like. Higher numbers lead to smaller files and lower quality. 0, 1, 2 or 3 are good for high quality, 4, 5 and 6 are good for mobile use (when your storage is limited). 7 and higher don't sound very well.

Now click close, click close again, make sure your preferred format is "CD Quality, MP3" and click the final close button.

When you add a CD to your library now, it will be VBR Mp3.

---

### Post by OzzyFrank on 2010-10-09
Hi. I noticed that besides changing the VBR quality, you also added **[COLOR="Purple"]xingmux ![/COLOR]** so was wondering the significance of that. Thanks for your guide. Cheers.

---

### Post by growingneeds on 2010-11-02
Many thanks. But only 2 metapackages are required:
[LIST=1]
[*]gstreamer0.10-plugins-ugly-multiverse
[*]gstreamer0.10-plugins-ugly
[/LIST]

I finally can rip into VBR MP3s with normal seek times! Hallelujah!

---

### Post by Subito Piano on 2011-01-02
=D> thank yew, thank yew...  (they need a "thank you" button for these posts....)

---

### Post by oaxacamatt1 on 2011-01-06
Hi All,
I was curious about the Xingmux too, so I looked it up and found it adds a header to .mp3.  Appaerently the header gives info regarding the duration and size of the file and a seek table and is very useful for getting an almost correct duration and better seeking on VBR MP3 files.

Check it out, (good question):
[http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-xingmux.html](http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-xingmux.html)

Cheers,
M

---

