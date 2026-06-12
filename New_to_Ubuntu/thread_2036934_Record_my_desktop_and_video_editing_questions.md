---
title: "Record my desktop and video editing questions"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by Sarys on 2012-08-03
So I have record my desktop and I want hints how to use it with best effect (I want to do let's play/gameplay videos to youtube. And then I want to know how to know video editing program so I can edit them so I can but them to youtube.

---

### Post by NikTh on 2012-08-03
Hi , 
personally use ffmpeg to record my desktop.  Depends of quality you want , give appropriate command in terminal. 
Take a look --> [http://ubuntuforums.org/showthread.php?t=1710642](http://ubuntuforums.org/showthread.php?t=1710642)

For editing video , I use openshot. --> [http://www.openshotvideo.com/](http://www.openshotvideo.com/)
Video review - ("tutorial")  for openshot here --> [http://www.youtube.com/watch?v=Oy7sOxUg3Hc&feature=relmfu](http://www.youtube.com/watch?v=Oy7sOxUg3Hc&feature=relmfu)

Thanks

---

### Post by Sarys on 2012-08-03
> **NikTh said:**
> Hi , 
personally use ffmpeg to record my desktop.  Depends of quality you want , give appropriate command in terminal. 
Take a look --> [http://ubuntuforums.org/showthread.php?t=1710642](http://ubuntuforums.org/showthread.php?t=1710642)

For editing video , I use openshot. --> [http://www.openshotvideo.com/](http://www.openshotvideo.com/)
Video review - ("tutorial")  for openshot here --> [http://www.youtube.com/watch?v=Oy7sOxUg3Hc&feature=relmfu](http://www.youtube.com/watch?v=Oy7sOxUg3Hc&feature=relmfu)

Thanks

Ffmpeg looks way too complicated compared to record my desktop.

EDIT: But can I use ffmpeg to record my webcam and game at the same time? and mix them with openshot?

---

### Post by NikTh on 2012-08-03
> **Sarys said:**
> Ffmpeg looks way too complicated compared to record my desktop.

EDIT: But can I use ffmpeg to record my webcam and game at the same time? and mix them with openshot?

Hi , 

I don't know if you can record at the same time from your desktop and camera.  

You can use an external camera and mix all together with openshot. 

Thanks

---

### Post by Sarys on 2012-08-04
> **NikTh said:**
> Hi , 

I don't know if you can record at the same time from your desktop and camera.  

You can use an external camera and mix all together with openshot. 

Thanks

So I can mix them?! Finaly free program to that but only problem is that I still need to learn how to use ffmpeg....Or find another one.

---

### Post by HermanAB on 2012-08-04
Also try Istanbul and VLC.

---

### Post by Sarys on 2012-08-08
> **99sanni said:**
> Camtasiais surely your best choice, but it is a little expensive. of course, you also can consider another one, [video editor mac]("http://www.videoeditormac.net/"), which can help you edit and convert video to youtube flv files for uploading to youtube with ease.

I'm looking for free programs for the time being and I'm not gonna use apple.

---

### Post by FakeOutdoorsman on 2012-08-08
> **NikTh said:**
> Hi , 
personally use ffmpeg to record my desktop.  Depends of quality you want , give appropriate command in terminal. 
Take a look --> [http://ubuntuforums.org/showthread.php?t=1710642](http://ubuntuforums.org/showthread.php?t=1710642)

You'll possibly get better performance by using lossless H.264 as shown here: [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719)

(or simply add **-preset ultrafast -crf 0** to shantiq's libx264 examples.)

---

