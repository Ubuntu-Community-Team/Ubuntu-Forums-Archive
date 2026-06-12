---
title: "Back up a bootable sd card"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by rvabdn on 2008-09-17
I created a bootable SD card for installing windows using this method

[http://www.eeeguides.com/2007/11/instal](http://www.eeeguides.com/2007/11/instal) … thumb.html

Now it took quite a while so I would like to back it up on a hard disc in case I need to use it again.  I tried to copy the partition from the sd card to the 16 gig ssd on my 901 using Gparted I then copyied that partition on to another sd card to check if it worked but no luck.  I wouldn't boot up.  I set the flags to boot and lma which is what my original card was set as.

Is it possible to completely back up a bootable sd card?

---

### Post by billgoldberg on 2008-09-17
> **rvabdn said:**
> I created a bootable SD card for installing windows using this method

[http://www.eeeguides.com/2007/11/instal](http://www.eeeguides.com/2007/11/instal) … thumb.html

Now it took quite a while so I would like to back it up on a hard disc in case I need to use it again.  I tried to copy the partition from the sd card to the 16 gig ssd on my 901 using Gparted I then copyied that partition on to another sd card to check if it worked but no luck.  I wouldn't boot up.  I set the flags to boot and lma which is what my original card was set as.

Is it possible to completely back up a bootable sd card?

The 901? The asus 901 EEE pc?

That runs Xandros. 

This is an Ubuntu forum. 

Not a xandros or windows forum.

Try another forums like this one:

[http://episteme.arstechnica.com/](http://episteme.arstechnica.com/)

---

### Post by MegaJim on 2008-09-17
It is certainly possible, using the dd program, try reading the manpages (man dd)

---

### Post by rvabdn on 2008-09-17
> **billgoldberg said:**
> The 901? The asus 901 EEE pc?

That runs Xandros. 

This is an Ubuntu forum. 

Not a xandros or windows forum.

Try another forums like this one:

[http://episteme.arstechnica.com/](http://episteme.arstechnica.com/)

Sorry I should have said I used my Asus 901 EEEpc which is running ubuntu.  I thought the ubuntu prefix might have given that away.

---

### Post by t0p on 2008-09-17
> **billgoldberg said:**
> The 901? The asus 901 EEE pc?

That runs Xandros. 

This is an Ubuntu forum. 

Not a xandros or windows forum.

Try another forums like this one:

[http://episteme.arstechnica.com/](http://episteme.arstechnica.com/)

My favourite forum for eeepc questions is at [forum.eeeuser.com/]("http://forum.eeeuser.com/")  But it is certainly possible to put ubuntu on an eeepc, which would make it highly relevant for this site.

---

### Post by rvabdn on 2008-09-17
> **MegaJim said:**
> It is certainly possible, using the dd program, try reading the manpages (man dd)

Thanks MegaJim

I got it to work using DD.

---

### Post by stalkingwolf on 2008-09-17
another option is remastersys.  You can make a bootable ISO of your system with it.

I have an EEEPC 701 that is running Ubuntu.EEE Hardy 8.04.1. as is the
desktop I am posting this on.

BillGoldberg, " Never assume. It makes " an *** of U and ME".

The EEE's also run Win XP.  I got a steal on mine just because it had the Japanese version of XP on it.
I stole it for 165.00 including shipping.  Within hours it had 8.04 on it and screamed.

---

