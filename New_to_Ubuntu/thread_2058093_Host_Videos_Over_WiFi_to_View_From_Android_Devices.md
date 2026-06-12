---
title: "Host Videos Over WiFi to View From Android Devices"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by rez182 on 2012-09-14
Hello, is there anyway to host files from my laptop through the router/wifi & be able to stream those files/videos in my Android Device?

Please dumb it down for us Noobs to understand...

Thanks...

---

### Post by cyb3r_sn4k3 on 2012-09-15
You could create a shared folder on WLAN and copy the video there and connect to the folder using the Android device(I think you have to install an app to accomplish this.) 

Hope it helps :)

---

### Post by lalitnagrath on 2013-01-13
here is how i have done it.

i am running Apache webserver on my ubuntu box, i created a new folder named movies and dropped stuff i want to stream on my phone in same directory i putted my website files in. ubuntu box and android device are accessing same Wi-fi. so if my ubuntu machine is having IP 192.168.1.2. i can open Browser in android and type 192.168.1.2 and i can access files hosted on ubuntu box.

i have been able to stream HD movies this way, without any lag.

ps- First post in five years , yay! :D

---

### Post by rez182 on 2013-01-14
> **lalitnagrath said:**
> here is how i have done it.

i am running Apache webserver on my ubuntu box, i created a new folder named movies and dropped stuff i want to stream on my phone in same directory i putted my website files in. ubuntu box and android device are accessing same Wi-fi. :D



Thanks alta lot this seems promising..

---

### Post by alan21276 on 2013-01-14
I've found PS3 media server to be a good solution for this.

check out the linux section in the forum on this site for good instructions on how to set up.

[http://www.ps3mediaserver.org/forum/](http://www.ps3mediaserver.org/forum/)

---

### Post by John_Swing on 2013-01-14
You can also use [ushare]("https://help.ubuntu.com/community/Xbox360Media#Configuration") to create an UPnP server, its very simple to do. Videos files are streamed on demand and can easily be read by you android device.

John.

---

### Post by sandyd on 2013-01-14
If you don't mind paying for the android app, Plex Media Server is pretty good.

---

### Post by eenofonn on 2013-01-14
I stream videos to my iphone through apache (reads mp4s just fine) not sure what codecs are included on android so the apache method might not work as easily with different formats.  You could also look into minidlna as another option.

---

