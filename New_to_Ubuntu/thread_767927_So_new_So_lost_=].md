---
title: "So new So lost =]"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Rifts on 2008-04-26
haha ok so i'm now dual booting my laptop with xp and Ubuntu 8.04 as of about 4 hours ago. I have one question and one problem:

Question: What are these names like feisty fawn? are those names of the different versions of Ubuntu? or are they something totally different? 

Problem: After installing Ubuntu 8.04 my AR5006X wireless card does not work... I have googled and searched so much but nothing is working. Any help?

 Thanks

ok im attaching 2 screen shots, one of the network window and one of the drivers window 

also heres my terminal stuff
```
lspci:

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1b:38:50:f3:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158600 (154.8 KB)  TX bytes:158600 (154.8 KB)


```
 
thanks for looking

---

### Post by tango_ninja on 2008-04-26
Yes, they are codenames for different version releases (just as *Longhorn* is vista's codename). Feisty Fawn refers to 7.04.

As for wireless, I know it's a problem with a lot of people....have you checked the wireless troubleshooting guide? (here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide))

---

### Post by HunterThomson on 2008-04-26
Yes they are different versions like 8.04 is hardy 7.10 is gusty and 7.04 is feisty.

I just was looking for your driver last night and found a grate one so you can put it into monitor mode and do packet injection so you can do cool things like crack WPA-PSK and WEP. I will get the links and report back....

---

### Post by Technoviking on 2008-04-26
> **Rifts said:**
> haha ok so i'm now dual booting my laptop with xp and Ubuntu 8.04 as of about 4 hours ago. I have one question and one problem:

Question: What are these names like feisty fawn? are those names of the different versions of Ubuntu? or are they something totally different? 

[https://wiki.ubuntu.com/DevelopmentCodeNames](https://wiki.ubuntu.com/DevelopmentCodeNames)
> **Rifts said:**
> 
Problem: After installing Ubuntu 8.04 my AR5006X wireless card does not work... I have googled and searched so much but nothing is working. Any help?

Does any wireless drivers show up under
```
System --> Administration --> Hardware Drivers
```

---

### Post by axor1337 on 2008-04-26
look like your gonna get all the help you need but did you check the restricted drivers

---

### Post by buntunub on 2008-04-26
> **Rifts said:**
> haha ok so i'm now dual booting my laptop with xp and Ubuntu 8.04 as of about 4 hours ago. I have one question and one problem:

Question: What are these names like feisty fawn? are those names of the different versions of Ubuntu? or are they something totally different? 

Problem: After installing Ubuntu 8.04 my AR5006X wireless card does not work... I have googled and searched so much but nothing is working. Any help?

 Thanks

Ubuntu uses year/month release names. 8 = 2008, 04 = April. The logo names are just that, but are also symbolic of the "tone" of the release. Feisty Fawn was a rather feisty release with some new technologies, Gutsy Gibbon was even more Gutsy, and Hardy Heron symbolizes an LTS (Long Term Support) releases "Hardiness" or stability.

That wireless chip is totally new to me. Beyond whatever a Google search could turn up, I could not be of much help on that one.

---

### Post by Rifts on 2008-04-26
wow first of all thank all of you for such fast answers... I understand so much more just answering that code name part.. and for the wireless as soon as i get back to my laptop ill post that info 

 thanks again

---

### Post by Technoviking on 2008-04-26
I think it can use the madwifi driver. Search madwifi and Ubuntu.

---

### Post by HunterThomson on 2008-04-26
Ya that's the one, You can use the Madwifi driver and you can use it to put it into "monitor mode" and do "Packet injection" I wish I had your wireless chipset. I had to buy a Liksys WUSB54GC.

---

### Post by Rifts on 2008-04-26
thanks for the help i edited my first post with needed information

---

### Post by Rifts on 2008-04-26
bump bump =]

---

