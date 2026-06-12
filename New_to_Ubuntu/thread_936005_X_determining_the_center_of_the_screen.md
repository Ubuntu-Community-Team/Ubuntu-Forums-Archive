---
title: "X: determining the center of the screen"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by crowhill on 2008-10-02
Hi there!

First of all, this forum rocks! The Ubuntu/Linux community is simply awesome!

I have three little questions:

1. I'm trying to get my XTerm windows to open in the center of my screen. How can I determine it's EXACT coordinates? How can I figure out what I have to type into the <left>+<top> field in 'xterm*geometry: <width>x<height>+<left>+<top>' (located in my .Xresources file) in order to get XTerm to open in the center of my screen?

2. How can I restart X without restarting my machine?

3. I was trying to use the output from xprop | grep WM_CLASS to get the window for my Maple12 (math software) to behave in a certain way when it starts. However, it doesen't work. Is there another way to figure out the name of a software? It's about Openbox (I want Maple to be without decor and maximized).

Thanks a lot in advance,
cheers,
crowhill.

---

### Post by Polygon on 2008-10-02
restarting x i believe is the key combo:

ctrl+alt+backspace

---

### Post by Rhubarb on 2008-10-02
1, I'm not sure, you may have to get your calculator out to work out that one.

2, Press Ctrl + Alt + Backspace
Please note when doing this, it will kill any child processes of X (which is an awful lot), so save what ever you're doing first.

---

### Post by aeiah on 2008-10-02
location is from the top left, so

top = (resheight/2)-(height/2)
left = (reswidth/2)-(width/2)

where resheight and reswidth is your resolution (1024x768, 1280x1024 etc)
height and width is the terminal windows height and width, and can be whatever you want i guess.

unless ive fried my brain with coffee today

---

### Post by crowhill on 2008-10-02
Hi there

Thanks a lot for that! However, it doesen't work. My resolution is 1280x800 an I have 80 for width and 30 for height in XTerm -geom. Is there an issue with units? It seems that the top left corner is centered by 1280/2 for width and 800/2 for height.

---

### Post by urukrama on 2008-10-02
> **crowhill said:**
> 3. I was trying to use the output from xprop | grep WM_CLASS to get the window for my Maple12 (math software) to behave in a certain way when it starts. However, it doesen't work. Is there another way to figure out the name of a software? It's about Openbox (I want Maple to be without decor and maximized).

Some applications don't have a WM_CLASS. You could try with WM_NAME (xprop WM_NAME), though that will probably not give anything either.

EDIT: Regarding xterm at the center of your screen: if you use Openbox, you could bring it to the center of the screen with the action [MoveToCentre]("http://icculus.org/openbox/index.php/Help:Actions#MoveToCenter"). You can then use something like [xget-mouse-position]("http://dzen.geekmode.org/dwiki/doku.php?id=misc:xget-mouse-position") to find out the x and y coordinates of your mouse cursor (which you'd place at the upper left corner of the xterm window).

---

### Post by crowhill on 2008-10-04
> **urukrama said:**
> Some applications don't have a WM_CLASS. You could try with WM_NAME (xprop WM_NAME), though that will probably not give anything either.

EDIT: Regarding xterm at the center of your screen: if you use Openbox, you could bring it to the center of the screen with the action [MoveToCentre]("http://icculus.org/openbox/index.php/Help:Actions#MoveToCenter"). You can then use something like [xget-mouse-position]("http://dzen.geekmode.org/dwiki/doku.php?id=misc:xget-mouse-position") to find out the x and y coordinates of your mouse cursor (which you'd place at the upper left corner of the xterm window).

Thanks a lot for your answer. I solved the problem with centering xterm. I just figured it out by trying and calculating.

However, the problem with Openbox not liking Maple 12 remains. I don't know what name this program has. When I installed it, I created a link in my home folder to the executable (I tried to use the path to this executable but that doesn't work either). Is there another way to figure this out?

Thanks a lot in advance,
cheers,
crowhill.

---

