---
title: "After upgrade to 8.04 MPG videos won't work"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Hubb50 on 2008-07-22
I upgraded to ubuntu 8.04, now when I try to view a mpg video, it seems to download and then when it starts playing it only runs for a second or two and them stops.  Before I upgraded mpg videos worked fine.  Any thoughts on what is causing this and how to fix it?

---

### Post by Joeb454 on 2008-07-22
Try running ```
sudo apt-get install libxine1-all-plugins
``` from a terminal, and see if it still won't play

---

### Post by fidamehran on 2008-07-22
Doesn't installing the Medibuntu repositories from Syanptic help solve this?

---

### Post by tjwoosta on 2008-07-22
it could be a few different things


it could be that you forgot to install the codecs necessary to play the media
(you can get the w32codecs (or w64codes for 64bit ubuntu) from the medibuntu repository but first you will have to add the repository)

here is a guide
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

or it could be that the video player itself is the problem
(i had that problem and i instaled mplayer and now everyting works)

---

