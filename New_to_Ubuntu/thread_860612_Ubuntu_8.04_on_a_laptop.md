---
title: "Ubuntu 8.04 on a laptop"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by richg on 2008-07-15
I have switched my desktops from Linspire/Freespire to Ubuntu 8.04 and I have a wireless laptop still running Linspire 5.1.427. I would like to switch it over to Ubuntu 8.04. Right now with Linspire, I have a DVD player application that starts up as soon  as I slip a movie DVD into the CD/R DVD reader. Is it possible to install Ubuntu 8.04 and have a movie DVD option?
Here are the PC specs. It came new configured with Linspire 5.1.427 and has run with no issues.

    * AMD Mobile Sempron 2800 (black chassis)
    * 15" XGA 1024x768 Display
    * 1256MB DDR400 RAM DDR400 PC3200 DDR 200-pin SODIMM
    * VIA K8N800 Chipset and Onboard VGA (AGP 8X, 3D Capable)
    * CDRW/DVD Combo Drive
    * 40GB Hard Drive
    * 4 x USB 2.0
    * Integrated 10/100 Mbps Ethernet, 56k v.92 modem
    * Linspire O/S + DVD Player & 1yr CNR Gold Subscription
    * Mini-PCI Wireless 802.11G 
    * Weight 7 lbs
If there issues that someone has run into with a setup like this, I wll stick with Linspire. I do not like running the OS, only applications.
Thanks

Rich

---

### Post by runemaste644 on 2008-07-15
As far as I know Ubuntu will automatically play a DVD. Linspire is just Ubuntu with a $40 price tag anyway.

---

### Post by pi.boy.travis on 2008-07-15
Just install the nessesary packages described in the Ubuntu documentation:

libdvdnav4

libdvdread3

then run:

sudo /usr/share/doc/libdvdread3/install-css.sh

to play encrypted DVDs.

As far as automation:

install gxine

system/preferences/file management

then select the media tab, and select your preferred DVD application from the drop down list.

Hope this helps!

---

### Post by richg on 2008-07-15
Thanks, but I see two different suggestions. The second one is kind of techie. 
I have tried to view a movie in my Ubuntu 8.04 desk top and I am getting an error message. "Could not read from resource". Ubuntu opens Totem Movie Player when I put the DVD in the machine. Apparently this is not plug and play with Ubuntu and I have all the latest Ubuntu updates. If I am having issues now, I can see what will be coming down the line. Thanks anyway. I will leave the laptop software alone. I have read of issues concerning laptops on Ubuntu.
Maybe the next Ubuntu upgrade will solve this issue.

Rich

---

### Post by halitech on 2008-07-15
by default Ubuntu will not play dvds (legality of using the codecs in some areas of the world) so you need to enable them. Just open a terminal and copy/paste this in

```
sudo apt-get install libdvdnav4 libdvdread3
```

then run, again in the terminal

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

this will enable dvd playback. then to play them when you put a dvd in automatically, still in the terminal type
```
sudo apt-get install gxine
```

once everything is installed, go to system -> preferences -> file management and select the media tab. Find gxine in the list and select it and click okay.

---

### Post by k3lt01 on 2008-07-15
Check out the [Comprehensive Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=766683") thread for playing DVDs.

---

### Post by seagullplayer77 on 2008-07-15
Sorry to drop in the thread like this, but I just realized that I'd never attempted to play a DVD on my HP laptop running Ubuntu Studio Hardy. Anyway, I figured I'd give it a shot and it didn't work. I followed Halitech's instructions and now I can play DVDs without any problems at all. Thanks for the help!

---

### Post by halitech on 2008-07-15
glad it helped you out :)

---

