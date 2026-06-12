---
title: "Radio Tray AWOL in Lubuntu 10.04."
date: 2011-10-15
forum: New to Ubuntu
---

### Post by casbahdk on 2011-10-15
I installed Radio Tray on my EeePC 701 running Lubuntu 10.04 and am getting the following errors:

$ radiotray
Loading configuration...
/home/user/.local/share/radiotray/bookmarks.xml
/home/user/.local/share/radiotray/config.xml
/usr/share/radiotray/config.xml
PLS playlist decoder
M3U playlist decoder
ASX-familiy playlist decoder
XSPF playlist decoder
ASF playlist decoder
RAM playlist decoder
Using url timeout = 100
Traceback (most recent call last):
  File "/usr/bin/radiotray", line 15, in <module>
    radiotray.main(sys.argv[1:])
  File "/usr/lib/pymodules/python2.6/radiotray/radiotray.py", line 37, in main
    RadioTray()
  File "/usr/lib/pymodules/python2.6/radiotray/RadioTray.py", line 63, in __init__
    self.audio = AudioPlayerGStreamer(self.mediator, self.cfg_provider, self.log)
  File "/usr/lib/pymodules/python2.6/radiotray/AudioPlayerGStreamer.py", line 37, in __init__
    self.souphttpsrc = gst.element_factory_make("souphttpsrc", "source")
gst.ElementNotFoundError: souphttpsrc

I have looked through a lot of postings, but I haven't found anything relevant to my situation. I have checked the libraries that Radio Tray depends on. I have also installed the gstreamer bits that are included in the ubuntu-restricted-extras package and no luck there either.

Does anyone have an idea what is happening?

---

### Post by casbahdk on 2011-10-16
I found the answer. Install gstreamer0.10-plugins-good

---

