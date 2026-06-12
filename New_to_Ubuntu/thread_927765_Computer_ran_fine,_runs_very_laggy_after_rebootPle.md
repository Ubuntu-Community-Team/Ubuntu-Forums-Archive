---
title: "Computer ran fine, runs very laggy after reboot?Please help!"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Felliph3 on 2008-09-23
I am running an operating system called gOS and when it says ubuntu in the grub loader so Im assuming its derivative from it. When I used to run ubuntu I had the same problem

Basically the screen refreshes slowly. Its like you cut the screen diagonally and the left top half refreshes and then .3 seconds later the bottom right half refreshes. So when scrolling down a webpage it will load the top left half and then the right bottom half. The same diagonal cut refresh thing shows up when i minimize a window. The whole pc is slow. It ran fine b4 but even the dock lags when i hover. I havent really done much besides trying to install compiz and I did do a sudo apt-get update and sudo apt-get upgrade but thats all i can remember. i installed gwenview but that has nothing to do with it. Any commands that i should enter to give you guys info?

Acer aspire 5000 series 100GB 1.6ghz turion dual boot win xp and gOS, something like 1gb of ram(956MB i think)


THank you

---

### Post by phidia on 2008-09-23
Goslinux is still in development (it's in beta) so you are not using a finished release. 
It is based on hardy heron but the devs (google) are using a totally different DE-it's not a full gnome desktop obviously. There is a [google group for goslinux]("http://groups.google.com/group/goslinux?hl=en")

To troubleshoot this you should look at /var/log/syslog & /var/log/messages. 
Also do you know what your video card is and have you tried to get the best driver working for that?

---

