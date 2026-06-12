---
title: "CPU usage on Linux"
date: 2017-03-10
forum: New to Ubuntu
---

### Post by charlie102 on 2017-03-10
Hello

I use dual boot. I have Lubuntu 16.04 and win7. It is curious but when I open a 720p video on YT on Linux CPU usage is 100% and the video hangs every few seconds. On Win7 cpu usage is about 60% and the video goes smoothly (we are talking here about the same 720p video on YT). I use integrated graphics. My MOBO is g31m-es2l. What comes to my mind is that it could be the problem with video driver on lubuntu that seems not good enough. I use integrated graphics. 

What underlies this problem and how to fix it?

thx

---

### Post by oldrocker99 on 2017-03-10
You can't use different drivers. The Intel drivers are all open-source (Intel's doing) and are updated semi-frequently.

---

### Post by ajgreeny on 2017-03-10
Are you using flash or html5 to view the videos in both OSs or does one use flash and the other html5?
Flash in Linux tends to use a lot of resources; html uses fewer resources, but still quite a lot, and it may also have problems with hardware acceleration, therefore using the cpu instead of graphic chip.

---

