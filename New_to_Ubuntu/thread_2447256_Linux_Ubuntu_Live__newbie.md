---
title: "Linux Ubuntu Live / newbie"
date: 2020-07-15
forum: New to Ubuntu
---

### Post by suzbossons on 2020-07-15
I have a sony notebook vpcm111E running extremly slowly sometimes crashing on user start up. 
Is there a way to find and install apps as well as drivers? Im so confused. I wish to be able to use virtual box, mixx, gimp, inkscape, browsers and clemintine. 
Im wondering if there is a app? 
i dont want to loose work and intend on buying a new system. 
Is there also a guide on what i should be looking for in systems?

---

### Post by Holger_Gehrke on 2020-07-15
Is [that the machine]("https://www.sony.de/electronics/support/laptop-pc-vpc-series/vpcm11m1e/specifications") you have ? In that case you have a problem.

It's decidedly on the lower end for any of the Ubuntu flavours; Sony give the maximum amount of RAM as 1GB, but that is probably what they tested it with; speicher.de (a german shop specializing in RAM) have it as being able to take 2GB. Adding RAM, starting with one of the lighter Ubuntu flavours ([LUbuntu]("http://lubuntu.me"), [XUbuntu]("http://xubuntu.org") or [Ubuntu Mate]("http://ubuntu-mate.org")) and carefully tuning the OS and the software might get you a stable and usable system, but it's going to be quite a bit of work.

With a maximum of 2GB I wouldn't even try using Virtual Box and an N450 isn't even capable of virtualization; mixx I'm not familiar with, but a search led me to mixxx.org - the homepage for a DJing application that does look like it will take quite a bit of power to run; GiMP and Inkscape will probably run but will be slow, especially Inkscape until you switch the view to not show filters; modern browsers -- both firefox and chromium -- are among the most RAM devouring apps around (until I upgraded from 4 GB to 8 GB my machine tended to hang after a few hours of browsing), so expect a lot of trouble with that; clementine is one of the heavier music players around, I'd try audacious unless you ***absolutely* need** all of clementine's features.

And yes, there's an app for installing programs. Here's a [link]("https://help.ubuntu.com/lts/ubuntu-help/addremove-install.html.en") to the page in the Ubuntu manual.

As far as guides to compatible systems are concerned, there are four sticky threads in the hardware forum on this site, compatibility and incompatibility lists for both laptops and desktops.

Holger

---

### Post by guiverc on 2020-07-15
Holger's response is excellent, so I'm limited in what I can provide.

I have a 

asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated)

and it's still useful to me (it has good battery life, and if I dropped/lost it the loss wouldn't hurt much which is an advantage and thus my choice for some use-cases).

Mine has 1GB ram which is it's biggest hurdle (after it's horrid keyboard), so I'd opt for Lubuntu 18.04 LTS unless you want to create something lighter yourself (or use Debian or other non-Ubuntu system). I wouldn't attempt to run many of the things you mention on mine, but I also have alternative boxes with more resources. 

For music ([https://packages.ubuntu.com/bionic/clementine](https://packages.ubuntu.com/bionic/clementine)) I'd for example opt for other programs, as whilst `clementine` will run, it'll use too many resources (Qt4) on Lubuntu 18.04, meaning less resources for other tasks I would perform at the same time (I'm using `clementine` on this box to play music as I write this; but this box has  more RAM and suffers no resource (Qt5) hit  due a different release; a setup I'd not attempt on my eeepc with atom cpu & 1gb ram).

If your box isn't reliable though, I'd start with testing RAM & working out why it's not reliable.  I would operate/test the system using 'live' media first, and prove to myself it was reliable (running ram test for a couple of days constantly, checking for overheating, validating drive health etc) before I spent time and put any data on it that mattered.

---

