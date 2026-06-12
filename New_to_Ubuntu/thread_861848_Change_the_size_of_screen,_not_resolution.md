---
title: "Change the size of screen, not resolution"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-07-17
I have installed Xubuntu on a PC attached to my TV. I upgraded the video connection from S-video to DVI->Hdmi and did a clean install. The resolution looks spectacular, but the screen size is too big. The desktop is cut off on all the corners. How do I adjust the size of the screen? It's not the resolution, though. Resolution is set at 1280x720. 

I think it is the Nvidia GeForce4 MX 440 graphics card because BIOS and Grub are also cut off. I have installed the Nvidia drivers, but the problem existed before that. 

I have used this card before with S-video and it had black bars on the side. I thought it had something to do with the max resolution that S-video can display, but maybe it's related. 

Thanks for the help in advance.

---

### Post by tuxxy on 2008-07-17
I think you can do this in the nVidia XServer Settings app that should should be installed with the driver in the administration menu, you can run this from the terminal;

```
gksudo nvidia-settings
```

---

### Post by jbrown96 on 2008-07-17
I tried the nvidia-settings and there isn't anything like that.
Is there a way to use non-standard resolutions? Like 1100x680 or something that I could tinker with. 

I can't get LinuxMCE to load anymore, but when configuring the video settings in it, there is a step when it lets you shrink/enlarge the screen size. Anyone know where to get this utility?

After doing some research, I've found that the problem is overscan. Now I just need to find out how to adjust the overscan.

---

### Post by markbuntu on 2008-07-17
Some tvs use overscan. That could be your problem. You should try to find something in your tv's setup menu to turn overscan to off. Also, the nvidia driver has an overscan feature, I am not familiar with it myself so cannot help you with that.

---

