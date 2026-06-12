---
title: "how do I browse the LAN in Krusader"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by yaque on 2008-05-09
When I press the yellow star (preset bookmarks) and press "Local Network" I get an Error message:
"Protocol not supported by Krusader: lan:/"

I tried to cut-and-paste a lan location from the ubuntu file browser:
smb://new//c/ where "new" is the name of my other computer (running windows XP home).
I get the same error message.

I have a working internet connection via the "new" computer,
and I can browse the "new" computer using the ubuntu file browser as well, so the lan works.

in hardy heron on dual boot with wxp home.
other computer on lan with wxp home.
when both computers are booted, no problem browsing between them.

---

### Post by ZabiGG on 2008-05-15
Hi ;)

If you're still waiting for an answer, please say so.

I'll try to find you help...

---

### Post by yaque on 2008-05-21
Thanks, yes I'm still wondering. 

Do you (or anybody else) have any recommendations for a 
good Total Commander style file manager for linux/ubuntu?
Thanks.

---

### Post by Xiong Chiamiov on 2008-05-21
Though they're not nearly as complicated-looking as Total Commander, both konqueror and dolphin support splitting your window in two like that.  Of course, they're both KDE apps...
You can take a look through [here]("http://en.wikipedia.org/wiki/Comparison_of_file_managers").

---

### Post by rduke15 on 2009-11-16
> **yaque said:**
> any recommendations for a 
good Total Commander style file manager for linux/ubuntu?

Unfortunately Total Commander users like us have been so spoiled by the best of the file managers, that Linux (and Macs) are quite frustrating for us.

In Terminal, Midnight Commander is almost as good as TC. But it doesn't have "synchronize dirs", and has a few other problems. Nevertheless, it's a must-have, and I use it a lot.

In the GUI, I have been mostly using Krusader recently. The alternative seems to be Gnome Commander. Both have their advantages and drawbacks, and I don't remember the reason why I ended up using Krusader over GC.

My latest problem with Krusader is that it doesn't copy file timestamps when doing synchronize dirs from Ubuntu to Windows. My solution for such problems is often to start WinXP in a virtual machine, just to have the power and reliability of Total Commander.

Other current Krusader shortcomings seem to be the poor file viewer, and also (like several other Linux apps) that it will occasionally just crash.

On the other hand, it does seem to be very configurable, and the Useractions stuff may prove an advantage over TC (in part because it has access to bash instead of the ridiculous cmd.exe)

On Mac, I have been using muCommander. It crashes often and is definitely not comparable with TC, but it's the best I could find for Mac. There are commercial alternatives, of which I tried Disk Order, which was also way behind TC, though in different areas than muCommander.

---

### Post by Ganton on 2010-12-13
> how do I browse the LAN in Krusader
When I press the yellow star (preset bookmarks) and press "Local Network" I get an Error message:
"Protocol not supported by Krusader: lan:/"


This was due to a bug of the Ubuntu package and you can see if it is solved now (the bug was marked as "closed"). If you keep having a problem, you can see
[https://launchpad.net/ubuntu/+source/krusader/+bug/69016](https://launchpad.net/ubuntu/+source/krusader/+bug/69016)

---

### Post by Ganton on 2010-12-13
> My latest problem with Krusader is that it doesn't copy file timestamps 
> when doing synchronize dirs from Ubuntu to Windows. My solution for 
> such problems is often to start WinXP in a virtual machine [...]

If it may be of interest for anyone, I have been doing this for 3 years without problems. I just have tried it now and the problem didn't happen.

---

### Post by ionospheric on 2013-02-21
One way of doing this is by going to Places -> Network on the Gnome menu and finding the volume that you are looking for. Then, when you open Nautilus, there should be a new volume in the left pane. Click on it and hit CTRL-L to get the path. You can then copy the path and enter it in Krusader
For example:

```
smb://m1/movies/
```

---

