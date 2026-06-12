---
title: "Huawei E173 USB Modem Xubuntu 12.04 [LTS]"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by fleamour on 2012-06-27
Thinking of dipping my toe in water, IE: PAYG UK mobile broadband from o2.  Anyone have [this]("http://shop.o2.co.uk/promo/o2mobilebroadband/tab/Pay_and_Go") modem working out the box with Network Manager?

I've checked [here]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G/")

But figure list is outa date.  Any company make a low profile modem?  USB sticks out kinda long way, but hey ho.

---

### Post by fleamour on 2012-06-28
OK, quick Google search & this is working under 12.04 AMD64, which is all fine & dandy.

Regarding topping up, the man on the phone says a screen appears when you plug it in.  If he means it opens a browser then maybe it'll work under Linux.  Otherwise it'll need topping up under Windows I guess.

Anyone have experience of topping up a WWAN dongle on a Linux machine?

---

### Post by fleamour on 2012-06-29
Somewhat tantalisingly Network Manager seems to auto detect but I am held up by:

"A Password is required to connect to 'O2 Pay and Go (Prepaid)'."

It is beyond the scope of O2 technical support to provide support for Linux, so I am reliant on the kindness of others.

Anyone know what password this refers to?  (Please, please, please!)

:confused: :confused: :confused:

---

### Post by rai4shu2 on 2012-06-29
I have no idea what you're doing, but I took a brief look and found this:

> When you placed your order either online or over the phone, you selected a Username and Password. The username and password are needed to access 'My O2' and to view your bill.

Regardless of how you placed your order, the first email you received from O2 entitled 'Welcome to O2' will have included your username and password.

[http://shop.o2.co.uk/FAQ?category=Password%2C+Username+and+Email+address&question=FAQ_I_CANT_FIND_MY_USERNAME_AND_PASSWORD__WHAT_SHOULD_I_DO](http://shop.o2.co.uk/FAQ?category=Password%2C+Username+and+Email+address&question=FAQ_I_CANT_FIND_MY_USERNAME_AND_PASSWORD__WHAT_SHOULD_I_DO)

---

### Post by fleamour on 2012-06-29
You were right, however even the correct settings entered into Network Manager do not fly.

Had to use third party Spanish utility following [this]("http://frontlinesms.ning.com/forum/topics/ubuntu-linux-driver-for-huawei") guide:

however, under 12.04;

```
sudo ./install
```

needs to be;

```
sudo bash install
```


You will also need to switch utility language to English, then enter your username & password agreed upon/given by your network provider.  I could not get O2 to connect 'till switching to dynamic APN.

I now have working connection, totally bypassing Network Manager.  Will blog exact process/full report, as had to coble together several sources combined with intuitive guess work.

Phew!  Hate it when something does not work/works incorrectly.

):P :guitar: :mrgreen:

---

### Post by p1977p on 2012-07-01
> **fleamour said:**
> OK, quick Google search & this is working under 12.04 AMD64, which is all fine & dandy.

Regarding topping up, the man on the phone says a screen appears when you plug it in.  If he means it opens a browser then maybe it'll work under Linux.  Otherwise it'll need topping up under Windows I guess.

Anyone have experience of topping up a WWAN dongle on a Linux machine?
I have a Tata Docomo 3G card with Huawei E173 modem.  I use wammu to send and SMS in the form RC<$$$> ($$$ is the amount of 3G recharge pack) to Customer service number (121 in my case). But note that:

1)  you must have sufficient cash balance in your account (more than $$$ + minimum balance necessary to surf --- Rs. 10 in my case)

2) wammu works only when the modem is disconnected  and 'Mobile Broadband' option is disabled in NetworkManager applet

you get a confirmation message immediately -- this is immediately visible in wammu -- then disconnect wammu and reenable MobileBroadband.

---

