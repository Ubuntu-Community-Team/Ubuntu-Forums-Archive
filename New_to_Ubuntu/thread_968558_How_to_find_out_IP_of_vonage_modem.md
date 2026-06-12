---
title: "How to find out IP of vonage modem"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by TJCIB on 2008-11-02
Hi, this isn't really Ubuntu related, but I'm using Ubuntu =)

I have a Motorola VT1005 modem for vonage.

I cannot remember the IP address I manually gave to the thing about 2 years ago.  How can I figure it out.  It is not set as a DHCP server, so the computer doesn't get an address from it when I plug in.

There is NO reset button to set it back to factory settings (stupid huh).

Any ideas?

---

### Post by handydan918 on 2008-11-02
> "I have no fear of drowning its the breathing that's taking all the work." - Jars of Clay 

After living half a century, I think I can relate.


Are you talking about the internal ip of the device? You describe it as a modem, but google shows it a s a router in several places.

To find out what the public ip is try [http://checkmyip.com/]("http://checkmyip.com/")

---

### Post by TJCIB on 2008-11-02
yes, i got my public IP.

I need the internal LAN address.  Sorry for not being more specific, and yes, it is a router (i call it a modem for my wife, she only knows that term).

I tried plugging it into a Windows box and it gives me some strange "Private Network" thing.  It doesn't assign an IP because it's not a DHCP server, so I don't know what the default gateway would be to connect to to access its gui config.

---

### Post by TJCIB on 2008-11-02
oh yeah,

There is a MAC ID printed with the serial number on the bottem.

Is there any way I can ping/scan a specific MAC instead of an IP address?

---

### Post by handydan918 on 2008-11-02
> **TJCIB said:**
> oh yeah,

There is a MAC ID printed with the serial number on the bottem.

Is there any way I can ping/scan a specific MAC instead of an IP address?

Okay, a little more info helps a lot,
If yo want to scan your network, you can use nmap at the command line.

Howeveer, if you can give us 2 crucial pieces of info, it may help.
1) What is the make and model of your router,,,
2) What is the internal ip of  your network. 

i.e., 192.168.1.x
or 192.168.0.x

or 10.0.0.x


etc...

---

### Post by TJCIB on 2008-11-02
Well it gets complicated.  I don't use the Vonage router for routing, i HAD a separate router for that.  It got struck my lightning today, which is why I'm trying to get the Vonage router going.


Here was the info for our network as it was, and the vonage router should fall in this somewhere (i know its not standard protocol either):

IP: 10.1.1.x
Subnet: 255.255.255.0
Gateway: 10.1.1.1

The router I am trying to into is a Motorola VT1005

---

### Post by handydan918 on 2008-11-02
This kind of thing is very difficult to  do via telepathy, Not knowing what your physical topography is, or little details like what you physical topography WAS before the lightning strike...

Seriously.

You could write a 20000 word document and not describe all the possible variables in this scenario.

---

### Post by TJCIB on 2008-11-02
serves me right for not writing it down...

i appreciate the effort...

I'll keep messing around until I break this thing.

---

### Post by Kellemora on 2008-11-03
Hi TJ

The IP to get into the Set-Up is 192.168.102.1

It's also a good idea to have Tech Support FORCE your UDP Port to something like 5062 also.

You do know that you have to turn on the Motorola and WAIT 2 FULL MINUTES, before booting up the computer so it finds the internal IP number I hope.

Here is a link to the [Full Service Manual]("http://74.125.45.104/search?q=cache:Gu4zVDby9R0J:www.bizsyscon.com/tech_doc/MOTOROLA_VT1005.pdf+Motorola+VT1005+internal+IP&hl=en&ct=clnk&cd=7&gl=us&client=firefox-a") for your VT1000v series.

Hope the link still works, it's old.

TTUL
Gary

---

