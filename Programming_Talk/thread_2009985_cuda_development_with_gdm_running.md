---
title: "cuda development with gdm running"
date: 2012-06-25
forum: Programming Talk
---

### Post by eotakos on 2012-06-25
Hello everyone,

This is not exactly a programming thread, but rather a technical thread that might help with cuda code development.

From previous experience with my laptop (that has a cuda-enabled graphics card, but one of the first out in the market, with not much memory etc...), seems that if I would execute a cuda program I created, with gdm turned on, there is a good chance that the results i'd take would be garbage, because gdm would have the device reserved... So what I would do is stop gdm, and do everything from the tty_s. (not very convenient when there is still lots of debugging to do)

The situation now on the desktop, is that I also have only one graphics card (and cuda-enabled), but there is also a i3 processor, which I've come to understand that is capable of performing graphic-card's tasks. So the idea would be to have gdm be working on the processor, leaving the graphics-card to me, to do my cuda work.

(at this point maybe I should say that I'm running 10.10)

Now, let's go to the implementation of what I just said... which is the point where I'd appreciate your help: 

I thought that switching the 
/etc/X11/xorg.conf    to its backup   /etc/X11/xorg.conf.failsafe  might do the job, since there are no nvidia-specific things said inside the later, and most probably won't be using any of the features of the graphics card. But, would that be doing the job? or it might still be using the same graphics card and therefore potentially messing up my results...?

anyone with any ideas on how to be sure which graphics card is been used by gdm??

thanks for your time and any answers in advance

---

