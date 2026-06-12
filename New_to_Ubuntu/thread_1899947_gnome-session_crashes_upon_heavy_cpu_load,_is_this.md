---
title: "gnome-session crashes upon heavy cpu load, is this a bug, or just me?"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by thebestofall007 on 2011-12-24
hello everyone, i am having issues with gnome-session going crazy if i do something that is cpu intensive or (sometimes) run wine apps. i am using linux mint 9 and ubuntu lucid on a 4th generation macbook pro (early 2008 model). i can reproduce the problem if i compile rockbox firmware as per instructions in this link [http://www.rockbox.org/wiki/LinuxSimpleGuideToCompiling]("http://www.rockbox.org/wiki/LinuxSimpleGuideToCompiling"). when i get to the "make -j" part (as i am using a multicore system and the -j flag speeds up the process a bunch) the system will understandably slow down (due to the heavy cpu load) and exhibit the issue. what happens is the window decorators disappear, the terminal turns transparent, i cant right-click anything, compiz dies, i cant use alt+f2, or anything, the gnome panel disappears, but i can run these commands on a Pentium dual-core desktop with no problem; the system slows, but doesn't go crazy like on my macbook. if i am able to get to a terminal, i can type gnome-session in it and restart the shell and it works again, as well as killall gnome-panel, then restarting gnome-panel, then i can press alt+f2 and start compiz again. the problem shows itself frequently, but not all the time. is this just me or is this a bug, and why? what's going on?

---

### Post by 2F4U on 2011-12-24
Is your laptop getting hotter than usual when this problem happens? If the problem happens on one hardware platform but not on another (I consider Mac's to be a platform on their own), then it may be a hardware problem. Has the Pentium dual core desktop the same software installed than the Mac?

---

### Post by thebestofall007 on 2011-12-24
> **2F4U said:**
> Is your laptop getting hotter than usual when this problem happens? If the problem happens on one hardware platform but not on another (I consider Mac's to be a platform on their own), then it may be a hardware problem. Has the Pentium dual core desktop the same software installed than the Mac?

it doesn't get much hotter than usual (thank goodness) as the fans rev way up on demand via mbfancontrol when the operation starts (as a cpu intensive operation naturally WOULD make the cpu run hotter) and that keeps the laptop fairly cool usually. i even verified that using sensors -f and gkrellm. 

the desktop is running the same exact operating system with the same software setup installed.

---

