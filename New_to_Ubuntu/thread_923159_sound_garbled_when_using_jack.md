---
title: "sound garbled when using jack"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by pangil on 2008-09-18
hi, i'm using 8.04 on a compaq presario c700. everything seems to be working fine. (except for wireless and lan. thankfully i can still use the usb modem to connect to the internet.) 

the problem i have is during sound capture when using jack. there's no problem with capture when jack is turned off, but when jack is running sound capture is choppy when playback. oh yeah it's also choppy when i'm recording. oh forgot, even when i'm not recording and simply listening to myself talking in the mic, it's still choppy.

i can't seem to find any help concerning this problem in jack's forum so i had to try here. has anybody had this problem? and found the solution? i finally found the software that i can use (ardour2) instead of sonar, but then this problem comes up. help please. thanks

---

### Post by rolnics on 2008-09-18
The reason you might be getting the garbled sound could be a number of things. My thoughts are is your pc up to the job? Was is your pc's spec? And also if you are using a standard 8.04 install then you might need to get a low latency kernel.

---

### Post by markbuntu on 2008-09-18
It could be other operations interfering with jack's use of the cpu. But it could be that your jack setup needs to be adjusted. Are you getting a lot of xruns?

Have you looked in here:

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

---

