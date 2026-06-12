---
title: "Connecting to the internet"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by mmm2010 on 2008-06-06
I installed Hardy Heron to my desktop computer, and it won't connect to the internet.  I followed the instructions to [this]("https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html")troubleshooting article, and tried to ping the IP address they gave you.  I was told there were 0% successful packets.  I then ran the second test by typing in ubuntu.com instead of the IP address, and I was told that it could not connect to it.  According to the article, I cannot connect to a DNS sever.

I have Comcast cable internet, which is plugged into a modem, and from the modem to a Belkin router, and then to my computer via ethernet cable.  It works fine on Windows, so I'm thinking it might be my router.  In Ubuntu the network manager shows that I am connected, and when I go to connection information it tells me that it's at 100 Mb/s, but I can't connect to anything.

Attached are the results of me entering "ifconfig eth0," just in case that helps.

---

### Post by iaculallad on 2008-06-06
Try to enable "Roaming Mode" in your network settings. System->Administration->Network. In the "Connections" tab, click on "Wired Connection" and click on Properties, check "Enable Roaming Mode" and click on OK then close.

Open your terminal try to restart network:

```
sudo /etc/init.d/networking restart
```

Then try browsing the net..

---

### Post by cariboo on 2008-06-06
How are you connecting to the internet? Is it through a router or some other type of network?

From your attached text you don't have an ip address. If selecting roaming mode in network manger doesn't help select automatic configuration (DHCP)

Network manager is located in System-->Administration-->Network. Just click the ulock button enter your password and its ready to go. Highlight your connection and click properties.

Jim

---

### Post by mmm2010 on 2008-06-08
It was set to roaming mode automatically, and the automatic configuration didn't work. As I said in my first post, I'm hooked up to the internet with an Ethernet cable that goes through a router.  I don't know if that's the problem or not, because when I had Gutsy installed on my laptop and I needed to download the driver for my wireless card, I could just hook it up to the router and it worked just fine.

Does anyone have any ideas?

(If it doesn't work, I'll try reinstalling Heron and if it still doesn't, I'll try Gutsy.)

---

### Post by maximillian3000 on 2008-06-08
For what it's worth, I also have a comcast cable modem (but maker is arris). I installed ubuntu 8.04 (my very first ubuntu installation from being an xp user) and *wow* it looks great on a 22" lcd!) and am using an asus P5N-E SLI motherboard with Marvell 88E1116 LAN controller. I could not seem to get the net work no matter what i did, until I finally pinned down the following- in admin->network set to roaming mode. Then unplug the coaxial cable from your modem for at least 30 seconds or so and reconnect. After I did this the net came up for me.

---

