---
title: "Compiz - stupid little problem- Desktops"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by bgast1 on 2008-05-10
I have Ubuntu Hardy Heron installed with KDE desktop at the moment. I am showing 4 Desktops at the bottom of the screen. Advanced Desktop Settings under General does not allow me to change the number of Desktops above 1. I would like to be able to get the cube and get it to rotate. 

It works perfectly under the default Gnome Desktop. I am trying to determine which Desktop environment I prefer. So far KDE is winning out.

---

### Post by mgranet on 2008-05-10
You want to go into CCSM, then to the General window, then to the Desktops tab. Set the Horizontal Virtual Size to the number of desktops you prefer.

---

### Post by bgast1 on 2008-05-10
I did that and it didn't work. Even tried raising it to 5. Another little problem that I have noticed in CCSM is that when I try to x one of the boxes I get a dotted line rectangle that blocks out the box and I can't tell if I've x'd it until I move away from that area. 

It is beginning to look like I might need to stick with Gnome for functionality until I can resolve some of these KDE issues, which I really would like to do.

---

### Post by mgranet on 2008-05-10
What graphics card/drivers do you have? Do any of the other compiz effects work?

EDIT: Verify that the key combo to start the cube are the same between GNOME and KDE.

---

### Post by bgast1 on 2008-05-10
My graphics card is an ATI Radeon X1950 Pro PCIe. I have installed the restricted drivers. I have the ATI Control Catalyst installed as well. (Don't know if that is relevant)

```
@bob-desktop:~$ glxgears
26483 frames in 5.0 seconds = 5296.459 FPS
26499 frames in 5.0 seconds = 5299.795 FPS
26536 frames in 5.0 seconds = 5307.155 FPS
26552 frames in 5.0 seconds = 5310.383 FPS
26530 frames in 5.0 seconds = 5305.925 FPS
26610 frames in 5.0 seconds = 5321.968 FPS
26621 frames in 5.0 seconds = 5324.168 FPS
25591 frames in 5.0 seconds = 5118.025 FPS
25660 frames in 5.0 seconds = 5131.952 FPS
25354 frames in 5.0 seconds = 5070.640 FPS
26113 frames in 5.0 seconds = 5222.447 FPS
23568 frames in 5.0 seconds = 4713.542 FPS
25543 frames in 5.0 seconds = 5108.300 FPS
25764 frames in 5.0 seconds = 5152.758 FPS
26186 frames in 5.0 seconds = 5236.913 FPS
```

I also forgot. In other distros that I have gotten Compiz to work in KDE the key combos between KDE and GNOME were the same.

---

### Post by mgranet on 2008-05-10
:confused: Hmm....I'm fresh out of ideas as to what could be causing this. I'm pretty sure it's not a KDE thing, as Compiz worked with little hassle for me on Kubuntu Gutsy. The only odd setting I have is my KDE desktops are set to 1, while I have 4 Compiz desktops. You might play with the number of KDE desktops, just to see what happens.

---

### Post by mgranet on 2008-05-10
Just thought of some more stuff. What packages do you have installed relating to compiz? Make sure compiz-kde is installed.

---

### Post by bgast1 on 2008-05-10
I now would like to mark this thread as solved. I appreciate the help here. I did indeed find a KDE-Compiz menu item which I must have overlooked and did indeed install it. Now I have a triangle and not a cube.:lolflag:

---

### Post by mgranet on 2008-05-10
> **bgast1 said:**
> I now would like to mark this thread as solved. I appreciate the help here. I did indeed find a KDE-Compiz menu item which I must have overlooked and did indeed install it. Now I have a triangle and not a cube.:lolflag:

Now go set your Horizontal Virtual Size to 4 to get a cube. Or 5 to get a pentagon, etc, etc. You can mark the thread as solved under Thread Tools. (Near the top of the page)

---

### Post by bgast1 on 2008-05-10
Hmmmm. Checked thread tools and didn't see anything for marking this as solved. I'll just try to edit the title.

---

