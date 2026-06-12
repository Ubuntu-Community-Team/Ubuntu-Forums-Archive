---
title: "Can someone help me get embedded videos to play?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-05-25
Okay this is sort of urgent and I want to have it fixed ASAP. For the people who have been keeping up on the NASA Phoenix Lander today would know why, lol. 

Anyways when I try view a video I get this: [http://www.nasa.gov/help/multimedia/odplayer.html](http://www.nasa.gov/help/multimedia/odplayer.html)

So I do not really know what to do to correct this issue. 

The page I tried to view was: [http://www.nasa.gov/multimedia/nasatv/](http://www.nasa.gov/multimedia/nasatv/) and it directed me to that page above.

Any help would be greatly appreciated.

---

### Post by abn91c on 2008-05-25
try with firefox?

---

### Post by ImThatNerd on 2008-05-25
I was viewing the page with FireFox...

---

### Post by spiderbatdad on 2008-05-25
plays fine for me. Are you running "No Script" firefox extension? If so allow the site.

---

### Post by euchrid33 on 2008-06-05
I'm having a similar problem with embedded videos - have you had any luck getting it sorted out?

---

### Post by st33med on 2008-06-05
Disregard!

---

### Post by st33med on 2008-06-05
You might need the gstreamer plugins. Not sure which:
```
sudo apt-get install gstreamer0.10-plugins-good
sudo apt-get install gstreamer0.10-plugins-bad
```

Edit: The gstreamer0.10-plugins-bad should do since it is a WMA9 video.

---

