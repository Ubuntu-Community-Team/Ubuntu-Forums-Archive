---
title: "X10 Elegance vs. Speed"
date: 2007-04-29
forum: Other OS Talk
---

### Post by GaryH on 2007-04-29
To all the CS majors out there,
It would seem to me that running a GUI (mouse, keyboard, graphics) through the X  communication protocol,  while an elegant way to partition a system,  is intrinsically slower than *more* directly communicating with GUI devices. **Is the X GUI approach intrinsically slower than the Microsoft Windows approach?**
Thank you,
GaryH

---

### Post by coxy on 2007-04-29
I'm not sure I follow you. Are you asking if Linux takes longer to partition a drive than Linux? Or are are you asking if partitioning takes longer with a GUI based program rather than using the CLI?

---

### Post by nixclusive on 2007-04-29
It used to be inefficient when we did TCP/IP communication even on localhosts. The use of local sockets and shared memory for all local communication significantly speeds up X -- comparably to Windows and in some cases even faster. TCP/IP communication is deployed in remote logins which is really helpful in (trusted) local area networks where an ssh tunnel would be an unnecessary overhead.

---

### Post by mips on 2007-04-29
Hmm, comprehension ?

He is asking whether using the X window system to to facilitate communications between the "mouse, keyboard, gfx" & GUI is faster or slower than that directly accessing the GUI by bypassing X.

---

### Post by 3rdalbum on 2007-04-29
Remember, the Windows solution (at least, with XP) is to put parts of the graphical display system and shell into the kernel. This is bound to be faster than having the graphical display system as strictly userspace.

However, the benefits outweight the disadvantages. Computers are fast enough to make any X inefficiency completely theoretical; and besides, there are plenty of parts of any operating system that are in need of some tuneup.

---

### Post by GaryH on 2007-04-29
Thanks everybody for responding to my question and sorry for not wording it more succinctly.:redface:

I'm trying to understand why my IBM T20 GUI runs slower with Feisty than with the previous OS,  Microsoft Windows 2000. Here's what I know and what I've done so far:

[LIST]
[*]The IBM T20 uses a savage graphics chip set and Feisty chose the savage driver during installation so I'm reasonably sure the graphics are running properly. 

[*]The Feisty installation went very well as can be seen on my thread at [http://ubuntuforums.org/showthread.php?t=411498](http://ubuntuforums.org/showthread.php?t=411498). 

[*]Speed enhancements which are detailed on my thread at [http://ubuntuforums.org/showthread.php?t=425411](http://ubuntuforums.org/showthread.php?t=425411) were added.

[*]glxgears runs at 306 fps.
[/LIST]
I thought maybe the extra graphic software layers, the X server & window manager, in Feisty  were causing the GUI sluggishness. I'm still not sure what the heck is going on.](*,) 

Thanks again for all the fine responses to my question.

Peace,
GaryH

---

### Post by igknighted on 2007-04-29
> **GaryH said:**
> Thanks everybody for responding to my question and sorry for not wording it more succinctly.:redface:

I'm trying to understand why my IBM T20 GUI runs slower with Feisty than with the previous OS,  Microsoft Windows 2000. Here's what I know and what I've done so far:

[LIST]
[*]The IBM T20 uses a savage graphics chip set and Feisty chose the savage driver during installation so I'm reasonably sure the graphics are running properly. 

[*]The Feisty installation went very well as can be seen on my thread at [http://ubuntuforums.org/showthread.php?t=411498](http://ubuntuforums.org/showthread.php?t=411498). 

[*]Speed enhancements which are detailed on my thread at [http://ubuntuforums.org/showthread.php?t=425411](http://ubuntuforums.org/showthread.php?t=425411) were added.

[*]glxgears runs at 306 fps.
[/LIST]
I thought maybe the extra graphic software layers, the X server & window manager, in Feisty  were causing the GUI sluggishness. I'm still not sure what the heck is going on.

Thanks again for all the fine responses to my question.

Peace,
GaryH

The problem is a lack of good drivers for your graphics card.  S3 is very bad with their linux drivers.

---

### Post by 3rdalbum on 2007-04-30
> **GaryH said:**
> 
I'm trying to understand why my IBM T20 GUI runs slower with Feisty than with the previous OS,  Microsoft Windows 2000. 

I'd agree that you should check your graphics card drivers, but seriously; Windows 2000 was released seven years ago, and Ubuntu Feisty was released two weeks ago. It's like wondering why Vista runs slower on your computer than Win2000 - it's a newer operating system with many more features and orders of magnitude more complexity.

---

### Post by GaryH on 2007-04-30
Ii'm going to follow the communities advice and pursue a graphic's fix for my speed issue. Maybe my X11 configuration isn't setup properly or maybe I can find a better driver. I will post my findings in a few days.

Thanks to the community for all the support.

Peace,
GaryH

---

### Post by PrimoTurbo on 2007-04-30
**GaryH**:

I know exactly what you are talking about, the sluggish GUI performance compared to windows is the result of the fundamental design of the X11 GUI. For example the redraw speed of the GUI when resizing a window is slightly slower in any major GUI interface, people on newer computers don't notice any difference but someone with an older system definitely sees a more sluggish performance. It's probably possible to tweak it but for the last 2-3 years I haven't been able to find a solution. :(

I noticed when using Beryl it's less obvious, not sure why.

---

### Post by igknighted on 2007-04-30
> **PrimoTurbo said:**
> **GaryH**:

I know exactly what you are talking about, the sluggish GUI performance compared to windows is the result of the fundamental design of the X11 GUI. For example the redraw speed of the GUI when resizing a window is slightly slower in any major GUI interface, people on newer computers don't notice any difference but someone with an older system definitely sees a more sluggish performance. It's probably possible to tweak it but for the last 2-3 years I haven't been able to find a solution. :(

I noticed when using Beryl it's less obvious, not sure why.

It probably improves in beryl because the system offloads the graphics straight to the graphics card (like Aero).  If you have a decent card, it should improve performance if you don't turn on all the beryl options.

---

### Post by PrimoTurbo on 2007-04-30
Still the whole desktop rendering is buggy on Linux in general.

---

### Post by GaryH on 2007-05-02
Hi Everybody,

I re-configured gnome for slow hardware and to my surprise window dragging and resizing operations sped up. 
> gconftool-2 --set /apps/metacity/general/reduced_resources --type=bool true
Of course there's a catch. I think it's called wireframe. See what you think. I like it.

GaryH

---

### Post by 3rdalbum on 2007-05-02
> **GaryH said:**
> Hi Everybody,

I re-configured gnome for slow hardware and to my surprise window dragging and resizing operations sped up. 

Of course there's a catch. I think it's called wireframe. See what you think. I like it.

GaryH

Back in the olden days, all windowing operating systems used wireframe. Copland PPC (my Linux distribution, hoping to release it soon) also uses it because it's more resource efficient.

---

### Post by GaryH on 2007-05-02
Hi 3rdalbum,

Best of luck with your distro! :guitar: 

Peace,
GaryH

---

