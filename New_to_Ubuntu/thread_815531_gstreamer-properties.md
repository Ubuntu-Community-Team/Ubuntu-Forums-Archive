---
title: "gstreamer-properties"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by frank002 on 2008-06-01
Hello:
 I just installed cheese and seems to be working ok. When I looked at the FAQ's on cheese, it mentioned "gstreamer-properties". I would like to know what this is and how to test using it. I am referring to the instructions below.

 You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the  Video   tab
      and change the appropriate settings.

---

### Post by spiderbatdad on 2008-06-01
From the terminal run:
gstreamer-properties

select the vidoe tab. You will see a drop down menu for selecting the appropriate parameter...nothing to code or edit, just click to select.

---

### Post by frank002 on 2008-06-01
Thanks.

---

