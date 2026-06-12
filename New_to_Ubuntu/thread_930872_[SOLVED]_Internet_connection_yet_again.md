---
title: "[SOLVED] Internet connection yet again"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2008-09-26
Hi All,
I'm sure some of you are getting tired of what must seem like the same question over and over again, but here goes. After some great advice from this forum I have just bought a Dell laptop  complete with Ubuntu after years of not very computerate frustration with Microsoft. Everything has worked perfectly straight out of the box and I am delighted. All except the internet. Perhaps the way I put my problem will give you some idea of my lack of knowledge. I had Virgin broadband over my telephone line via a splitter and a speedtouch 330 (whatever that is) plugged into a USB port on my Sony Vaio running XP home edition. I have since managed to get it working on a friend's pc (while he house sat for me) by bunging in Virgin's CD and letting it do its stuff. However, my new Dell didn't automatically open the CD so I did it manually, but couldn't find anything obvious to let me install and run whatever it has on it. When I plug in the speedtouch the Dell doesn't seem to recognise it as existing at all since it doesn't appear anywhere I can see.
I have searched the forums here for hours, but either the problems weren't exactly the same or I didn't understand the answers. Either way I'd be grateful if anyone can talk me through the problem. 
Thanks,
Dermot
Oh, by the way, I phoned Virgin's technical helpline and was told that Virgin didn't support Linux and it wouldn't work!

---

### Post by shifty_powers on 2008-09-26
ooh a speedtouch 330, nasty. they are horrible nasty little things. i've ahd some arguements with them over the years.

tbh, i would look into buying a modem/router which you plug into your laptops ethernet port, and will be soooo much easier. are you using virgin adsl or their cable internet?

---

### Post by bobnutfield on 2008-09-26
This is quite a long thread, but apparently the user was able to solve the problem:

[http://ubuntuforums.org/showthread.php?t=796697&highlight=Speedtouch+330]("http://ubuntuforums.org/showthread.php?t=796697&highlight=Speedtouch+330")

---

### Post by Dermot Doyle on 2008-09-26
Hi,
I assume it's ADSL since it says that on the speedtouch (I certainly don't have cable)and I don't seem to have an ethernet port on the laptop. I do have what Dell calls a modem connector (port) which it says I can connect to a telephone line. Is that what I should be using? I'm sure you're right about the speedtouch since others have said the same. Can you suggest another modem/router I could buy?
Cheers

---

### Post by xpod on 2008-09-26
Not that it solves your actual problem but could`nt you just upgrade to Virgins cable Broadband,if it`s available of course.
I know they`d give you the USB>Ethernet adapter if you dont have your own.
I`ve never owned one of those speedtouch`s but i`ve watched many a nightmare unfold on here with the things.

> I phoned Virgin's technical helpline and was told that Virgin didn't support Linux and it wouldn't work! 

Thats what most of them will tell you sadly,even with the Cable Broadband, which works just fine.I think the only time i`ve booted into (my own)Windows this last couple of years has been during those tedious calls to VM`s tech support.I always started out with my "unsupported" OS of course but most times i`d have to eventually admit defeat and go find an XP install to wire up directly to the Modem.

---

### Post by shifty_powers on 2008-09-26
[http://www.ebuyer.com/product/118662](http://www.ebuyer.com/product/118662)

is the one that i have got, first class, but if you are not bothered by wireless then:

[http://www.ebuyer.com/product/118658](http://www.ebuyer.com/product/118658)

would be fine.

first is about £40ish and second is £25ish.

you can get cheaper, but they can be a nightmare to set up. linksys is known for having wellmade and reliable equipment. either would work. a router is much easier, as they are completely transparent to the os. (oh and btw the linksys routers often have a customised linux as their firmware :D)

edit: whoops, amended second link, which is for an adsl modem/router that is NOT wireless...

---

### Post by Dermot Doyle on 2008-09-27
Thanks for the replies. I don't really want to go down the cable route since I don't have a TV and I assume the package wouldn't be worth it for me. 
Shifty-powers, you put the same links for the two different routers. Could you ammend the second, wireless one for me? Thanks a lot.

---

### Post by shifty_powers on 2008-09-27
whoops, sorry. done :D

---

### Post by Dermot Doyle on 2008-09-27
Thanks again. Just discovered my computer does have an ethernet port (Dell call it something else in the guide) and a modem built in. The piece of kit you suggest calls itself a modem as well. Do I still need it?

---

### Post by xpod on 2008-09-27
> I don't really want to go down the cable route since I don't have a TV and I assume the package wouldn't be worth it for me. 

You dont need to have the TV or the phone to have the Cable Broadband and the prices start out at less than Virgins lowest ADSL offerings.

Even forgetting the Cable Broadband they are giving away free Wireless Kits to New ADSL Customers so mabey you could call them up and try pushing for one yourself?
[http://allyours.virginmedia.com/html/internet/noncable.html](http://allyours.virginmedia.com/html/internet/noncable.html)

And the Cable Prices
[http://allyours.virginmedia.com/websales/service.do?id=2](http://allyours.virginmedia.com/websales/service.do?id=2)

---

### Post by Dermot Doyle on 2008-10-01
I hope new posts to oldish threads are still read. If not I'll have to start a new one. Right, round two. I bought the wired router/modem suggested by shifty_powers and the install CD only works with windows so I must manually set it up. My first problem is that the modem doesn't appear anywhere on the computer so I have no idea if it's even there. Troubleshooting suggested I go to the Device manager via Systems, Preferences/ Hardware information, but Hardware information is missing from the Preferences list. What can I do?
It's non appearance could be related to the second problem. Dell mention a J45 ethernet port in their blurb for the Inspiron 1525, but none in the set up guide. I assume they mean the Network connector (which certainly matches the ethernet plug from the new modem). Am I right? Also the Hardware check facility says it has detected a Marvell Technolgy Group Ltd 88E8040 PCI-Fast Ethernet Controller (rev 12), but then asks me if that is right. I have no idea. How do I find out?
That's probably enough for now.
Thanks for any advice in advance.
Dermot

---

### Post by Dermot Doyle on 2008-10-05
Just thought I'd give whatever advice I could on solving this issue in case someone else is in the same boat. I bought the modem as suggested by shifty_powers and it works well. My last problem was that the computer didn't recognise the modem so I couldn't configure it. A friend of a friend came round and configured it according the the instructions using his own computer (he told me it didn't have to run on Linux to configure it) and as soon as I plugged it in I got on the net. He did say that he could have got my computer to recognise the modem, but it was quicker for him to do it on his.
Points worth noting with the Linksys AM200:
The set values for the VPI and the VCI are certainly incorrect as delivered. Change them according to the instructions.
By default the firewall is not enabled. Enable it.
So, thanks again for all the advice

---

