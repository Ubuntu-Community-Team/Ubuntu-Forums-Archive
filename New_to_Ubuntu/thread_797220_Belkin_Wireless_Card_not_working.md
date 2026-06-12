---
title: "Belkin Wireless Card not working"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by tonyp1969 on 2008-05-17
This is for a desktop not a laptop :-)

The machine is working fine with my wired card but the wireless is not working, I ran a lspci and this is the result for the cards in question.

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

I am running Hardy Heron and I was led to believe that this would work out of the box. 

The Belkin card is a F5D7000 series Wireless G

Any and all help appreciated. Comments of search the forum are not very helpful as I have already.

Thanks

---

### Post by shadow-of-sin on 2008-05-17
There is a guide for your card here:
[https://help.ubuntu.com/community/WifiDocs/Device/F5D7000](https://help.ubuntu.com/community/WifiDocs/Device/F5D7000)

---

### Post by tonyp1969 on 2008-05-17
> **shadow-of-sin said:**
> There is a guide for your card here:
[https://help.ubuntu.com/community/WifiDocs/Device/F5D7000](https://help.ubuntu.com/community/WifiDocs/Device/F5D7000)

This didn't work for me but I found another way of getting it to work. I inserted the CD-Rom and copied the Win2000 .inf file to my machine, I then ran the ndiswrapper and all is happy. 

Thanks for your help.

---

