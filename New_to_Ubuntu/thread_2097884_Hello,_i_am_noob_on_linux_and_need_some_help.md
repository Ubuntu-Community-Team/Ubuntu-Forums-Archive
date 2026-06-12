---
title: "Hello, i am noob on linux and need some help"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by vitorcampea on 2012-12-24
Hello, i just installed ubunto on my laptop  HP G7018EP

but the wireless isnt working, cant find the drivers anywhere :(

can some one help me please?

thanks!

---

### Post by BelugaWail on 2012-12-24
I had a similar issue with my Lenovo.  In my case the wireless card was not turned on.

I used the instructions in [this]("http://exain.wordpress.com/2011/10/16/wireless-on-ubuntu-11-10-and-lenovo-thinkpad-e420/") article to turn on my wireless card and make it so whenever I restarted my computer it would stay on.

I'm not sure if this would work with an HP or not.

---

### Post by BelugaWail on 2012-12-24
Also, it looks like this person had the same issue and solved it.

[http://forums.linuxmint.com/viewtopic.php?f=90&t=120651&p=663869]("http://forums.linuxmint.com/viewtopic.php?f=90&t=120651&p=663869")

Good luck

---

### Post by vitorcampea on 2012-12-24
well that was me, that problem was on linux mint and the same doesnt work for ubunto for some reason


i still dont know what linux and i gonna use xD
i think i am gonna go back to mint, ubunto its slower i think


i did sudo apt-get install firmware-b43-installer, but he doesnt find firmware-b43-installer

---

### Post by BelugaWail on 2012-12-24
> **vitorcampea said:**
> well that was me, that problem was on linux mint and the same doesnt work for ubunto for some reason


i still dont know what linux and i gonna use xD
i think i am gonna go back to mint, ubunto its slower i think


i did sudo apt-get install firmware-b43-installer, but he doesnt find firmware-b43-installer

Well I tried :D

---

### Post by vitorcampea on 2012-12-24
> **BelugaWail said:**
> Well I tried :D

worked on ubunto?

---

### Post by audiomick on 2012-12-24
It might help to mention what wireless card it is. If you are unsure, do

```
sudo lshw -C network
```

---

### Post by vitorcampea on 2012-12-24
> **audiomick said:**
> It might help to mention what wireless card it is. If you are unsure, do

```
sudo lshw -C network
```

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:91300000-91303fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:8f:e6:e3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff

---

### Post by BelugaWail on 2012-12-24
> **vitorcampea said:**
> *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       

Ok.  Since it's a BCM4311 try this:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04")

or this

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

---

### Post by Mijuca on 2012-12-24
....

---

### Post by vitorcampea on 2012-12-24
sudo apt-get install b43-fwcutter firmware-b43-installer

why he doesnt find it?

vitor@vitor-HP-G7000-Notebook-PC:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-installer

i dont undertand, it work on linux mint....

maybe i need to be in a especific dir?

---

### Post by Cheesehead on 2012-12-24
He doesn't find it because the mirror is temporarily down, or because he has a network problem. Both of those packages are in the Ubuntu repositories.

If the problem persists, try a different mirror.

---

### Post by vitorcampea on 2012-12-25
problem solved

the stupid solution:
must have internet connection, to fix wireless... -.- srly
do update to linux, like 265 mb, install it and reboot
after reboot, go to terminal and 
sudo apt-get install firmware-b43-installer
this time he will FIND the b43 and install it

and its done

but...its a little bad to need internet connecting to fix your wireless, you will need a wire or a wireless pen
in my case i used wireless pen and didnt need any drivers for it

thanks everyone for your help
mary christmas xD

---

### Post by Cheesehead on 2012-12-27
> **vitorcampea said:**
> its a little bad to need internet connecting to fix your wireless

That's usually the fault of the hardware manufacturer, who refuse permission to distribute drivers with the kernel, or who refuse to release the API for their hardware at all.

Hardware maker's fault. Complain to them.
Not Linux's fault. Not Ubuntu's fault.

---

### Post by rrich1974 on 2012-12-28
still, we must to face it that proprietary firmware for broadcom (i also have bcm4311) , despite the tricky way of installing, works damn good in linux.

---

