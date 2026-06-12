---
title: "do I really need drivers?"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Myxoma on 2012-02-02
Hey there fellow newbie. I think I can at least answer your question about the hard disk... If you're planning on installing ubuntu to to disk c:// then your secondary shouldn't be affected at all. I actually loaded the os onto my primary along with my old windows os and the installer gave me the option to partition off space for ubuntu so none of my files would be affected.

I can also safely my brief experience with linux has been pleasant so far. Only trouble I'm having is connecting to the internet. I'll leave everything else you asked to the pros though.

---

### Post by Ljano on 2012-02-02
Hi there, this is my first thead, I've just joined this site some minutes ago so nice to meet you guys. 

Yesterday I used the LiveCD to check how ubuntu works in my laptop.  There was a sample song and a video in a folder so i oponed them and I  could watch the video perfectly and I could listen to the song aswell  (they were neither MPEG nor MP3). Even my printer also worked out well  and my webcam light was on. :razz:

My card is an ATI Mobility Radeon HD 2400 and my speakers are Realtek. I  have downloaded a drivers pack for my laptop (fujitsu siemens pi2540)  just in case.

I have only had problems with the wifi (I guess I'll try a wire)

_So my questions are:_


[LIST]
[*] Is it possible that my laptop works so well with ubuntu??  Because I have only heard scary stories about going to ubuntu. Using the  LiveCD is enough to make sure if things work out correctly?
[/LIST]

[LIST]
[*]If I install Ubuntu in C://, all the stuff I've got in my secondary hard disk, D://, will be erased?
[/LIST]

[LIST]
[*]Even if the audio and video seem to work well in ubuntu, should I have to install any driver anyway?
[/LIST]

[LIST]
[*]Any other tip?
[/LIST]
Thanks :wink:

---

### Post by raja.genupula on 2012-02-02
[LIST]
[*] Is it possible that my laptop works so well with ubuntu??  Because I have only heard scary stories about going to ubuntu. Using the  LiveCD is enough to make sure if things work out correctly?
[/LIST]
It will be fine with Ubuntu in you laptop. But its better gives us your configuration information .

[LIST]
[*]If I install Ubuntu in C://, all the stuff I've got in my secondary hard disk, D://, will be erased?
[/LIST]
At what partition you install Ubuntu, only that partition will get the effect and no other partition and hard disk will be effected .

[LIST]
[*]Even if the audio and video seem to work well in ubuntu, should I have to install any driver anyway?
[/LIST]

Then , No need to install any drivers .

after installing Ubuntu in your laptop ,if you got any problem please post here . we are here to help you . 

All the best and i am sure you wont get any problem .

---

### Post by sanderd17 on 2012-02-02
All drivers are normally directly in the kernel. Only for some stubborn companies, extra drivers are needed. This is Linux, not Windows.

Normally, you don't install "in a partition". If you use a Live CD to install, it will ask to shrink a partition and create a new partition on that free space. So nothing will be lost (but make a backup, just in case something crashes).

---

### Post by Frogs Hair on 2012-02-02
I am assuming you are referring to graphics card drivers , so if I am wrong correct me . 

If you are content to run Unity 2D or don't need 3D drivers to run effects of any kind , the answer is no . If you would like to experiment with the CCSM and plug-ins then you will .

---

### Post by N00b-un-2 on 2012-02-02
That is entirely dependent on your hardware and which version of Ubuntu you're running, and which kernel.  There are in fact free drivers ie; radeon and nouveau which do provide 2d and 3d acceleration for ATI and nVidia graphics cards respectively.  That being said, typically you will get better performance out of most (not all) graphics cards by using the proprietary binary drivers like fglrx and nvidia.  On the other hand, certain legacy hardware which had proprietary drivers in prior versions of Ubuntu/Linux have been superseded by the free drivers either because the free drivers provide greater or equal functionality to the proprietary ones, or because the manufacturer has dropped support for the legacy hardware.
For example, I have a desktop PC which has onboard ATI Radeon Xpress 200 graphics.  Ubuntu 9.10 and before had proprietary fglrx support for the X200 chipset, but since 10.04 and later, only the xserver-xorg-video-radeon driver is available because ATI no longer supports this hardware with the FGLRX package.  The reason being that the open driver meets or exceeds the performance of the proprietary driver and has done so since at least Ubuntu 8.10 and later so eventually the driver was dropped in order to reduce footprint.
However, if you have a later model ATI or nVidia graphics card you should install the driver that jockey-gtk prompts you to install. 
Hope this helps.

---

### Post by oldos2er on 2012-02-02
Threads merged. Please don't start more than one thread per topic.

---

