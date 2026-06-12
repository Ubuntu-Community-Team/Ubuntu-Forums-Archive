---
title: "Brand new to Ubuntu and confused about drivers"
date: 2018-03-15
forum: New to Ubuntu
---

### Post by slim6y on 2018-03-15
Hello forum :)

I installed the latest version of Ubuntu on my old Alienware laptop (M17x R2 I believe from 2008). Windows just wasn't working on it and to be honest, I had given up. So I got out a USB and installed Ubuntu successfully. 

Now my problem is drivers and Google searches reveal methods to install drivers that I don't seem to have privilege to. 

I have a Broadcom wireless adapter that is not functioning (this will be the first thing to overcome). So I found my adapter series and a Linux based driver. I downloaded the Linux based drives and put them on a USB. I then transferred the drivers to the Ubuntu desktop. Now what? What is the next step in this series of things I should be doing? 

I think this is the package I downloaded [https://launchpad.net/ubuntu/+source/b43-fwcutter/1:019-3](https://launchpad.net/ubuntu/+source/b43-fwcutter/1:019-3) (sorry, not on the Ubuntu computer right now). What is the next thing to do?

---

### Post by Frogs Hair on 2018-03-15
Support request moved.

Hello and Welcome, check software & updates under additional drivers before trying to install any drivers from the web.

---

### Post by slim6y on 2018-03-15
Sorry for posting in the wrong forum channel. A real noob mistake. 

So I need to connect to the web via ethernet then?

---

### Post by #&amp;thj^% on 2018-03-15
> **slim6y said:**
> 
So I need to connect to the web via ethernet then?
Yep.
Then update and upgrade.
There are many here that can help you.
Good luck.

---

### Post by Geoffrey_Arndt on 2018-03-15
Or get a compatible usb wifi dongle such as listed below.   No drivers required.   About 10-15 USD on Amazon.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by hrsetrdr on 2018-03-15
> **slim6y said:**
> Hello forum :)

I installed the latest version of Ubuntu on my old Alienware laptop (M17x R2 I believe from 2008). Windows just wasn't working on it and to be honest, I had given up. So I got out a USB and installed Ubuntu successfully. 

Now my problem is drivers and Google searches reveal methods to install drivers that I don't seem to have privilege to. 

I have a Broadcom wireless adapter that is not functioning (this will be the first thing to overcome). So I found my adapter series and a Linux based driver. I downloaded the Linux based drives and put them on a USB. I then transferred the drivers to the Ubuntu desktop. Now what? What is the next step in this series of things I should be doing? 

I think this is the package I downloaded [https://launchpad.net/ubuntu/+source/b43-fwcutter/1:019-3](https://launchpad.net/ubuntu/+source/b43-fwcutter/1:019-3) (sorry, not on the Ubuntu computer right now). What is the next thing to do?

I agree with others that plugging into ethernet and pulling updates is a good first step.    Looking under Preferences>Hardware>Additional Drivers would be a good next step.

Here is some support information regarding your bcm43xx  wifi hardware;[  https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by wildmanne39 on 2018-03-15
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

