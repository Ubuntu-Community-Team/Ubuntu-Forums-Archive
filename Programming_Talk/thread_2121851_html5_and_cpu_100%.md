---
title: "html5 and cpu 100%"
date: 2013-03-03
forum: Programming Talk
---

### Post by jaho22 on 2013-03-03
if i run html5 tutorials, they often work my cpu 100%, does firefox and google have an build in plugin to make sure that i can safely use html5 + canvas tutorials.

This is a beginner question, i dont know how html5 + canvas games work, my cpu is mostly time, with about every html5 + canvas tutorial and demo a somewhat exat at 100%.

How these html5 + canvas tutorials and demos work, they really run at cpu 100%, is this really ok and something that browser knows how to handle ?

I am a beginner html5 trainer, i know that if i run with openjava a cpu or gpu 100%, then cpu or gpu can broke.

---

### Post by greenpeace on 2013-03-03
> **jaho22 said:**
> if i run html5 tutorials, they often work my cpu 100%

Hey there, 

Can you post some links to these tutorials?  that way we can try to see the problem on our own machines! :)

cheers
Gp.

---

### Post by jaho22 on 2013-03-03
I think that the problem is that linux dont support hardware acceleration for graphics with html5 + canvas2d.

As there is no hardware acceleration with graphics on canvas2d, then software is drawing the graphics, this will cause cpu to go 100%, i am wondering is this problem taken care by the browser, so is there a check of cpu and gpu heat on browser when javascript with html5 is on ?

---

### Post by greenpeace on 2013-03-04
As far as i know there are no such checks on cpu/gpu temperature by browsers... and the statement about hardware acceleration support; where are you getting that from?  

Can you post some links to the tutorials?

Cheers
gp

---

### Post by lykeion on 2013-03-04
How to tell if you are using hardware acceleration, see [http://blog.mozilla.org/joe/2010/11/10/how-to-tell-if-youre-using-hardware-acceleration/](http://blog.mozilla.org/joe/2010/11/10/how-to-tell-if-youre-using-hardware-acceleration/)

But apparantly hardware acceleration in Firefox is disabled for linux, see [http://ubuntuforums.org/showthread.php?t=1976988](http://ubuntuforums.org/showthread.php?t=1976988)

My suggestion: Try chromium

---

