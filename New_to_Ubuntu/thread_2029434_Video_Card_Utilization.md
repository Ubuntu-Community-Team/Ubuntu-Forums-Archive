---
title: "Video Card Utilization"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by lemmingrebel on 2012-07-19
I have an ATI Radeon HD 4350, and am running Ubuntu 12.04.

What I would like to know is whether or not I am utilizing the full capability of the video card.  The hardware is physically installed, and my monitor is plugged into it.

I am attaching a screenshot that seems to confirm that it is being utilized, but I'm an uber noob and want to get some more experienced confirmation.


Thanks!

---

### Post by z3nhakr on 2012-07-19
try installing a benchmarking application like glmark2-es2 and then use google to compare your fps to what other people with your card are getting

---

### Post by lemmingrebel on 2012-07-19
> **z3nhakr said:**
> try installing a benchmarking application like glmark2-es2 and then use google to compare your fps to what other people with your card are getting

How do I use it?  I installed it ... how do I run the test?

---

### Post by z3nhakr on 2012-07-19
open terminal and type "glmark2-es2"

---

### Post by lemmingrebel on 2012-07-19
> **z3nhakr said:**
> open terminal and type "glmark2-es2"

lol ... sorry if my questionz has teh dumb

---

### Post by lemmingrebel on 2012-07-19
> **z3nhakr said:**
> open terminal and type "glmark2-es2"

I'm guessing a score of 23 isn't that great.

---

### Post by z3nhakr on 2012-07-19
hmmm tbh your card should get a higher score than mine but i got 201. lemme rerun it with my amd card and i'll post back...it may be a problem with the amd driver

---

### Post by z3nhakr on 2012-07-19
i got 34 with my 1gb amd gcard. there is definitely a bug in the amd driver. that's the reason i switched to the intel card but it's good to know im not the only one with that problem although that doesnt help you much. you can fiddle with the settings in catalyst control center to improve your score a bit but if it's the same as mine, only a bit. also someone mention to me that it may be syncing vblank which for sure would cause a slow fps but tbh if it is i havnt found a place to turn it off. if you do let me know ;)

---

### Post by lemmingrebel on 2012-07-19
Thanks for trying!

---

### Post by z3nhakr on 2012-08-06
try this. it worked for me
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Alternative_Manual_Installation](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Alternative_Manual_Installation)

---

### Post by bogan on 2012-08-07
Hi!**, Z3nhakr**,

I stumbled on your glmark2 tip and am very puzzled by the results you quote, & even more by my own, which are, in effect, meaningless.

How reliable is this Benchmark tool?

Can you Post a link to other peoples scores?  I could not find anything useful with Google, it all seemed to be about crashes, or compiling other versions.

I have two 12.04 installations on the same desktop, running a Nvidia 7650 GS.

One an updated version, uses the nvidia 295.59 driver and glmark2-es2 gave a very smooth display with most readings being between 38 & 74, with a final score of 48. The test took what seemed to me to be a reasonable time.

The other, a direct install of the pae kernal, uses the default nouveau driver, and gave a quite appallingly jerky display, frequently stalling, though the individual images were very clear. Most readings, nonetheless, were between 250 & 300, except for the last 5 tests which took for ages and showed scores of 1.

 I twice thought the program had crashed as there was no response to any input ,except the mouse cursor was moveable and did nothing, but actually displayed as a text cursor; finally it gave a Score of 173.

Strangely in both cases, the GL_Renderer showed as :Gallium 0.4 & the GL_Version as: Mesa 8.02.

---

### Post by z3nhakr on 2012-08-09
To be honest this was the first time I've ever used this utility. I found it in a quick search of software center and my only use for it was to compare my score to the OP, s to help me better understand the problem. Sorry I can't help.

---

