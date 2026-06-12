---
title: "Downloading Flash player"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Gela on 2012-06-05
I am an absolute Ubuntu beginner although Iam familiar with Windows and the EEC PC version of Linux which is nothing like Ubuntu. However, the BBC told me that I needed Adobe Flash Player if I wanted to hear a programme on the radio.  I went to the Adobe site, downloaded the required Adobe program and received a message "Download complete" but I was still unable to hear the program on the BBC.  I don't know where Ubuntu has hidden the download and if I found it would not know how to install it or where. Can anyone help me please? It would also be helpful if I could be advised of any publication which might unlock Ubuntu's working practices. Cheers - Gela

---

### Post by orange2k on 2012-06-05
1. Open the Ubuntu Software Center.

2. Type "flash" without quotes into the search box and hit enter.

3. Click on Adobe Flash Plugin in the search results.

4. Click the Install button.

The flash plugin will work with Firefox, Chromium, SeaMonkey, Iceweasel, Iceape, Galeon, Epiphany and Konqueror (among others).

---

### Post by oklokl on 2012-06-05
[http://ubuntuforums.org/showthread.php?t=1954542](http://ubuntuforums.org/showthread.php?t=1954542)
sudo add-apt-repository ppa:tikhonov/misc ## libvdpau1 bug 
[https://launchpad.net/~tikhonov/+archive/misc](https://launchpad.net/~tikhonov/+archive/misc)
[http://www.ubuntuupdates.org/ppa/canonical_partner](http://www.ubuntuupdates.org/ppa/canonical_partner)  ##  flash

Firefox to exit
Open a terminal
ctrl + alt + T

```
sudo sh -c 'echo "deb http://ppa.launchpad.net/tikhonov/misc/ubuntu  precise main" >> \/etc/apt/sources.list.d/tikhonov.list'
sudo sh -c 'echo "deb http://archive.canonical.com/ubuntu/ precise partner" >> \/etc/apt/sources.list.d/canonical_partner.list'

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B44C294F ## libvdpau1 bug flash

sudo apt-get update && sudo apt-get install adobe-flashplugin libvdpau1
```

---

### Post by Gela on 2012-06-05
> **orange2k said:**
> 1. Open the Ubuntu Software Center.

2. Type "flash" without quotes into the search box and hit enter.

3. Click on Adobe Flash Plugin in the search results.

4. Click the Install button.

The flash plugin will work with Firefox, Chromium, SeaMonkey, Iceweasel, Iceape, Galeon, Epiphany and Konqueror (among others).


Thank you so much - worked a treat first time! Cheers Gela

---

