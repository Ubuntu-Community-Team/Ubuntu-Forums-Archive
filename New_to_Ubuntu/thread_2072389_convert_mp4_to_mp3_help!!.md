---
title: "convert mp4 to mp3?? help!!"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by sunnypt on 2012-10-17
Hi i tried to convert a file from mp4 to mp3 using this [http://askubuntu.com/questions/80954/how-to-convert-a-video-to-mp3](http://askubuntu.com/questions/80954/how-to-convert-a-video-to-mp3)  right? but i get this error when  i try to get libavcodec..

sunnypt@sunnypt-Satellite-P300:~$ sudo apt-get install libavcodec-unstripped-52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libavcodec-unstripped-52

i checked my software sources and i have everything checked so it should show up right? 
what should i do now?

---

### Post by OGpmpdog on 2012-10-17
> **sunnypt said:**
> Hi i tried to convert a file from mp4 to mp3 using this [http://askubuntu.com/questions/80954/how-to-convert-a-video-to-mp3](http://askubuntu.com/questions/80954/how-to-convert-a-video-to-mp3)  right? but i get this error when  i try to get libavcodec..

sunnypt@sunnypt-Satellite-P300:~$ sudo apt-get install libavcodec-unstripped-52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libavcodec-unstripped-52

i checked my software sources and i have everything checked so it should show up right? 
what should i do now?

Hi There!!

I have a small brain; I keep it simple.

Download "sound converter" from the repositories.  This simple program is very useful.

Also, if you'd like more options and control, which will probably lead to more headaches:), download "Avidemux" from repositories.

Good Luck.

P.S. you can probably enable the livavcodecs, and many other restricted extras, by installing the Medibuntu PPA to your software sources...

---

### Post by sunnypt on 2012-10-17
> **OGpmpdog said:**
> Hi There!!

I have a small brain; I keep it simple.

Download "sound converter" from the repositories.  This simple program is very useful.

Also, if you'd like more options and control, which will probably lead to more headaches:), download "Avidemux" from repositories.

Good Luck.

P.S. you can probably enable the livavcodecs, and many other restricted extras, by installing the Medibuntu PPA to your software sources...


thx. im looking in medibuntu ppa .. managed to find a howto on adding that :) problem maintains tho..  gonna tri sudo apt-get upgrade and sudo apt-get update and then gonna try again :)

---

### Post by Jakin on 2012-10-17
Sound Converter is pretty good, if you want something abit more advanced later on though- XCFA is darn good. (You will find it already in the Ubuntu Software Center)

---

### Post by oldos2er on 2012-10-17
> **sunnypt said:**
> Hi i tried to convert a file from mp4 to mp3 using this [http://askubuntu.com/questions/80954/how-to-convert-a-video-to-mp3](http://askubuntu.com/questions/80954/how-to-convert-a-video-to-mp3)  right? but i get this error when  i try to get libavcodec..

sunnypt@sunnypt-Satellite-P300:~$ sudo apt-get install libavcodec-unstripped-52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libavcodec-unstripped-52


Depending on which version of Ubuntu you're running, the latest packages are libavcodec-extra-53 and libavcodec53.

---

### Post by sunnypt on 2012-10-17
So after some digging i finally found out how to install medibuntu repositories and found out that i needed to do this
$ sudo apt-get install libavcodec-extra-53
cuz after putting medibuntu repositories that was the only libavcodec available. tried it and now it works :D thx for the help guys!

---

