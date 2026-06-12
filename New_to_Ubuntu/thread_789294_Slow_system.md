---
title: "Slow system"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by jagr303 on 2008-05-10
OK, well let me start off with my situation. I have a 1.7ghz P4 with 256 mb ram with a 60GB  harddrive and Ubuntu is SLOOOOOW. I'm talking click and wait 5 seconds slow. As a former open BSD user, is there any way to speed up my system? I like it so  far, if it would run faster.

Next, the add/remove programs utility does not work. You can select all you want and when you confirm the changes it just sits there. I have been able to use apt-get from the console. Problem is that my girlfriend uses the computer too and being a non geek she can't do that.

Finally  how in all hell can i get mpegs and avis to work?  I did find  a thread [http://ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins](http://ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins) but the files don't exist any more. Ahh yes and I can't talk to my windows box either.

Been a while, thanks for the help!

Jason

---

### Post by cubeist on 2008-05-10
> **jagr303 said:**
> OK, well let me start off with my situation. I have a 1.7ghz P4 with 256 mb ram with a 60GB  harddrive and Ubuntu is SLOOOOOW. I'm talking click and wait 5 seconds slow. As a former open BSD user, is there any way to speed up my system? I like it so  far, if it would run faster.

Next, the add/remove programs utility does not work. You can select all you want and when you confirm the changes it just sits there. I have been able to use apt-get from the console. Problem is that my girlfriend uses the computer too and being a non geek she can't do that.

Finally  how in all hell can i get mpegs and avis to work?  I did find  a thread [http://ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins](http://ubuntuforums.org/showthread.php?t=60505&highlight=mplayer+plugins) but the files don't exist any more. Ahh yes and I can't talk to my windows box either.

Been a while, thanks for the help!

Jason

For the speed issue, it could be so many things, but a good place to start is to open your system monitor (system/admin/system monitor) and see if there is any particular program or process hogging your cpu.

The second suggestion is to turn off tracker.  I think the control panel is in system/prefs and it is called something like search settings... (sorry I completely uninstalled it from my system)
or, perhaps an easier way is to go into system/prefs/sessions and unclick tracker and tracker applet. reboot. and see if you get a big speed improvement.


As for the add/remove problem, can you go into system/admin/synaptic package manager and add programs that way?

---

### Post by kerry_s on 2008-05-10
get more ram or go lighter.

---

