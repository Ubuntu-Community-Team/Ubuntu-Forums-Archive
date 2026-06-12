---
title: "Integrated Mic doesnt work on Acer Aspire 4810T on ubuntu 12.04"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by kuerbiskernoel on 2012-09-17
Hello people out there,

I already spent hours even days to find out how to fix my integrated mic :D I'm using the current version of ubuntu 12.04 on my Acer Aspire 4810T.....I already downloaded the PulseAudio, but it didnt really change anything! When I'm checking my audio settings there's no input device which I could chose (system settings > audio> input, box on the left side is empty)?! 
So I would be so glad if anybody could help me :)

thanks in advance 

kuerbiskernoel

---

### Post by heyandy889 on 2012-09-17
Hi, pal. Welcome to the forums.

Honestly, trying to get Audacity working in Ubuntu is kind of a hassle. My usual troubleshooting:

* pre-installed Sound Recorder application. Lets you check levels (if anything is there), record something if possible.

* "Sound" preferences. Looks like you have already tried that, but anyway you can find it just by hitting Super/Dash and typing Sound. 

* Audacity's audio meters. Maybe the app you're trying has some sort of mic diagnostic?

Beyond that

```
sudo apt-get update
```always a good call. Maybe it is a bug that was just fixed, or you have package dependencies that are screwy . . . honestly, it's a long shot, but hey, why not.

Also, what happens if you try an external mic? On my laptop, the built-in mic is extremely noisy. Using just a karaoke-style mic with an 1/8" jack will usually work. 

Good luck, pal!

---

