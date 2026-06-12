---
title: "Video card and printers"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by davidtheo on 2012-06-26
Can anyone please tell me what are the best  video cards to run on a ubuntu System.

I am not playing games BUT I do Need to run Two monitors so the card need to support two monitors.

I would prefer split screen NOT mirror screens

Also what are the best printers I would prefer an all in one printer and one that has Wifi but wifi  not it is not that important

Thanks

---

### Post by TheFu on 2012-06-26
Perhaps these links will help in your research?
* [https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
* [http://www.linux-drivers.org/](http://www.linux-drivers.org/)
* [http://linuxhcl.com/](http://linuxhcl.com/)
* [http://tldp.org/HOWTO/html_single/Hardware-HOWTO/](http://tldp.org/HOWTO/html_single/Hardware-HOWTO/)

I have used $50-$100 nVidia cards the last 12 yrs with Linux.  Started using dual monitors about 10 yrs ago.  [http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver) explains how to get dual monitors working with nVidia cards.  My newest card is a 430gt. Dual monitor support basically comes down to the card having multiple video out ports. I use the DVI and VGA ports on my desktop to drive 2 monitors.  My laptop has a VGA and HDMI which also drives 2 monitors when both are connected.

Printers are hit or miss. Newer models are harder for Linux to support, unless an already supported printer with a nearly identical engine is already working. I have 2 printers.
a) Samsung Laser for 99.999999% of my printing.
b) All-in-One inkjet that is never used to print, but works with dry ink as a fax and sheet feed scanner.  The ink simple costs too much.

Both devices work and work well, but I'm a pretty lite user of printers.

Both printers are connected to the home server, so the print queues are available to anyone on the network all the time, even when the printer is turned off.  I am not a fan of wifi devices for most things. Sorry.

Basically, start with those web links, look for non-binary blob drivers (i.e. you want 100% F/LOSS drivers) and good luck!

---

### Post by mapes12 on 2012-06-26
> Printers are hit or miss.No there not. HP are by far the best supported. You will find that by default Ubu has the HPLIP driver package installed but the default driver is out of date. Go to the HPLIP website (Google it) and follow the instructions to load the latest driver. All HP printers/scanners/all in ones, work perfectly with it.

---

### Post by Cheesemill on 2012-06-26
For a printer compatibility list check out [http://www.openprinting.org/printers](http://www.openprinting.org/printers).

Anything with a status of 'perfectly' will surprisingly enough work perfectly :)

---

### Post by davidtheo on 2012-06-27
Thanks for your help and I will look and the links :p

---

### Post by kurt18947 on 2012-06-27
For printers, HP is excellent and I've had good luck with Brother.  Installing Brother printers are really simple when using Brother's installer script.  Scanners can be a little more of a challenge.  There's a glitch in Brother's scanner .deb package that puts files in the wrong folder.  There are instructions depending on the model in Brother's FAQ section.  It seems like Epson works pretty well.  Canon is spotty, Lexmark is best avoided.  Openprinting.org is good but the database could sure do with some updating.

---

### Post by kafkaian on 2012-06-28
> **Cheesemill said:**
> For a printer compatibility list check out [http://www.openprinting.org/printers](http://www.openprinting.org/printers).

Anything with a status of 'perfectly' will surprisingly enough work perfectly :)

My HP Laserjet P1005 printer is listed in 'mostly' and it's right, it MOSTLY NEVER WORKS. It always works perfectly and flawlessly in Windows however.

So you get recommended to use HPLIP rather than the standard Ubuntu drivers. And guess what? It becomes even more unreliable.

So you follow flawed directives given to you in terms of supplying error log reports through HPLIP Launchpad and you more than likely don't get a response.

I've been with Ubuntu since Dapper, and I've never found printing to be an easy and reliable process - and that's with the printer above, a common HP Deskjet and a Canon Pixma 4300. The Deskjet has been the most reliable. The other two have been a veritable nightmare. If anything, it's just traumatic - especially when you're under pressure to get a report out etc. And then you get people on here telling you to stick to LTS versions and if you don't, it's inferred that you're just plain stupid etc etc. 

So why does the Ubuntu team insist on informing you of new non-LTS upgrades without a disclaimer in the update manager if it's stupid to do so?

I've upgraded to 12.04 LTS and intend to give this a try for 6 months in the hope that printing becomes more reliable. If it proves to be robust, I'll stick with it until the next LTS version - just like I'm told. If it isn't, then my wife and I will simply have to find something that works. We can't continue with an operating system where you're wondering if a printing job has to be forwarded to an off-site system using Windows etc, and ready to be picked up the following morning, in order to do your job effectively. It's pathetic.

Let's see.

---

