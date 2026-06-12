---
title: "sound trouble anybody ?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by spencer218 on 2008-06-17
Hello all. I have a problem and so far havent fount any info on to fix it , wondering if anybody has seen the same thing. I installed Xubuntu on my gateway desktop a couple weeks ago and cant get the sound to work right. I get a loud hisss with the sound very low in the background. I can hear music when I play it but it has to be turned way up and still not very good over the static or hissing sound. The computer is an older gateway model 500C and I am not sure whether the sound is from a card or onboard. I found that it is soundblaster live but not sure of much else about it. Is there anybody that can help me or point me to where I can be helped ?  When I opened alsa mixer it says at the top,... sound blaster live value ( ct4871 )  and the chip is  cirrus logic  cs4 297a rev 4 
 I was trying to make sense out of the alsa website but most of it is greek to me.   Any help is very much appreciated,  thanks.

---

### Post by mali2297 on 2008-06-18
Just to be clear on what kind of card and driver you have, enter the following commands in the terminal and post the output.
```

lspci | grep udio
aplay -l

```

---

### Post by spencer218 on 2008-06-18
Thanks for offering some help Martin , I was about to give up. But just a few minutes ago I fixed my problem through alsamixer , wich I already tried before but was unaware that I could scroll sideways and view even more slider controls. I scrolled over to SB live analog/digital output jack , pushed the M key and muted it and now I have crystal clear sound from the speakers. For anybody else that may be trying to fix a similar  problem , here is a helpful web page I found.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61)

Its not the version of ubuntu I have or the same computer , but a lot of the information was "general" enough to help.

---

