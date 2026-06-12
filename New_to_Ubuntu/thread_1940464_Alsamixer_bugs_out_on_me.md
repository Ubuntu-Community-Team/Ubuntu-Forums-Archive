---
title: "Alsamixer bugs out on me"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by Shob on 2012-03-13
Hello,

I have been trying to get my sound working for the better part of 2 days now (ubuntu 11.10).  I read up on all post relevant to my problem with no luck.

Problem:  
After a couple clean installs, the alsamixer stops working, in-turn the sound as well and the speaker icon disappears.
Now this happens very randomly, 3 days ago it happened after a reboot.  I though I might have downloaded some corrupt package.  
Yesterday, it happened while I was in xbmc tweaking the appearance and settings in windowed mode and started skype which ended up bugging on me and not displaying the window.  I went ahead and did a reboot, and no sound.
Today after a clean install, I did a software update, reboot, still had sound, install nvidia proprietary driver, reboot, still had sound, tweaked my display, reboot and no sound...

Troubleshooting:
I've un-installed, purged, cleaned and re-installed alsa-base and pulseaudio, I do not see my hardware or speakers (usb).
In the terminal "alsamixer" gives me: cannot open mixer: No such file or directory
when I do "which alsamixer"  I get: /usr/bin/alsamixer
when I do "/user/bin/alsamixer/ it gives me: cannot open mixer: No such file or directory
Before the loss of sound, the alsamixer command worked fine, it did pop up and I could adjust the volume andI did see my on-board sound card and speakers in the "system settings>sound" module. 
I've done the troubleshooting guides that I could find, but without he alsamixer I barely get past the first few steps.

Solution:
I hope someone can help me find one, I am really inclined to think something is corrupting my alsamixer though, I dunno I am noob at linux.

Please help :)

Thanks.

---

### Post by lidex on 2012-03-13
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

