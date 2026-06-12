---
title: "Acer aspire 5100"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by matdombrock on 2008-06-30
So when i first put ubuntu on this laptop it gave me the restricted drivers notice and all i had to do was enable them to get the wireless card to work. How ever now that the hard drive is compleatly dedicated to ubuntu and windows does not exist there is no restricted drivers message and i cant get the wireless to work! Im going o try ndiswrapper but i cant find the driver anywhere!

please help me I love ubuntu!

---

### Post by phidia on 2008-06-30
Are you running heron (8.04) and have you looked at the System>Admin>Hardware Drivers menu item?
What does it say there now? And while your at it what's the output of > lshw -C network

---

### Post by beren.olvar on 2008-06-30
take a look at [http://www.acerpanam.com/flex/acerdrivers/bin/drivers.html?CFID=1913580&CFTOKEN=92727695](http://www.acerpanam.com/flex/acerdrivers/bin/drivers.html?CFID=1913580&CFTOKEN=92727695)
(thats the offcial acer download)

i have the same computer and ndiswrapper works fine with the 5.3 driver
sometimes i have to reload the module if I cant connect. that is:
 
sodo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

good luck!

---

