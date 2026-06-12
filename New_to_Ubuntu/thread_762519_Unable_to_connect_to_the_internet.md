---
title: "Unable to connect to the internet"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by faytaliti on 2008-04-22
I have an Intel v Pro on board LAN card and I use an ADSL connection.
It's a 2Mbps connection. Also I have a Huawei ADSL router with Ethernet and wi-fi support. But I use only the the Ethernet connection. I am able to get high speed connectivity on windows vista but the connection does not seem to be working on Gutsy. Any solutions :confused:?

---

### Post by PriceChild on 2008-04-22
Turn the machine off, and unplug it from the mains & take battery out if its a laptop. Leave it a minute and then plug it all back in and boot Ubuntu.

Xp on my other machine is very evil about not letting go of the ethernet card.

---

### Post by faytaliti on 2008-04-22
I tried that but it is no use. :confused:

---

### Post by aeiah on 2008-04-22
what are you using to test the speed? perhaps you should test downloading the ubuntu iso or go to speedtest and see if its actually a speed issue, or do you mean you arent getting 100/1000mbit LAN connectivity?

---

### Post by alexandremrj on 2008-04-22
Hello,

I had a similar problem with my ADSL connection. My connection didn't like very much that the ethernet was in roaming mode, it only wanted Automatic configuration (DHCP).

To check the mode of your connection go to:
System --> Administration --> Network. Select your connection and click on Properties.
Play with roaming mode and DHCP.

P.S: I had a router doing the connection to the ADSL line so I didn't need to enter my username and password. If you need to do that in Windows Vista then you will also need that in Ubuntu (place a post if you need that help).

Hope it helped

Alex

---

### Post by russo.mic on 2008-04-22
> **PriceChild said:**
> Turn the machine off, and unplug it from the mains & take battery out if its a laptop. Leave it a minute and then plug it all back in and boot Ubuntu.

Xp on my other machine is very evil about not letting go of the ethernet card.

I can't imagine how XP could "hold" the ethernet card after it's been shutdown and linux has been booted.  Like, some buffer on the card or something?  Could I inquire as to an explanation?

Thanks!

Russo

---

### Post by faytaliti on 2008-04-22
Firstly even my router configuration page isn't being displayed when I type [http://192.168.1.1/](http://192.168.1.1/) in my address bar. This probably means that my Ethernet card is not connected to my router. The problem must be clear now.[]("http://192.168.1.1/")

---

### Post by PriceChild on 2008-04-22
> **russo.mic said:**
> I can't imagine how XP could "hold" the ethernet card after it's been shutdown and linux has been booted.  Like, some buffer on the card or something?  Could I inquire as to an explanation?

Thanks!

RussoHappens with my old webcam too, gets initialised, firmware loaded, but unless it loses power, windows' control over it isn't lost.

---

### Post by Trandre on 2010-03-14
Have you tried to restart your router?

Are you able to ping your router?

And can you checked if there are lights(red and green) turned on, where the cables go into your machine?

Trandre

---

### Post by unknowndude on 2010-03-14
is networking enabled in your computer?check that first

---

