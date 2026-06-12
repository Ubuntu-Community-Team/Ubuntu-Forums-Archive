---
title: "[SOLVED] Sharing the net, (via wired router)"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by GeordieJedi on 2008-10-28
Hi there, hope your all doing well.

I have a quick question that I hope has a simple answer?

I've been fixing a friends laptop, Installed Linux in it.
And now I want to connect it to the net, so I can download a
few codecs and apps, so that he can use the machine properly
when I return it to him.

My set up is as follows =

Cable net provider
I personally use Wi-Fi for my desktop PC (sent via a Linksys router).

Laptop = 
Ubuntu 8.04.01

I was hoping I could use a ethernet cable, and connect the laptop directly
 to the router and then surf the web. (But so-far, its a no-go).

When I click on the wired network (the radio button). It asks me for a
 number of things (inc a password. Is that the one I origionally used to set up my
 initial conection. When I first registerd with my service provider?) 

So what am I doing wrong?
How do I share the connection?

Thanks in advance for any help. :)

---

### Post by brandoncolorado on 2008-10-28
When you left click on the network manager icon, then choose the one that says eth0 - wired or something like that, it asks you for a password?

---

### Post by brandoncolorado on 2008-10-28
Try a few things:

1)  Plug in to router - make sure you have the right port
2)  Power off/on the router
3)  Restart your computer 

Try again, and screenshot if you have the same problem (function -printscrn)

---

### Post by boof1988 on 2008-10-28
I looked up support for my router (Belkin) online and found out how to log onto the router from the mfr website.  Used the model number etc to find online documentation for how to log on to the router.  In perticular they provided the ip address I needed for the router.

---

### Post by brandoncolorado on 2008-10-28
That is the login to edit the router's settings.  You shouldn't need that to simple connect to the internet.

---

### Post by Iowan on 2008-10-28
Never mind - I thought you were talking about the 'network admin' password that's requested before you can change system settings. Otherwise, you should be able to select DHCP.

---

### Post by GeordieJedi on 2008-10-29
Sorted!!

I needed to go into network manager, and enable roaming and allow DHCP.

Once I'd done that. I was online! Woohoo. :)

Thanks to everyone who offerd help and advice
 and to pwbrum61 from the LXF forums for helping sort this one out.

---

