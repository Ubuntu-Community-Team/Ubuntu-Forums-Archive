---
title: "Better driver for Intel graphics card, Ubuntu 64bit"
date: 2016-06-22
forum: New to Ubuntu
---

### Post by ctrl2 on 2016-06-22
I just installed **16.04 LTS [64bit]** version of **Linux Ubuntu**, but it says that my Graphics are: **Intel Sandybridge Mobile**,  and the problem with that is that I cant open more than 2 windows of  youtube videos in my browser, because temperature of my computer keeps  rising like crazy, and I believe its because of this Sandybridge driver,  my 2nd operating system is Windows 7 and everything is fine, and plus,  its 32bit, so...is there a way to get better driver than this  Sandybridge thing, because I think that my first display adapter  [Intel(R) HD Graphics 3000] is the main [**integrated**] one [and more important one]  than Nvidia [**dedicated**] one, but now that this driver doesnt work like it should,  Nvidia is the main one [which it shouldnt be, like it isnt on Windows  also] and my computer overheats, am I wrong here maybe? Thanks
  [I]
Computer specs: Samsung laptop, Intel i3 (2.3ghz) processor, 4gb  ram, 64bit based processor, 2 display adapters: 1. Intel(R) HD Graphics  3000 2. NVIDIA GeForce GT 520MX (1gb each) 500gb hdd[/I]

  
Maybe this pic might help [please ask if you need more information]

[http://i.stack.imgur.com/yUGNn.png](http://i.stack.imgur.com/yUGNn.png)

---

### Post by grahammechanical on 2016-06-22
You have hybrid graphics. Sadly, Nvidia has not provided Linux drivers that are as efficient as the Nvidia Windows drivers. In Windows the Nvidia driver will automatically switch to the Intel graphic adapter when the graphic load is low and then switch to the Nvidia adapter when the graphic load increases.

The Linux Nvidia drivers do not do that. You are in a situation where the system either runs on Intel graphics or Nvidia graphics. No automatic switching. When the Nvidia driver is installed we also get an Nvidia settings utility. I believe we can use that Nvidia settings utility to switch between Intel & Nvidia graphics.

I also think that nvidia 361 is the latest stable Nvidia driver. There are newer, untested, versions available but I have not heard of them doing the automatic switching that the Nvidia Windows drivers do. And that is what is causing this heating issue.

Regards

---

### Post by ctrl2 on 2016-06-22
Awesome, so, I'm done with Ubuntu? Because there is no way I can let my laptop go 80+ 90+ degrees all the time...There is no some program [from some other developer, not only Nvidia] that can switch from one graphics to another?

---

### Post by X-RED_Tech on 2016-06-22
No, there isn't but you can switch them yourself, manually, as explained above, whenever you want. Or just select Nvidia if you need better graphics performance and forget about the flimsy Intel altogether. It won't make much difference energy wise anyway.

---

### Post by wildmanne39 on 2016-06-23
Please use thumbnails or Url's when posting images because many people have slow internet conections and loading pages with large images is very difficult for them.

---

### Post by buzzingrobot on 2016-06-23
Intel releases open source drivers and has a better working relationship with the Linux community than Nvidia, which does not release source for its drivers. One impact of this is that the appropriate Intel driver is loaded by default if Intel video is active when the machine boots.  Nothing more to be done. 

If your BIOS allows you to disable Intel video and use only the Nvidia, then that's probably going to give you the best performance,  (The Intel 3000 Sandybridge GPU is a few generations behind current Intel video.)

Temperature control  and battery life probably are going to be noticeably worse than on Windows because Windows often has access to proprietary techniques Linux does not. However, there are a number of packages available that can help you optimize those as much as possible.

---

