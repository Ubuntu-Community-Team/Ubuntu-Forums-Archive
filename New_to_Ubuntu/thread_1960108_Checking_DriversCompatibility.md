---
title: "Checking Drivers/Compatibility"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by GuitarHero on 2012-04-16
I just picked up a Lenovo Ideapad Z575 and installed Ubuntu on it.  It's been at least 5 years since I've run Ubuntu and I was no more than a beginner back then.  Things look like they've improved a lot since then(my wireless worked without me doing anything!) but I'm pretty unfamiliar.  How do I know if everything is working correctly?  For instance, how do I know if the video card is working or if it's just using on board graphics?  It seems a little sluggish so I thought it might not be using the video card.

Any other tips/reccomended apps I should install are welcomed.

Thanks!

---

### Post by d4m1r on 2012-04-16
What version did you specifically install? Specs of the machine?

As for checking what GPU Ubuntu is using, search for something called "Additional Drivers" in the HUD (windows button). It should tell you if Nvidia/ATI drivers are installed and active which should narrow it down ;)

---

### Post by GuitarHero on 2012-04-16
I installed the most recent build of Pangolin.  Details are here:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834246328&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-](http://www.newegg.com/Product/Product.aspx?Item=N82E16834246328&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-)

AMD Radeon HD 6650M
AMD A6-3420M 1.5GHz

---

### Post by anewguy on 2012-04-17
Also, go to system settings, then system info - it will tell you what graphics it thinks it is using.

Welcome back!

Dave ;)

---

### Post by 3rdalbum on 2012-04-17
Open the Additional Drivers program (you can just press the Windows key and start typing "additional drivers") and it will offer a driver for the ATI graphics card in your computer.

---

### Post by anewguy on 2012-04-17
> **3rdalbum said:**
> Open the Additional Drivers program (you can just press the Windows key and start typing "additional drivers") and it will offer a driver for the ATI graphics card in your computer.

EDIT: Removed previous text I posted because it was incorrect and I don't want to confuse anyone.

Dave

---

### Post by Curtis6767 on 2012-04-17
Have you downloaded the restricted updates?

```
sudo apt-get install ubuntu-restricted-extras
```
When I upgraded to 12.04, I was told you update daily.

---

### Post by 3rdalbum on 2012-04-17
> **anewguy said:**
> I believe GTX is an nVidia card, so it will be an nVidia driver.

Dave

The OP said it has an ATI Radeon :-)

---

### Post by anewguy on 2012-04-18
And I went and looked and it was the specs on d1m4r, not the OP's.  So I really messed that up!  Also, while I was looking at that, I was thinking my 450 was GTX, but it's GTS, so I really screwed up this time!  

Thanks for straightening that out!  

Dave ;)

---

