---
title: "How to set up the wi-fi using a wired Ethernet cable?"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by amityadav9314 on 2012-04-17
Hi,
I am using Ubuntu and need to set up the wi-fi. My current internet connection is via a wired ethernet cable **without a Modem**. But in almost all the cases of setting up process they say,"Connect the wire from the modem to the router.", while setting up the router. So in my case where I dont have a modem, so do I just need to connect my ethernet wire to the router while setting up?
Secondly , will all the settings will be lost when the router will be rebooted?

---

### Post by roger_1960 on 2012-04-17
Hi

What is at the other end of your ethernet cable?  They have a limited maximum length.

---

### Post by grahammechanical on 2012-04-17
Who says this?

> But in almost all the cases of setting up process they say,"Connect the wire from the modem to the router.",

When you load Ubuntu do you see a network icon on the right of the top panel?

It should be between the mail icon and the sound icon.

What does the network icon look like? When we are connected by ethernet cable it will look like two arrows going in opposite directions.

Click on the icon. Do you see a list of wireless networks that are in range? Is you wireless network in the list?

By the way, there are different set ups.

Modem/router (I have this) or Modem + router/hub.

I am guessing that your router is also a modem. I also was confused about this when I first brought a broadband router/modem/hub.

If you are seeing wireless networks in the list that network manager gives you, then Ubuntu is recognising your wireless card and is using a driver for it.

You just now need to follow the directions for connecting to the router/modem by wireless.

Remember, you will need to enter a password. This is not our login password but the pass phrase or wireless key needed to access the router/modem. You should have all the necessary information in a guide that came with the router/modem or you may find it on a label stuck on the bottom of the modem/router.

Different setups

Computer wireless card > wireless modem > telephone line.

Computer wireless card > wireless router/hub > ethernet cable > modem > telephone line.

Computer ethernet card > ethernet cable > modem > telephone line.


Regards.

---

### Post by I2k4 on 2012-04-18
> **amityadav9314 said:**
> Hi,
I am using Ubuntu and need to set up the wi-fi. My current internet connection is via a wired ethernet cable **without a Modem**. But in almost all the cases of setting up process they say,"Connect the wire from the modem to the router.", while setting up the router. So in my case where I dont have a modem, so do I just need to connect my ethernet wire to the router while setting up?
Secondly , will all the settings will be lost when the router will be rebooted?

I think this user ought to describe exactly what hardware is being used.  There are modems, routers, modem/router combinations - I  couldn't make heads or tails.  Normally, to _set up_ a modem or modem/router by going into its internal settings you do that via the ethernet.  

Once the modem/router set up to _broadcast_ wi-fi, and the user knows the SSID and the encryption passphrase or code, the user disconnects the ethernet and switches on the laptop wi-fi receiver.  The laptop will identify the SSID and, and you take steps to log in from there.  That is the normal procedure.

---

### Post by MartyBuntu on 2012-04-18
> **amityadav9314 said:**
> So in my case where I dont have a modem...

Are you on a school network?

---

