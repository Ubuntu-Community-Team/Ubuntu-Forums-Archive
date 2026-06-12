---
title: "Can't get wireless working.."
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Gabzilla on 2008-06-18
My Netgear WG111T wireless adapter isn't working on Ubuntu. 

My problem is that it's not connecting to my wireless network here at home. Its recognized on ubuntu and the little blue light is blinking like it should, I just can't seem to get it to connect.

I'm using the right WEP passphrase, but it just won't connect.

Help please? I'm incredibly new to all of this and I'm not sure what I'm doing half the time on ubuntu so PLEASE help!

---

### Post by phidia on 2008-06-18
What type of wireless card is in the computer your trying to connect? (lspci -v will output info on devices) and what is selected in System>Administration>Network? See if you can configure your card normally listed as wlan0 there.
The [community docs on networking]("https://help.ubuntu.com/community/NetworkDevices") include troubleshooting and set up info. It's a good place to start.
The commands, typed in terminal, ifconfig, iwconfig, and lshw -C network can be useful also.

---

### Post by anewguy on 2008-06-18
Be sure at the network key prompt that you are entering the correct number of bits as well.  It used to default to 64 bit but now defaults to 128 bit.  Select the 64 bit wep and see what happens.  If that doesn't work, try connecting (hardwire or perhaps windows) to your router and temporarily leaving it wide open (e.g., no wep, no MAC filtering, etc.).  Try to connect - if you succeed then move on to 1 thing at a time - like adding a wep passphrase or password. :)

---

### Post by Gabzilla on 2008-06-19
> **phidia said:**
> What type of wireless card is in the computer your trying to connect? (lspci -v will output info on devices) and what is selected in System>Administration>Network? See if you can configure your card normally listed as wlan0 there.
The [community docs on networking]("https://help.ubuntu.com/community/NetworkDevices") include troubleshooting and set up info. It's a good place to start.
The commands, typed in terminal, ifconfig, iwconfig, and lshw -C network can be useful also.

Its a Netgear WG111T dongle and the documents in the wiki are out of date. They're for previous versions and I'm using Hardy Heron.

---

### Post by UniverseA7X on 2008-06-19
Hi.

I'm the one who set up ubuntu on Gabzilla's computer.

I read up on using ndiswrapper for the WG111T dongle. I installed the Windows drivers for the dongle and we could see her network, but we couldn't connect to it. I did end up reading that there were some issues with this particular dongle and Hardy Heron, and I'm wondering if there are any workarounds at all for this? She's really eager to use Ubuntu, and it'd be amazing if we could get her wireless working, as it's the only way she has to get on the internet. 


Thanks.

---

### Post by tysonh on 2008-06-19
Does it show up when you type lsusb in a terminal window?

---

### Post by UniverseA7X on 2008-06-19
> **tysonh said:**
> Does it show up when you type lsusb in a terminal window?

It appears so.

```
Bus 005 Device 002: ID 1385:4250 Netgear, Inc  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse  
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp.  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by Kevbert on 2008-06-19
There's a comunity document for this [dongle]("https://help.ubuntu.com/community/WifiDocs/Device/WG111T").
Good luck.

---

### Post by UniverseA7X on 2008-06-19
That was the thing though...

Tried it, and It seemed to not work at all... Maybe I'll give it another shot. I was wondering if there was another workaround, because when I was over there working on all this, that document in the wiki did nothing for me, because nothing worked out of the box in the first place. The card was recognized, but no connection. Confusing... :/

---

### Post by Kevbert on 2008-06-19
There's another [guide for Kubuntu]("http://infinity-sama.blogspot.com/2007/07/wg111t-in-kubuntu.html") which may help (commands will be the same).  It seems that the dongle is a bit of a problem for 64 bit and also fixes are dongle version and Ubuntu version dependent.

---

### Post by rhlobo on 2008-06-19
There are some users experiencing some wireless problems when connecting thrue WEP/WAP after 06-17 ubuntu updates. The list of disponible networks works correctly but the connection process just hangs and wont connect.

If you think this is your problem, I will be checking [https://answers.launchpad.net/ubuntu/+question/36575](https://answers.launchpad.net/ubuntu/+question/36575) constantly.

Best regards

---

### Post by UniverseA7X on 2008-06-19
> **rhlobo said:**
> There are some users experiencing some wireless problems when connecting thrue WEP/WAP after 06-17 ubuntu updates. The list of disponible networks works correctly but the connection process just hangs and wont connect.

If you think this is your problem, I will be checking [https://answers.launchpad.net/ubuntu/+question/36575](https://answers.launchpad.net/ubuntu/+question/36575) constantly.

Best regards


That does seem to be it. Thank you for keeping up on that. I'm also going to keep that kubuntu tutorial in my bookmarks. May have to do with the version of ndiswrapper. I will try 'till it works. :KS

---

### Post by UniverseA7X on 2008-06-20
Okay. Wireless is connected to her network. BUT, No internet. Now I've read up on WPA supplicant, not sure if that's what I need though. Any thoughts?

---

### Post by anewguy on 2008-06-21
As best as I have understood it, if you use WPA encryption you will need wpa supplicant.  The fact that you have connected to the router and to her network (e.g., you can see other nodes,etc., correct?) but not get to the internet would point to a little bit deeper problem - perhaps the bug mentioned above.

Good Luck!! :)

---

### Post by UniverseA7X on 2008-06-21
Okay. I'm not at her house anymore, but we were able to connect through the option that says 128 bit Hex, but I'm not sure if that's WPA or WEP. If it was WEP, I would assume wpa supplicant would be useless, right?

---

### Post by UniverseA7X on 2008-07-07
Are there any updates on if the 8.04.1 release solved this issue, or is it a better idea to just go back to 7.10 for the moment?

---

