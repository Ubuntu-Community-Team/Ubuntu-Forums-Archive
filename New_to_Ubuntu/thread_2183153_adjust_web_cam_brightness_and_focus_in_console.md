---
title: "adjust web cam brightness and focus in console"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-10-23
Hi all, 

this is my "script" for saving picture from web cam: 

fswebcam  --quiet --device /dev/video0 --resolution 640x480 --top-banner  marchelloUA_webcam1 --gmt --png 9 --save /mnt/wd_incoming/test.png

It works, but I need your help, how do I adjust web cam brightness and focus in console?

---

### Post by newb85 on 2013-10-24
I don't have any experience with fswebcam (apparently I don't even have it installed) but in skimming the man page I noticed it has a "-s" option for setting controls like brightness, framerate, etc.  See the manpage for syntax.  Also, use the "--list-controls" option to see what controls are available for your camera.

---

### Post by coldraven on 2013-10-24
You might try running uvcview and set the brightness, you might need to uncheck "Auto levels".
When you quit uvcview these should become the default settings for your webcam. There is no need to save before quitting.

---

