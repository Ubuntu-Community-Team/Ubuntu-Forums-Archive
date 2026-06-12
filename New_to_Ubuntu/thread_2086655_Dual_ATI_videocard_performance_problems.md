---
title: "Dual ATI videocard performance problems"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by ProtoPrism on 2012-11-21
Hey,

I recently started using Ubuntu, and with the release of the Steam Beta I got more aware of my video drivers, and how good my video performance is. But it seems something is not configure right, as the performance is not even a third of the performance I have when running windows. I think this is partially due to the fact that my laptop has a dual videocard configuration AMD Radeon HD 6540G2 (6520G + 7470M). I´m running 64-bit Ubuntu with (I think) the 64-bit beta fglrx driver from ATI. I have no idea where I have to look to configure the video card properly,  even after looking on the internet. I have attached some info which I thought to be useful. I hope anyone can help me with this problem.

~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9647
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]


:~$ aticonfig --list-adapters
* 0. 00:01.0 AMD Radeon HD 6520G
  1. 01:00.0 AMD Radeon HD 7400M Series

* - Default adapter


~$ glxgears
302 frames in 5.0 seconds = 60.214 FPS
298 frames in 5.0 seconds = 59.488 FPS
300 frames in 5.0 seconds = 59.888 FPS
299 frames in 5.0 seconds = 59.687 FPS

---

### Post by QIII on 2012-11-21
You have what ATI calls "dual graphics"

What you would expect is that Crossfire would improve performance.  In this case, since you have one on-die GPU and one dedicated, you use what I believe ATI calls "hybrid Crossfire".

I don't know how well that works with Linux, but I'll do some research.

First, though:  when you installed the driver, did you do
```
sudo amdconfig --initial --adapter=all
```

Also, in CCC you can change settings for quality vs speed.  In on a cell phone right now so I can't look at it to tell you exactly where to look.

---

### Post by ProtoPrism on 2012-11-21
I believe I did that, but since I was not 100% sure, I ran it and rebooted just to be sure. It did not give any different results..

As for the CCC settings, when I switch to full focus on performance, I get the following stats from glxgears:

2052 frames in 5.0 seconds = 410.085 FPS
2047 frames in 5.0 seconds = 409.378 FPS
2060 frames in 5.0 seconds = 411.703 FPS
2053 frames in 5.0 seconds = 410.537 FPS


What I forgot to mention is that, when running (720p/1080p) videos/glxgears(video ´heavy´ material) , I get a weird horizontal line of what seems to be adjacent frames. But this is probably just a result of the problems also causing the other symptoms.

---

### Post by QIII on 2012-11-21
In CCC, there is a setting for "Tear Free".

Does that help?

---

### Post by ProtoPrism on 2012-11-21
I´ve checked, but I have no such option in my CCC. :( It should be under Display options, but the only thing there is Xinerama.

---

### Post by QIII on 2012-11-21
Hmmm...  Maybe I'm mixing up my OEMs.

I'll take a look when I get home.

---

### Post by QIII on 2012-11-22
Under "3D", "More Settings", do you have "Wait for vertical refresh" and can you set it to "Quality"?

---

### Post by ProtoPrism on 2012-11-24
Sorry for my late response, I tried updating to 12.10, but I managed to  ruin my grub2 as well as the Ubuntu installation. I have my grub back  now, and can boot to my Windows, but Ubuntu is lost.. I will reinstall as soon as possible, possibly even this evening, and will then try the 'Wait for vertical sync' setting.

---

### Post by ProtoPrism on 2012-11-25
When it's set to quality, it gives this with glxgears:

175 frames in 5.0 seconds = 34.984 FPS
180 frames in 5.0 seconds = 35.897 FPS
179 frames in 5.0 seconds = 35.772 FPS
161 frames in 5.0 seconds = 32.158 FPS

---

