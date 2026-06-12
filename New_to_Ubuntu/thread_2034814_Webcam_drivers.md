---
title: "Webcam drivers"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by ebo007 on 2012-07-29
Hi,
I've got an old laptop, it's a HP Pavilion dv6000... I've installed ubuntu 12.04 on it but the webcam doesn't work when I run skype... How can I find out and install the drivers I need for my webcam??

Thank you

---

### Post by dave0109 on 2012-07-29
When I tried to do something similar, I came across the following page:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I only got as far as running the webcam under VLC, because it's actually a camcorder that I was plugging into the computer, but it only runs at 12fps, so a bit rubbish and I couldn't be bothered progressing further.

---

### Post by Matt__ on 2012-07-29
If its the ricoh webcam there are some [_drivers & firmware here_](http://download.tuxfamily.org/arakhne/pool/universe/r/)

I don't know how viable they are and you may have to install gdebi if 12.04 complains about installing, as well as installing Xawtv.

good luck.

---

### Post by NikTh on 2012-07-29
Hi , 
is the cam works with other applications ? 
e.g 
open a terminal and paste this command
```
gstreamer-properties
```
at opened window go to Video > Input > Test , see anything ? 

If yes , then your cam works and the problem is specific to skype , so
install newer version of skype by downloading from here --> [_**Skype 4.0 for linux**_](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/) and see if problem fixed.

Thanks

---

### Post by madjr on 2012-07-29
> **NikTh said:**
> Hi , 
is the cam works with other applications ? 
e.g 
open a terminal and paste this command
```
gstreamer-properties
```
at opened window go to Video > Input > Test , see anything ? 

If yes , then your cam works and the problem is specific to skype , so
install newer version of skype by downloading from here --> [_**Skype 4.0 for linux**_](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/) and see if problem fixed.

Thanks

nice, this was useful, as I usually install cheese just to test things out.

I believe ubuntu also comes with a system-test tool , that can be used for this too.

---

