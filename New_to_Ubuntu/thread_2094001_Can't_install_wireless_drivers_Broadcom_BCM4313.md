---
title: "Can't install wireless drivers Broadcom BCM4313"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by Najmudin on 2012-12-12
Hi
I'm not a beginner but i'm stuck here,i bought a new laptop a lenovo G580, installed ubuntu on it and can't install wireless driver on it from the "Additional Drivers" tab in "Software Sources",before installing in the live cd mode i'v installed them from "Additional Drivers" so i can install the updates during installion but after finnishing installation and rebooting wireless was not recognized so i put the ubuntu cd and tried to install it from the cd as a source but when ever i hit the apply changes the progress bar moves quikly and stops and nothing happens ,tried to install the deb package manually from the cd pool folder but it didn't work.
lspci -v
Broadcom corporation BCM4313 802.11b/g/n wireless LAN controller...
Any help is appriciated.

---

### Post by audiomick on 2012-12-12
The machine needs to have an internet connection to get the proprietary drivers. The easiest thing is to connect to the router with a cable until it has had a chance to get the drivers for the wireless sorted out.
If you have to install them "by hand", it gets complicated (and I don't know off hand how to do it...)

---

### Post by Najmudin on 2012-12-12
Tried that but the ethernet cable is not working also maybe it requires a driver or something not sure.

---

### Post by audiomick on 2012-12-12
Hmmm, cable should work no matter what....

Can you also post the model of your ethernet controller?

If you don't know it, do
```
sudo lshw -C network
```

in a terminal. The command list all your hardware, the option -C network restricts it to only network related.

I'm not going to be back for a while, I have to go to work. I hope that someone else will be able to help you here.

---

### Post by Najmudin on 2012-12-12
Thanks mate ,its ok i hope someone else can help.
here is a screenshot.
[IMG]http://ubuntuone.com/35mia4OQistBVicEtQCJ8A[/IMG]

---

### Post by sidzen on 2012-12-12
Get a wired connection and then go [here]("http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-card-bcm43xx")

---

### Post by Najmudin on 2012-12-12
> **sidzen said:**
> Get a wired connection and then go [here]("http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-card-bcm43xx")
I tried to connect a wire to it but there is no connection no internet  this is another issue i'm having.

---

### Post by sidzen on 2012-12-12
Get the Atheros AR8162 ethernet working first -- [see here]("http://www.linuxfoundation.org/collaborate/workgroups/networking/alx") -- then worry about the bcm43xx driver! ;)

---

### Post by sidzen on 2012-12-12
(Sigh)
Download the tarball compat-wireless-2012-11-25-p.tar.bz2
If you need help extracting it, go [here]("http://www.cyberciti.biz/faq/tar-extract-linux/")

This should get the ethernet card up

Best wishes!

---

### Post by coffeecat on 2012-12-12
@Najmudin, since your ethernet is also not working are you sure this isn't a problem with your internet connection? The BCM 4313 wireless card works out of the box with the default open source driver with every release since 11.04. The driver is called brcm80211 in 11.04 and brcmsmac in 11.10 and later.

You can install the proprietary STA driver for that card if you want, but for most people there would be no need.

---

### Post by squakie on 2012-12-13
You may to try lsmod and look for any module that begins with "ath".  If you find one, and it's not ath9k, then I would sudo rmmod <the ath module name here>.  After that, try sudo modprobe ath9k.  This would be for your wired adapter.  As coffeecat said though, the bcm4313 seems to have a driver already installed.  If you click on the network manager icon on the top bar, does it say wireless is enabled?  Does it show any wireless connections?  Perhaps it says something like "firmware is missing".  If so, we need to know that as well.

---

### Post by Najmudin on 2012-12-13
> **sidzen said:**
> (Sigh)
Download the tarball compat-wireless-2012-11-25-p.tar.bz2
If you need help extracting it, go [here]("http://www.cyberciti.biz/faq/tar-extract-linux/")

This should get the ethernet card up

Best wishes!

Ok the wired connection got fixed after following your method but the compat-wireless-2012-11-25-p didn't work it after finnishing installation and rebooting the system refused to start i did some research and found that earlier version of compat-wireless should work so downloaded version 2012-5-10 from here [http://linuxwireless.org/download/compat-wireless-2.6/]("http://linuxwireless.org/download/compat-wireless-2.6/") 
and reinstalled ubuntu and tried to compile it and this time it worked ,installing Broadcom drivers was easy from the Additional Drivers.
Thanks ziden for your help

---

### Post by Najmudin on 2012-12-13
> **coffeecat said:**
> @Najmudin, since your ethernet is also not working are you sure this isn't a problem with your internet connection? The BCM 4313 wireless card works out of the box with the default open source driver with every release since 11.04. The driver is called brcm80211 in 11.04 and brcmsmac in 11.10 and later.

You can install the proprietary STA driver for that card if you want, but for most people there would be no need.

There is no problems with the internet connection the same cable it tried is connected to my desktop and its working wireless it working also i can connect my mobile device to it.
The default open source driver didn't work ,but i have to say that i noticed that sometimes the network icon was blinking and trying to connect to the wireless connection in my place i clicked on it and it showed the wireless point but failed to connect to it and after a while it disappears.

---

### Post by dex07 on 2012-12-20
Please check:

      lspci -nn   
Is it's pci.id 14e4:4727?
 If so, this may be helpful: 
      sudo apt-get install linux-headers-generic 
    sudo apt-get install --reinstall bcmwl-kernel-source     sudo modprobe wl 

good luck

---

### Post by Beanmonster on 2012-12-25
Thank you dex07!!!

I have a Lenovo G780 and I have had to download tarballs to get my BCM4313 working everytime I install linux. (both adapters go unclaimed after updates for some reason)

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

Did the job wonderfully! Now it's just the ethernet issue.

Thanks again.

---

