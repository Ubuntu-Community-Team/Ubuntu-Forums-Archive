---
title: "Segmentation fault when using libavg on Ubuntu?"
date: 2010-07-08
forum: Programming Talk
---

### Post by yogeshmathews on 2010-07-08
I have been in search of a tool to develop multi  touch applications on linux. I happened to come across libavg a few days ago, but when I tried to run  a sample program using libavg the program showed segmentation fault. I  am using Ubuntu 10.04. When I looked it up on libavg's Wiki page they  had given a few workarounds, but none of them worked. What should I do?  Has anyone else come across similar problems with libavg on linux? Here's the code:

#!/usr/bin/env python
# -*- coding: utf-8 -*-

from libavg import avg

player = avg.Player.get()
player.loadFile("text.avg")
player.play()


Contents of avg file:

<?xml version="1.0"?>
<avg width="640" height="480">
<words id="ClashText" x="10" y="10" font="arial" text="Should I stay or should I go?"/>
</avg>


I got this code from [here]("https://www.libavg.de/wiki/index.php/Getting_Started")
Please help.

](*,)

---

### Post by Queue29 on 2010-07-08
Are you trying to use a 32 bit library on a 64 bit machine?

---

### Post by yogeshmathews on 2010-07-08
Yes mine is a 64 bit machine(Intel Atom CPU 230 @1.60 GHz)
But my ubuntu is 32 bit.
Why?
Is that a problem?

---

