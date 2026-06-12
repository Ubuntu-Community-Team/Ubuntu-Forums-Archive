---
title: "installing SSD"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by ub9876 on 2013-06-28
when I put a new SSD in as a HDD replacement.... do I let it boot up before I install an OS iso??? or should the iso be in the CD drive from the first startup...any tips???  thanks

---

### Post by macguges on 2013-06-28
You can put your install disk (iso) in your CD drive straight away after installing your new SSD disk.  Assuming you've connected both cables (power and data) correctly to your new disk, the installation program can use it.

---

### Post by Mark Phelps on 2013-06-29
Don't understand ... a new SSD will be blank, so there will be no way to "boot" it.  You need to boot from installation media with the SSD already connected and powered.  Then, just install to the SSD.

---

### Post by ub9876 on 2013-06-29
I got it going...but my Samsung 840 PRO is very skinny and my Toshiba does not use a tray to mount the SSD in. It just plugs in but
it is loose up and down  because it is so thin. Anybody know if thats ok??? The instructions were nill ...they said nothing.
ANother thing....I tried to find AHCI or whatever its called and I cant find it in the boot menus.....  where is it??? is it possible I dont have it
???Toshiba  A 105   S4384
Any problems with downloading Chrome in 13.04...???surprised it didnt come with it...
and any other tweaks for SSD  ????thanks

---

### Post by londontechie on 2013-06-30
> **ub9876 said:**
> I got it going...but my Samsung 840 PRO is very skinny and my Toshiba does not use a tray to mount the SSD in. It just plugs in but
it is loose up and down  because it is so thin. Anybody know if thats ok??? The instructions were nill ...they said nothing.


I have 2 of these on 2 different laptops. in My Toshiba laptops I used the mechanical hard drive bracket with SSD and it fits perfectly in the slot. If you don't have a bracket then you can buy one and use. You should not let the SSD dangling, it might damage the pins.

---

### Post by newb85 on 2013-06-30
> **ub9876 said:**
> Any problems with downloading Chrome in 13.04...???surprised it didnt come with it...

Yes and no.  Ubuntu upgraded the libudev library in 13.04 from libudev0 to libudev1, and at the time, Google had not upgraded Chrome to accept libudev1 as a dependency instead of libudev0.  The workaround was to install libudev0 alongside libudev1 before installing Chrome.

Google may have fixed this issue already, but if they didn't there are very painless, straightforward instructions for the workaround at [http://www.omgchrome.com/install-google-chrome-in-ubuntu-13-10/](http://www.omgchrome.com/install-google-chrome-in-ubuntu-13-10/).

---

