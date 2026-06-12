---
title: "monitor  issues with Ubuntu 8.04"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by jwrobbs on 2008-06-08
Hi! I'm pretty new to Ubuntu. But I was able to install Ubuntu on to an old laptop. It worked and still works great. I even managed to set up a server correctly. 

I now want to put the laptop on a shelf and run a monitor off it. I plugged in an LG flat panel. It will display the initial boot sequence and then I get garbage for a couple seconds. After that, the monitor gives me an error (Out of Range 46.4kHz/43Hz) and stops displaying. The laptop screen works fine the entire time. I don't even know where to look for help. General searchs haven't helped.

Laptop: HP ze5730us
Ubuntu: 8.04
Video Card: ATI Mobility Radeon 4x AGP

Thanks for the help,

Josh

---

### Post by faktorqm on 2008-06-10
Hello! 

Try pressing the combination Ctrl - Alt - + or Ctrl - Alt - - to change the screen resolution on the fly. When you see a login screen, log in and go to applications -> accesories -> terminal and type

```
sudo displayconfig-gtk
```

to reconfigure your video settings. Bye!

---

