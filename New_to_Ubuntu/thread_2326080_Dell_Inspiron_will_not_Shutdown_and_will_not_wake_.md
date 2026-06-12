---
title: "Dell Inspiron will not Shutdown and will not wake after suspend"
date: 2016-05-28
forum: New to Ubuntu
---

### Post by tony122 on 2016-05-28
This is my first time trying Linix. I have installed Ubuntu 16 on a Dell Inspiron 11.6. It is a 2 in 1 laptop/tablet and have 2 really annoying problems that effectively make the laptop unusable.

1. When I shut the computer down it just reboots. 

  2. When the laptop goes to sleep it wont wake up,I have to hold the power button on to restart it. 

I can live with out suspend if I have to but if I cant get the computer to shut down I guess Ill have to go back to windows :(

  I'm very new to all this but am keen to learn if anyone has the time to offer me some guidance.  I see that on the Dell USA website they actually sell these laptops with Ubuntu installed so it must be possible to get it all working properly :/

---

### Post by tony122 on 2016-06-10
Can Anyone Please offer any advice or direction?:confused:

---

### Post by howefield on 2016-06-10
> **tony122 said:**
> ... I see that on the Dell USA website they actually sell these laptops with Ubuntu installed so it must be possible to get it all working properly :/

Did you see any driver downloads for Ubuntu that might help.

Is this the Inspiron 11 3000 that you are talking about ?

---

### Post by tony122 on 2016-06-11
> **howefield said:**
> Did you see any driver downloads for Ubuntu that might help.

Is this the Inspiron 11 3000 that you are talking about ?

yes its the Dell Inspiron 11 3000 series. The actual model number is 3147. its a touch screen (2 in 1) laptop that the screen flips right back to become a tablet.

I'm not sure where to find drivers for it. I have checked in Software & Updates /  Additional Drivers and it doesn't find anything that it isnt already using. Is there another place I should be checking for drivers?

---

### Post by howefield on 2016-06-11
> **tony122 said:**
> ... Is there another place I should be checking for drivers?

I quoted what you said about Dell selling this with Ubuntu, that was meant to be the clue that I was pointing you to check the Dell website for drivers. [Enter your Service Tag]("http://www.dell.com/support/home/uk/en/ukdhs1/Products/?app=drivers") and see what is offered ?

The laptop appears to have been certified to work with Ubuntu, however that was Ubuntu 12.04.
 
[http://www.ubuntu.com/certification/hardware/201403-14889/](http://www.ubuntu.com/certification/hardware/201403-14889/)

---

### Post by tony122 on 2016-06-13
Yes I have checked the Dell site with my service tag and there are plenty of drivers for this model but they are all windows files, nothing specifically for Linux. Im guessing the drivers need to actually be written for Linux?

---

### Post by tony122 on 2016-06-13
I have had a win. I found a suggestion on another forum and it seems to have helped.
[http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa](http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa)

 I can now shut down the and it stays off. Keyboard/mouse inputs still don't wake it up from suspend but closing and reopening the lid does actually wake it up. For anyone who experiences these same shutdown/suspend problems try editing the /etc/modprobe.d/blacklist.conf by adding the lines:

  blacklist dw_dmac   
blacklist dw_dmac_core

I really don't understand what it does but im guessing to disables some drivers or operations? Anyway its great to be able to shut down my laptop:)

Thanks for your help @howerfield :) I would still love to know if there are any linux drivers for this laptop as it does freeze up quite a lot. But I have no idea where to find drivers, I have done a lot of searching online but all I can find are those windows drivers on the Dell site.

---

