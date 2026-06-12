---
title: "Should I have a Mac laptop or use GNUstep library to learn Objective-C?"
date: 2013-12-24
forum: Programming Talk
---

### Post by pavelexpertov on 2013-12-24
Hello guys, I have a little problem here. I have a tough time deciding on how to learn Objective-C: whether I spend 700 dollars on mac or download GNUstep library for linux. The thing is though, I am going to university next year and I am not sure if I will have time to learn Objective-c, at the same time, I would like to know how close GNUstep is following Cocoa API so I can follow one good tutorial I found, which looks at main language and some parts of the framework. Can anyone give advice on this issue? Thanks and merry Xmas guys!!!

---

### Post by tgalati4 on 2013-12-24
If you want to code in Cocoa, then you will need a Mac for sure.  What computer will you need for college?  I would get that covered first, then figure out what languages and development environments you can install.  You might need triple-boot (Mac, Windows, Linux) to get through college:  Mac to program in Cocoa and Objective-C, Windows because 90% of your assignments will require Windows, and Linux to preserve what little is left of your sanity after dealing with the first two.

What are your goals for learning objective-c and gnustep?  What type of apps do you want to program?

If you really want to get into something different (development-wise), look into beos or now Haiku.  [https://www.haiku-os.org/](https://www.haiku-os.org/)

---

### Post by pavelexpertov on 2013-12-24
> **tgalati4 said:**
> If you want to code in Cocoa, then you will need a Mac for sure.  What computer will you need for college?  I would get that covered first, then figure out what languages and development environments you can install.  You might need triple-boot (Mac, Windows, Linux) to get through college:  Mac to program in Cocoa and Objective-C, Windows because 90% of your assignments will require Windows, and Linux to preserve what little is left of your sanity after dealing with the first two.

If you really want to get into gnustep, look into beos or now Haiku.  [https://www.haiku-os.org/](https://www.haiku-os.org/)
Well, I am still deciding upon which computer I want to use in college (sorry, it's university coz I live in UK). I do not think it matters what computer it is, but I have been looking forward to lenovo laptop with very powerful spec (at least $850-900) and dual-boot so I can try using virtual machine to run mac os x, while still having two OSs. Furthermore, it gives more power processing for photoshop to design fancy user interfaces. However, I can go for a mac, but I am gonna talk to one man who sells second hand mac laptops (he offered me 13inch non-retinal mac book pro with dual core i5 and ram upgradable to 16 GB for 700-760 pounds, which is not a bad offer) and probably wait until some mac with i7 comes up in his list.
Furthermore, I thought GNUstep has a library that is close to cocoa that allows me to port applications to linux, windows etc. I am aware it does not have cocoa touch, but I just wanted to learn objective-c in the future and know some classes in the cocoa framework, because god knows when I am gonna do that. However, my choice for a laptop can affect me in a long-term. Thanks for advice on haiku and I will try that when I have some free time in summer.

---

### Post by tgalati4 on 2013-12-24
GNUstep was the basis of the Cocoa framework, but Cocoa is a proprietary graphics framework that is used only for Mac OS X applications.  But, yes, you could write an application using gnustep and port it to different platforms.  

Here's an example of one way to use gnustep:  [https://forums.freebsd.org/viewtopic.php?&t=39466](https://forums.freebsd.org/viewtopic.php?&t=39466)

You are an xcode programmer on the Mac and you have an application that you would like to port to FreeBSD.  You can use gnustep to take your objective-C code and compile it on FreeBSD.

---

### Post by pavelexpertov on 2013-12-24
I see, thanks for replying, however I am still confused if I should go with low or high spec PC, or definitely go for mac? For mac, I read a tutorial on how to install ubuntu on it, but it has some issues when it comes to some parts of mac and only certain distros are supported on certain macs.

---

### Post by tgalati4 on 2013-12-24
Linux will run on any curb-side PC.  You can install the gnustep development environment on it and play around, do some compiling and see how it is laid out.  Some macs can be problematic running linux, so you have to do your research.  Older macs tend to have more support, because the latest mac's will have hardware drivers written yet for linux.  So a used mac from your local source would be good place to start.

Mac OS X will run the Ports system, so you can install just about any BSD program and many Debian packages that have been ported.  I have a G4 powerbook with Tiger OS X with 8 desktops (using desktop manager) and one of those windows runs a X11 server with an older gnustep environment.  Within that X11 environment, I can ssh into any other Ubuntu machine and run a remote X session and get a full Ubuntu desktop (Dapper Drake at the time).  I haven't tried it with newer Ubuntu desktops, but I image it would work the same.

So to answer your question, you should have all three computers:  Low-end curbside PC to run Haiku or other environments.  High-end PC for serious development, games and whatnot, and a mac because you want to experiment with Cocoa and gnustep and the ability to dual-boot or run virtual environments.

---

