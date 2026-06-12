---
title: "Problem when i try to configure network/interfaces..ifdown and ifup dosent work."
date: 2018-01-21
forum: New to Ubuntu
---

### Post by jonna81 on 2018-01-21
Hi All!!):P
This really confuses me..
Totally new to ubuntu and have tried to watch Youtube videos to find a solution but ... no.
When i try to configure my network/interface nothings happens.. or well things happends but not what i want to happen. Hope someone can point me in the right direction.

I start with 
sudo nano /etc/network/interface
(putting in my password)
 and enter the code 

iface lo inet loopback
auto lo

#auto ens32
#iface ens32 inet static
address 10.0.0.2
netmask 255.0.0.0

after that i hit ctrl +x answers Y and enter for exit.

Now my problem starts.:confused:
When the command  ifdown ens32 / ifup ens32 
i got a message "/etc/network/interfaces/ :6: missplaced option
 ifput/ifdown couldent read interface file "/etc/network/interfaces"

---

### Post by steeldriver on 2018-01-21
Hello and welcome to the forums

What exactly is your end goal? Are you using the Desktop or Server edition of Ubuntu?

The desktop version uses NetworkManager rather than the traditional networking service - if you are using that, you should configure your interfaces via the GUI applet

FWIW my guess is that the address option is "misplaced" because the # characters turn the preceding lines into comments

---

