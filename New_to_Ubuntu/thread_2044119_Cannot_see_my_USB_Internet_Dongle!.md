---
title: "Cannot see my USB Internet Dongle?!"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by LinuXofArabiA on 2012-08-18
Hello Everyone, 

It has been a while since I have been here, but then again it has been a while since I last needed the professional help provided here :)

Quick question. I am in the middle east, so for reasons beyond the grasp of most of the people in developed countries, the quickest way to gain internet access was to buy a prepaid 'USB activated SIM card dongle' (that is the best description I came up with, you know what I am talking about). The thing is, when I plug it into my computer the autorun program doesnt start, and I cannot see the USB stick in my file manager :( 

I asked the service provider, and they told me that their service works on Ubuntu, so any ideas how I can start the program and my internet up and running? I am running Ubuntu 11.10

P.S. I exaggerated a bit for dramatic purposes about the middle east not being so technology friendly. Actually, the beauty over here is that any technology or gadget you can think of is available, and for the fraction of a price you would pay elsewhere. Just for clarification.

Thanks for your help in advance.

:)

---

### Post by ixtok on 2012-08-18
On my USB dongle the auto run only worked for windows or mac. I used the file manager to look at what was on the dongle and found some installation files for linux which I used to successfully get it to work.

---

### Post by LinuXofArabiA on 2012-08-18
Thx for the reply, but could you give me more details. Like more step-by-step instructions?

---

### Post by ixtok on 2012-08-18
Sorry but I'm not that experienced to be able to give step by step instructions. Maybe wait for someone else with more experience to help you or search the forum. There is a ppa or something like that out there somewhere which will get a usb dongle going too. I don't remember what it is called or where it is.

---

### Post by cariboo on 2012-08-18
IF you open a terminal and type the following command, you should see if your device is detected properly:

```
lsusb
```

the output should look similar to this, I just plugged in a usb wireless device as an example:

```
lsusb
Bus 001 Device 004: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 002 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

In the output above you can see in Bus 001 Device 004 my wireless device.

---

