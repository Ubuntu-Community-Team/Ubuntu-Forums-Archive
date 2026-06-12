---
title: "Strange change of MAC address"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-11-13
Dear All,
Recently I am facing a strange problem of machine MAC address being reset to some strange value. (Please see my previous post on this, [http://ubuntuforums.org/showthread.php?t=1873116](http://ubuntuforums.org/showthread.php?t=1873116), I am yet to receive a response). Problem like this never happened before.

After a reboot, machine MAC address changes to aa:00:04:00:0a:04, where the actual MAC address (00:14:22:50:78:71) of my Ethernet card is far from this. This is also frustrating since my service provider authenticates connections based MAC address and you get disconnected from Internet if your MAC address changes.

After some hours of exasperation, the situation got remedied by setting the cloned MAC address (originally empty) in Edit Connections which is the same as the actual one. See the attached image. But this solution does not persist since after a reboot, the MAC address changes again irrespective of the set value in Edit Connections. Both the correct values are there, as you see in the image, but /sbin/ifconfig shows the incorrect value of aa:00:04:00:0a:04. To get out of the situation, I have to delete a digit from the MAC address in Edit Connections, put it back again, click Save, and the click Enable Networking twice in sequence (disable then enable). 

Here is my /etc/network/interfaces file
```
auto lo
iface lo inet loopback

```
I tried setting hwaddress in this file, without any avail.

So, my machine IP is being set in networking-manager. 

Since the changed MAC remained the same at every reboot, I suspect that this was hard coded somewhere. And I would like to find out where this was/is coming from.

Any suggestion will be highly appreciated.

---

### Post by jasmin123 on 2011-11-13
Hi ,you must change mac adress in the terminal 
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 00:00:00:00:00:00

sudo ifconfig wlan0 wit this code you looking your mac if is changed you can setup conenction

---

### Post by mmasroorali on 2011-11-13
> **jasmin123 said:**
> Hi ,you must change mac adress in the terminal 
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 00:00:00:00:00:00

sudo ifconfig wlan0 wit this code you looking your mac if is changed you can setup conenction

But does not this provide only a temporary solution? I am looking for something permanent. And I want to find the reason behind the change.

---

### Post by bkratz on 2011-11-14
> **mmasroorali said:**
> But does not this provide only a temporary solution? I am looking for something permanent. And I want to find the reason behind the change.



Two things come to mind, ( I am in a motel and have to do the same thing). First, I have to do it every boot, so I just leave it on ( not much help!) Secondly, if you want to do it as described, the correct version would be 

sudo ifconfig eth0 down hw ether xx:xx:xx:xx:xx:xx
sudo ifconfig eth0 up

Since this is a wired connection, not a wireless.

---

### Post by aeiah on 2011-11-14
just put it in a startup script, perhaps? one that runs as root, so you don't need sudo.

there's probably network startup commands in one of the /etc/init.d/ scripts - you could put it in there.

alternatively, you could put the commands in /etc/rc.local

---

### Post by mmasroorali on 2011-11-14
Thanks to all those who responded with the remedial solutions. Still I would like to know the reason behind the change. Any suggestion, however remote, will be appreciated.

---

### Post by soltysh on 2012-01-16
I've just encountered the same problem, after googling around I found your post, unfortunately without answer :(. Yet [here]("http://www.fantaghost.com/2010/06/eth0-mac-address-fixed-on-aa0004000a04/") you'll find answer to your question, the problem is with DECNet libraries. Just remove libdnet, libdnet-dev, dnet-common reboot and you'll be fine. I just checked - working :)

---

