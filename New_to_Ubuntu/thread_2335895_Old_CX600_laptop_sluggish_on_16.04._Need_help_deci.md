---
title: "Old CX600 laptop sluggish on 16.04. Need help deciding if and how to switch versions"
date: 2016-09-02
forum: New to Ubuntu
---

### Post by walrustooth on 2016-09-02
Hi there,

I've got an old **MSI CX600** laptop that I'm trying to revitalize for a family member, and I've put **Ubuntu 16.04** on it. It originally had Vista and I installed Ubuntu alongside it. While everything seems to be working, the laptop feels a little sluggish. This particular model has **4GB of RAM, a core 2 duo processor, and a Radeon mobility HD4330 GPU**. They're hoping to use this laptop mainly to watch content streamed from another PC with Kodi. It honestly seems fine for that purpose but I'm wondering if there is any reason to consider trying an older version of Ubuntu considering the age of the laptop, or if switching to a derivative like Kubuntu would be likely to substantially improve how snappy the laptop feels when browsing the Internet and such. At the moment things seem pretty slow to open and it seems to struggle with things like, for example, the speedometer animation that plays on speedtest.net.

My level of experience with Ubuntu and Linux in general is relatively low but I do have *some* experience troubleshooting things, sometimes with help, so I should be able to follow instructions without *too* much hand holding. I know that Kubuntu is essentially just Ubuntu but with KDE and googling led me to a relatively simple process to make the switch, but the instructions I found appear to possibly be for older distributions so I'm not sure how to proceed. If I do a complete reinstall I also need to be sure that I am able to do so without breaking the Vista installation as they want to keep that intact.

**TL;DR Should I switch to an older version of Ubuntu or to a lighter derivative like Kubuntu on this old laptop, and if so how can I do that without breaking the Vista install?**

Thanks a lot for your time.

---

### Post by oldrocker99 on 2016-09-02
Kubuntu isn't very lightweight. You'd be better off installing Ubuntu MATE, Lubuntu or Xubuntu, all of which are lighter-weight than Ubuntu or Kubuntu.

Start a live CD or USB with the version you want to install, and look for "Replace Ubuntu," which **should** be there. Install your version over Ubuntu and your Vista installation should be OK.

---

### Post by walrustooth on 2016-09-02
Thanks for the info, I'll give that a try. Do you have a personal recommendation out of the three? Also, I was taking a look around the forums and saw people mentioning that older AMD GPUs may not be properly supported in Ubuntu 16.04 and that some people with the affected GPUs should go back to 14.04. Is that something that affects this PC with the Radeon 4330HD? Should I go to the 14.04 version of one of the ones you suggested, or just stick with 16.04? Thanks again!

---

### Post by Bucky Ball on 2016-09-02
Welcome. That machine should take whatever flavour of Ubuntu you want to throw at it so odd it is sluggish. :-k You could try a lighter version or try a dig for what could be the issue here. 

The CPU and 4Gb of RAM are fine. Yes, there is an issue, temporary, with Radeon support on some older cards, but not sure which. That could be your only issue. You could try 16.04 LTS and see what happens or go straight to 14.04 LTS and upgrade when the new driver is ready (which they are currently working on).

PS: My preference is for Xubuntu; lighter, snappy and easy to configure. In fact, I go for [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/"), which is lighter again, and add what I want. Bit of a learning curve for a newcomer, but if you're game ... 

If you mainly want to stream using Kodi, figuring that out is the stuff of another thread, but you don't need a full Ubuntu. Kodi is installable on any flavour. I'd do a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") and massage that to my purpose.

---

### Post by poorguy on 2016-09-02
I'm running Ubuntu Mate 16.04 without any sluggishness. 

ASUS M2A-VM Motherboard 06/15/2007
Dual core AMD Athlon 64 X2 5200+  2700 MHz. 
ATI Radeon X600 256 MB Graphics card.
Memory 3.0 GB DDR2.

---

### Post by wildmanne39 on 2016-09-02
I run ubuntu mate 16.04 perfectly on my laptop with the same specs as yours. I would not run unity on it.

---

### Post by walrustooth on 2016-09-02
Thanks for all the help, guys. I'll mark this solved and will make a new thread if I run into any new issues during the process of replacing Ubuntu.

---

