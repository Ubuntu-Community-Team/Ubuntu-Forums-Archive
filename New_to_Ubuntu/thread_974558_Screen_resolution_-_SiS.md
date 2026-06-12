---
title: "Screen resolution - SiS"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by blizma on 2008-11-07
Hey.

I installed ubuntu 8.10 today =D
After tackling the wifi problem, I need assistance solving the screen resolution..

Its stuck at 800x600

i tried reconfiguring the xserver but it doesnt even ask me for screen resolutions or anything..

Im on a Fujitsu Siemens Esprimo Mobile laptop which is 17inch widescreen i think.. On a sh*ty SiS Mirege 3 graphics card =[

Heeeeeeeeeeeeeeeeeeeelp!

---

### Post by Crafty Kisses on 2008-11-07
I'm not really sure if you can get this graphics card to work with Ubuntu 8.10, you may want to try Ubuntu 7.04, here is a driver which appears to be for your card for Ubuntu 7.04, > [http://barroslee.blogspot.com/2007/11/release-sis-671sis-672-linux-3d-driver.html](http://barroslee.blogspot.com/2007/11/release-sis-671sis-672-linux-3d-driver.html) I haven't verified if it works for the fact that I use Sabayon, but it might.

Upon further research on the issue, it seems as if you can only get a higher resoultion but no desktop effects. Hope this helps.

---

### Post by blizma on 2008-11-07
Oh well that sucks LOL i spent the entire day backing up and formating and partitioning :(
Will it ever be suported do u think?

---

### Post by Peter09 on 2008-11-07
As a First Pass at configuring your Video Driver:
1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select 'xfix' from the menu, this may resolve it. (Check 1. after doing this as well)

Can you post the output of the terminal command to confirm the driver that you are using.
lshw -C display

---

### Post by Crafty Kisses on 2008-11-07
According to their website they do offer Linux drivers for some of their products, > [http://www.sis.com/support/support_faqs_16.htm](http://www.sis.com/support/support_faqs_16.htm). I'm not really sure if that particular piece will be supported. I'm sorry for the issues you are having, I know how it feels. I have had a similar problem a while back, so I do know it can be frustrating.

---

