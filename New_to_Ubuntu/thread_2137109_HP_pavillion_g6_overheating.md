---
title: "HP pavillion g6 overheating"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by abhich on 2013-04-19
I have a HP pavillion g6 laptop  and have recently installed ubuntu 12.04 . recently my laptop has started overheating a lot , within 5 mins the fan starts going crazy and the temp reaches ~80 c . 

i am new to linux . please help

---

### Post by m4gnus on 2013-04-19
Hello!
I had that issue on my HP during Ubuntu 11.10. I had to grab an older power saving tool to stop the CPU from going Ludicrous Speed off the starting line. I am currently using a tool called [TLP]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html") to handle power consumption and whatnot on my lappy. 

Give that a shot and hopefully it takes care of your overheating issue. If you have some time, read through [this]("http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html") article so you can get a review of the tool and a repository so it can get updated along with the rest of your packages.

---

### Post by pqwoerituytrueiwoq on 2013-04-19
you could try a newer kernel version, or upgrading to 12.10 or 13.04
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) (i have attached a installer/updater for this)
since you are using a APU a kernel upgrade is probably what you need, also the proprietary driver should help
add the xswat ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
then check for updates
then go into additional drivers (under software sources in newer releases) and pick the appropriate driver

---

### Post by mörgæs on 2013-04-19
These laptops are infamous for overheating, both using Windows and Buntu. Googling will give you a massive amount of links.

The best workaround I know of is throttling the CPU as mentioned above and/or running light software as for example Lubuntu.

---

### Post by abhich on 2013-04-22
i have already updated the kernel . but no change in the performance . same old problems start over again . 

and even if i install an additional driver and reboot it . it shows 'driver installed but not currently in use'

---

### Post by abhich on 2013-04-22
i have even tried most of the ubuntu versions 10.10 , 12.04 and even 12.10 . 
10.10 installation freezes and just shows a blank screen . 

do you think i show try Lubuntu ?

---

### Post by sandyd on 2013-04-22
Have you tried using something like cpufreqd to throttle down the CPU, or change the CPU power governer?

---

### Post by abhich on 2013-04-22
i have tried jupiter . it delays the overheating by little time

---

### Post by 90Ninety on 2013-04-22
How long has the thermal compund been in the laptop? 
 
 This should be re-applied every couple of years, my laptop runs very cool since replacing the thermal compound ( use antec or reputable brand ) 

 Also clean fans and blow out old dust , makes a great difference potentially 20-30 Celsius

---

### Post by abhich on 2013-04-22
good news ... i tried Xubuntu 12.04 and its working perfectly ... installed the proprietary driver with no problems ... the fan stays quiet and even the battery life is now better

---

