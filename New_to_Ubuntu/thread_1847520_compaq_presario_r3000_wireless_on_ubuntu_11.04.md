---
title: "compaq presario r3000 wireless on ubuntu 11.04"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by airheads on 2011-09-20
OK, after no less than 6 hours of combined searches for an answer I think it's safe to ask the local community for help

I have a compaq presario r3000, and its wireless doesn't work. When I go to check the connection it says "Device not ready (firmware missing)".

lspci | grep Wireless revealed the following information:
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I found a number of threads on this forum, but they all have to do with earlier versions of Ubuntu, providing instructions to use functions that don't exist in this version (example [http://ubuntuforums.org/showthread.php?t=1162187](http://ubuntuforums.org/showthread.php?t=1162187))

Any help would be appreciated.

Keep in mind, I'm a complete newbie, things like sudo chops may as well be pork chops as far as I'm concerned =)

---

### Post by wildmanne39 on 2011-09-20
Hi, welcome to the forum! let's see where you are at I am thinking you have tried to install drivers is that correct?

Please post the results of these commands:
```
sudo lshw -C network 
```
```
cat /etc/lsb-release; uname -a
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by airheads on 2011-09-22
Thank you for your reply wildmanne39, but I'm giving up on Ubuntu. 

This is my 3rd attempt at switching to it after it first became available, but every time there are glitches that just aren't worth the time.

Point in case - suddenly it won't boot for some reason. It gets stuck on purple screen

I had that problem the first two times I installed Ubuntu, but it resolved itself on the third attempt. however now that it's back i really don't feel like wasting time trying to solve one issue just so i could start troubleshooting another

I think I'll wait a few years for Ubuntu to become a stable OS before i attempt a forth go at it.

You guys are awesome though. Great response time and awesome knowledgeable support community. Keep at it guys!

Between Windows (that is just as glitchy) and Ubuntu, if I had to approach a computer for the first time, I'd choose Ubuntu. It's just that the evil you know is lesser than the one you don't =P

---

### Post by wildmanne39 on 2011-09-22
Hi, I am sorry to hear that you are leaving and that you are having other issues with ubuntu.

The things you mentioned do happen, but they are not usually hard to fix, when your are ready someone will be here if you need help.

---

### Post by wiltk on 2011-09-22
Hey airheads, sorry to hear you are leaving.  Just in case you care to give it another try (or if anyone else is looking for a solution):

I actually just went through this problem (fixed it 2 years ago, new install yesterday).  This problem is very easy to fix, assuming you are having the same problem as me.  The wireless chipset that the presario R3000's have (mine is a R3210US) is the broadcom BCM43xx.  Ubuntu help has this on the chipset: [BCM43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

What worked for me was the following:

1) Open up a terminal and run the command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

which will install the necessary driver/firmware for the chipset.

2) Restart the laptop
3) Upon reboot, the wireless light on my laptop was off.  
Checking the syslog:
```
cat /var/log/syslog|grep b43
```
indicated that the firmware was loaded correctly but was just disabled.  Pressing the wireless button on the laptop does not turn on the light but checking syslog again, it says that the wireless radio is "ENABLED".  I assume you're computer will act the same, that is, not light up the wireless light even if the radio is on.

At this point, my wireless started working.  Hopefully these steps will help for you.

---

### Post by nicocuve on 2012-04-24
Help!! 11.10 installed on a Compaq laptop.
 
I had some wireless issues but installing b43 drivers fixed it.
However, boot up for 11.10 (with Unity) is very random. When it boots, everything works fine but sometimes I need to reboot the PC 3 or 4 times before it kicks in. 
When it doesn't boot, I am left with, either, a purple screen or a black screen (with a flashing cursor in the top left hand corner) and the laptop doesn't respond to any combination of keys pressed.
Laptop is a Compaq Presario R3200 series with NVIDIA GeForce4 420 graphics.
 
Live CD's always boot but once I have installed.
Usually, after install, when prompted to restart, the laptop fails to boot first time.I have tried new nvidia drivers (96) with no change.
In order to boot I go in recovery mode and launch several checks and continue boot process.
 
I did'nt find any solutions on other forum but the problem seems to affect presario r3000 in general.
[http://askubuntu.com/questions/87187/11-10-randomly-fails-to-boot-on-compaq-presario-r3000](http://askubuntu.com/questions/87187/11-10-randomly-fails-to-boot-on-compaq-presario-r3000)
[http://askubuntu.com/questions/92344/ubuntu-11-10-black-screen-with-blinking-cursor-on-boot](http://askubuntu.com/questions/92344/ubuntu-11-10-black-screen-with-blinking-cursor-on-boot)
 
This problem seems to be related to this issue :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720)
But I don't use the legacy drivers (only b43) and the issue should be fixed in 11.10...
 
I follow the instructions below as my broadcom card model is a BCM4318:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers)
 
 
I'm new on Ubuntu and so far it'is pretty interesting but I really have no clue on the boot problem...
And if my laptop boots only when it wants, it wont be easy to use...

---

### Post by NikTh on 2012-04-24
Hello** @niconuve** , 
i think would be better if you started your own thread. This thread is 'dead' from 2011. Also your problem with wireless as you mentioned solved. 
I suggest you open a new thread with title as much as possible closer to you problem and describe there your excactly problem.
Thanks

---

### Post by ph4nt0m117 on 2012-04-24
> **airheads said:**
> Thank you for your reply wildmanne39, but I'm giving up on Ubuntu. 

This is my 3rd attempt at switching to it after it first became available, but every time there are glitches that just aren't worth the time.

Point in case - suddenly it won't boot for some reason. It gets stuck on purple screen

I had that problem the first two times I installed Ubuntu, but it resolved itself on the third attempt. however now that it's back i really don't feel like wasting time trying to solve one issue just so i could start troubleshooting another

I think I'll wait a few years for Ubuntu to become a stable OS before i attempt a forth go at it.

You guys are awesome though. Great response time and awesome knowledgeable support community. Keep at it guys!

Between Windows (that is just as glitchy) and Ubuntu, if I had to approach a computer for the first time, I'd choose Ubuntu. It's just that the evil you know is lesser than the one you don't =P

I've found XFCE to work nicely.

Also, try a different card.  Yours could be dead.

Or get an external card.  Taht always works.

---

### Post by nicocuve on 2012-04-24
> **NikTh said:**
> Hello** @niconuve** , 
i think would be better if you started your own thread. This thread is 'dead' from 2011. Also your problem with wireless as you mentioned solved. 
I suggest you open a new thread with title as much as possible closer to you problem and describe there your excactly problem.
Thanks


OK,

I will create an other thread.
Can an admin close this post ?

---

### Post by firemex on 2013-01-20
Excelente!! tenia ese problema, y quedo todo arreglado.. gracias por tu aportación!! 
tengo muchas otras dudas, espero puedas ayudarme, saludos!

> **wiltk said:**
> Hey airheads, sorry to hear you are leaving.  Just in case you care to give it another try (or if anyone else is looking for a solution):

I actually just went through this problem (fixed it 2 years ago, new install yesterday).  This problem is very easy to fix, assuming you are having the same problem as me.  The wireless chipset that the presario R3000's have (mine is a R3210US) is the broadcom BCM43xx.  Ubuntu help has this on the chipset: [BCM43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

What worked for me was the following:

1) Open up a terminal and run the command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```which will install the necessary driver/firmware for the chipset.

2) Restart the laptop
3) Upon reboot, the wireless light on my laptop was off.  
Checking the syslog:
```
cat /var/log/syslog|grep b43
```indicated that the firmware was loaded correctly but was just disabled.  Pressing the wireless button on the laptop does not turn on the light but checking syslog again, it says that the wireless radio is "ENABLED".  I assume you're computer will act the same, that is, not light up the wireless light even if the radio is on.

At this point, my wireless started working.  Hopefully these steps will help for you.

---

### Post by photonian on 2013-02-15
Even though this is an old thread, I see there's still an interest.

The easiest way to solve this proplem since 11.10 is to:

1.) First get online through a wired LAN or Wireless USB device.
2.) Install the package: [COLOR="SeaGreen"]linux-firmware-nonfree[/COLOR]
3.) Reboot your computer
4.) Sign in to your desktop
5.) Press the physical wireless botton on your computer - The light will/should come on.
6.) You can now sign-on to your wireless network

tada!:popcorn:

---

### Post by wildmanne39 on 2013-02-18
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

