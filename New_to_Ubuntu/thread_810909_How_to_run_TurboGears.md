---
title: "How to run TurboGears"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by MayaJ1 on 2008-05-28
Hi,

I am completely new to Linux systems and I have just installed Ubuntu (dual boot with XP).  I need to re-write an Access database I was using in Windows XP so I can remove XP completely.  A friend recommended using TurboGears and Python.  

I think I have installed TurboGears using the Package Manager (I selected it and applied and it downloaded without errors) but I have no idea how to run it.  It is not listed under the Applications menu and I haven't got a clue where to look for it or how to start it if I find it :confused:

Any help would be greatly appreciated, and please excuse my ignorance. :)

---

### Post by bwhite82 on 2008-05-28
Alot of programs in Linux are command-line-only, ie use them with a terminal. Turbogears may be one of them. An easy way to check is to open back up Synaptic, search again for turbogears, it should show it as installed. Now highlight it in the list and click the 'properties' button at the top. Then go to the 'installed files' tab. It will list each and every file that that package installed. Hopefully, one of them should be a binary, (/usr/bin/turbogears?) Check to see what its called, then run that command in a terminal. I hope I made sense.

---

### Post by LarryJ2 on 2008-05-28
Do you mean GLXGears?

If so,  Applications -> Accessories -> Terminal.

When the "command prompt window" opens,  enter glxgears  like this

> lj@lian:~$ glxgears

You'll get a report similar to this and the "gears" will rotate in a separate window
> 10206 frames in 5.0 seconds = 2041.171 FPS

You can run multiple instances of glxgears by opening another terminal and entering glxgears if you want to stress your graphics card.

---

### Post by bwhite82 on 2008-05-28
> Do you mean GLXGears?

No, turbogears, its in the repos.

---

### Post by MayaJ1 on 2008-05-29
Hi Soldierboy,

I have checked everything you suggested and confirmed that it is installed.  I was able to do some things from the command prompt like start a new project so it is working OK.  Ideally I need to open the GUI.  I will have a play around with at lunchtime and see if I can work out which file launches the GUI.  Thank you for showing me where to look for the files that was a big help :)

---

