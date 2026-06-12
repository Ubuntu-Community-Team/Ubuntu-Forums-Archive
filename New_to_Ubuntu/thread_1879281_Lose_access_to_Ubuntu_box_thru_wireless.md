---
title: "Lose access to Ubuntu box thru wireless"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by ledzepp817 on 2011-11-11
Hi everyone,
 
I have a 10.10 Ubuntu box running apache/Samba.  I want to turn it into a media server however  I randomly lose connectivity to the box.  At random times, I can't get any web pages, can't SSH to it, can't ping it.  But then after 10 minutes or so, I can.  The logs I look at show nothing.  Its like the wireless card becomes unresponsive.
 
I have a Linksys Wireless PCI card installed in it.  [http://www.google.com/products/catalog?q=linksys+pci+card&rls=com.microsoft:*&oe=UTF-8&startIndex=&startPage=1&um=1&ie=UTF-8&tbm=shop&cid=16885923583789986977&os=reviews](http://www.google.com/products/catalog?q=linksys+pci+card&rls=com.microsoft:*&oe=UTF-8&startIndex=&startPage=1&um=1&ie=UTF-8&tbm=shop&cid=16885923583789986977&os=reviews)
 
When I am physically at the terminal, I never had a problem reaching the Internet.  Its only when I try to access it from another computer/device.
 
I have deleted Network Manager and installed Wicd.  Same issue.  I have also updated 10.10.  Same issue.
 
Is it kernel related?  Driver? Settings?  Is it me :)  ?  Any specific logs I should be looking in?
 
Any help would be greatly appreciated.  Thanks!

---

### Post by acrazyplayer on 2011-11-11
Please answer these questions, 

What are you accessing your media server with? How far away is it? Are there any walls between it and the media server? Is there any interference like a microwave located nearby or maybe an incoming call on a wireless phone. It could be a lot of things causing you to lose connection bu the more questions you answer the more you can narrow down. 

Another possibility is that the network card is overheating, I had a wireless card do that and stop working until it cooled back down.

---

### Post by ledzepp817 on 2011-11-11
> **acrazyplayer said:**
> Please answer these questions, 
 
What are you accessing your media server with? How far away is it? Are there any walls between it and the media server? Is there any interference like a microwave located nearby or maybe an incoming call on a wireless phone. It could be a lot of things causing you to lose connection bu the more questions you answer the more you can narrow down. 
 
Another possibility is that the network card is overheating, I had a wireless card do that and stop working until it cooled back down.
 
 
- I am using a number of things to access server- laptop, roku device, outside computer, everything loses connectivity to it.
- the server is only about 50 feet away
- a few walls, nothing that would cause interference.... but most of the time, no problems connecting to it, no speed issues...just random times can't get to it at all
 
- the overheating could be an issue
 
But one thing I am trying right now is a constant ping to 4.2.2.2. Since the ping has been running, I have yet to lose connectivity to my server. 
 
I think there is something to do with the way my server handles ARP replies/requests. Sometimes I can never ping the server from my laptop, but I can ping the laptop FROM the server no problem....THEN, with the server's MAC in the laptop's cache, I can ping the server fine until the MAC disappears from cache then I can't ping anymore.
 
So, it might be something with that. I don't know. Weird.
 
Thanks for chiming in!

---

### Post by acrazyplayer on 2011-11-11
Could it be that it is going into "power saving mode"? with you saying that keeping it active makes it not disconnect then it kinda seems like it could be some sort of power saving function, though I'm not even close to 100%  sure.

---

### Post by ledzepp817 on 2011-11-16
> **acrazyplayer said:**
> Could it be that it is going into "power saving mode"? with you saying that keeping it active makes it not disconnect then it kinda seems like it could be some sort of power saving function, though I'm not even close to 100% sure.
 
Is there a log or setting I can check to see if wlan0 does in fact go into power saving mode?
 
I did an ifconfig/iwconfig and the setting power management=off.  unsure of where else to look.

---

