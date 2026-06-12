---
title: "Amarok"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by johndingli on 2008-11-30
hello i have a problem with amarok.No sound comes out when playing mp3 on amarok.Can anyone solve me the problem.I am using ubuntu 8.10 thanks

---

### Post by SunnyRabbiera on 2008-11-30
well first do you have all your codecs and stuff installed?
MP3's dont work by default in ubuntu for legal reasons but its easy nough to install.

second assuming you did install MP3 support, are you running two applications that have sound at the same time?
There is still an issue with playing multiple sounds for some people.

---

### Post by johndingli on 2008-11-30
sorry but did not install codecs can you please tell me were to find codecs and when you say more than one application running is that you open two applications at the same time or more than one application installed sorry if i may have to ask these questions as i am new to ubuntu and dont want to go back to windows thanks

---

### Post by SunnyRabbiera on 2008-11-30
> **johndingli said:**
> sorry but did not install codecs can you please tell me were to find codecs and when you say more than one application running is that you open two applications at the same time or more than one application installed sorry if i may have to ask these questions as i am new to ubuntu and dont want to go back to windows thanks

i was referring to the ice age old linux issue of playing multiple audio at the same time, so just a bit of warning when you have firefox open and you watch a flash video or something to not have amarok running as it can make the audio device hang and not work.
As for codecs, there is an application called synaptic to help you there, its located under system> administration> synaptic package manager.
From there after you type in your password go up to "settings"
then to "repositories"
from there enable the repositories you will need by clicking the boxes in tabs 1 and 2 but ignore the source code repositories
hit "refresh"
and you should be able to install the ubuntu restricted extras package and MP3 support.

---

### Post by johndingli on 2008-11-30
Thanks SunnyRabbiera for your time i will check this up

---

### Post by SunnyRabbiera on 2008-11-30
If you have issues just ask, lucky for you Ubuntu is quite easy under the hood... its just knowing what to do where you may bump into something.
Also give medibuntu a shot as well:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Elfy on 2008-11-30
you might well need to install libxin1-ffmpeg for amarok, open a terminal - Appllciations >Accessories>Terminal

```
sudo apt-get install libxine1-ffmpeg
```

If you've not done so yet - password is your logon one - it will be invisible in terminal.

---

### Post by markbuntu on 2008-11-30
Get

amarok-engines

it will pull in a bunch of packages with a lot of codecs and decoders etc. also get

ubuntu-restricted-extras

---

