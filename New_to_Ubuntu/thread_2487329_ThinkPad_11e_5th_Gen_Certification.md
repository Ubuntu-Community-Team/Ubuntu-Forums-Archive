---
title: "ThinkPad 11e 5th Gen Certification"
date: 2023-05-30
forum: New to Ubuntu
---

### Post by circularreference on 2023-05-30
Hi, all. I recently purchased two Lenovo ThinkPad 11e 5th Gen laptops specifically because [they are certified to work with Ubuntu]("https://ubuntu.com/certified/202001-27670"). Does anyone know where I can find the customized installation media for this device, and/or if a general Ubuntu desktop or server installation will find all drivers required? Thank you!

---

### Post by MAFoElffen on 2023-06-01
You could talk with Lenovo Support, to try to get their OEM image of Ubuntu for that Laptop, but they usually will ask you for the Serial Number and check if that specific machine was sold with what OS and only provide you with that specific OS... You just might get them to give you a link to download that, but maybe not. It will be version 18.04 though...

In my experience, when it was released, some of them came pre-installed with Ubuntu 18.04. The OEM version provided the wifi drivers for that machine. Standard Ubuntu Install ISO's, you had to find that driver and install it. I think later versions of Ubuntu came with that.

---

### Post by MAFoElffen on 2023-06-01
Adding to that, the background explanation may mean that you boot from the Ubuntu LiveUSB media, use "Try" and see if you can connect to a wireless network....

If you can not, then you might need a Hard wired Ethernet connection to do the initial installation. Then on first reboot, start Software & Updates > Additional Drivers tab... Install the wifi driver.

---

### Post by circularreference on 2023-06-03
Okay, yeah, seems like those my options. I had hoped Lenovo to be more like, "Here's the Linux version certified for the hardware you bought," so I thought maybe I was supposed to come here for it. I mean, what do they gain by keeping it from their users -- or at least publishing a recipe? Anyway, not you guys' problem, I appreciate you trying to help! I'll keep looking, thanks!

---

### Post by grahammechanical on 2023-06-03
I may be wrong but I am not sure that the version of Ubuntu installed by Lenovo is as specialized as you think.

I have an OEM laptop that came with Ubuntu 20.04 installed. It had a special keyboard driver that gave extra functionality to the keyboard. This extra functionality was lost when I did a dual boot by adding Ubuntu 22.04.

The supplier put a repository in the sources.list file and a gpg key in /apt/trusted.gpg.d folder of 20.04. So, in 22.04 I added the supplier's repository address in the sources.list file and copied the gpg key into the 22.04 /apt/trusted.gpg.d, I run update. I then installed Synaptic Package Manager and searched for the supplier's name and found a few packages including a keyboard driver. When I installed that I got full keyboard functionality on 22.04 just as I do from supplier installed 20.04. I have since repeated the same operation for 23.04. This method works.

So, I am thinking that what you need is the address of Lenovo's Linux driver/software repository and a gpg key that you can download.

[https://www.theregister.com/2020/06/03/lenovo_certifies_all_workstations_for_linux/](https://www.theregister.com/2020/06/03/lenovo_certifies_all_workstations_for_linux/)

Regards

---

