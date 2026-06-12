---
title: "Dial up (driver)"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Corey4666 on 2008-07-02
[http://www.ubuntu1501.com/search/label/conexant%20modem](http://www.ubuntu1501.com/search/label/conexant%20modem)
cpu: Dell inspiron1501

I followed this guide. Installed the driver, then i installed Gnome PPP dial up tool. I configured the numbers and password etc the rest i was not sure about. In the setup it says type of modem analog, usb, isdn. I assume mine is a analog modem because it sure isn't a usb and i'm not sure what a isdn modem is. also it says "device" and i click detect and it says "no modem was found on your system" thats what i need help with because i did install the driver. my modem is not showing up is there any command i can use via terminal to check if my modem is there?

---

### Post by editrix on 2008-07-03
lshw will give you the hardware. I have a non-functional winmodem that's listed as:

            *-communication UNCLAIMED
                description: Communication controller
                product: LT WinModem
                vendor: Agere Systems
                physical id: 1
                bus info: pci@0000:01:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252

I didn't check out the page you cited (only so much time on dialup) but Ubuntu's Dialup HowTo is really the place to start: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

There's also [http://linmodems.org/](http://linmodems.org/)

From what I understand, there are often problems with laptop modems.

---

