---
title: "[SOLVED] 8.04LTS or 8.10? What is the difference?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by jolly_grunt on 2008-11-05
I'm planning to install ubuntu on my Dell e1505, which has a 1.6ghz centrino core duo processor(t2050), 2gb ram and an ATI x1400. I'm just looking to use it for fun, fairly light duty stuff such as browsing the net, media playing and light gaming(just the free stuff that's already available).

As per advice I read on these forums, I downloaded live cd's of both ubuntu 8.10 & kubuntu 8.10. They both worked with no apparent problems. Of the two, I preferred the look and feel of ubuntu. 

Now, I want to find out the differences if any between 8.04 LTS and 8.10.

Thank you.

---

### Post by Idefix82 on 2008-11-05
8.10 is newer (only released six days ago). On the other hand 8.04 is supported for longer (which is what LTS =long term support means). If 8.10 works fine then I would stick with it.

---

### Post by torgrot on 2008-11-05
The other thing he failed to mention is that 8.04 works and 8.10 is a disaster if you have a video card made by ATI or NVidia and even some Intel cards. I first installed v 5 many years ago and have slogged through a lot of problems since then, but 8.10 is the first release that I have had to advise against.

torgrot

---

### Post by rrashkin on 2008-11-05
While I understand the issues that users are having with 8.10, I have to say that my experience is the diametric opposite.  I started using gOS, a totally different OS built on Ubuntu (7.x I think).  I tried moving to Ubuntu 8.04 and found that my graphics card (VIA) was not supported.  On 8.10 I'm loving life.

---

### Post by eldragon on 2008-11-05
> **torgrot said:**
> The other thing he failed to mention is that 8.04 works and 8.10 is a disaster if you have a video card made by ATI or NVidia and even some Intel cards. I first installed v 5 many years ago and have slogged through a lot of problems since then, but 8.10 is the first release that I have had to advise against.

torgrot

exactly, 8.10 is regression heaven. which means lots of things that used to work in 8.04, dont, or are terrribly supported.

id stick with 8.04 for the time being. wait till the complain pile in the forums gets smaller.

---

### Post by Therion on 2008-11-05
To understand the technical differences you'd need to compare the release notes between both versions (8.04 and 8.10).  If one works better for you than another, then obviously that's the distro you should probably go with.  Some people will find Intrepid the vastly superior choice, others, like myself, will find Hardy is the "sweet spot".  Regardless of what experience someone else is having, the only way to find the right distro for your system is to try them.  Try the LiveCD's, try them in a virtual machine, whatever floats your boat; but nobody is going to be able to accurately predict which distro is going work out best for you.

---

### Post by jolly_grunt on 2008-11-05
As mentioned in my 1st post, the 8.10 live cd worked when I tried it on my laptop. What are the chances it wouldn't work when it's actually installed? 

Is there better support for ati video cards on 8.04 as compared to 8.10? Are the video card drivers the biggest concern?

Thanks again. I appreciate the discussion.

---

### Post by Idefix82 on 2008-11-05
> **jolly_grunt said:**
> As mentioned in my 1st post, the 8.10 live cd worked when I tried it on my laptop. What are the chances it wouldn't work when it's actually installed? 

Is there better support for ati video cards on 8.04 as compared to 8.10? Are the video card drivers the biggest concern?

Thanks again. I appreciate the discussion.

The chances that an installation doesn't work if the live CD did are close to zero. I wouldn't pay too much attention to comments from frustrated users who had bad luck with Intrepid. If you are happy with the way the live CD works on your machine then go for it.

Judging by the discussions on the forums, graphic cards are a major conecrn on Intrepid. Having said that, other things like wireless support are supposed to have improved between Intrepid and Hardy. I can't judge for myself since I have had no time to sort out possible regression bugs and I am sticking with Hardy for now, which works like a dream for me (after tinkering with Wifi and even with Ethernet for quite a while). Since you have to do a fresh install anyway and the live CD works, the newer system seems the more natural choice.

---

### Post by clive littlewood on 2008-11-05
Hi

If 8.10 worked from live CD then all should be OK to install.

In theory graphics cards that worked in Hardy "should" work in intrepid but the vibrations from this forum would suggest that some are not.

For me 8.10 worked OOTB so i think it is great and would recomend it to you.

Good Luck and welcome to the wonderful world of Ubuntu.

Clive

---

### Post by LowSky on 2008-11-05
My graphic card is working fine. I have a Nvidia 8600GT and not one issue using 8.10.

Most of the graphic complaints are based on the Performance of the application Compiz while try to play video at the same time. For me I can run Compiz and Video with no issue, but for some, especially ATI it can be an issue and all you have to do is turn off compiz. Regardless Ubuntu will work fine without the Compiz's eye candy, so don't worry too much. If you are only using it for basic internet use and word processing, you will be fine. The complainers are trying to run Compiz + Google earth, or Compiz and a Video, or Compiz and a Game. Two programs trying to use the graphic card are going to be an issue, I dont know why people dont get that... stick to a normal or basic desktop and you should have any issues

enjoy

---

### Post by Zohso on 2008-11-05
> **torgrot said:**
> The other thing he failed to mention is that 8.04 works and 8.10 is a disaster if you have a video card made by ATI or NVidia and even some Intel cards. I first installed v 5 many years ago and have slogged through a lot of problems since then, but 8.10 is the first release that I have had to advise against.

torgrot

While I do agree that my video card drivers were not initially installed, therefore causing noticeable issues; once I downloaded the proper drivers did my system function properly.

I wanted a 1280x1024 (fullscreen) resolution and got 1920x??? (widescreen).  I went to:
System - Administration - Update Drivers
I then selected the "recommended" driver from the list of available drivers and it installed just fine.  I rebooted and it immediately recognized my monitor's appropriate settings.

---

### Post by torgrot on 2008-11-05
I wish that had been my experience with my two ATI video cards.  Running off the LiveCD, on both I was greeted with a badly flickering, red spot sparkling almost unuseable video display.  There is nothing remarkable about either computer.  They are both Dells, one an Optiplex 330 with an ATI 2400 and an older Dimension 4500 with an ATI 9700.  Both computers are unuseable under 8.10.  I tried both the 32 bit and 64 bit versions and finally attempted to install under WUBI on the Optiplex 330 with the ATI 2400.  The screen blinking, not flickering was so bad I thought I was going to seize.

torgrot

---

### Post by MrWES on 2008-11-05
I'm running 8.10 Ibex on my laptop with and ATI 9000 and I don't have any issues -- worked OOTB.

---

### Post by rrashkin on 2008-11-05
> **Idefix82 said:**
> The chances that an installation doesn't work if the live CD did are close to zero. 

That's exactly the experience I had with 8.04 on a VIA chipset.  The LiveCD worked fine but when I installed it, I had only low-resolution video.  With 8.10 both modes work fine.

---

