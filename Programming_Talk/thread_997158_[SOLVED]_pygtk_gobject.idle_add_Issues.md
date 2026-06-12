---
title: "[SOLVED] pygtk gobject.idle_add Issues"
date: 2008-11-29
forum: Programming Talk
---

### Post by flyguy97 on 2008-11-29
I am trying to extend vlc with the [python bindings]("http://wiki.videolan.org/Python_bindings"). One of the requirements I have is a label that displays how much time I have left with the current movie file. I realised I needed to update the gui so I decided to go with the gobject.idle_add function so I can take advantage of the idle time in my program, other methods were tried but all severely hampered playback. Using idle_add seemed to work fine but after some thorough testing from my kids I realised my program would segfault after about 15 minutes. 

Watching the resource footprint may yield a decent clue to my underlying issue(s). CPU usage hovered around 50% and memory for my little program jumped to 1.6 GB. To contrast these numbers without the idle_add my program yielded a much lower resource footprint, around 7% CPU usage and 18 MB of RAM. A paste bin can be found [here]("http://dpaste.com/hold/94663/"). I also included a copy of the python bindings source which I downloaded from vlc along with a compiled vlc.so. If you're like me and won't use files other people posted compiling was a straightforward process, just need vlc and libvlc2. In the archive I also included a copy of the source I am having issues with, it is called custom_vlc.py. I appreciate any help or suggestions and I thank you in advance for looking into this.

---

### Post by flyguy97 on 2009-01-10
This was a nightmare, finally I decided to go with a separate thread to update the ui. A couple of thorough examples of what finally worked can be found [here]("http://http://code.google.com/p/sopcast-player/source/browse/trunk/sopcast-player.py"). Look for the ui woker classes, there are two in this example.

> **flyguy97 said:**
> I am trying to extend vlc with the [python bindings]("http://wiki.videolan.org/Python_bindings"). One of the requirements I have is a label that displays how much time I have left with the current movie file. I realised I needed to update the gui so I decided to go with the gobject.idle_add function so I can take advantage of the idle time in my program, other methods were tried but all severely hampered playback. Using idle_add seemed to work fine but after some thorough testing from my kids I realised my program would segfault after about 15 minutes. 

Watching the resource footprint may yield a decent clue to my underlying issue(s). CPU usage hovered around 50% and memory for my little program jumped to 1.6 GB. To contrast these numbers without the idle_add my program yielded a much lower resource footprint, around 7% CPU usage and 18 MB of RAM. A paste bin can be found [here]("http://dpaste.com/hold/94663/"). I also included a copy of the python bindings source which I downloaded from vlc along with a compiled vlc.so. If you're like me and won't use files other people posted compiling was a straightforward process, just need vlc and libvlc2. In the archive I also included a copy of the source I am having issues with, it is called custom_vlc.py. I appreciate any help or suggestions and I thank you in advance for looking into this.

---

