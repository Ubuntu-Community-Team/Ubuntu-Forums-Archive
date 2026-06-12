---
title: "Would somebody be able to make me a very simple program that does this please?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-07
I'm using ubuntu 8.04. My webcam is a logitech quickcam orbit mp. It works with skype and aMSN but doesn't work with EasyCam, Camorama or flash. There's a program for windows called manycam which applies special effects to your webcam and the output is a video feed which shows up in flash, msn, skype etc. as a webcam option. I was wondering if somebody could make a very simple program that connects to my webcam in the same way that skype and aMSN do and then simply puts the image from it directly into a new video feed.

Not only would this help me, it would also help a load of other people who are having problems getting their webcams to work. If somebody could do this then please reply.

---

### Post by SunnyRabbiera on 2008-05-07
well you see Ubuntu usually uses pre made software, ubuntu doesnt make most of the programs and applications you see though there are a few ones they can claim.
Webcams are tricky too, remember most of the crap out there are made for windows only and the community can only do so much without support by companies like logitech,

---

### Post by gottabeandrew on 2008-05-07
Yes, i know that if the webcam doesn't work and logitech isn't helping, it's not easy to fix at all. The webcam does work though in some programs so all i need is for this new program to be able to access that feed.

---

### Post by SunnyRabbiera on 2008-05-07
well its a shame this manycam program is for windows only itself and I doubt its team will port it to linux...
But be patient, maybe in a short time from now someone will come along with a fix for this who knows.
I know things in linux seem to work at a glacial pace for some people but if you look around in actuality there is something new for linux almost every day.

---

### Post by gottabeandrew on 2008-05-07
I'm not saying i'm wanting it ported over because i don't need all of the special effects. I would just like a program that simply turns my webcam into a new video feed so i can use it with other applications.

---

### Post by gottabeandrew on 2008-05-09
I'm still in need of a program that does this please. I've discovered that my webcam works with Cheese and luvcview. Maybe if somebody wouldn't know how to make a program to show my webcam and then make it into a video feed, they could perhaps make an add-on for one of these programs which makes the output also be a video feed.

---

### Post by patrickballeux on 2008-08-25
Hi,

If you want to broadcast your desktop as a virtual webcam, it is possible by using recordmydesktop, ffmpeg, flashcam and mjpegtools_yuv_to_v4l.



See [http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html](http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html) for complete details (in french...)


#Sample script...
mkfifo stream.ogg
sudo modprobe vloopback
echo "CTRL-C to stop the capture"
sleep 5
recordmydesktop -width 320 -height 240 -fps 15 --no-sound --on-the-fly-encoding --follow-mouse --overwrite -o stream.ogg & sleep 10 & ffmpeg -i stream.ogg -an -s 320x240 -r 15 -f yuv4mpegpipe - | mjpegtools_yuv_to_v4l /dev/video2
killall recordmydesktop
rm stream.ogg

---

