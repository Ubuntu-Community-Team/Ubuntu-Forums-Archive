---
title: "laptop wireless 3945G dose not work with ubuntu  8.10"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by DO55 on 2008-04-24
in 7.10 the wireless card work ok with my lenovo n100 but the wireless card dose not work with cd live for ubuntu 8.10 (hardware wireless LED is off )

why ?

---

### Post by Paqman on 2008-04-24
In what way is it not working? Can you see the wireless networks at all?

---

### Post by DO55 on 2008-04-24
> **Paqman said:**
> In what way is it not working? Can you see the wireless networks at all?

no nothing 

the hardware wireless LED is off

---

### Post by itisi on 2008-04-24
make sure the card is enabled in the bios menu at boot.  Also, when it's booting, press the key combo to turn on and off the wireless. do it several times throughout boot to see if you can get the led to come on.

I had the same card, and had to do that occasionally to get it to be recognized.

---

### Post by DO55 on 2008-04-24
> **itisi said:**
> make sure the card is enabled in the bios menu at boot.  Also, when it's booting, press the key combo to turn on and off the wireless. do it several times throughout boot to see if you can get the led to come on.

I had the same card, and had to do that occasionally to get it to be recognized.

there is nothing in the bios about wireless card

---

### Post by Joeb454 on 2008-04-24
I have the same wireless card. It works fine over here in 8.04

Though I don't quite know how you're running 8.10 already ;)

---

### Post by elmer_42 on 2008-04-24
I know that the only laptop I have had with a WiFi LED had a button built into the LED. When you pressed it, it activated the card or deactivated the card. Is it possible that the card has a button on the laptop like that and it has been accidentally pushed?

---

### Post by DO55 on 2008-04-24
Joeb454 
what is  your laptop model ?


elmer_42

the switch is on but there is no wireless connection

---

### Post by DO55 on 2008-04-25
help

---

### Post by DO55 on 2008-04-25
help

---

### Post by Technoviking on 2008-04-25
What model laptop do you have? 

Also, do an lsmod in the command line and tell me if you see iwl3945 loaded.

---

### Post by DO55 on 2008-04-25
I have lenovo N100 
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)

I use Lsmod and i found iwl3945 in the text but i dont know if it loaded

---

### Post by amazoohwawa on 2008-04-25
i have the exact same laptop "lenovo n100" it worked fine with 7.10 but since upgrading to 8.04 this morning the wireless card stopped working and the indicator light is not coming on?? and no one seems to have any idea on how to fix this:confused:

i might just have to revert back to 7.10

---

### Post by DO55 on 2008-04-25
> **amazoohwawa said:**
> i have the exact same laptop "lenovo n100" it worked fine with 7.10 but since upgrading to 8.04 this morning the wireless card stopped working and the indicator light is not coming on?? and no one seems to have any idea on how to fix this:confused:

i might just have to revert back to 7.10

me too. im using now 7.10 

i have report the bug 
[https://bugs.launchpad.net/ubuntu/+bug/221633](https://bugs.launchpad.net/ubuntu/+bug/221633)

---

### Post by jo.cisco on 2008-04-27
I have the same laptop and i cant seem to get the 3945G to work, i tried everything i could find. The LED light wont turn on and it wont show or find any wireless networks. The conclusion i came to in the end is that the wireless card comes up as wmaster0, which has no driver and is not recognized by the system. While the wireless interface that the system is trying to use and loads the driver for is wlan0, which doesn't exist!? because i only have one wireless card. I think it needs some tinkering to get wmaster0 to load the correct driver and not wlan0, if someone knows how to do this please post it here i dont mind trying.

btw i get the same message from iwconfig as DO55 does.

HELP PLEASE

---

### Post by stix213 on 2008-04-29
The LED issue seems fixed for my T60 with 3945 wifi using ubuntu backports using these instructions:

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

Although I still get flaky at best wifi.  I've had partial success getting wifi to work by trying to force settings with iwconfig and following up with dhclient (I'm using wifi on Hardy right now, but it wasn't working for me for a few hours).  Also I have better luck it seems when I have a network cable connected to the wired NIC, even if it is just connected to another machine, during the boot process, otherwise my wired NIC (eth0) doesn't get started properly - not sure yet why that matters, but I haven't gotten wifi to work yet without eth0 showing up.  My wifi card is detected as eth1.  

You can also use iwevent to kinda watch what is happening in a separate window.  

Example:
sudo iwconfig eth1 essid LINKSYS ap 00:0B:86:97:34:A0 channel 1
(wait a moment)
sudo dhclient eth1

I'd really like someone to actually figure this out though, as this is an intermittent & admittedly completely half-*** fix.  :)

---

### Post by stix213 on 2008-04-30
Forgot to mention, use iwlist to try to force a scan for local wifi networks

sudo iwlist scan

---

### Post by chili555 on 2008-04-30
Mine works fine, including the LED, with:```
sudo apt-get install linux-backports-modules-hardy-generic
```

---

### Post by MaindotC on 2008-04-30
If that doesn't work you should know that the ipw3495 driver is replaced with the iwlwifi driver.  Please follow the directions here at [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) for installation.

My T60 actually worked - the LED is not lit but I don't have any problems connecting to wireless networks - but this should resolve your problems.  Please let me know if you have difficulty following the directions...

---

### Post by fkamp on 2008-05-03
> **chili555 said:**
> Mine works fine, including the LED, with:```
sudo apt-get install linux-backports-modules-hardy-generic
```

Thank you very much. Now the light on my dv6000 works and the connection is better!!!:KS:popcorn:

---

