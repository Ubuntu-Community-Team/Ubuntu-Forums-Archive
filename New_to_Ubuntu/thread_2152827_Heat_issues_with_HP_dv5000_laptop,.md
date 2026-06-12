---
title: "Heat issues with HP dv5000 laptop,"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by Marbash on 2013-06-09
Hey.

I've just isntalled Kubuntu 13.04 on my brother's six year old laptop and I'm having some isses with heat. I've tried to clean the fan with an air canister, but still I'm having "idle" temps. on around 70-80 celcius. I've read some stuff online about powermanaging the gfx card, but I've been unsuccessful while trying to implent in on this system. Then again I just opened the cover to both of the HDD's and I found out that it's actually one of the hdds causing all the heat. Is there a way I can scale down this somehow to prevent the laptop from getting overheated? - Without having to go out to buy an external fan-stand to cool it down from beneath.


All help is appriciated.

---

### Post by Isamu715 on 2013-06-09
You can try installing *laptop-mode-tools* and adding *pcie_aspm=force* to the GRUB commandline.

---

### Post by 23senick on 2013-06-09
Have you tried looking for proprietary drivers? Go to system and the additional drivers icon. I had similar issues with an HP laptop (tho different model) and one thing that helped was installing fglrx drivers. The additional drivers button should tell you if any are available. 

Another thing that helped was installing the Jupiter power control. It isn't in the Ubuntu repos as far as I know, but google it and there are loads of instructions to install it by adding the Jupiter repo.

---

### Post by Feathers McGraw on 2013-10-19
Hi,

I have a different HP laptop (HP Pavilion DV6-3122sa), but I had a similar problem. Are you sure it's the hard drive? In my experience, most overheating issues are caused by graphics cards.

Based on [this spec sheet for your laptop]("http://www.cnet.com/laptops/hp-pavilion-dv5000z-turion/4505-3121_7-31727903.html") it looks like you have an AMD processor (with integrated graphics) and an AMD/ATI graphics card. The integrated graphics do the low-end stuff, and the discrete card does the high end.

I wrote a tutorial on my site for dealing with dual AMD graphics cards, since I had a problem with mine. It's a solution that I came to with the help of people at [KubuntuForums]("http://kubuntuforums.net") - basically it involves turning off the power to the one that isn't in use, as that power is just being converted into heat.

For me, this reduced the temperature by 25*C.

Here's a link if you's like to try it:

[http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/](http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/)

Feathers

---

