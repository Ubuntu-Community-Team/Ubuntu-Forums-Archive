---
title: "What is the best nvidia driver for Ubuntu 14.04?"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by cwmoser on 2014-05-04
When I installed Ubuntu 14.04, the desktop would freeze right after I logged in.

I had to remove all the nvidia video drivers and install nvidia-current.  

I have noted some minor issues with Compiz and wondered if there is a better
driver that I can use?

Carl

---

### Post by buzzingrobot on 2014-05-04
> **cwmoser said:**
> When I installed Ubuntu 14.04, the desktop would freeze right after I logged in.

I had to remove all the nvidia video drivers and install nvidia-current.  

I have noted some minor issues with Compiz and wondered if there is a better
driver that I can use?



Nvidia drivers aren't installed by default.  If you did a clean install on a machine with a active Nvidia card, the open source Nouveau drivers was almost certainly in use.

What's the best driver from Nvidia? Depends on your card.  In theory, that could be the latest available from Nvidia.  But, since that might not be packaged for Ubuntu, or might have introduced new bugs, it might not be the best choice. For very new cards, I'd go to the Nvidia site and see which drivers provide support.  Life is easier if you install a driver packaged for Ubuntu rather than install the Nvidia-way using the archive they provide on site.

The Additional Drivers tool on Ubuntu (in Software & Updates) will display and allow you to install proprietary Nvidia packages Ubuntu maintains for the card in your machine. My usual appoach is to go with the recommended driver and cross my fingers.  Proprietary drivers can be fickle things.

My only provlem with Compiz on Unity (and I never add CCSM and play with it) is that the first click on the desktop switcher after I add it to the launcher prompts a lot of disk activity for a 30-45 seconds, followed by an Apport error popup.  Once that's out of the way, it works fine. Been happening for a few releases and, last time I looked, was a known bug.

---

