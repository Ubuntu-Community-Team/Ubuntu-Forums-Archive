---
title: "How to reinstall 11.10 once you have 12.04."
date: 2012-06-04
forum: New to Ubuntu
---

### Post by pokerkid on 2012-06-04
i think i am ready to install 11.10 now. I believe I have the right iso file on my CD but when I put it in to run, it won't let me. 

This is what I have: 
[B]
#define DISKNAME  Ubuntu 11.10 "Oneiric Ocelot" - Release amd64
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  amd64
#define ARCHamd64  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1[/B]

My PC is a AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ × 2 

This should be the right boot disk right? 

Can anyone just tell me what I need to do to get 11.10 on my system?

Thanks.

---

### Post by traditionalist on 2012-06-04
> **pokerkid said:**
> 

My PC is a AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ × 2 

This should be the right boot disk right? 

Can anyone just tell me what I need to do to get 11.10 on my system?

Thanks.

You need a disk that works.  What does the machine tell you when you try to boot that disk. Please give EXACTLY what it says.

---

### Post by critin on 2012-06-04
When you say 'run', do you actually mean 'boot'?  It won't just run to  install itself.  If it won't boot there's possibly an issue with the  burn.




> **pokerkid said:**
> i think i am ready to install 11.10 now. I believe I have the right iso file on my CD but when I put it in to run, it won't let me. 

Can anyone just tell me what I need to do to get 11.10 on my system?

Thanks.

---

### Post by pokerkid on 2012-06-05
Ok, I figured everything out...

1. I cracked open my tower and felt the video card, let's just say, I burned my hand...that sucker was hot and I removed it. I was then able to reinstall 11.10 without the monitor shutting down. Which means the video card was overheating. 

2. Well now that I put the video card back in while running 11.10 it is not over heating.

3. This leads me to the conclusion that 12.04 may have been taxing my video card or that since I took it out and put it back in, something changed for the video card and it is now not over heating. 

I don't know enough of all this to say what was causing the video card to overheat. 

That being said, is there a way to monitor my nvidia video card in ubuntu??

---

### Post by traditionalist on 2012-06-05
Try this;

[http://askubuntu.com/questions/34449/how-to-see-the-video-card-temperature-nvidia-ati-intel](http://askubuntu.com/questions/34449/how-to-see-the-video-card-temperature-nvidia-ati-intel)

---

