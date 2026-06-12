---
title: "What is the minimum amount of memory needed to run Unity desktop?"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by Punchy71 on 2014-01-14
Greetings,
  Can someone please tell me what is the minimum amount of memory required to run Ubuntu with the Unity desktop at a reasonable speed?

Thank you

---

### Post by monkeybrain20122 on 2014-01-14
I would say 2 G on the safe side but even less is known to work based on other people's testimonies.

---

### Post by vasa1 on 2014-01-14
And, unless you turn off the "automatic internet search" feature, you'll need a fast net connection to complete your searches via the Dash.

---

### Post by deadflowr on 2014-01-14
768MB is the lowest I was ever able to get a functional unity desktop going.
512MB is completely unusable.
But as a base I would say 1GB is a good minimum, the 768MB gets a desktop but, that's about it.
The recommendation of running 2GB is spot on, though. It'll give you a little breathing room, if needed.

---

### Post by Bucky Ball on 2014-01-14
This took literally 15 seconds to find:

> Ubuntu Desktop 11.04 and up uses Unity as the default GUI while the previous releases used GNOME Panel by default. In order to run Unity the system needs a more capable graphics adapter &#8211; see more here or below:

* 1000 &#924;Hz processor (about Intel Celeron or better)

* 1024 MiB RAM (system memory)

* 3D Acceleration Capable Videocard with at least 256 MB 

From here:

[https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition](https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition)

Please do some digging before posting. The answer to your question is widely available online.

---

### Post by deadflowr on 2014-01-14
Yep.
The third requirement is actually the most needed to run unity.
A good graphics card.
You could have 16GB of RAM, but without a decent/modest graphics card, it'll run like garbage.

---

### Post by mastablasta on 2014-01-15
hah: 3D Acceleration Capable Videocard with at least 256 MB

just recently i instaleld KDE on mashcine with 128MB card and is very fluent - 1 GB ram... oh it was 32bit OS not 64bit so it uses a bit less ram.

it seems Unity is a bit more demanding than KDE.

---

### Post by Topsiho on 2014-01-15
"it seems Unity is a bit more demanding than KDE": I am quite certain it does. Ubuntu is less and less fit for old hardware, especially not for older graphics cards.
Fortunately Lubuntu and Xubuntu exist.

Topsiho

---

### Post by monkeybrain20122 on 2014-01-15
> **mastablasta said:**
> 
it seems Unity is a bit more demanding than KDE.

My experience is the opposite, especially since Compiz is optimized in 13.04 +. Indeed in my experience KDE is by far the heaviest of all DEs, and I can actually feel how slow it is even without benchmarking.

I find the assertion that Unity is a resource hog is a myth from people using VERY old hardware. I honestly cannot find anything made in the last 8 years that had 512M or 768M of Rams., these numbers are unreal.

---

### Post by oldfred on 2014-01-15
I have 12.04 64 bit Ubuntu on my 2006 laptop with 1.5GB RAM and default dual core Intel video. I find Unity to be slow but fallback/flashback to be acceptable. But with 1.5GB I cannot load very many larger apps before I run out of RAM and I see it pause while it swaps. My normal workload of Firefox & one or two smaller apps works well.

---

### Post by grahammechanical on 2014-01-15
Ubuntu Trusty Tahr (14.04) + Unity 7 + measured from a re-start and System Load Indicator shows 371 MB memory usage out of 1GB. This level increases to 418 MB as Ubuntu One loads. Swap is not used as much as in the past as Ubuntu now makes better use of cache memory and is better at giving up memory once it is now longer used. Ubuntu 12.04 was using 70% of 1 GB memory. Ubuntu Trusty Tahr is using 15% to 20% less memory.

Regards.

---

### Post by walterdowis on 2014-01-15
I recently obtained a 10 year old laptop with 500MB memory.  I removed Windows on it and installed Ubuntu 13.10, 32bit, with Unity desktop.  It ran but very poorly with 500MB of memory.  I added 1Gig of memory for a total of 1.5Gig.  Adding more memory helped a great deal with the laptop's performance and the laptop is working fine.  But I can't open a lot of applications at the same time and large applications like Chromium browser open slowly.  So I can see where having 2Gig of memory is better.  Soon I plan to increase the memory to 2Gig.

---

