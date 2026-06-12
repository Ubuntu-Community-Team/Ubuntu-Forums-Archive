---
title: "Internet not working (ubuntu does not see network cars)"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by n_alexx on 2011-12-01
Hello

I have a notebook acer 5750G ,and Ubuntu 10.4 does not see network cards(wireless and wired)
when i try comand ifconfig :[ http://postimage.org/image/b46mpzlyd/]("http://postimage.org/image/b46mpzlyd/")
also i tried pppoe but nothing
comand lspci : [http://postimage.org/image/44i20jx79/](http://postimage.org/image/44i20jx79/)
comand iwconfig :  lo ni wireless extensions.

In Windows works in both network cards.

---

### Post by gandaran on 2011-12-01
try Ubuntu 11.10 from live cd/usb then if wired internet works I would suggest to install it over 10.04, it would save you a lot of work as if you have wired internet it would be easier to activate/install the broadcom wireless drivers.
> also i tried pppoe but nothing
why pppoe? do you connect to wired internet in windows with a miniport pppoe setup? or is just a normal router configuration setup?

---

### Post by sandyd on 2011-12-01
> **n_alexx said:**
> Hello

I have a notebook acer 5750G ,and Ubuntu 10.4 does not see network cards(wireless and wired)
when i try comand ifconfig :[ http://postimage.org/image/b46mpzlyd/]("http://postimage.org/image/b46mpzlyd/")
also i tried pppoe but nothing
comand lspci : [http://postimage.org/image/44i20jx79/](http://postimage.org/image/44i20jx79/)
comand iwconfig :  lo ni wireless extensions.

In Windows works in both network cards.
BCM57785 uses the tg3 driver.

Try 
```
sudo modprobe tg3
```

---

### Post by n_alexx on 2011-12-02
> **gandaran said:**
> try Ubuntu 11.10 from live cd/usb then if wired internet works I would suggest to install it over 10.04, it would save you a lot of work as if you have wired internet it would be easier to activate/install the broadcom wireless drivers.

why pppoe? do you connect to wired internet in windows with a miniport pppoe setup? or is just a normal router configuration setup?


When i try to instal ubuntu 11.10  or load without install   it appear this lines but instead of device number 5 is 6 ,7 ,8 ...  to infinity 
  ```
 udevd[106]: timeou: killing '/sbin/modprobe -bv pci: v00008086d00000116sv0001025sd00000504bc03sc00i00' [205]

udevadm settle - timeout of 120 seconds reached ,the event queue contains:
/sys/devices/pci0000:00/0000:00:02.0 (1082)
[127.475227] usb 2-1.2: USB disconnect, device number 5
[128.951368] usb 2-1.2: new low speed USB device number 6 using ehci_hcd
[129.051421] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input7
 
```i tried pppoe because   i tried to fix the wired connection
by put the cable(not from route) in notebook and set the ppoe connection...i set user and password but nothing.

@sandyd

bcm57785 is driver for ubuntu ?   i must download it in wondows and then put on usp stick and after that put on ubuntu sistem?

---

