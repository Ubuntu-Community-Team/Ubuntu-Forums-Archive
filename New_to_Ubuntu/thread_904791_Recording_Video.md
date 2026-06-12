---
title: "Recording Video"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by GreenFire08 on 2008-08-29
Ok so first off I think Ubuntu is really awesome - I have had absolutely ZERO problems with my computer ever since I got rid of Windows Vista. However, there is one particular activity that I simply cannot figure out how to do, and that is record video.

Before while running Vista I used a program called Studio 10 by Pinnacle Systems with a Dazzle DVC 100 USB recording device. I'm pretty sure I can't install that onto Ubuntu using the CD (if this is wrong let me know). However, I can find no suitable recording software anywhere.

If at all possible, could somebody please point me in the right direction as to what I can do? Any help is appreciated.

---

### Post by Crafty Kisses on 2008-08-29
Depends if you want to record your desktop, try using Isntandbul or RecordMyDesktop, both are in the repos.

---

### Post by GreenFire08 on 2008-08-29
No, not desktop - external video, like from a VCR using the USB device I mentioned.

---

### Post by Crafty Kisses on 2008-08-29
I'm not sure, but I have the same device as you the Dazzle DVC100, and some people have claimed they got the Pinnacle software to run under Wine, so you may want to look into that, I personally haven't tried it, but it's possible.

---

### Post by GreenFire08 on 2008-08-29
Wine, eh? I'll look into it, thanks.

---

### Post by Crafty Kisses on 2008-08-29
> **GreenFire08 said:**
> Wine, eh? I'll look into it, thanks.

Yeah no problem, you have the red card right? If so I have the same one.

---

### Post by GreenFire08 on 2008-09-01
Unfortunately I can't get the Studio Software to work under WINE. From what I can tell a lot of people can't do it either, so that avenue seems to be closed. Is there any other software that can record video from an external source?

---

### Post by halitech on 2008-09-01
mencoder will do it but only from the command line. I found this script works (except I have no sound for some reason) but haven't had much time to play with it. You can change the norm and width/height for the location you are in.

mencoder -tv norm=ntsc:driver=v4l2:width=352:height=240:input=0:fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=900:vrc_maxrate=1500:vbitrate=1300:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o capture.mpg

ps. I did not write the script and I can't find the thread I found it in so if it doesn't work, I have no idea why.

---

