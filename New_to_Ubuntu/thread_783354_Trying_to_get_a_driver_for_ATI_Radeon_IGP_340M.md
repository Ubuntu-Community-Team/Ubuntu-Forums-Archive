---
title: "Trying to get a driver for ATI Radeon IGP 340M"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Torgeirz on 2008-05-05
I've just recently put Ubuntu 8.04 on an old Compac Presario 2100(2190US) and everything has been going very well.  The only thing is that my graphics card (ATI Radeon IGP 340M) is running on a vesa driver and I cant get any fancy 3d and stuff.  
I tried EnvyNG and that didn't do anything so I was wondering if you could help me get a graphics driver that lets me use visual effects and stuff.

I have no experience with linux so please talk slow and loud :)

---

### Post by mmb1 on 2008-05-05
If you're running GNOME, try going to system-administration-hardware drivers, and see if you're driver is listed there.

---

### Post by Torgeirz on 2008-05-05
I'm using GNOME. Could not find any graphics drivers there

---

### Post by mmb1 on 2008-05-05
A google search yielded the following guide:

[http://www.rage3d.com/content/articles/atilinuxhowto/](http://www.rage3d.com/content/articles/atilinuxhowto/)

The debian portion should apply to ubuntu, good luck

And if you have any questions or concerns feel free to ask.

---

### Post by mmb1 on 2008-05-05
After looking at the guide, it may not be the best course of action, this card seems to be particularly troublesome, are desktop effects a nessecity for this hardware?  Does everything else display correctly?

---

### Post by Torgeirz on 2008-05-05
Everything displays correctly.  I can only use one resolution, 1024x768 and it seems that all 3d acceleration is turned of. Video can sometimes be choppy... 

I was thinking about trying some games and it doesn't seem doable if 3d is turned of...

I think....

:)

---

### Post by mmb1 on 2008-05-05
Yeah, you'll need 3d acceleration for most games, can you run the command, "glxgears" in a terminal and post the output for me, please?  This will let me know whether or not you have any 3d acceleration.

---

### Post by Torgeirz on 2008-05-06
I ran the command "glxgears" and what I got was a window with a red, green and blue gears turning.  The output  in terminal was
```

940 frames in 5.0 seconds = 186.800 FPS
980 frames in 5.1 seconds = 192.788 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 4997 requests (36 known processed) with 0 events remaining.

```

---

### Post by mmb1 on 2008-05-06
Alright, don't worry, the gears are normal, your output tells me that you have no 3d acceleration.  I'm a bit stumped.

bump.

---

### Post by Torgeirz on 2008-05-07
bump

---

### Post by shae on 2008-05-08
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Follow method 2.

---

### Post by Torgeirz on 2008-05-08
I'll try method 2 and let you know how it worked.

---

### Post by Torgeirz on 2008-05-08
I followed the guide as best I could and now I'm stuck in low graphics mode :(

---

### Post by thasban on 2008-11-01
thign is.. in method 2, u need catalyst. There's no catalyst for IGP 340M, from there, i'm stumped...

---

