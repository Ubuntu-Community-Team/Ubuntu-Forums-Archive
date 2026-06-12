---
title: "still cannot record sound"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by Unguidedone on 2011-09-12
I have been using ubuntu for a year or so now and I still cant figure out for the life of me how to record the sound?  When I try and record audio with recordmydesktop it records no sound or records static.  Any help?

---

### Post by robert shearer on 2011-09-12
If it is audio **only** that you want then see this thread....
[http://ubuntuforums.org/showthread.php?t=1835212](http://ubuntuforums.org/showthread.php?t=1835212)

For audio and video then the next along may have your answer..

Cheers, Bob

---

### Post by Unguidedone on 2011-09-12
I did everything it said from :   [http://ubuntuforums.org/showthread.php?t=1672679](http://ubuntuforums.org/showthread.php?t=1672679)

and i had all the audio encoders already installed then tested a audio sample and nothing was heard :(  I am thinking that i dont have audio drivers installed correctly.

---

### Post by robert shearer on 2011-09-12
No, beep, wrong !
Use the first link...
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

and read to see that **all** you have to do, to install the Audio recorder, is enter the following commands....

```
sudo apt-add-repository ppa:osmoma/audio-recorder
```
```
sudo apt-get update
```
```
sudo apt-get install audio-recorder
```



Start the program from Applications -> Sound & Video menu
 or run in a terminal:
```
audio-recorder
```

Presumably you have sound when playing audio normally ?
if so the drivers are installed.
(If not then you can't record what you can't hear :D)

Recording is a whole other kettle of fish and the Audio recorder app is the best I have found yet.

---

### Post by Unguidedone on 2011-09-12
i had already installed that program :( 

I can hear audio from cd/s dvds/ youtube but i cant seem to record it.

It might be a hardware issue then a software

[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/dumbmic.png[/IMG]

---

### Post by dniMretsaM on 2011-09-12
Try OutRec. I don't remember if it's in the repositories or not, but here's the project's homepage on SF: [http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

---

### Post by robert shearer on 2011-09-12
Looking at your screen-shot you have the connector selected for **Analog microphone**.

Is that what you are trying to record from ??? 'cause that might explain your > records no sound or records static

Try using the drop-down menu to select the source you want to record.

---

