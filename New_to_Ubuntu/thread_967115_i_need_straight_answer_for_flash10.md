---
title: "i need straight answer for flash10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by fignig on 2008-11-01
is flash 10 working for the 64bit systems in intrepid ibex? and if so how do i enable/install them...i'm tired of sometimes, or not being able to watch some flash videos. i need my fantasy football help. so can anyone give it to me straight w/o beating around the busH?

---

### Post by Sealbhach on 2008-11-01
See here:

[http://queleimporta.com/installing-flash-10-on-intrepid-ubuntu-810-64-bits/en/](http://queleimporta.com/installing-flash-10-on-intrepid-ubuntu-810-64-bits/en/)


.

---

### Post by Pro-reason on 2008-11-01
It's hard to say, because both Flash 10 and Intrepid Ibex have only just come out.  Instead of asking, why don't you just try it?

Boot from an Intrepid 64-bit live CD, install Flash 10, and examine its performance.  You can post your results here to help others.

---

### Post by fignig on 2008-11-02
is there any other flash? or anything else i can use instead of it. b/c i can't see a lot of videos that i need to see, now i'm probably gonna lose in fantasy football this week..

---

### Post by diablo75 on 2008-11-02
What method did you use to install Flash?

---

### Post by handydan918 on 2008-11-02
> **fignig said:**
> well it's saying that i have the most updated version of flash. and it doesn't work for ****. it's been working worse than hardy heron flash...wtf is up w/ this. if this is not fixed in the near future. i will be giving my money to the gates corp.

Let me draw you a picture. 
Flash is a proprietary software product from Adobe. It will only do what Adobe codes it to do. If they write a version for linux and it also handles 64 bit kernels, then all is well. 
None of this had **** to do with the kernel developers, Ubuntu, Mark Shuttleworth, the forum staff, or the Presidential candidates.


If you want flash to work, do what I do. 
Install a 32 bit O/S.

---

### Post by gandaran on 2008-11-02
> **fignig said:**
> when did i ever say anything about the developers ubuntu, or whoever mark shuttleworth is, or the forum staff....i think you're fuking crazy. what i was saying that it doesn't work, i don't know why it doesn't work. and if this continues, i will not continue my linux usage. that's it, it's a simple story. but sorry if u can't comprehend that you stupid fuk.
flash 10 works for most people in 64-bits just as well as it does for 32-bits systems, I don't really know why some have problems, I can only ask what else (flash packages) you have been installing besides adobe flash?
you can try other flash applications like the **gnash** plugin for firefox or swfdec-mozilla plugin but remove any other flash package first before installing any.

---

### Post by fignig on 2008-11-02
> **gandaran said:**
> flash 10 works for most people in 64-bits just as well as it does for 32-bits systems, I don't really know why some have problems, I can only ask what else (flash packages) you have been installing besides adobe flash?
you can try other flash applications like the **gnash** plugin for firefox or swfdec-mozilla plugin but remove any other flash package first before installing any.

the only flash thing i have installed is adobe, none of the swfdec-mozilla plugins or any of that sort. i searched "flash" in synaptic and all was installed was the adobe flash. i'm having a lot of trouble opening flash programs/videos. even when i close all firefox's and i open them again, then try watching the video after the advertisements it goes gray. the trouble has been here since hardy heron, and i switched to intrepid ibex hoping that the flash problem would be fixed, but it's not...

---

### Post by bodhi.zazen on 2008-11-02
> **fignig said:**
> the only flash thing i have installed is adobe, none of the swfdec-mozilla plugins or any of that sort. i searched "flash" in synaptic and all was installed was the adobe flash. i'm having a lot of trouble opening flash programs/videos. even when i close all firefox's and i open them again, then try watching the video after the advertisements it goes gray. the trouble has been here since hardy heron, and i switched to intrepid ibex hoping that the flash problem would be fixed, but it's not...

Yikes, that behavior is uncalled for. I jailed your inappropriate posts.

To install flash, 

```
sudo apt-get install flashplugin-nonfree
```

Then re-start firefox. Go here to test :

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

It is working in 8.10 64 bit.

============

Second may I remind you to two things. First we are all volunteers here and your approach does not motivate people to help you.

============

Last, flash is proprietary software. As such ranting on the Ubuntu forums is just inappropriate, please complain to Adobe, ask them to opensource flash / shockwave or publish Linux drivers.

============

QED: I am closing this thread now to prevent further trolling.

---

