---
title: "Using a computer as a wireless card for another computer"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by NoGumption on 2012-03-08
I just set up Ubuntu 10.04.4 desktop i386 on an old laptop last night. It doesn't have a wireless card. I have another, newer laptop with Window 7 which *does* have a wireless card. I'm trying to use the newer laptop as a wireless card for the older laptop basically.

I looked around on Google some, and tried to bridge the connection as instructed (through Windows 7), but couldn't figure out what to do on the Ubuntu computers end.

I have the laptops connected through the ethernet ports, and the newer laptop is connected to the network (wirelessly).

How close was I? Is this possible crossing operating systems? What do I need to do in addition or differently to get this working?


Thanks in advance for any help!

---

### Post by jerome1232 on 2012-03-08
edit: Forget what I said, your connecting to a router through the wireless card, bridging should've been enough.

What is the result of ifconfig from the Ubuntu box?

```
ifconfig
```

---

### Post by jerome1232 on 2012-03-08
After much expermenting in my own virtual machines, I managed to get Ubuntu connecting through windows 8 (should be same for 7) using ICS (I thought I was on the right track at first)

So disable the bridge, Right click one of the connections, click properties, click sharing, select the interface that is connecting to the ubuntu computer, apply.

On the ubuntu computer run this command to refresh it's address

```
sudo dhclient
```

all should work.

---

### Post by HermanAB on 2012-03-08
Here is another trick:
[http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html](http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html)

---

### Post by |{urse on 2012-03-08
[http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html](http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html) <-- nice!

---

### Post by NoGumption on 2012-03-08
Ah-ha! I was pretty close then. The only thing I didn't do was run the command on the Ubuntu computer.

:D!Thank you very much!:D

I'm not sure what you mean by "select the interface that is connecting to the ubuntu computer" though. "Allow other users to connect through this user's internet connection" and "Allow other users to control or disable the shared internet connection" are the only options I have, both with checkboxes next to them. Below that is some hotlinked text "Using ICS (Internet Connection Sharing)" and a button labeled "Settings..."

How do I go about posting a screenshot? I found an attachment section below, so I attached the screenshot, but when I clicked the "Insert Image" button it asked me for a URL. Do I just need to know the location on my computer and put that in? Or do I need to upload it to an image hosting site and put that URL in?

---

### Post by jerome1232 on 2012-03-08
I did use windows 8 for my setup and it has an additional drop down box that apparently windows 7 doesn't have, so it's no problem.

---

