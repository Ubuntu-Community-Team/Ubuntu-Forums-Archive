---
title: "Gaming with Optimus and Nouveau. Is it possible?"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by oapeter on 2014-05-17
Hi All.

I've got a pretty fresh install of Ubuntu 14.04 running on my MSI GT60-0NC laptop that has an Nvidia Optimus graphics setup that uses the Intel HD4000 and an NVIDIA GTX 670M. By default, Nouveau is supporting the low power mode of the card and appears it can switch back and forth between the Intel and Nvidia card when it sees fit during bootup. This is fantastic. 

However, I'm wondering if there's a way I can trigger the switch, similar to how the Bumblebee package works. And, if I can, are the drivers capable of running games at a reasonable framerate?

I'd like to start out by being able to play some of my Steam games like Portal 2 on the Nouveau driver. I've tried running them from Steam but it looks like Nouveau doesn't switch to the Nvidia card.

Thanks for anything!

---

### Post by grahammechanical on 2014-05-17
Have you seen this?

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

That was written back in December 2013 and since then 14.04 has been officially released so Nvidia Prime should be in the stable repositories or be included with the latest Nvidia driver. I do not have an Optimus set up, so I cannot confirm this. But I can tell you that the latest Nvidia driver in Additional Drivers is Nvidia 331.38.

Regards.

---

### Post by oapeter on 2014-05-18
> **grahammechanical said:**
> Have you seen this?

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

That was written back in December 2013 and since then 14.04 has been officially released so Nvidia Prime should be in the stable repositories or be included with the latest Nvidia driver. I do not have an Optimus set up, so I cannot confirm this. But I can tell you that the latest Nvidia driver in Additional Drivers is Nvidia 331.38.

Regards.

I hadn't heard about it until you posted it, no. I've tried to use it but it appears to need a bit of configuration, which I'll work on and report back!

I'm not sure if its a better solution than Bumblebee, because it sounds like I'll have to re-log in order to switch graphics cards. Bumblebee can do it without logging out.

What I was hoping for though, was to not use an Nvidia driver at all and stick with nouveau completely. I'm guessing that's not possible.

Thanks a lot!

---

