---
title: "Slow webcam?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-10-05
My built in dell webcam which works out of the box with Ubuntu hardy heron seems really kinda slow? is this normal? as I don't remember it being like this in XP:confused:

---

### Post by kamitsukai on 2008-10-05
> 5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

Just tried the advice i found in the cheese faq but it didn't help (do i need to restart?)

---

### Post by kamitsukai on 2008-10-05
OK scrap that just tried a program called "luvcview" and my webcam works flawlessly...but how do I get it to work flawlessly with everything else?

---

### Post by kamitsukai on 2008-10-11
<Bump> Anyone?

---

### Post by bisconer on 2009-09-09
BUMP

Did any one find an answer to this issue? i need it to work smooth in other programs as well.

---

### Post by malkyus on 2010-05-20
In Cheese - go to edit - preferences - resolution - lower the resolution - I'm using 640x480

Good luck!

---

### Post by mcbelisle on 2010-05-30
I just tried that and it worked. I was looking for something like that for a while now. Thanks. 

I just don't see why that setting would make a difference.

---

### Post by Bob Bertrands on 2010-05-30
lower resolution means less presure on your graphics card?

---

