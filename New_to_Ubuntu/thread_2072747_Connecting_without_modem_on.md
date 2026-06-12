---
title: "Connecting without modem on"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Nwnighthawk on 2012-10-18
I use century link as provider.  I can connect to ubuntu with out turning router on,, Why?  I am concerned about privacy issues!  Where or what am I connecting to?  Using Dell laptop with wireless modem.  Wireless connection not linked to modem because power to that modem in off.  I live in apt complex where a linux connection registers as poor but does not indicate I am connected.  What's happening here?

---

### Post by audiomick on 2012-10-18
> **Nwnighthawk said:**
> I can connect to ubuntu with out turning router on,...

Can you elaborate on that a little more? Do you mean that when you open your web browser, you can get to the Ubuntu web site, or something else?

---

### Post by Cheesemill on 2012-10-18
Sounds like you are using someone else's Wi-Fi connection.

Depending on which country you live in this may be illegal.
Either way it is definitely a bad idea from a security point of view.

---

### Post by Nwnighthawk on 2012-10-18
Normally when I want to go to the internet I turn on wireless modem, boot Dell laptop and choose between using Windows Explorer or ubuntu and proceed to email account or what ever.  The other day I wanted to check email fast and booted and if I don't choose it automaticly takes me to ubuntu.  I choose email account and read and answered and turned off the computer, I then noticed that the century link modem was not on.  I rebooted and went back to ubuntu with out the modem on.  And the wireless connection in the lap top only showed modems that were available but not connected to.  There was a funny little red check on a linux connection and read poor but did not say I was connected.  I turned on the wireless modem and in a few minutes my laptop showed my correct connection.  So the mistery still continues...who am I connecting to and how about my privacy.  There are 25 apartments here in this area as well as several homes this is a city in Oregon, USA.  Thanks for help!

---

### Post by audiomick on 2012-10-18
I think cheesemill is right. Someone in the block has probably got a WiFi going with no password on it. Your computer is finding it and logging in. 

I think it is possible in the network manager somewhere to turn off the function that looks for an available Wifi and connects automatically, but I am not sure. Also, if you do that, you might also have to connect your own WiFi manually. You'll have to look at that yourself, I am not too sure about it.

As far as security goes: you don't need to panic, but if you can get into whichever network it is, then so can probably anyone else who wants to, and once in the net there are ways to look for other computers on the same net and try and look in them. It is probably a good idea not to use whatever connection it is.

---

### Post by Lisiano on 2012-10-18
Generally, Ubuntu won't try to connect to an unknown network it never saw before, maybe it's connecting automatically to a nearby coffee shop or the likes, which you have visited or which has the same name as another hotspot you've been on. Also, a picture can tell a million words so could you post a screenshot of your networking menu with your modem off?

---

### Post by newb85 on 2012-10-18
Click "Edit Connections..." in the networking menu and go to the Wireless tab to see which networks are set up to connect automatically.  

Ubuntu shouldn't just connect to random unprotected networks without you telling it to.  However, if you had previously connected to an unprotected network with a common name (linksys, for example) and are now in range of a different unprotected network with the same name, it won't know the difference.

---

### Post by newb85 on 2012-10-18
> **Cheesemill said:**
> Depending on which country you live in this may be illegal.

CenturyLink is a U.S. provider.  As I understand it, it's not illegal in the U.S. to use someone else's unprotected network, as long as you don't add repeaters.

But no, it's not a good idea from a security standpoint.

*Note: I'm not a lawyer, and none of the above should be taken as legal advice.*

---

### Post by Cheesemill on 2012-10-18
I believe that in the US this falls under 'Theft of Services', so yes, it is illegal.

*I'm not a lawyer either but I did a fair bit of research into the subject some years ago.*

---

### Post by Lisiano on 2012-10-18
In my country, Estonia, usage of unprotected networks (linksys, etc) is equivalent to usage of public hotspots (Free-WiFi, Airport, CoffeeShop).

*Also not a lawyer, this might or might not be true in any other country.*

If anything happens, you could just say "It was an open network, so my laptop did it itself."

*Might or might not work in the court of law, but will work on any(*) human.*

---

