---
title: "Compiz WMV Fix"
date: 2006-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by jdusablon on 2006-06-13
Some have noticed weird behavior in certain WMV files that used to play in regular Gnome and now look screwy in Compiz.
Symptoms are bad interlacing, which looks like double, triple or quadruple-vision.
I'm going to assume you have or know how to install the codecs necessary to handle WMV media.

**_To fix this:_**

**Warning:** this switches your video rendering from totem-gstreamer to totem-xine. If this bothers you, stop reading.

- Open terminal
- Type:```
sudo apt-get install totem-xine
```
- Type:```
sudo gedit ~/.gnome2/totem_config
```
- Find the following section:```
# video driver to use
# string, default: auto
#video.driver:auto
```
- Add the following line:
```

video.driver:opengl
```
- Save and close gedit.
- Logout and then back in. WMV should now work.
-------
Credit to aamukahvi for the fix.

---

