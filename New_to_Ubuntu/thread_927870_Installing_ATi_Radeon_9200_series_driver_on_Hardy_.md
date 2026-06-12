---
title: "Installing ATi Radeon 9200 series driver on Hardy Heron"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Kazarelth on 2008-09-23
Hello all,

I am very new to Ubuntu and Linux as a whole. I searched around this (and other forums) on installing the driver from the vendor's website.
I know that the easier way is to use the "Hardware Drivers" Administration option, but for some odd reason when I open it , it tells me that there are no proprietary drivers installed in this system! Which makes me want to ask you guys if something went wrong with my installation.

I'd really appreciate it if you help. :)

Also, if I install the drivers, will my Windows games (run with WINE) work somewhat properly?

Thanks!

---

### Post by SpenceMakesSense on 2008-09-23
well i can answer the wine question. Wine is half as good as windows. And from what Ive seen running games is worth a shot but dont depend on it. Wine for me is only good for running windows only programs. Try running updates to see if maybe the drivers pop up in the restricted drivers section. cant nhelp here im at school sorry:/

---

### Post by Tatty on 2008-09-23
Unfortunately

> The 'fglrx' driver does not support cards earlier than the 9500. 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The fglrx driver is the proprietry ATI driver, so it looks like you arent going to be able to install it.

ATI has a poor reputation for linux driver support, and tends to drop out support for older cards. I do recall being able to install fglrx for a 9200 a long time ago - possibly in edgy.

Saying all that, there has been a lot of talk about ATI opening up now it is owned by AMD, and there has been a lot of open source driver work happening.  Im not quite sure what the current status is, you may wish to do some research, but i wouldnt get too excited.

---

### Post by Kazarelth on 2008-09-23
> Note that if you own an ATI card from the R400 series or below, you already have working 2D and may have accelerated 3D with the default drivers.

And the cards below 9500 are listed. So does this mean that I have to somehow enable 3D acceleration? Because when I use PlayOnLinux, it tells me that I don't have 3D accleration. :/

---

