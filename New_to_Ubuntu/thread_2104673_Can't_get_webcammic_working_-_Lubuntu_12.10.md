---
title: "Can't get webcam/mic working - Lubuntu 12.10"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by DiabolicalClaptrap on 2013-01-13
Hi,
I plan to make a slow switch over to Lubuntu from Windows because  frankly, I'm a bit tired of the bloat and security holes present in  Windows. Always trying to get more bang for my buck, I sought out  Lubuntu and I'm glad that I did! It's a good, no nonsense alternative to  all the bloat and face palm worthy issues that exist in Windows.
Anyway,  my problem is that I can't get either of my webcams/mics to work. I own  an Acer Aspire 5740 (6378) laptop which has an integrated mic and  Crystal Eye webcam. I also own an HP 3110 webcam (which has a mic). I've  scoured the web (this forum included) and can't seem to find any  solutions. Is there anything I can do to mend this? Any suggestions  would be appreciated.
Thanks in advance!

---

### Post by cariboo on 2013-01-13
It would help if you told us what version you are using, and what have you tried. I'm running Raring (13.04) and my web cam works in skype, but not cheese.

---

### Post by DiabolicalClaptrap on 2013-01-14
> **cariboo907 said:**
> It would help if you told us what version you are using, and what have you tried. I'm running Raring (13.04) and my web cam works in skype, but not cheese.

I'm using Lubuntu 12.10 (Quantal Quetzal) (which I put in the title :) ) and I've tried Cheese, Skype and Camorama.

Edit: Add guvcview to that list.

---

### Post by DiabolicalClaptrap on 2013-01-14
I went out on a limb and contacted HP support. They can't do anything. However, my suYin crystal eye cam seems to be registering in Lubuntu. Though I haven't gotten it to work just yet (with cheese :( )

---

### Post by matt_symes on 2013-01-14
Hi

I have/had (It's currently broken) the same laptop as you and had Lubuntu 12.04 (the previous version). The webcam was working correctly.

To see if it a regression can you download 12.04 and out it on a usb stick and boot from it to try your webcam ?

You have uvcvideo.ko kernel module loaded ?

What messages do you get if you start cheese et al from the command line ?

As for the mic, you have checked it is on using alsamixer ? It has input volume in sounds applet ?

Kind regards

---

### Post by DiabolicalClaptrap on 2013-01-15
I can try, though I'll have to create another disc for 12.04 (currently, I'm out). Perhaps I could try from VMware in the meantime?

To answer your other questions:
I can't be sure that I did have uvcvideo,ko loaded

Haven't tried running any of the aforementioned programs via terminal.

Also haven't tried alsamixer. I will give that a try. And no, no input is displayed in the volume mixer. :(

Edit: Booted up an older VM w/ Lubuntu 12.10 installed, Suyin cam attached, ran GUVCVIdeo (from the menu) and my cam shows. :) Now onto Skype to test a/v together.

---

### Post by DiabolicalClaptrap on 2013-01-15
This is odd. Both webcams now work right out of the box! (Installed Lubuntu on an older lappy w/ Wubi) However, the microphone on the HP 3110 doesn't work and lacks options in volume control. Hmm...

---

### Post by DiabolicalClaptrap on 2013-01-17
Experimented a little in VM workstation (with Lubuntu 12.10, full install). I ran a check on my audio devices with ```
cat /proc/asound/cards
``` and I noticed that:
1) My sound card is recognised as 0 [AudioPCI      ]:ENS1371 -Ensoniq AudioPCI
Ensoniq AudioPCI ENS1371 at 0x2080, irq 16

My HP webcam is picked up as well:

1 [H3110I      ]:USB-Audio - HP Webcam 3110
HP HP Webcam 3110 at usb-0000:00:1d.7-6, high speed

2) When connecting my HP 3110 webcam, I can change its mic volume in the capture menu in alsamixer. In the same menu with my built in mic, I can only adjust the capture volume, and not the mic volume.

[IMG]http://oi46.tinypic.com/334u78i.jpg[/IMG]



I ran tests on both mics with ```
arecord -d 10 /tmp/test-mic.wav
``` and Skype. On the former, I hear static noise on playback. However, I don't hear anything on Skype. I also made sure the proper device was selected for each test.

Is there any way I can go about getting either of these mics to work?

---

### Post by DiabolicalClaptrap on 2013-02-16
Just thought I'd reply back to say that using PA server fixed my issue.

---

