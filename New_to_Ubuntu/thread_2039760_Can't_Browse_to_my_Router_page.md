---
title: "Can't Browse to my Router page"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-08-09
Hi,     I have a dual-HD system, one HD w/ W-XP, the other w/ Ubuntu 11.10.  But my Windows HD seems to be dying.  While it was working, I set up a new DSL router, & accessed its settings by entering an address in my Firefox Browser.  It's all numbers and dots, like:  ###.###.#.#.   Is this what's called an IP address?

Anyway, I could access it w/ Firefox in Windows, but now that I've been only able to use my Oneiric system, I can't open it.  Firefox opens all other webpages just fine.  But when I enter the one for my router, it says "Connecting" for a long time, but never does.

Luckily, I did enough setup for the router to be working!  But is there a way to access that address in Ubuntu?

Thanks!   :)

---

### Post by papibe on 2012-08-09
Hi BlueAZ.

What error do you get when trying to open the router's page from Ubuntu?

Could you post the result of this commands?
```
route -n
```
Regards.

---

### Post by NikTh on 2012-08-09
Hi , 
you can see the correct address for router , by right click on network-manager (icon up left) and then click on "Connection Information" . Router's page  address is "Default Route". 

Also , try to connect in page , via cable. (ethernet)
Thanks

---

### Post by andox on 2012-08-09
I don't know if it's much help but try typing in the http:// in the address bar. IE, my router usually just takes 192.168.1.1 in the address bar, but every so often I have to type in [http://192.168.1.1](http://192.168.1.1)

---

### Post by jockyburns on 2012-08-09
I used to be able to access my router page by simply typing [www.routerlogin.com](www.routerlogin.com). Since then I now have a VM Superhub and it's address is 192.168.0.1 Just by typing in that IP address I access the login page (without the http:// )

---

### Post by ajgreeny on 2012-08-09
Are you actually connected to the router; can you browse the internet?

On the assumption that you can, and are therefore connected to it, have a look on the manufacturer's label on the back or under the router where it will tell you the IP address.

It is, as others have said most often **192.168.0.1** or **192.168.1.1**, but that is not always so, so look at labels, router documentation etc etc and I'm sure you'll find it.

---

### Post by sid0972 on 2012-08-09
try routerlogin.net instead of routerlogin.com

---

### Post by BlueAZ on 2012-08-10
> **papibe said:**
> Hi BlueAZ.

What error do you get when trying to open the router's page from Ubuntu?

Could you post the result of this commands?
```
route -n
```
Regards.
Hi, In Terminal, I ran 'route -n' and got this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         67.40.227.238   0.0.0.0         UG    0      0        0 ppp0
67.40.227.238   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0

I have tried both the 67.40 one (it just immediately says it can't connect) and the 169.254 one -- it does the same thing as the original 192.168 one I used in Windows, just keeps saying it's connecting, but never does.

I have Firestarter firewall, but it says it's disabled because eth0 isn't ready...

Thanks.

---

### Post by papibe on 2012-08-10
Thanks.

It looks that you are not using a router, but a modem instead.

If you do have a router, my guess is that you are not connecting the cables correctly (you are getting both a ppp connection and a directly IP from your ISP).

Regards.

---

### Post by BlueAZ on 2012-08-10
Oops, guess I used the wrong word.  It's a Motorola 3347 modem that's also a wireless router, connected to Century Link DSL.  I'm pretty sure all cables are run correctly.  It connects to the internet & does everything fine except open its own settings page.  And it did that fine in Windows XP (RIP).   But I am also having trouble connecting wirelessly with my netbook...

If it's the settings, how can I fix this?

P.S.  Love yr dog!      Thanks!

---

### Post by blueshead on 2012-08-10
Try This

```
192.168.1.254

user ID = admin

Password = serial number of your router unit 
```

---

### Post by papibe on 2012-08-10
For what I can tell, your device is a router/modem. Right now it seems to be in bridge mode.

I found a lot of references on how to bridge it, but none on how to set it back to router mode. 

I would advice you to request support from your ISP since that feature is not well documented.

Regards.

---

### Post by BlueAZ on 2012-08-11
Thanks for all the tips & ideas!  But I'm still having the problem.

To recap:  I had no problem accessing this 192.168...  address in my Windows XP Hardrive, using the latest version of Firefox.  I only have the problem in Ubuntu 11.10, also with the latest Firefox.  So it must be a setting in Ubuntu.  My W-XP drive has died, so I'm completely dependent on Ubuntu now.

If I call the ISP, they'll ask what OS I'm using, & when I say Ubuntu, they won't be able to help me.

So far, I haven't been able to access any sites with just numbers, even if I preface with http:/ or any variant of that.  Is there a sure-fire address I could try?  I'm able to access all other websites, just not the ##'d ones.

Thanks mucho!

---

### Post by steeldriver on 2012-08-11
Like papibe said, you have a non-standard setup there - typically your ISP would give you a public IP that is part of their network address range (67.40.227.238 would be qwest) but that would only be visible on the WAN (upstream) side of your router. The router would then do *address translation* (NAT) and hand out IP addresses from a private *LAN pool*, typically by default 192.168.x.x in consumer grade routers. The fact that you are getting 67.40.227.238 on the LAN side (as well as the connection name 'ppp0') suggests you are not behind a NAT (router) but are connecting directly to a DSL modem

[The only exception I can think to that is if someone manually configured the LAN pool of the router to be in the 67.40.x.y address range for some reason]

The problem with that is the device's management interface is almost certainly in the 192.168.x.x address range - you simply will not be able to connect to that if your host interface / gateway is 67.40.x.x because the 2 subnets are distinct

You *may* be able to connect to the management interface if you set up a temporary connection (via Network Manager applet or /etc/network/interfaces if you prefer) with a static IP in the 192.168.x.y address range

OTOH if you are sure you have a regular router setup then you need to figure out why you are getting a modem (ppp) connection and why "eth0 is not ready"

---

### Post by BlueAZ on 2012-08-11
Sorry, forgot to repeat: This IS a DSL modem/router.  I did set it all up in Windows XP with ISP phone guidance and could access it perfectly.  It is only since my W-XP drive has failed, & I'm trying to access it in Ubuntu 11.10 that I have this problem.

---

### Post by sffvba[e0rt on 2012-08-11
Are you using a static IP in the same range as the device?


404

---

### Post by marlow59 on 2012-08-11
Did you try to connect to the setup page after connecting through ethernet(the cable) ?

---

### Post by BlueAZ on 2012-08-12
> **not found said:**
> Are you using a static IP in the same range as the device?


404
I have no idea...  What does this mean?  I'm on Century Link DSL, so I'm going with whatever they set up.  I got the Motorola 3347 Modem/router at a yard sale, so it had somebody else's settings at first.  When I could access those setting thru Windows, I changed everything as instructed by a Century Link tech person.

---

### Post by sffvba[e0rt on 2012-08-12
> **BlueAZ said:**
> I have no idea...  What does this mean?  I'm on Century Link DSL, so I'm going with whatever they set up.  I got the Motorola 3347 Modem/router at a yard sale, so it had somebody else's settings at first.  When I could access those setting thru Windows, I changed everything as instructed by a Century Link tech person.

Have a look a this [blog post]("http://www.sureshpw.com/2012/04/static-ip-address-under-ubuntu-1110.html"). 

If you go to **Settings->Network->Your-Network-Connection->Configure->IPV4 Settings **as mentioned and shown you can specify what IP address you would like your system to use.

Typically to access a router/modem's interface you need to be on the same sub-net as the device.

As I don't know what IP you are trying to use I will substitute a different one to illustrate:

Router/modem IP - 192.168.1.1
Change Ubuntu to - 192.168.1.**50** (anything from 2 to 255 should work) (also it is important that the first 3 number pairs are identical to the one you use for the router/modem)
Ubuntu subnet mask - 255.255.255.0

**NOTE: Before making any changes write down the values as they where before.  I am pretty sure your IP is set to automatically getting an IP using DHCP so when you are done you want to revert back to these settings to be able to connect to the Internet.**

Hope that helps.


404

---

### Post by BlueAZ on 2012-08-12
Thanks!  I think I found the problem...  It's me!  As usual, I made a mistake trying to do manual setup.  I set up 'DSL Connection 1', but my system had already set up for my current modem/router as 'Wired Connection 1'.   Now that I've switched to using 'Wired Conn. 1', I can access the modem's settings, and all other websites.
Sorry...   Hope maybe this helps someone else!  And thanks again!

---

### Post by sffvba[e0rt on 2012-08-12
:) glad you got sorted.


404

---

