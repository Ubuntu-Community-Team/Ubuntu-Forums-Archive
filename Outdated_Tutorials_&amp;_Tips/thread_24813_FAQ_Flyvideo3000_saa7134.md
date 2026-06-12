---
title: "FAQ: Flyvideo3000 saa7134"
date: 2005-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by humanity_to_others on 2005-04-08
Learn your card number in this page: [http://linux.bytesex.org/](http://linux.bytesex.org/)
For Flyvideo 3000 number is 2```
sudo gedit /etc/modules
```add the line```
saa7134 card=2
```and I use tvtime for viewing:```
sudo apt-get install tvtime
```after next reboot for channel scanning:```
tvtime-scanner
``` you can run it from menu

If you want to use mplayer for viewing first install it:```
sudo apt-get install mplayer-386
sudo apt-get install mplayer-fonts
sudo apt-get install w32codecs
```then edit config file,```
gedit .mplayer/config
```and add the following line:```
tv=driver=v4l2:device=/dev/video0:fps=25:chanlist=etc:norm=pal:
audiorate=32000:adevice=/dev/dsp1:input=0:amode=1:normid=4
```and```
mplayer tv://
``` for recording install mencoder:```
sudo apt-get install mencoder
```edit config file```
gedit .mplayer/mencoder
```
add this line:```
tv=driver=v4l2:device=/dev/video0:fps=25:norm=pal:amode=1:
width=640:height=480
```and recording command:
```
mencoder tv:// -ovc lavc -oac mp3lame
```

for radio listening and recording gnomeradio is well enough, first download it:
```
wget -c http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/packages/gnomeradio_1.6-1_i386.deb
```
then install:```
sudo dpkg -i gnomeradio_1.6-1_i386.deb
```I also changed default device from /dev/radio to /dev/radio0 in settings.
you can run it from menu.

---

### Post by steven_ellis on 2005-06-13
Just a quick note on

[QUOTE=humanity_to_others]If you want to use mplayer for viewing you should edit config file,```
sudo gedit  /home/your_user_name/.mplayer/config
```and add the following line:```
tv=driver=v4l2:device=/dev/video0:fps=29.97:chanlist=etc:norm=pal:
audiorate=32000:adevice=/dev/dsp1:input=0:amode=1:normid=4
```and```
mplayer tv://
```[/QUOTE]

fps=29.97 is wrong for any european PAL countries, should be fps=25

Steve

---

### Post by LINJEinc on 2005-08-06
I don't understand how to find the "card number".
I'm trying to get my ASUS TV/FM Card to work under Ubuntu,
and it's using saa7134.

---

### Post by humanity_to_others on 2005-08-18
[QUOTE=steven_ellis]Just a quick note on



fps=29.97 is wrong for any european PAL countries, should be fps=25

Steve[/QUOTE] Thanks for correction, I changed the post.

---

### Post by humanity_to_others on 2005-08-18
[QUOTE=LINJEinc]I don't understand how to find the "card number".
I'm trying to get my ASUS TV/FM Card to work under Ubuntu,
and it's using saa7134.[/QUOTE]
you can also look at this page :> [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)
**17** -> ASUS TV-FM 7134

---

### Post by fragmental on 2005-10-31
If it's not listed in the list of saa713x cards then it could be an OEM product of lifeview.  You can see those cards here [http://www.lifeview.com/usa/html/products/OEM/OEM-main.htm](http://www.lifeview.com/usa/html/products/OEM/OEM-main.htm).  In my case, i believe my card is the goog though it says it's branding is kobian mercury.  the goog card is based on flyvideo 2000 so I know that my card is, for driver purposes, a flyvideo2000.  If it were one of the other 2 cards, it would be a flyvideo3000.  Finding the card number is only half the battle, though.

The driver doesn't always detect the right tuner.  The website says the card  has three different versions with three different tuners, but considering that two of the three are pal only, I know that mine has to be the third.  That still doesn't help me a whole lot, it just tells me that the tuner is universal and can do all the broadcast modes.  I went through the list of possibly tuners by hand.  The card works with tuners 9 and 39, and some of the pal ones, but I live in an ntsc zone.  I just found something that says that the alps tuners(9) are compatible with the lg_api(39).  I sent an e-mail off the lifeview to see if I they can tell me what tuner they use.   I still don't have the radio or the remote working.  I gave up after about an hour.

---

