---
title: "Broadcomm BCM4320, network controller drivers"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by Conan_Troutman on 2014-02-16
Hi there,

I just installed lubuntu 12.04 (I used the alternate installer) on my old laptop (Dell Latitude 505). I'm a total noob and now don't have a clue how to set up WiFi (or everything else, really... but I guess I can figure the rest out if I only could get that damn internet working). I guess I have to install drivers manually first, but how do I do that? My network controller ist a Broadcomm BCM4320 (terminal also says it's a rev03, whatever that is) and the internet says rndis_wlan driver will work. But I can't find a file and wouldn't know how to install it anyway. I tried connecting the laptop via ethernet and then run Additional Drivers, but the latter simply doesn't pop up. The one time it actually did it just froze at about 20 percent in. So what do I do now?

Thanks for your help!

---

### Post by Vladlenin5000 on 2014-02-16
[http://ubuntuforums.org/showthread.php?t=1738740](http://ubuntuforums.org/showthread.php?t=1738740)

---

### Post by Conan_Troutman on 2014-02-16
Sorry, I don't understand what that means. 

Okay, after following a couple of links I now know that I need a bcmwl kernel source file (which apparently wasn't on the alternate install CD). I tried the one from the desktop version, but that doesn't seem to be the right one. If I try to install it (double click), then the software center opens and says "Dependency is not satsfiable: dkms". It also lists the version this version is made for: 4311, -12, -13, -21, -22, -23, -24, -25, -27 and -28. 

But I need the one for 4320 (the rndis_wlan thing I suppose). Where can I find it? Google doesn't get me anywhere.

Edit: I finally found the right drivers, it's the b43-fwcutter. Installing it now...

---

### Post by Conan_Troutman on 2014-02-16
So, I managed to get it installed. However, if I click on the connections icon in the main bar (or whatever it is called), the "wireless networks" is greyed out and it says "device not ready (firmware missing)". What's wrong now? :confused:

---

### Post by Conan_Troutman on 2014-02-16
I tried to follow the advise on [this site]("http://www.omattos.com/node/6") but I don't have the permissions to paste in the firmware directory. I found out that there is command line with chmod to fix that, but how do I do it without changing the rights permanently and screwing the whole system up?

---

### Post by wildmanne39 on 2014-02-16
Hi, download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
any questions feel free to ask, and watch for errors while the commands complete.
Thanks

---

### Post by mörgæs on 2014-02-17
Besides: Lubuntu 12.04 is out of support and should not be used. 
If you installed this one because of the PAE problem there are some options here: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

