---
title: "noooob question: How to switch to second X screen"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by DexterLB on 2008-05-25
So, I've configured NVidia to use my TV as a seperate X screen. When I turn on the PC, a second desktop shows on the TV. My question: how can I switch my keyboard and mouse to work on the second X screen and back?

---

### Post by Sam Lars on 2008-05-25
There's a program called nvidia-settings.  You may have to install it.  If you run that you can control how it handles multiple screens.

---

### Post by DexterLB on 2008-05-26
that's what I did.
Everything is configured fine, all I have to do is to use the second screen

---

### Post by Sam Lars on 2008-05-26
There's an area in there to configure the X screens, and how it handles more than one.

---

### Post by chattanoga on 2008-11-15
> **DexterLB said:**
> So, I've configured NVidia to use my TV as a seperate X screen. When I turn on the PC, a second desktop shows on the TV. My question: how can I switch my keyboard and mouse to work on the second X screen and back?

Im am bumping this tread because I have the same problem (and I am not sure if got the correct answer)

So, I have installed and configured Nvidia-settings and everything seems to be working fine. When I boot I will see desktops on my display and on the TV. 
But nothing happens on the TV, it is just an empty desktop.

How do I switch to the TV (ie "X screen 1")?
Suppose I want to watch a video on the TV, with XBMC for example and not on the computer monitor?

---

### Post by Sam Lars on 2008-11-15
I'm not sure what you mean by switching to the second screen.  The desktop is extended to the second screen via some side of your main screen, and you should be able to move your mouse and drag things to it and use it as if it were part of the main screen.
So if you want to watch a movie on one screen, you move the movie window to the second screen, and work on the first screen.

---

### Post by nova47 on 2011-03-05
I realize this is waaaaaay late but I'm having the same issue. I have a blank desktop and my mouse can move in and out of this desktop. However, nothing can be dragged into the desktop. My question is how do I use it?

EDIT: Scratch that I just realized I had a very unique problem. The resolution on the TV was perfectly off in such a way that I couldn't see any of the menus so I assumed I was looking at a blank desktop when in fact the menus were just hidden.

---

### Post by ddssff on 2011-10-30
The answer is - its awkward.  One way is to start a terminal and type something like:

xeyes -display :0.1

---

