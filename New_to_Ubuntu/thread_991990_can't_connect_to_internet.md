---
title: "can't connect to internet"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by faim2600 on 2008-11-24
Ok so i've been troubleshooting for about an hour now with no success.  I'm pretty sure i haven't tried everything or even close but i am getting really frustrated and don't know what i'm doing!!!

i'm trying to use my wireless connection.  i have a pc that is using the wired connection, if thats relevant.

that is what i'm using the internet on now.  i cant seem to figure out the username or passcode, or whatever it is i would need to log in on ubuntu (i don't even know the difference between wep 128 bit passphrase and all the others)

i am 90% sure its the access code on the bottom of the modem, but when i try it on my laptop it doesn't seem to work.

basically i really could use the advice of an informed ubuntu user:

i'm very tired of having these internet issues, i am willing to troubleshoot a bit to avoid use of windows, but is there anyway for it to automatically identify networks so i can use wi fi i don't necessarily know the name of the network of??  because if not, i think i may want to just switch back to windows for now for convenience, i often only have a few minutes to get online and this is getting quite frustrating!!!

thanks for all advice.


edit: i was thinking maybe i could do some troubleshooting on the laptop if i connected it to the internet manually but i'm not even sure which cord to use or if that would solve the real problem of wireless connectivity.

---

### Post by superprash2003 on 2008-11-24
ok , first lets see if ubuntu has recognized your card, go to the terminal and type the following commands and post their output here
1)iwconfig
2)lshw -C network

---

### Post by faim2600 on 2008-11-24
ok so i cant copy and paste and am unsure which is most important, or if all info is equally important but ill be on the safe side and just type it all out

insidious@insidious:-$iwconfig
lo no wireless extensions
eth0 no wireless extensions
eth1 unassociated essid:off/any
mode: managed Frequency=nan khz acces point: not-associated
bit rate: 0 kb/s  tx-pwer:16 dbm
retry limit: 15 rts thr:off fragment thr:off
power management:off
link quality:0 signal level: 0 noise level: 0
rx invalid nwid:o rx invalid crypt: 0
tx excessive retries:0 invallid misc: 475 missed beacon:0

lshw -C network
Warning: you should run this program as super-user.
*-network
description: Ethernet interface
product: 88e8036 pci-e fast ethernet controller
vendor: marvell technology group ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 16
serial: 00:13:a9:80:d7:54
width: 64 bits
clock: 33mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=n/a latency=0 module=sky2 multicast=yes
*-network
description: wireless interface
product:pro/wireless 3945abg network connection
vendor: intel corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: eth1
version: 02
serial: 00:19:d2:60:2d:d5
width: 32 bits
clock: 33mhz
capabilities: bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=ipw3945 driverversion-1.2.2mp.ubuntu1firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated

phew, that was a lot of technical typing hope this gets us closer to a resolution!

---

### Post by razy60 on 2008-11-24
Which wireless router is it, i.e Belkin,Netgear,BThomehub ?
Do you know the ip adress of the router? so that you can get into it to see if it has the wireless activated?
Who set up the wireless router you or someone else?
I am assuming you have enabled wireless in network manager. if so you should be able to ask it to scan for available networks.

---

### Post by faim2600 on 2008-11-24
its a siemens speedstream 4100.

on this pc theres been an unresolved issue of approximately every 3-10 minutes the connect to the internet dialog will open even though the internet is connected.  until you exit that dialog, the internet will be perma-loading.  once closed, everything works again.

anyways i say this because when i went to my ip adress for configuration that dialog pops up, so i am unsure what to do.  

someone else set up the wireless, and claims to have forgotten any pertinent info haha so i'm basically in the dark as far as that goes... 

are you referrring to network settings on ubuntu?  i have both wireless and wired enabled.

on windows im not sure where to even find wirelss settings but under network connections "broadband connection" is listed under disconnected.

---

### Post by razy60 on 2008-11-24
Hate to say this but does that router actually have wireless ability it looks more like a nonwireless modem, there is no wireless light or indicator only 1 Ethernet connector,(just googled it):(

---

### Post by halitech on 2008-11-24
I found the same thing ( [http://gigaset.com/shc/0,1935,hq_en_0_141386_rarnrnrnrn_variation%253A-5_pageType%253ATechnical%2Bdata_imagePos%253A0,00.html#content](http://gigaset.com/shc/0,1935,hq_en_0_141386_rarnrnrnrn_variation%253A-5_pageType%253ATechnical%2Bdata_imagePos%253A0,00.html#content) )

maybe they have a wireless router plugged into it?

---

### Post by faim2600 on 2008-11-24
i have a router too.  linksys broadband router wireless-g 2.4 ghz

---

### Post by razy60 on 2008-11-24
> i have a router too. linksys broadband router wireless-g 2.4 ghz 
In that case is the linksys a modem router or wireless only if its a modem router and the modem is active you will get conflicts with the siemens modem, can you get into the liksys by typing 192.168.0.1 or something close sometimes 1.1 or1.0 at the end, type that  into youadress bar of your internet explorer

---

### Post by faim2600 on 2008-11-24
yes i can this time it worked... just needed to know if it worked or is there info i should copy and paste?

---

### Post by razy60 on 2008-11-24
No you just need to get into the router and ensure the wireless is on and that you have set the security to whichever is best for you. 64 0r 128 wep or wpa, basically wpa is better than wep and 128 is better than 64 in both cases the passwords/codes you set will be more complex in the better settings.

---

### Post by faim2600 on 2008-11-24
well it is working now!  at least for now.... thanks for all the help!!!!

---

