---
title: "No Sound &amp; graphic driver problem in my hp 630 laptop"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by loveguzzy on 2013-02-15
This is the deal, I installed Ubuntu and I came across several problems and researched and made it work with the help of this forum, actually they were not problems, but minor tweaks to be made...anyways the thing is I tried installing the Additional Drivers from the Software Center and opened it but there was only two drivers for my Wireless Card and Bluetooth Card which actually uses the same driver, I didnt find any other driver like graphic or audio. I dont suppose my laptop doesnt suppose Ubuntu very well, cuz I believe Ubuntu supports anything with a bunch of tweaks.....and here I am...to get some tweaks :D

OS > Ubuntu 12.10
Problems : No Sound & Graphic driver i guess (aero effect doesnt work)

Thankz :)

---

### Post by auxilium on 2013-02-15
Hi,

Open terminal by pressing

CTRL ALT t

type in the command

```
lshw
```

and

```
lsmod
```

so we can see the list of your hardware
btw how did u install your video driver? on my experience sometimes "Additional Drivers " fails. So you do it manually

Popular video card driver was from ATI or Nvidia
for ATI, check this out
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

for Nvidia the manual way
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

for Nvidia using the Binary
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

when Tweaking, Manual is your best friend. Good thing we have this forum to get help and also help other


Cheers

---

### Post by squakie on 2013-02-15
Just a silly addition:  for your sound, be sure it's not muted in any of the mixers.  For some reason when I first installed 12.04 my sound was muted and I had to go and "un-mute" it.

---

### Post by Mark Phelps on 2013-02-16
Couple of comments ...

If you are able to see a desktop, your graphics driver IS working; otherwise, you would have a blank black screen.

Second, Aero is a Window graphics function, not Linux.

---

### Post by loveguzzy on 2013-02-16
Guyz....forget about the video driver.... I really need sound to work...what do u suggest I do?

---

### Post by auxilium on 2013-02-17
HI,

Had  you checked your Sound setting on Preferences

Application > Preferences > Sound

You could to some test using that program or play around with the settings until you get them work.

Change the Output Settings and see what works. Then try using some of your audion programs or by playing audio file.



Cheers,

---

### Post by Yellow Pasque on 2013-02-17
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by loveguzzy on 2013-02-17
> **auxilium said:**
> HI,

Had  you checked your Sound setting on Preferences

Application > Preferences > Sound

You could to some test using that program or play around with the settings until you get them work.

Change the Output Settings and see what works. Then try using some of your audion programs or by playing audio file.



Cheers,


I tried at the beginning itself, testing and going through all the system settings. Can hear nothing yet...

---

### Post by loveguzzy on 2013-02-17
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

hey there, I uploaded the Also Info thingy...what now?

---

### Post by Yellow Pasque on 2013-02-18
Now you post the link to it.

---

