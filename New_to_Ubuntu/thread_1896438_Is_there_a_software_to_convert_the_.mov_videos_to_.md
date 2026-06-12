---
title: "Is there a software to convert the .mov videos to Video DVD in Ubuntu ?"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by arai on 2011-12-16
I have a Canon Digital Camera. I capture videos with it. The videos are in .mov format. I want to make it viewable in normal DVD players so that I see the videos in my Television. 

Is there a software to convert the .mov videos to Video DVD in Ubuntu ?

---

### Post by kostkon on 2011-12-17
Try DeVeDe. It will convert the videos for you and also allow you to  create a DVD menu. 

It will create an iso file for you to burn.

Hope that helps.

---

### Post by ajgreeny on 2011-12-17
> **kostkon said:**
> Try DeVeDe. It will convert the videos for you and also allow you to  create a DVD menu. 

It will create an iso file for you to burn.

Hope that helps.
+1

I have used it several times to burn DVDs which will play on any DVD player.

---

### Post by arai on 2011-12-17
> **kostkon said:**
> Try DeVeDe. It will convert the videos for you and also allow you to  create a DVD menu. 

It will create an iso file for you to burn.

Hope that helps.

Thanks. It worked but without sound. VCD created but there is no sound. Any solution ?

---

### Post by Buntumatic on 2011-12-17
You should understand what you are doing first. For instance, mov is not a format, it is a container. Usually containing MPEG-4 compliant video and AAC sound (maybe something else, though). You do not want to recode the video, all codecs are lossy, resulting in degraded quality. 
What kind of device it is you are trying to play it with? Most of DVD players can play MPEG-4 nowadays.

---

### Post by arai on 2011-12-17
> **Buntumatic said:**
> You should understand what you are doing first. For instance, mov is not a format, it is a container. Usually containing MPEG-4 compliant video and AAC sound (maybe something else, though). You do not want to recode the video, all codecs are lossy, resulting in degraded quality. 
What kind of device it is you are trying to play it with? Most of DVD players can play MPEG-4 nowadays.

Samsung DVD Player

It does not play Data CD/DVD. It plays only Audio CD/DVD and Video CD/DVD.

---

### Post by Buntumatic on 2011-12-17
Invoking mplayer with -identfy will tell you what you are dealing with, the next step is to learn more about capabilities of your DVD player. Less recoding you do better the result.

---

