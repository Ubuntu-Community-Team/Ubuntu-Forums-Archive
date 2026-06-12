---
title: "Random crashes"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by spankme on 2008-05-02
I am having terrible problems with random crashes running Ubuntu on an AMD Athlon 64 X2 3800+ machine with an NVIDIA nForce 430 (GeForce 6150 LE) chipset.  When it crashes, it really dies - the system essentially just switches off, which suggests to me a low-level driver problem.  I suspect a video driver as extensive memory testing, etc. hasn't turned anything up.  Sadly, the power cord is not loose, either.  The problems started using Gusty but I just fresh-installed Hardy Heron and used EnvyNG to install the latest NVIDIA drivers in an effort to solve the problem, but the system still crashes as soon as I resize a desktop window 3-4 times.

I am going nuts trying to fix this.  Any ideas would be greatly appreciated. :confused:

---

### Post by lincoln32 on 2008-05-02
had same concern after installing 8.04 and i blamed 8.04
stupid me! power supply went south

---

### Post by mister_pink on 2008-05-02
When it crashes can you still move the mouse, its just nothing happens? I had crashes like that, and also music would continue to play in the background. Apparently there was a bug in the "animations" plugin in compiz, theres a fix on the way, its currently in the proposed updates repo. In the mean time you could turn that plugin off. To recover from the crash you can press "Alt + Sys Rq + R" and then ctrl alt f1 to get to a terminal. Then you can do a clean restart from there.

If your symptoms aren't quite like that then I'm afraid I have no idea what the problem is!

---

### Post by spankme on 2008-05-02
When it crashes the screen goes black and I lose ping and any remote ssh sessions.  It really goes down hard.

The power supply isn't a bad thought and I also thought about an overheating problem (my Acer L100 does run a little hot) but I can leave the system stably in memory testing for several days at a time and it seems to only crash when I'm either (1) resizing a desktop window or (2) playing back a XviD file.

---

### Post by dokdoom on 2008-05-02
After it crashes, open a terminal and run

ls -ltr /var/log

This will list your logs by timestamp giving you a good idea of what is causing the shutdown. If it has anything to do with your video driver I would like to think you are looking for the Xorg.0.log

---

