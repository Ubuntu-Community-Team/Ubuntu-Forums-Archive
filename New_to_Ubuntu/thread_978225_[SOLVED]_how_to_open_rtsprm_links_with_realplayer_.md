---
title: "[SOLVED] how to open rtsp/rm links with realplayer in firefox (intrepid)"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-11-10
I spent a couple hours trying to figure out why firefox would tell me that it could not find the real stream file whenever I clicked on a "watch this" link on cspan.  It turns out that the realplayer package in the repositories is flawed!!  When it sets up the "helpers" for firefox, it tells it to use /usr/local/real/realplay to open the files.  Unfortunately, it should be /usr/bin/realplayer.  Notice that not only is the directory wrong, but so is the app.  

By changing the setting in "edit>preferences>applications>rtsp to use the appropriate app, the problem is solved and rm links will work.

I know I should be asking for help here, but I figured that if I had to figure it out, so will someone else.  Hopefully this saves someone some time.

JTS

---

