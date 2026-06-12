---
title: "Wireless networking without a router"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by BetterSense on 2008-10-14
This question is so noobish I decided to ask it here instead of networking.

I have DSL, with AT&T DSL 'box'.

I used to have a linksys WRT54g router so that I could have my desktop plugged in with wired and use the wireless with my laptop. A friend set it up for me to work. It just died. No worky. So I disconnected it, reset the DSL box, and plugged my computer straight into the DSL box with wired. Hurray, I have tubes. But no wireless network anymore.


Now, I actually have a wireless card for my desktop, and I installed it, and it works (I see my neighbor's networks in knetworkmanager). So why can't I use the wireless card on my desktop to set up a wireless network so that I can get my laptop onto the internets THROUGH my desktop's wireless card? Is this possible, and is there any noob guides online? Security is important to me, what encryptions are safe nowadays?

---

### Post by handydan918 on 2008-10-14
"Is this possible?"

Yep. iptables is capable of doing this. If only humans could use it....
As for noob friendly tutorials...good luck, and standby for one of the geniuses here who has mentally cataloged all the html code on this site alphabetically, by height.

---

### Post by mikewhatever on 2008-10-14
> So why can't I use the wireless card on my desktop to set up a wireless network so that I can get my laptop onto the internets THROUGH my desktop's wireless card?

Because wireless cards are not designed to hand out IP addresses. A router is the device designed for it, and you'll need one to have a wireless network.

> **handydan918 said:**
> "Is this possible?"

Yep. iptables is capable of doing this. If only humans could use it....
As for noob friendly tutorials...good luck, and standby for one of the geniuses here who has mentally cataloged all the html code on this site alphabetically, by height.

Errr, iptables?:confused:

---

### Post by handydan918 on 2008-10-14
> **mikewhatever said:**
> Because wireless cards are not designed to hand out IP addresses. A router is the device designed for it, and you'll need one to have a wireless network.

Sit down.

"Because wireless cards are not designed to hand out IP addresses."

Wireless cards transmit data in the form of high and low voltage signals. The Linux kernel is pefectly capable of "handing out IP addresses."

If you are going to pretend authoritative knowledge, get some first.

---

### Post by DGortze380 on 2008-10-14
> **BetterSense said:**
> This question is so noobish I decided to ask it here instead of networking.

I have DSL, with AT&T DSL 'box'.

I used to have a linksys WRT54g router so that I could have my desktop plugged in with wired and use the wireless with my laptop. A friend set it up for me to work. It just died. No worky. So I disconnected it, reset the DSL box, and plugged my computer straight into the DSL box with wired. Hurray, I have tubes. But no wireless network anymore.


Now, I actually have a wireless card for my desktop, and I installed it, and it works (I see my neighbor's networks in knetworkmanager). So why can't I use the wireless card on my desktop to set up a wireless network so that I can get my laptop onto the internets THROUGH my desktop's wireless card? Is this possible, and is there any noob guides online? Security is important to me, what encryptions are safe nowadays?

More trouble than it's worth. Go buy a $40 router and follow the step-by-step's.

---

### Post by BetterSense on 2008-10-14
Ok so I should just forget about it then? I was just thinking that people build linux routers out of atticware all the time, but I know they usually use linux distros that are pre-designed for it. So I knew it would be possible in theory. 

> Go buy a $40 router

Recommend a $40 wireless router that doesn't explode from torrenting or need reset constantly, mysteriously? My linksys was $60, and it's dead now.

---

### Post by Old_Grey_Wolf on 2008-10-14
The link below tells how to do it with MS Windows. I have no idea how to do it with Ubuntu.

[http://www.microsoft.com/windowsxp/using/networking/setup/adhoc.mspx](http://www.microsoft.com/windowsxp/using/networking/setup/adhoc.mspx)

I prefer a router myself.

Edit:  You should use WPA or WPA2 in my opinion. The longer the passphrase the better. Anyone can crack WEP.

---

### Post by mikewhatever on 2008-10-14
> **handydan918 said:**
> Sit down.
Wireless cards transmit data in the form of high and low voltage signals. The Linux kernel is pefectly capable of "handing out IP addresses."

If you are going to pretend authoritative knowledge, get some first.

Now I am even more confused. If you know how to set it up, why not simply tell the OP? Everyone will benefit from it. If you don't know, why talk about the kernel and iptables?

---

### Post by dhtseany on 2008-10-14
handydan918: I'm sure your intentions are to help but being a jerk isn't going to help anyone.


Now, I know you can do this just fine. As shown through the link above it's easy to do on window$. Now Ubuntu is a little different. First, you'd have to find a tutorial on how to route IP packets from eth0 (where your DSL modem is plugged in) through to the wireless (probably wlan0). You'll have to use PPPoE to authenticate your account with your DSL provider before you'll get an IP address from your ISP. Then, you'd have to setup the DHCP server/service from apt and configure it to your liking. The somehow figure out how to make your wireless transmit an SSID so your other computers will see it. 

When you've gotten that far start to research how to use WPA2 to secure the signal.

Now, if you ask if this is going to be an easy task, the answer is most likely no. You'll probably have to piece together your own how-to guide.

Yes, it'd probably be much easier to replace your router. Also, try and call Linksys' tech support and see if they'll help you; no hurt in trying.

If you have more specific questions on your quest please ask and I'm sure some of us will be able to help.

Peace
Sean

---

### Post by handydan918 on 2008-10-14
> **dhtseany said:**
> handydan918: I'm sure your intentions are to help but being a jerk isn't going to help anyone.

Sean
Who is the jerk? The fool who claims the possible is impossible, or the "jerk" who calls him on it?

Might help the OP to learn the diff between someone pretending to know something and someone who does know something.
And no, I don't know how to do it. I merely know it can be done. life is not like windows...all point and click, menu guided. It is more like Linux, with virtually infinite choices and variables. 
I only intended to ensure that the OP knew that what he proposed was possible, and that the pretender knew that he should read up. 
If I caused offense to any reasonable person, my apologies. 
 And peace to the rest of you, too.

---

### Post by BetterSense on 2008-10-15
well it's kind of depressing to find out that anything is better on windows, to be honest. I think this might be the first thing I've found.

---

### Post by bobnutfield on 2008-10-15
I certainly don't purport to be an expert, but apparently it is possible.  See this HOWTO, though it is written for Ubuntu 6.06, the fundamentals look the same:

[http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/]("http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/")

Apprently, the key is setting IP address of the desktop wireless router as the gateway and nameserver on the laptop.  But is much more complicated than just that.

---

### Post by iponeverything on 2008-10-15
Its quite easy. First you need to find out if the driver for wireless card support either AP mode or Ad-hoc mode. 

Not only I am doing this same thing with an old laptop, its configured as an AP, is handing out ip addresses via dhcp and its doing wpa2 encryption. Why waste $40 on wireless router if you don't have to -- and you can have some fun in the process?


> Because wireless cards are not designed to hand out IP addresses. A router is the device designed for it, and you'll need one to have a wireless network.


Wireless routers and linux PC's have a lot more common you think. And unless the wireless router is running dd-wrt, the linux box will be far more capable.

If you want to give it a shot, I'll be happy to help you out with it.

Unfortunately, there is not going to a one size fits all way to do this it is going to depend capabilities of your wireless driver and version of Ubuntu or linux distro that your using..

so with that said:

What are you running?
What is wireless hardware? (also post the the line from the output "lspci" that shows your wireless card)

---

### Post by BetterSense on 2008-10-15
I'm running Hardy with kubuntu-desktop. This is the wireless card I have:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041")
I don't know how to figure out what drivers I'm using. I just yesterday installed the wireless card, and it automagically worked when I rebooted...much easier than when I had it installed in windows.

```
01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI E                                                                                                   xpress Gigabit Ethernet controller (rev 01)
chaz@brutus:~$

```

```
chaz@brutus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:30:8d:1e
          inet addr:192.168.1.64  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe30:8d1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:185099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:120703111 (115.1 MB)  TX bytes:28611075 (27.2 MB)
          Interrupt:216 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:232588 (227.1 KB)  TX bytes:232588 (227.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:96:48:b5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-96-48-B5-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

chaz@brutus:~$


```

---

### Post by halitech on 2008-10-15
is the laptop windows or another version of linux?

---

### Post by BetterSense on 2008-10-15
The laptop is Hardy running gnome. I didn't think the laptop mattered, because I thought the desktop would just become another access point that the laptop could pick up and connect to. I need to use the laptop daily at work to connect to other wireless networks, so I can't, like, mess up its networking by 'binding' it to the desktop or anything.

---

### Post by iponeverything on 2008-10-15
Good new and bad news your driver rt61pci can be AP mode, the bad new is looks something very few people have managed to figure out:

ref:  [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4963](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4963)

Feel free to give this a shot -- its not really that hard, but it fraught with pitfalls for the inexperienced. The instructions are for hardy.

I would recommend that we go the Ad-hoc route.. much easier -- though it will limit you 10M.. not the end of the world.

It's my bedtime -- 10 pm here.. I am going to crash. I will post instructions for you tomorrow on setting a ad-hoc network, installing and configurint the dhcp server and enabling IP forward and IP Masquerade on the desktop machine.

---

### Post by halitech on 2008-10-15
reason I was asking about the laptop is to find out if it would be something easy to set up a static ip. In theory we should be able to set each machine with a static IP and have them connect at least to each other but not sure if it would help for the internet sharing in that way.

looks like the link iponeverything posted should work so give it a shot and hopefully it does

---

### Post by BetterSense on 2008-10-16
I bought a wrt54GL. Newegg was having a $10 off and free shipping promotion, ends tonight. O well.

---

### Post by iponeverything on 2008-10-16
> **BetterSense said:**
> I bought a wrt54GL. Newegg was having a $10 off and free shipping promotion, ends tonight. O well.

oh well! At least it was a good deal and with the wrt54GL you can do wpa/wpa2 without much adieu.

---

