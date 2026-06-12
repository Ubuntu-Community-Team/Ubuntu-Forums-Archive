---
title: "USB wireless, TV, FM"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by hill0093 on 2008-07-05
Is there an inexpensive (e.g., <=$50) USB wireless adapter (e.g., 802.11g) that has a driver that works for ubuntu amd64?
Is there an inexpensive and available (e.g., <=$90) USB TV stick (e.g., AverMedia? w/ FM also) that has a driver that works for ubuntu amd64?

---

### Post by neurostu on 2008-07-05
Find the USB stick you want, then google to see if that specific stick works with ubuntu.

I know that somewhere on the Ubuntu wiki is a list of wireless devices that are documented to work with ubuntu... try finding that.

---

### Post by wolfen69 on 2008-07-05
the [Linksys WUSB54GC]("http://www.bestbuy.com/site/olspage.jsp?skuId=7667009&st=linksys&lp=2&type=product&cp=2&id=1134701703165") will work. Not sure about a usb tv tuner though.  mine  is pci.

---

### Post by hill0093 on 2008-07-06
Thanks for the replies.
I picked up a Linksys WUSB54GC usb wireless stick.
But I can't figure out what and how to install for driver.
I downloaded linux_wlan_ng_0114_pre1_dr.tar.gz 
to /home/user1/Desktop/.
Is that the right one for my ubuntu amd64?

---

### Post by hill0093 on 2008-07-06
I don't know how to install the WUSB54GC.
Sorry to be so dumb.
Would someone please help me.

---

### Post by hill0093 on 2008-07-08
I have searched for drivers for Linksys WUSB54GC usb wireless adapter.
But I cannot figure out what driver to get and where to get it.
This must be real easy for someone other than me.
Please help.

---

### Post by wolfen69 on 2008-07-08
did you check system>admin>hardware drivers?

---

### Post by hill0093 on 2008-07-08
The only thing in system>admin>hardware drivers
is "NVIDIA accelerated graphics driver (latest cards)".
Don't I have to find the correct driver on the internet?

---

### Post by oldos2er on 2008-07-09
I have an external Hauppauge WinTV-PVR (USB2), and it works fine in Ubuntu.

---

### Post by hill0093 on 2008-07-09
Thanks, Ann, I’ll keep Hauppauge WinTV-PVR (USB2) in mind.
The ubuntu installation CDs have worked well through many versions,
but this is the first time I have got some extra features like printing from sun-java-jdk, printing to my Xerox P12 printer, and the DVD player to work. 
But I still cannot get my USB wireless stick (Linksys WUSB54GC) to work, and I don’t know how to proceed to get any USB TV and FM. 
(like AVerMedia AVerTV Hybrid Volar Max because it also has FM).

---

### Post by Kegusa on 2008-07-09
Your WUSB is listed as working out of the box in the list found here - [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys?highlight=(Linksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys?highlight=(Linksys))
Dunno if that list also includes the 64bit...

Is it responding when you plug it in? You might also try to search around for rt73usb drivers since your card is using that chipset.

---

### Post by oldos2er on 2008-07-09
hill0093, can you post the output of "lsusb" (typed in a terminal)?

---

### Post by hill0093 on 2008-07-12
Using Synaptic Package Manager, I searched for ndiswrapper and then  installed the ndisgtk, the ndiswrapper-common, and the ndiswrapper-utils-1.9 that showed up in the window.
 When I do “find ndis*” from the root directory (/), it says “No such file or directory”. Shouldn't there be one? Or am I not using “find” correctly for trees?
How do I install a driver for Linksys WUSB54GC using ndiswrapper?
Or is there a better way?

---

### Post by hill0093 on 2008-07-12
Sorry Ann and Kegusa, I missed 
you because I didn't expect 2 pages.
The first lsusb is without WUSB54GC.
Next is with it plugged in. This is 
on my mainboard next to the ethernet:
Gigabyte GA-M61P-S3 AMD-AM2-U8.04
I have 6 computers I am playing with.

user1@GA-M61P:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
user1@GA-M61P:~$ lsusb
Bus 002 Device 005: ID 13b1:0020 Linksys 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
user1@GA-M61P:~$

---

### Post by hill0093 on 2008-07-14
Well, I returned the Linksys WUSB54GC stick while I could still get my money back. 
It didn’t seem to work on XPx64 or on ubuntu amd64 ver8.04. 
Anyone get this combination to work? 
So I am still looking for an ubuntu-amd64-compatible USB wireless stick as well as ubuntu-amd64-compatible USB TV-FM stick or USB TV stick and USB FM stick. 
And since I am rather dumb, 
I’ll need to be told exactly how to install. 
I hope that ubuntu-amd64-compatible software will appear soon.
I want to get a new dual processor and motherboard for ubuntu. 
Is there any good reason to avoid AMD? 
Should I avoid 64 bit boards?
I had the impression that they are more powerful, 
but it seems that so much is incompatible with 64s.

---

