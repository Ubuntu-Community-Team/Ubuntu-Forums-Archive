---
title: "Convert linux programs to os x?"
date: 2008-10-01
forum: Programming Talk
---

### Post by pankirk on 2008-10-01
I recently installed os x, winxp, and ubuntu linux on my machine (partitioned 3 ways) and I wonder is it possible to actually get the source to a linux program and compile it for os x? I know os x is BSD or something along the lines of that... The only reason I ask this is because I'm having trouble getting wireless drivers to work on os X. So, I figured that I could just get the source and compile it to os x. I know this probably wont be a simple task at all, probably wont even work because I have minimal knowledge in c++, but enough to know about libraries ect... So, what do you think? Is it possible to port linux wireless drivers to mac os x (leopard)?

---

### Post by dribeas on 2008-10-02
Hardware drivers are not nearly 'programs'. It is way easier to port regular programs that it would be to port hardware drivers. I just tagged your post so that your intention is clearer. 

Modules/drivers depend quite a lot in your kernel design, which for MacOS X it is not a linux kernel. I would go to mac/bsd forums where they might have more information on how to build hardware drivers for those families of kernels.

---

### Post by tubasoldier on 2008-10-02
Is this an actual mac or some sort of hackintosh that you have put together?
Just curious. Hackintosh may not work with wireless at all. It would depend on your wireless card.

As far as installing linux wireless drivers and getting them to work on OSX, it won't happen. As dribeas stated drivers depend on your kernel design. linux kernel != OSX kernel

---

### Post by pankirk on 2008-10-02
Its a hackintosh :-#:-#:-#

Thanks for the help guys, I didn't know it was kernel programming. I figured it was just an application that ran when you booted up your computer.

---

### Post by Shin_Gouki2501 on 2008-10-02
yeah and a computer is a thing with all shiny colors on it , in it moved by the speed of light...
;)

---

### Post by Rich78 on 2008-10-02
You would be better looking into the darwin distribution.

[http://www.opensource.apple.com/darwinsource/]("http://www.opensource.apple.com/darwinsource/")

---

