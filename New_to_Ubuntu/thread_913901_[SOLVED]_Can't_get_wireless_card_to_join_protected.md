---
title: "[SOLVED] Can't get wireless card to join protected networks"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by njd4k on 2008-09-08
**My problem**: I can't get my wireless card to connect to an encrypted Internet connection. I've been posting about this in the Wireless forum, but I haven't been getting any responses, perhaps because I am a noob and the answer "should" be obvious. It isn't to me.

**What I have**: A laptop running 64-bit Hardy with a Dell wireless card. More specifically, using a command I found in another forum:
```
nic@nic-laptop:~$ lspci | grep Broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```
[B]
What I have tried[/B]:
-- when I try to connect using the GUI, it tries for a very long time and then redisplays the GUI interface.
-- unencrypted networks work very well
-- I set up my home network to switch from WPA to WEP and remove a special character from the network name. This didn't change the problem.
-- I tried connecting while running off the 32-bit Ubuntu Hardy install CD in case this was a 64-bit problem. Didn't work.
-- I tried to connect using this set of commands from the terminal:
```
iwconfig wlan0 essid [networkname]
iwconfig wlan0 key restricted [password]
iwconfig wlan0 mode managed
dhclient wlan0
```

But received this error:
```
nic@nic-laptop:~$ iwconfig wlan0 essid [networkname]
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
```

-- I enabled third-party repositories in case my driver was out of date, did apt-get update, and installed the updates. Didn't work.


What else can I try? I've already switched back to using Windows as my main operating system and coming to terms with the idea that Ubuntu might be nothing but a toy until my next computer purchase. I feel bad asking for so much help from these forums, but I don't understand Ubuntu well enough to help others yet...

---

### Post by rlzyoner on 2008-09-08
Run the commands as root
That error means that you do not have permission to execute the commands so prepending sudo will work

---

### Post by njd4k on 2008-09-08
Prepending with sudo gets rid of the error message (is that all that means?) but it doesn't result in an Internet connection.

---

### Post by MegaJim on 2008-09-08
Something to try to get more information about what is happening, is to open up the system log viewer (alt+f2, type gnome-system-log and hit enter).  When you try to initiate the connection watch for messages in syslog, kern.log and debug.

---

### Post by vikram on 2008-09-08
I managed to get my Dell laptop with the same or similar wireless card working so I'm pretty sure its possible. 

This is what I used 

ndiswrapper + windoze driver instead of native driver 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and to configure the connection using WPA

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

---

### Post by njd4k on 2008-09-08
> **MegaJim said:**
> Something to try to get more information about what is happening, is to open up the system log viewer (alt+f2, type gnome-system-log and hit enter).  When you try to initiate the connection watch for messages in syslog, kern.log and debug.

I tried this -- thanks for the idea. The relevant errors (I suspect) look like this:

```
Sep  8 19:04:03 nic-laptop kernel: [  267.168401] wlan0: no IPv6 routers present
Sep  8 19:04:34 nic-laptop kernel: [  267.803829] b43-phy0 debug: Using hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
```

I don't knoww what this means though.

Just to put more information up, the **debug **log said:

```
Sep  8 19:02:32 nic-laptop NetworkManager: <debug> [1220914952.733984] real_act_stage4_ip_config_timeout(): Activation (wlan0/wireless): could not get IP configuration info for 'jandd', asking for new key. 
Sep  8 19:02:32 nic-laptop kernel: [  262.399416] wlan0: deauthenticate(reason=3)
Sep  8 19:02:32 nic-laptop kernel: [  262.417437] b43-phy0 debug: Disabling hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
Sep  8 19:03:52 nic-laptop kernel: [  265.848104] wlan0: Initial auth_alg=0
Sep  8 19:03:52 nic-laptop kernel: [  265.848114] wlan0: authenticate with AP 00:1b:11:71:e1:ee
Sep  8 19:03:52 nic-laptop kernel: [  265.849598] wlan0: RX authentication from 00:1b:11:71:e1:ee (alg=0 transaction=2 status=0)
Sep  8 19:03:52 nic-laptop kernel: [  265.849604] wlan0: authenticated
Sep  8 19:03:52 nic-laptop kernel: [  265.849608] wlan0: associate with AP 00:1b:11:71:e1:ee
Sep  8 19:03:52 nic-laptop kernel: [  265.851766] wlan0: RX AssocResp from 00:1b:11:71:e1:ee (capab=0x431 status=0 aid=2)
Sep  8 19:03:52 nic-laptop kernel: [  265.851772] wlan0: associated
Sep  8 19:03:52 nic-laptop kernel: [  265.851778] wlan0: switched to short barker preamble (BSSID=00:1b:11:71:e1:ee)
Sep  8 19:04:03 nic-laptop kernel: [  267.168401] wlan0: no IPv6 routers present
Sep  8 19:04:34 nic-laptop kernel: [  267.803829] b43-phy0 debug: Using hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff

```


**Syslog**:
```

Sep  8 19:05:49 nic-laptop dhclient: wmaster0: unknown hardware address type 801
Sep  8 19:05:49 nic-laptop dhclient: Listening on LPF/wlan0/00:1a:92:1a:c9:30
Sep  8 19:05:49 nic-laptop dhclient: Sending on   LPF/wlan0/00:1a:92:1a:c9:30
Sep  8 19:05:49 nic-laptop dhclient: Sending on   Socket/fallback
Sep  8 19:05:49 nic-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Sep  8 19:05:53 nic-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Sep  8 19:05:53 nic-laptop dhclient: DHCPOFFER of 192.168.0.102 from 192.168.0.1
Sep  8 19:05:53 nic-laptop dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67
Sep  8 19:05:53 nic-laptop dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Sep  8 19:05:53 nic-laptop avahi-daemon[5062]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Sep  8 19:05:53 nic-laptop avahi-daemon[5062]: New relevant interface wlan0.IPv4 for mDNS.
Sep  8 19:05:53 nic-laptop avahi-daemon[5062]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Sep  8 19:05:53 nic-laptop dhclient: bound to 192.168.0.102 -- renewal in 4706 seconds.

```

Kern.log has a lot of output that doesn't look different from these, just a lot more of it. I can post it if you want, but this is already a lot.

---

### Post by njd4k on 2008-09-08
> **vikram said:**
> I managed to get my Dell laptop with the same or similar wireless card working so I'm pretty sure its possible. 

This is what I used 

ndiswrapper + windoze driver instead of native driver 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and to configure the connection using WPA

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

I will try this and report back.

---

### Post by njd4k on 2008-10-20
> **vikram said:**
> I managed to get my Dell laptop with the same or similar wireless card working so I'm pretty sure its possible. 

This is what I used 

ndiswrapper + windoze driver instead of native driver 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and to configure the connection using WPA

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

Sorry for the delay in following up on this problem. I had to fix an unrelated problem in by Ubuntu installation and wound up switching to 32-bit. I also had to not fail out of graduate school. And each time I checked, the ndiswrapper list of best drivers was down. Still is.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

So I'm just now getting to this problem.

I installed ndiswrapper as suggested, and used it to install my driver. (I just pulled the driver for my computer from Dell's web site.) I had no problem loading it with the Windows Drivers GUI, but it is not working.

Any other ideas? I think I'm going to have to give up on using Ubuntu, at least until I buy my next machine. I know it isn't the Linux community's fault that there isn't a usable driver -- at least the opensource driver works for unencrypted networks -- but this is the machine I've got for a few years yet...

---

### Post by eolson on 2008-10-20
The Broadcom support in 8.10 is much better.

I had difficult connecting to my wireless network also.   Ended up setting the router to open network,  connecting, then closing the network.   Think I needed to log back on using the network name and key, but everything worked after that.   What actually happened, I have no idea.

---

### Post by igknighted on 2008-10-20
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Try this out.  This is a brand new driver direct from Broadcom.  I have the same card as you, and this driver works flawlessly for me with unprotected, WEP and WPA wireless.

---

### Post by njd4k on 2008-10-22
> **eolson said:**
> The Broadcom support in 8.10 is much better.

I had difficult connecting to my wireless network also.   Ended up setting the router to open network,  connecting, then closing the network.   Think I needed to log back on using the network name and key, but everything worked after that.   What actually happened, I have no idea.

I tried it as an open network and then switched it back -- no luck with that. :(

I don't see anything about Broadcom in particular in the notes on the new Network manager, but maybe when it comes out of beta I'll install it and see. Can't hurt.

---

### Post by njd4k on 2008-10-22
> **igknighted said:**
> [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Try this out.  This is a brand new driver direct from Broadcom.  I have the same card as you, and this driver works flawlessly for me with unprotected, WEP and WPA wireless.

It doesn't seem to be working, but I think I may have installed it incorrectly. I'll look at the directions carefully and try again and see if that works. Thanks.

---

### Post by igknighted on 2008-10-22
> **njd4k said:**
> It doesn't seem to be working, but I think I may have installed it incorrectly. I'll look at the directions carefully and try again and see if that works. Thanks.

Actually, I just reinstalled 8.04.1 and the Broadcom STA driver has been pushed through updates and is available in the hardware driver app.  Just make sure you have the latest updates including kernel 2.6.24-21 and it should be as easy to set up as the b43 was.

---

### Post by njd4k on 2008-10-24
> **igknighted said:**
> Actually, I just reinstalled 8.04.1 and the Broadcom STA driver has been pushed through updates and is available in the hardware driver app.  Just make sure you have the latest updates including kernel 2.6.24-21 and it should be as easy to set up as the b43 was.

I reread the page you linked to and saw that was the case, but even though I'm up to date (apt-get update from the command line, right?) I don't have the STA driver. I have the b43 and something called wl which I'm assuming is the driver I installed.

---

### Post by njd4k on 2008-10-25
So: I got impatient and upgraded to 8.10 early. The network manager still has the new driver listed as "wl" not "Broadcom STA" so I suppose it's still using my manually installed version. But whatever the situation was, upgrading fixed it -- I'm typing this in Ubuntu 8.10 over the network that was giving me an ulcer. 

I am marking this solved, knocking on wood, and thanking the great penguin god that I can make XP my second OS again.

---

