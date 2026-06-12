---
title: "Network problem"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by 4400th on 2008-10-18
(how unoriginal title, but yeah, that's the main idea)

I'm new here (so I hope I'm posting this in the right section) and to Ubuntu too, I've recently installed Ubuntu 8.04 and it's working fine except...my network adapter won't start, in windows it works but on ubuntu it doesn't do anything, like it doesn't have any wire plugged in. I looked around but I didn't find anything that can solve my problem. On windows, the network is manually configured so i tried doing that on ubuntu too, but it didn't help.

I have an on-board network adapter, Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC, if this helps.

Also, this is what I get when running ifconfig -a

---

### Post by MunkyJunky on 2008-10-18
I had EXACTLY the same problem! Its due to a driver issue for the card, all you need to do is install the newer driver. I'll go on a hunt to find it, but... that's what your problem is. 

I'll post again when I find the right link for you! :D

---

### Post by 4400th on 2008-10-18
thanks a lot...i was thinking that it may be because a driver :)

---

### Post by MunkyJunky on 2008-10-18
Yea, I got really frustrated with it. Everything on the internet I found didn't seem to have much of a solution, the general idea was install the driver than patch it. Luckily, we live in the glorious times of newer drivers. 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

I'm pretty sure that's the right one for you (it does look VERY familiar), so download the package for Linux Kernel 2.6.x and 2.4.x (presuming your on one of those 2 kernels) extract it, and I'm pretty sure it has instructions in there on how to install.

---

### Post by Arthur Millar on 2008-10-19
I too am struggling with network issues related to realtek 
(Im guessing!)
RTL8101E PCI Express Fast ethernet controller (rev 01)
hardware testing detects my network controller, but network tools has no ethernet(eth0) only loopback(lo)?
I have a router and everything is as i left it from my last OS 
I tried static ip settings also no luck 
tried sudo pppoeconf 
eth0 was detected (possible other pppoe proccess controlling the modem
with further fooling around I tried changing my network settings which for some reason don't change 


any help would be appreciated

---

