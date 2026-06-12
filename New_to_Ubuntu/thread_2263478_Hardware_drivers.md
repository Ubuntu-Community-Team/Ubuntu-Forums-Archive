---
title: "Hardware drivers"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by mark193 on 2015-02-01
Hello everyone  For some years I have been desperately wanting to get rid of the horrible microsoft poison in my machines.  What I would like to have is a setup which is Linux by default and have an MS OS in a small highly supervised partition only for playing video games.  My problem? once I had used Ubuntu for the first time, next boot I would have no ethernet device, not even the BIOS would acknowledge it's existence. The only way to cure this problem was to find the jumper for clearing the BIOS and do it. So I left Ubuntu alone, got another version a couple of years later and tried again, same problem. When I've installed windows the next step is always to install the drivers that come with the components.  The trouble at that time was that it was much easier to find Linux drivers for laptops than for desktop hardware. I checked the manufacturers websites for drivers for my hardware to find that Linux was not supported.  So today I looked around the Ubuntu website and I can't see the wood for the trees, too much information and I can't find my answer. I just need to know, Can I install Ubuntu followed by Linux drivers for my motherboard, video card etc. It doesn't really matter what particular hardware it is, when my machine wears out or becomes outdated I build another one so it changes. How far has Ubuntu come with driver support?  Mark

---

### Post by mörgæs on 2015-02-01
This is a massive block of text. Many users are likely to skip reading. 

I suggest that you edit the post stating only a short and precise question.
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Mark Phelps on 2015-02-01
> How far has Ubuntu come with driver support?

The only way to find out is to boot your machine from a DVD or USB made from the latest version and see for yourself.

---

### Post by mooreted on 2015-02-01
Ubuntu has come a long way with hardware support. Most of the time you install it and it just works. The only driver I have installed so far is my video driver which was supplied by Ubuntu.

I would open up Device Manager and list your basic hardware like video card, sound card, wireless, Ethernet, amount of RAM, etc. Then we can see if there are any issues that need to be addressed before you install.

As stated above, you can boot to a Linux live CD or thumbdrive and see if it runs out of the box.

Linux is not like Windows. You almost never go to a website and download drivers or software. Drivers and software are kept in repositories which are monitored by teams of developers to make sure no one has tampered with it. Downloading random junk from the Internet is a bad idea no matter what you are running.

---

### Post by mark193 on 2015-02-01
Thanks for the answers so far. From those answers, am I to understand that there are linux programmers making drivers for all the popular components and laying them in the depository?  This would be good news, as some years ago that situation didn't exist. I would love to see Linux become the dominant OS, it already is for phones and tablets.  All of the software I use has Linux versions except for the games.  Mark

---

### Post by buzzingrobot on 2015-02-01
Hardware drivers for a *very, very large* collection of components are included in the default install of Ubuntu, as well as that of any comparable contemporary Linux distribution. 

The specific hardware components in a system will be identified and the appropriate drivers enabled.  User interaction is not required.

Open source drivers will be used for Nvidia and AMD video cards as well as onboard Intel video.   Proprietary drivers for Nvida and AMD (Intel open sources its driver)  may be installed later. Proprietary drivers can deliver better 3D and gaming performance, but may become out-of-sync with kernel updates, resulting in a broken display, or pose other annoyances. Occasionally, an open source driver does not work optimally with a card.  Guidance on fixes and work-arounds is often requested, and received, here.

As recommended earlier, boot an Ubuntu installation image in live mode (the "Try Ubuntu" option that you will see).  Check the performance of your hardware. If it's working there, it will work after a physical installation.

*Do not* waste time trawling around the net looking for drivers for Linux.  First, few are actually available in that fashion. Second, Linux distributions like Ubuntu are in the business of packaging software in a way that allows for simple and reliable installation and updating. If you install drivers, or any other software, from something like a zip archive (done as a matter of course in Windows) the least that will happen is that the programs on your system that track and control software installation and updating will be unaware of that software.  The worst:  You install something the breaks your system.

In fact, if you actually do have problems with a component and Ubuntu, the best approach is to post a query in the "Hardware" section of this forum.

---

### Post by mark193 on 2015-02-01
Well thank you all for your help. It certainly seems that what I wanted has come to pass. A long time ago there was joke about if Microsoft and Apple made cars, well here's my version of If Linux and Windows were cars. The linux car would seat 2-4 people, have a towbar and a boot big enough for luggage. It would weigh 500Kg. It would be powered by a 1200cc turbo diesel engine and acheive 80mpg. Top speed would be 80mph and it would include a built in navigator and a perfectly good heater and hi fi with bluetooth. It could be specified to suit from a two seat roadster to an eight seat minibus.  The Windows car would weigh in excess of 600 long tons in order to accomodate the missile launchers, cranes, earthmoving gear, steam shovels ad nauseam. It would require a fleet of seventeen support vehicles, including a refueling tanker, mobile homes for the three shifts of 37 crew members etc etc. It would be powered by a pressurised water reactor providing steam to large steam turbines which would drive several enormous General Electric generators to provide power to the Starter motor. Each journey would require an act of parliament and a new road some seven hundred feet wide with a gradient of no more than 1 in 100. Although it runs on Uranium, its fuel economy would equate to three millimetres per gallon. Of course 99.73% of all that lot would be dead weight since the customer would only wish to make short journeys to the shops and pick up the kids from school.  Mark

---

### Post by mastablasta on 2015-02-02
> **mark193 said:**
> Thanks for the answers so far. From those answers, am I to understand that there are linux programmers making drivers for all the popular components and laying them in the depository?  This would be good news, as some years ago that situation didn't exist. I would love to see Linux become the dominant OS, it already is for phones and tablets.  All of the software I use has Linux versions except for the games.  Mark

in Linux most drivers are part of Linux kernel (core of the OS). when upgrading kernel, drivers also get upgraded. newer kernel usually means newer driver. 

rarely you need to search for drivers.

---

