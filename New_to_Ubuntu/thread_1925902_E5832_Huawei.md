---
title: "E5832 Huawei"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by hsythe on 2012-02-15
Hi, I recently ran 11.10 64bit off of my USB to see how it ran on my system and I was unable to get my E5832 Huawei/Virgin Mobile Australia Wifi Modem to run although I am led to believe it should. 

When I plug it in, nothing happens so I tried my luck with Google and the best I found [**was this.**]("https://help.ubuntu.com/community/MobileWirelessBroadband") It shows up when I lsusb and the '/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi' file referenced in the 4.2.2 section doesn't seem to exist while the '/usr/share/hal/fdi/information/20thirdparty/' folder does. The page mentions adding a definition, is this something I need to do? Otherwise is there anything else I could try?

Thanks.

---

### Post by treehuggingoctopus on 2012-02-15
Hi all, 

the same problem here - it's E5832 Huawei and it just won't run. Any help would be greatly appreciated.

---

### Post by hsythe on 2012-02-15
> **treehuggingoctopus said:**
> Hi all, 

the same problem here - it's E5832 Huawei and it just won't run. Any help would be greatly appreciated.

It's good to hear I'm not alone. I'm unable to check for additional drivers as my E5832 is my only source of internet currently. Are you able to or are you in the same boat as me?

Edit: I just ran it on my laptop and tethered my phone with Bluetooth to search for drivers and it didn't come up with any drivers.

---

### Post by treehuggingoctopus on 2012-02-16
> **hsythe said:**
> It's good to hear I'm not alone. I'm unable to check for additional drivers as my E5832 is my only source of internet currently. Are you able to or are you in the same boat as me?

Edit: I just ran it on my laptop and tethered my phone with Bluetooth to search for drivers and it didn't come up with any drivers.

Yup, no drivers whatsoever.

Seems there's plenty of people in the same boat - only the solutions are scarce.

---

### Post by gandaran on 2012-02-16
question, isn't the E5832 modem a mobile internet _wifi hotspot_?
do you have a wireless card or wireless usb adapter to connect to the hotspot?
probably this is the reason it isn't supported yet with usb driver as the E5832 is mostly used as a wifi hotspot.

---

### Post by treehuggingoctopus on 2012-02-17
> **gandaran said:**
> question, isn't the E5832 modem a mobile internet _wifi hotspot_?
do you have a wireless card or wireless usb adapter to connect to the hotspot?
probably this is the reason it isn't supported yet with usb driver as the E5832 is mostly used as a wifi hotspot.

The weird thing is that the modem did work on the very same PC with Windows XP.

---

### Post by gandaran on 2012-02-17
> **treehuggingoctopus said:**
> The weird thing is that the modem did work on the very same PC with Windows XP.
why is that weird? 
don't hardware manufactures support windows and mac with drivers but not linux?

edit
was the E5832 configured on windows to connect to internet provider and work as a wifi hotspot?
I think if you have done this on windows then it should work on ubuntu just connecting the usb cable, you don't have to do anything on ubuntu, internet should work automatically with usb cable or at least that's how most of these type of devices work on PC once they are properly configured.

---

### Post by hsythe on 2012-02-17
> **gandaran said:**
> why is that weird? 
don't hardware manufactures support windows and mac with drivers but not linux?

edit
was the E5832 configured on windows to connect to internet provider and work as a wifi hotspot?
I think if you have done this on windows then it should work on ubuntu just connecting the usb cable, you don't have to do anything on ubuntu, internet should work automatically with usb cable or at least that's how most of these type of devices work on PC once they are properly configured.

That is true, but I managed to dig up a DWL-G132 this morning which didn't work either. It looks like I need 'ndiswrapper' or something which I'll try tonight.

And in my case it worked out of the box as a Wifi hotspot but it required a driver for it to use USB. (The E5832 just to avoid confusion)

---

### Post by treehuggingoctopus on 2012-02-17
> **gandaran said:**
> was the E5832 configured on windows to connect to internet provider and work as a wifi hotspot?
I think if you have done this on windows then it should work on ubuntu just connecting the usb cable, you don't have to do anything on ubuntu, internet should work automatically with usb cable or at least that's how most of these type of devices work on PC once they are properly configured.

It should - but it doesn't :-(

---

### Post by hsythe on 2012-02-17
> **treehuggingoctopus said:**
> It should - but it doesn't :-(

What s/he said. I forgot to write that sorry.

It looks as if my DWL-G132 won't work either 'cause I have the 64bit version. Looks like I'll just buy a new one that will work in Ubuntu.

---

### Post by treehuggingoctopus on 2012-02-19
[LEFT]Hm. There appears to be some sort of solution here:

[http://suhothayan.blogspot.com/2010/10/huawei-e1550-usb-3g-modem-on-ubuntu.html](http://suhothayan.blogspot.com/2010/10/huawei-e1550-usb-3g-modem-on-ubuntu.html)

But the complete and utter newbie that I am doesn't know:

1. if the number '155' should be left as it is or replaced by the number of my modem 

2. how to save anything in terminal
[/LEFT]

---

