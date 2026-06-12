---
title: "wlan won't connect at boot, dmesg weird"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by dmub82 on 2008-05-16
Using a Belkin F5D7050 v3000 USB wireless adapter that works fine in Hardy with the native rt73usb driver. I was playing around with an alternative rt73 driver (not serialmonkey or the Ralink) that works in monitor mode and enables packet injection for tha aircrack-ng suite.

That also works fine, I just use rmmod and modprobe to swap between the two drivers as needed, and I blacklist the alternative driver to avoid a conflict at boot. Only problem is somewhere along the way I did something causing my wireless connection not to automatically connect at startup.

The connection does work as soon as I open a terminal and do (output included in case that's a clue)

```
d@du804:~$ sudo ifdown wlan0
[sudo] password for d: 
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5012
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:df:1b:b7:40
Sending on   LPF/wlan0/00:1c:df:1b:b7:40
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
d@du804:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:df:1b:b7:40
Sending on   LPF/wlan0/00:1c:df:1b:b7:40
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPOFFER of 192.168.2.2 from 192.168.2.1
DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.2 from 192.168.2.1
bound to 192.168.2.2 -- renewal in 936563229 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.

``` everything works fine. Here's my /etc/network/interfaces, though I'm *pretty* sure it's fine.

```
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
auto wlan0
```

What's puzzling me is my dmesg. Most of it looks normal (to my limited understanding) until this:

```
[   57.238988] Netfilter messages via NETLINK v0.30.
[  167.006433] Inbound IN=wlan0 OUT= MAC=00:1c:df:1b:b7:40:00:1c:df:3b:97:75:08:00 SRC=74.181.76.25 DST=192.168.2.2 LEN=56 TOS=0x00 PREC=0x00 TTL=63 ID=817 DF PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.2.2 DST=74.181.76.25 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=24060 DPT=24060 LEN=109 ] 
[  168.281559] Inbound IN=wlan0 OUT= MAC=00:1c:df:1b:b7:40:00:1c:df:3b:97:75:08:00 SRC=192.168.1.254 DST=192.168.2.2 LEN=56 TOS=0x00 PREC=0x00 TTL=63 ID=0 PROTO=ICMP TYPE=3 CODE=4 [SRC=192.168.2.2 DST=83.233.38.158 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=18801 DF PROTO=TCP INCOMPLETE [8 bytes] ] MTU=1492 
[  168.633283] Inbound IN=wlan0 OUT= MAC=00:1c:df:1b:b7:40:00:1c:df:3b:97:75:08:00 SRC=192.168.1.254 DST=192.168.2.2 LEN=56 TOS=0x00 PREC=0x00 TTL=63 ID=0 PROTO=ICMP TYPE=3 CODE=4 [SRC=192.168.2.2 DST=83.233.38.158 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=18802 DF PROTO=TCP INCOMPLETE [8 bytes] ] MTU=1492 
```

Those "Inbound IN=wlan0..." lines are repeated a few dozen times, with about five or six different IPs I can see in the "DST=XXX.XXX.XXX.XXX" part. They end with:

```
[  256.350995] wlan0: deauthenticate(reason=3)
[  259.996065] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  261.935000] wlan0: Initial auth_alg=0
[  261.935009] wlan0: authenticate with AP 00:1c:df:3b:97:75
[  261.937031] wlan0: RX authentication from 00:1c:df:3b:97:75 (alg=0 transaction=2 status=0)


[  261.937035] wlan0: authenticated
[  261.937039] wlan0: associate with AP 00:1c:df:3b:97:75
[  261.946754] wlan0: RX AssocResp from 00:1c:df:3b:97:75 (capab=0x431 status=0 aid=1)
[  261.946762] wlan0: associated
[  261.946768] wlan0: switched to short barker preamble (BSSID=00:1c:df:3b:97:75)
[  261.949190] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

Then the "Inbound IN=wlan0..." lines start again, repeating until the end of the dmesg. No idea what that stuff is about, I couldn't ID the IPs.

What I can tell:
1) Pretty sure it's not the drivers since it works as soon as I ifdown and ifup; the rt73usb module loaded at boot and rt73 is not, as it should be.
2) It's not the router.
3) I'm pretty sure /etc/network/interfaces is good since I think I made a backup of it from a known good configuration before I did anything that might've changed it and then restored it. wpa_supplicant.conf is also correct.

Wow that was a long post for what I'm sure is a very minor issue. Now state the obvious answer and make me feel stupid!

---

### Post by dmub82 on 2008-05-16
Nothing? I probably should have put this in Networking & Wireless.

---

### Post by pytheas22 on 2008-05-16
Yes, you might get better luck in the networking subforum.  But my suggestion is to just use the serialmonkey drivers.  You should be able to sniff and inject with them on rt73 (I was able to a year ago) as well as connect--in fact I use them instead of the Ubuntu default rt73usb driver, which likes to break at inopportune times.

Where did you find an alternative driver anyway if it's not serialmonkey's or ralink's?

---

### Post by eldragon on 2008-05-16
on this thread, i explain how i got my rt73 wlan to work on my notebook with the latest serialmonkey drivers.
[http://ubuntuforums.org/showthread.php?t=704260&highlight=everex](http://ubuntuforums.org/showthread.php?t=704260&highlight=everex)


involves compiling the module, but it isnt that hard really :D

---

### Post by dmub82 on 2008-05-16
> **pytheas22 said:**
> Yes, you might get better luck in the networking subforum.  But my suggestion is to just use the serialmonkey drivers.  You should be able to sniff and inject with them on rt73 (I was able to a year ago) as well as connect--in fact I use them instead of the Ubuntu default rt73usb driver, which likes to break at inopportune times.

Where did you find an alternative driver anyway if it's not serialmonkey's or ralink's?

Got the driver [here]("http://homepages.tu-darmstadt.de/~p_larbig/wlan/"), linked from the aircrack-ng wiki and forums, it's a fork from serialmonkey. I thought that was necessary for aircrack but I may have misread; I do like that driver because it allows manually setting the bitrate for injection and supports fragmentation attack without patching the kernel (at least that's the way I read it, that stuff about ieee-something vs. mac80whatever stacks really confuses me), I don't know if serialmonkey does that. But now that you mention it, I can get the native rt73usb into monitor mode but I don't know about injection since it doesn't support the iwpriv controls, and "iwpriv rfmontx 1" is how I manually enable injection with the k2wrlz drivers if for some reason I don't just use the airmon-ng script.

You mentioned rt73usb breaking, I haven't really experienced any of that, what's the issue? I was just overjoyed with the rt73usb in Hardy cause it supported my Belkin dongle out of the box, whereas I had to compile the driver from the Ralink source under Gutsy (eventually worked, but intimidating when you have to do that as the first thing you ever try to accomplish in Linux). 

Anyway I'm pretty sure my won't connect at boot issue isn't directly related to the drivers because the correct (for me, at least) native rt73usb driver is properly loading at boot, and as I fuzzily recall, it was still connecting at boot for a little while after I started messing with this other driver. That's kinda just my intuition, but I think somewhere along the way I incidentally did something to disable connection at boot and I'm not sure how. Those dmesg look really odd to me but I can't say if those have changed from before I started experimenting.

Any way to move this thread now that we've gotten deeper into this wireless discussion?

---

### Post by pytheas22 on 2008-05-16
I was always able to get rt73 to inject just by starting aireplay; I didn't have to do anything with iwpriv (I also never had to use airmon, as the card went into monitor mode automatically when airodump started).

rt73usb used to break sometimes when I visited certain websites.  freerice.com is an example--the interface would crash and I would have to reinsert the module to get it to work again.  Occasionally the system would freeze as well when I unloaded the module.  That was in Gutsy, however, and I haven't used my Ralink card since I installed Hardy, as I purchased an Atheros interface.  Maybe it would work better now.

Also, did you think about trying to write a bash script and putting it in /etc/init.d to solve your problem?  Just run ifdown/ifup/dhclient during boot if that's what it takes to get it to connect.

---

### Post by dmub82 on 2008-05-16
/slaps forehead Yeah I really don't know why I haven't just done that yet. Thanks, that should take care of it.

That's really weird about rt73usb crashing on certain web sites, did you ever get an idea of what was going on? Like the site tried to open too many connections or something? If you do have any reason to want to use that card again, I'd recommend giving it a shot in Hardy, this series of drivers does seem much improved now.

Messing around with monitor mode on the rt73usb: My access point and one other in the neighborhood are both on channel 11 (but the other's far enough away that I don't see any interference in normal use). When I load that alternative rt73 driver, I can see both in airodump, but my AP never gets RXQ above 50 or so and I rarely catch any of its data packets and almost none at all from the other associated wireless client in my house; the other AP I see a slow stream of its beacons but no real data. When I try monitor mode with the native rt73usb driver, PWR is doubled, RXQ is a solid 100 and I see vastly more data packets coming from both the AP and the client. But the other AP disappears completely. Still can't tell if injection works with this native driver; I can't manually change the bitrate in monitor mode which was a big factor in getting injection to work with the other driver.

---

### Post by dmub82 on 2008-05-17
I put a little script in /etc/init.d that runs ifdown wlan0, ifup wlan0 and that does the trick, only if I boot when my router isn't on/won't connect for some reason it sits there waiting for an acknowledgment that isn't coming for like 30 seconds; any way to avoid that?

---

### Post by pytheas22 on 2008-05-17
It would probably work to add in a condition along the lines of:
```

if iwlist wlan0 scan | grep your-network-name
then dhclient wlan0
fi
```

then it would only try to connect if it scans and sees your network.

---

### Post by dmub82 on 2008-05-17
Thanks, that probably would work, but I wound up going back to rt73usb. Tried serialmonkey, unsatisfied, deleted the rt73 driver, cleared relevant lines from blacklist, now connects at boot. I've basically satisfied my curiosity with aircrack so I'm going to avoid these hassles and stick with the driver I know works the easiest. Thanks again.

---

### Post by pytheas22 on 2008-05-17
Sorry to hear that serialmonkey was disappointing, but I'm glad that things work properly during boot now.  I guess it was the serialmonkey drivers that were screwing things up after all?

---

### Post by dmub82 on 2008-05-17
From what I can tell, I don't think it was necessarily the alternative drivers (either k2wrlz or serialmonkey) preventing my connection from working at boot. My reasoning is it was something in /etc/modprobe.d/blacklist -- the fact that I had those other drivers on my system required me to blacklist either the rt73usb or the rt73, and something about the blacklisting caused the problem, but it wasn't really the drivers themselves. Deleting the k2wrlz/serialmonkey drivers allowed me to remove those lines from the blacklist, and that made the connect at boot work.

My disappointment with the serialmonkey driver was some similar issues. I couldn't get blacklist right so I had to unplug the stick before rebooting or it would hang and I couldn't get /etc/network/interfaces right so I couldn't control it with ifup/ifdown and had to use Rutilt, which was inconsistent at best. But monitor mode seemed OK, never really got around to testing injection. Just decided it was more trouble than it was worth when I found myself making [lengthy posts]("http://ubuntuforums.org/showthread.php?t=797248") to fix unnecessary problems I could easily avoid.

---

