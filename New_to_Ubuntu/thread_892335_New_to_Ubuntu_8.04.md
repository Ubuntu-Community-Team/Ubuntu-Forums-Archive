---
title: "New to Ubuntu 8.04"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Chris_UAE on 2008-08-17
Hi! I decided to look at using Ubuntu after I was sick and tired of all the nightmares surprises of Win XP , But I guess like any new user I find my self happy to look at the features of Ubuntu bit also worry about the support I require for applications and hardware. Firstly its my wireless internet connectivity I just cant get it to work, next I am not able to install all supporting drivers for other hardware device that I use:
HARDWARE
1) Logitech Cordless Desktop® MX&#8482; 3200 Laser
2) Creative - USB Sound Blaster Digital Music SX 
3) Nvidia graphics card
4) USB wi-lan 

SOFTWARE
1) MS Office 2007
2) Adobe Suite
3) Macromedia CS
4) Sonar 6 Cakewalk
5) iTunes / (iPod/MP3/MP4/Pod Cast support)

Well I was told about using WINE but I have no idea which one to use or is it already installed as a default application in Ubuntu 8.04.

Please advice how I could get all this stuff working on my PC. Any links out or advice would be highly appreciated.

Regards
Chris

---

### Post by crispy_420 on 2008-08-17
Hardware
1) Does that mouse have "extra" buttons like foward/backward?
2) not sure, I don't have one to test with... someone else chime in
3) NVidia, no problem
4) what chipset for wireless, hopefully Zydas

Software
1) OpenOffice
2) image editing? then gimp
3) don't use so not sure
4) simple audio editing? audacity but there are multitrack editors available as well
5) rhythmbox? don't use iPod right now

---

### Post by erickghint on 2008-08-17
Which nVidia card are you using? 

 Also, you can read up on Wine at [www.winehq.com](www.winehq.com) . They have a nice database on programs that will and will not work with Wine.

To install the newest version of Wine, go to Applications>Accessories>Terminal and type :
```
sudo apt-get install wine 
```

---

### Post by Chris_UAE on 2008-08-17
Thanks a ton..I will try to sneek out of my office early to try out your kind advice. The logitech hadrware is functioning except that the logitech software provides additional features such as onscreen displays etc. Could you provide me with any information about wine...and how to go about it...I was told that it helps install win hardware drivers into Ubuntu.
Thanks and Regards
Chris

---

### Post by Chris_UAE on 2008-08-17
Thanks I will take your advice and check the Nvidia postings to see which one suits my hardware...
Regards
Chris

---

### Post by 3rdalbum on 2008-08-17
> **Chris_UAE said:**
> Could you provide me with any information about wine...and how to go about it...I was told that it helps install win hardware drivers into Ubuntu.

Wine can help you run some Windows programs in Linux, but not hardware drivers, and not many Windows programs. Windows drivers are incompatible with Linux, and vice-versa.

When you move from one operating system to another, you're not just moving operating system. You are moving from an entire platform to another platform. As such, you need to leave behind many of the programs you already know, and learn new ones that are relevant to the Linux platform.

The Logitech mouse software (since when does a mouse need drivers, anyway?) is an example of something you'll be leaving behind, but there may be a way to get a similar function on Linux with different software.

If you are scared by the thought of learning new software, then you should move back to Windows. If you do really want to switch away from Windows as a platform, then welcome to Linux :-)

---

### Post by Chris_UAE on 2008-08-17
Thanks for the Tip...its makes a lot of sense...well off with the old and on with the new, my only fear is compatibility when it comes to work assignments. Since all my co workers are with Win XP I just noticed that office documents and power point files behave and look slightly different. As mentioned earlier I am really very new to Ubundu, I guess its just teething probs that one goes through at early stages. Thanks for the tips I will take your advice...
Regards
Chris

---

### Post by Crafty Kisses on 2008-08-17
Supposedly you can use iTunes through Wine, and if you don't know how to use Wine or what it is, here is a great link > [http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)****

---

