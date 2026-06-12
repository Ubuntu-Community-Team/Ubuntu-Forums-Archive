---
title: "Problem with vesa savage 4 on ubuntu 12.04"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by swamppy on 2013-05-31
Memory 353.6 MiB
Processoe AMD Duron
Graphics VESASavage4
OS type 32-bit
Disk 39.3gb
Version ubuntu 12.04 LTS
My problem: When I try to update my system to the next available release I get an error message saying : Warning your graphics card may not work with the upgrade and may result in critical failure and grpahic issues we recomend you not to upgrade
I have not upgraded since but am wondering how I can fix this issue and prepare my pc for the upgrade. Since I installed jaunty, karmic, lucid it was working fine but since I moved into the 12.04 I have had nothing but sow often freezing screen and youtube forget it it wont load at all spite I have flash and java

---

### Post by sandyd on 2013-05-31
**Moved to Absolute Beginners Section**

---

### Post by Ghil on 2013-05-31
Hello!

Here's the thing. Your graphic card is old, and newer ubuntu releases uses compiz as a renderer (which requires 3d acceleration). Your best bet if you want to continue following on ubuntu's releases is to change your DE to something much more light.

If you like a fully featured desktop, you should go with LXDE. There is an Ubuntu called Lubuntu ([http://lubuntu.net/](http://lubuntu.net/)) that you could upgrade to easily and would work a lot better with your card.

If you want something more light and fully customizable, go for Openbox. I am providing here the link to Ubuntu's wiki so you can know how to install/customize/use Openbox if you want to go that way. [https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
Once OB is installed, you should be able to upgrade no problems.

If you have any more questions about this, don't hesitate to PM me, I'm around often :)

---

### Post by swamppy on 2013-05-31
How to I upgrade into lubuntu using repositories thats how I moved on from jaunty to 12.04 cause I can not down load that to a disk my reader wont write

---

### Post by squakie on 2013-05-31
use unetbootin and put the installation "stuff" on a flash drive - *if* you can boot from usb.  then all you need to do is boot from the usb and you can start the install process.

---

### Post by Cheesemill on 2013-05-31
> **swamppy said:**
> How to I upgrade into lubuntu using repositories thats how I moved on from jaunty to 12.04 cause I can not down load that to a disk my reader wont write

If you want to install Lubuntu on your current system then you can just do...
```
sudo apt-get install lubuntu-desktop
```

You can now just select the Lubuntu session from the login screen.

One drawback of adding Lubuntu to your system like this is that you will still have all of the default Ubuntu applications installed, so you will end up with 2 file managers, 2 text editors, 2 terminal programs etc. If you decide to keep Lubuntu as your main OS then you can follow the instructions here to get rid of the default Ubuntu applications.

[http://www.psychocats.net/ubuntu/purelubuntuprecise](http://www.psychocats.net/ubuntu/purelubuntuprecise)

---

