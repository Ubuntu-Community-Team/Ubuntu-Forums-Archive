---
title: "Installation Ubuntu 14.04 in VAIO laptop with ATI Mobility Radeon HD 5400"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by goldendarkness1995 on 2014-05-25
In ubuntu 13.04 or lower , i am able to install proprietary graphic driver from AMD website and it worked properly but from ubuntu 13.10 with changes in kernel , is it still working with newest version of proprietary graphic drive from AMD ? 

I also heard that new kernel had better support in graphic performance so is it ok if i install ubuntu 14.04 in my laptop using open-source graphic driver ?

My graphic card : ATI Mobility Radeon HD 5400 series (according to dxdiag) 

Thanks,

---

### Post by squakie on 2014-05-26
Try booting a live media (dvd or USB flash) and selecting "Try Ubuntu".  See what works and what doesn't, what looks ok and what doesn't, then post back some questions on those.

---

### Post by deadflowr on 2014-05-26
You can follow the advice [here]("https://help.ubuntu.com/community/RadeonDriver#Power_Management"), on getting better power management for the open-source drivers on 13.10 and 14.04.

For the closed source, perhaps try installing them through Ubuntu's additional drivers application, rather then from amd's site.
Look in the program "Software and Updates" for the additional drivers application tab.

As of right now, your card is still supported by AMD, but who knows if/when that'll change.

---

### Post by goldendarkness1995 on 2014-05-27
I did try to install ubuntu 14.04 in VMware to test the "additional drivers application" and it appeared that there is no other driver for my graphic card. It is true that my graphic card is still suppported by AMD but i want to get used to ubuntu before my first university term start. 

[COLOR=#000000]Anyway, thank you very much for your advices :D I will try to use the open-sourse driver for a while. I hope the temperature won't go up to 65 ~ 70 C like i had in ubuntu 13.04 or lower :(
[/COLOR]

---

### Post by Vladlenin5000 on 2014-05-27
You can't do that in a VM. The virtualized hardware isn't the same as the real one.

---

### Post by goldendarkness1995 on 2014-05-27
Oh i see, thank you :D

---

