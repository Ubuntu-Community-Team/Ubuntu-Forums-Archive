---
title: "[SOLVED] Wireless not working, Help!"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-10-17
Hi All

My internet was acting up on me earlier, so i tried to disable the wireless adapter and then re enable it (ala windows repair connections), but it seems that that I am unable to turn re enable it.  I went to the docs, and it told me to check and see if the wireless is turned on, with lshw, so when I ran
```
sudo lshw -C network
```
it says wireless = radio off for eth0, eth1 seems to be my ethernet port, and needless to say, I have no internet, help!!

---

### Post by Bucky Ball on 2008-10-17
Could you post the results of:

**iwconfig**

... and 

**lspci**

please. This might be difficult without network so wlan0 is your wireless and eth0 is your hardwire connection. If wlan0 shows as happening, you may just need to fill in your ESSID and security details for you router (LAN) in System->Administration->Network. :)

---

### Post by rideburton56 on 2008-10-17
I actually just typed our all of iwconfig and then i got a page error, so I am going to try the essid thing first

---

### Post by rideburton56 on 2008-10-17
grr no luck, bear with me for a minute i am going to type it over again

---

### Post by rideburton56 on 2008-10-17
iwconfig:
lo
no wireless extensions
eth0
no wireless extensions
eth1
radio off ESSID:""
Mode: Managed Freqency 2.437 Ghz Access Point Not-Accociated
Bit Rate 0 Tx-power off sensitivity=8/0
retry limit 7 rts thr off fragment thr off
power management on
link quality 0 signal level 0 noise level 0
rx invalid nwid 0 rx invalid crypt 0 rx invalid frag 0
tx excessive retries 0 invalid misc 3 missed beacon 0

---

### Post by Bucky Ball on 2008-10-17
Did it give a result for wlan0 in iwconfig? That is the important bit. That should say whether your card is up and recognised.

If you run

**lspci**

the important part is to find what wireless card you have exactly, then you can work from there.

UPDATE: You beat me to it! lol Okay, you need to know whether you require security for your router. WPA or WEP security is the norm. And of course the ESSID.

---

### Post by rideburton56 on 2008-10-17
no sercurity on my router, and yes I do know the essid (name of the network, right?

---

### Post by rideburton56 on 2008-10-17
lspci (reduced to pertinent line)

02:01.0 Network Controller:interl corporation pro/wireless 2200bg network connection (rev 05)

---

### Post by rideburton56 on 2008-10-17
and no, iwconfig i copied in its entirety

---

### Post by rideburton56 on 2008-10-17
OMG....
so i was getting mad at my little box and i jsut cold rebooted and hit the buttons that i used to hit in windows to shut on and off the wireless, and this time it worked, so now i have internet.... now im REALLY CONFUSED.

But.. problem solved :)

---

### Post by Bucky Ball on 2008-10-17
Too cool. Maybe all will be revealed down the track. :)

BTW, your hardwire or wireless is up?

For the wireless, try this:

[http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)

I found it by putting the model of your card followed by 'hardy' in a search engine. :)

---

### Post by rideburton56 on 2008-10-17
Thanks for the research, i guess the driver that allows me to turn the wireless signal on and off with Function F2 is just iffy, it definitely turned it off, and i pressed it a bunch of times afterwards, but just after that cold reboot it turned it back on again.  Again, thanks so much for the time!

---

