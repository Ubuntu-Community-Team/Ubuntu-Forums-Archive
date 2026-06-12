---
title: "Can't install Broadcom STA wireless driver"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by TheNessus on 2011-09-07
I can't install it through "additional drivers"; I get this when trying:

SystemError: E:Unable to correct problems, you have held broken packages.

But I have no broken packages at all. Apt-get works flawlessly, so does software center and synaptic.

So when I install Broadcom STA with synaptic, it succeeds... but still, the driver is not activated on next boot. I have to activate it through "additional drivers" but it says the same error again when trying to download (it shouldn't download, I already have it installed!).

I need to use this driver because the built-in driver that comes with ubuntu is not the correct one I need for my wireless card, and sometimes my web-browsing is stalled entirely.

---

### Post by TheNessus on 2011-09-11
bump?

---

### Post by FlyingIsFun1217 on 2011-09-11
If it helps, I have a 4318, and I just had to search synaptic for b43, and install the driver. After each boot up though, I have to run the following to get it to work:

```

sudo modprobe -r b43 ssb
sudo modprobe b43

```

FlyingIsFun1217

---

### Post by cariboo on 2011-09-12
HAve either of you made sure the drivers you don't use are blacklisted in /etc/modprobe.d?

---

### Post by TheNessus on 2011-09-12
intalling this driver via jockey had always worked on previous releases; this is obviously a bug, but I don't know how to approach it. Plus, Jockey says "tested by ubuntu developers" when suggesting Broadcom-sta.

---

### Post by cariboo on 2011-09-12
There have been a few problems with jockey-gtk lately, so I originally installed it via synaptic, and now on my netbook, I have to re-install the driver every time there is a new kernel, I cd into /var/cache/apt/archives and  use the following command:

```
sudo dpkg -i  bcmwl-kernel-source
```

---

### Post by TheNessus on 2011-09-12
I dunno. I can install both broadcom-source (bc43) and broadcom-sta with synaptics but none actually work after installation and reboot. I have to remove them completely in order to have a working wireless again.

It seems as though installing them is not the problem; using them is. I don't know how to activate them without the use of jockey. I also found bug reports on this issue but it's not being addressed at all.

---

### Post by cariboo on 2011-09-12
After installing the STA driver, make sure the B43 drivers are blacklisted in /etc/modprobe.d

---

### Post by TheNessus on 2011-09-13
alright, i'll try that. But I have no idea how to do that actually...

---

### Post by ventrical on 2011-09-13
I had the exact same problems with Natty , however I was able to get them running. I had to make sure the
wireless card was 'turned on' because installing the STA driver in that version seemed to turn the wireless card off.

 Also , another thing that helped was that I went into Network Connections and configured a wireless connection from there and that helped also.  I am not sure if these tips will apply to Oneiric as I have not had any problems as of yet with Broadcom.

---

### Post by ventrical on 2011-09-15
> **cariboo907 said:**
> There have been a few problems with jockey-gtk lately, so I originally installed it via synaptic, and now on my netbook, I have to re-install the driver every time there is a new kernel, I cd into /var/cache/apt/archives and  use the following command:

```
sudo dpkg -i  bcmwl-kernel-source
```


Ummm...!!


madame@madame-ME051:~$ sudo dpkg -i bcmwl-kernel-source
[sudo] password for madame: 
dpkg: error processing bcmwl-kernel-source (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bcmwl-kernel-source
madame@madame-ME051:~$ sudo dpkg -i install bcmwl-kernel-source
dpkg: error processing install (--install):
 cannot access archive: No such file or directory
dpkg: error processing bcmwl-kernel-source (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install
 bcmwl-kernel-source
madame@madame-ME051:~$ 



Help please! What happened?

---

### Post by ventrical on 2011-09-15
The way I fixed this is:

remove the :
bcmwl-kernel-source
using synaptic package manager.
sudo apt-get remove bcmwl-kernel-source

then:in terminal

sudo apt-get install b43-fwcutter

and since Natty11.04 you will need:

sudo apt-get install b43-fwcutter firmware-b43-install

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by TheNessus on 2011-09-15
ok, nothing works.

currently I have no broadcom drivers install. not STA and not firmware and not nothing. but it works (very sluggishly and I have to re-connect frquently to access websites). I want to use a propriety driver so that it would work normally. everytime I install a propriety driver the driver doesn't work and I don't know why, so I have to remove it with synaptics again so the open source would work. currently the working driver is  "brcmsmac" (using "connection information" of current connection info in the network indicator. I have no idea what package this driver belongs to as "brcmsmac" yields nothing in synaptic).  anyway - in Oneric, wireless is barely working for me. This open source driver worked ok on previous versions, yet there too it didn't always work on boot and it was fixed on reboots.  Device is broadcom 4313.

---

### Post by cariboo on 2011-09-15
@TheNessus, did you see this?

[http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)

As you can see it's directly from Broadcom.

---

### Post by ventrical on 2011-09-15
OK.. I got ...


02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

@TheNessus

Please disregard above.

---

### Post by ventrical on 2011-09-15
> **cariboo907 said:**
> @TheNessus, did you see this?

[http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)

As you can see it's directly from Broadcom.

Ahhh.. thanks for that Caribou.. I was working with the Natty kernel.

---

### Post by TheNessus on 2011-09-17
I fixed it. i took the solution listed [here]("https://wiki.archlinux.org/index.php/Broadcom_wireless#Wi-Fi_card_locks_up_.28brcm80211.29"):

"I have found that to get the wl drivers working for the Broadcom 4313 chip, you need to blacklist brcm80211 along with b43 and ssb."

don't know how it fixed it but ok. cheers.

---

### Post by ventrical on 2011-09-17
Bravo!!

I know .. it's frustrating at first ... 

 Keep at it.

---

### Post by coffeecat on 2011-09-17
> **TheNessus said:**
> I fixed it. i took the solution listed [here]("https://wiki.archlinux.org/index.php/Broadcom_wireless#Wi-Fi_card_locks_up_.28brcm80211.29"):

"I have found that to get the wl drivers working for the Broadcom 4313 chip, you need to blacklist brcm80211 along with b43 and ssb."

don't know how it fixed it but ok. cheers.

Interesting. In Natty, if you install the STA driver through Jockey, this gets done for you. A /etc/modprobe.d/blacklist-bcm43.conf file is created which contains:

```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
```

From your experience it sounds as though this didn't happen in Oneiric.

---

### Post by TheNessus on 2011-09-17
> **coffeecat said:**
> Interesting. In Natty, if you install the STA driver through Jockey, this gets done for you. A /etc/modprobe.d/blacklist-bcm43.conf file is created which contains:

```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
```

From your experience it sounds as though this didn't happen in Oneiric.

I should have been more clear (and, update)
it at first seemed to have fixed the slowness issue I have experienced with the brcmsmac driver. very slow connection on some ports, while others are ok. Ping is terrible and download speed falls from my 5mb per second to about 5kb to 50kb. (this is traced to Oneric only as it doesn't happen on windows or natty on my machine).

But any way I was wrong, it does happen (it happens randomly, I can't control when). Problem still stands, and is fixed temporarily if I connect and disconnect to a wireless network. 

I still cannot use any propriety driver. it simply does not work. it may say a propriety driver is activated (if downloaded by synaptic) but in reality it is not. and I can't download it with Jockey as it says the error seen in first post.

---

### Post by coffeecat on 2011-09-18
By brcmsmac, I'm assuming you mean what appears as brcm80211 when you do a lsmod. I have the BCM4313 wireless card in my netbook and the brcm80211 driver works well in Natty as you say. I haven't tried Oneiric on that machine yet, so I'll try a daily-live from a USB later today and see how I get on.

---

### Post by coffeecat on 2011-09-18
OK, I see that the open source driver comes up as brcmsmac in Oneiric, where it was brcm80211in Natty.

I'm posting from a live USB prepared from today's daily ISO from my netbook. My wireless card is:

```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

I notice that although you've been referring to 4313, a lspci output you posted says that you have BCM4318, which is different, so this following may not be of help. I seem to be getting a good, stable connection with my router, and pings to google give me in the range of 57-59 ms. Seems that the Oneiric default driver is OK for my 4313 at least. Sorry you get poor results with the 4818 and sorry I can't help with the STA driver.

---

### Post by TheNessus on 2011-09-18
Nope, it was ventrical's output that indicates he has 4318. Mine is 4313. 

as I said earlier, it comes and goes, completely on random. I think you'd have to use it a whole while to notice if it suddenly starts to die on you to a halt. 
But that's one problem; the other being that installing a propriety driver is impossible, at least through Jockey, and activating a propriety driver through any means will not work. Is your Live CD persistent to allow check this out? 

*It may also be a problem that emanates from a dual core processor. Is your netbook single core?

---

### Post by coffeecat on 2011-09-18
> **TheNessus said:**
> Nope, it was ventrical's output that indicates he has 4318. Mine is 4313. 

Apologies. Missed that.

> **TheNessus said:**
> as I said earlier, it comes and goes, completely on random. I think you'd have to use it a whole while to notice if it suddenly starts to die on you to a halt.

Yes, that's a good point.
 
> **TheNessus said:**
> But that's one problem; the other being that installing a propriety driver is impossible, at least through Jockey, and activating a propriety driver through any means will not work. Is your Live CD persistent to allow check this out? 

I did a simple dd to get the ISO onto a pendrive. I'll redo the pendrive, but this time use startup disk creator (please work this time, sdc [-o<) and see what happens when I try to install the STA driver. That may take a day or more, but I'll come back to this.

> **TheNessus said:**
> *It may also be a problem that emanates from a dual core processor. Is your netbook single core?

Rather surprisingly, it's dual-core, and I was running the 64-bit ISO, if that's relevant. I didn't expect that when I opened System Monitor when I first installed Natty.

---

### Post by TheNessus on 2011-09-18
Thanks so much.  (mine is 64 bit too)

---

### Post by coffeecat on 2011-09-18
Well - first thing is that I can confirm that installing the STA driver in Oneiric is definitely broken. I'm now posting from a live USB Oneiric from today's daily but with persistence. I'll post what little I have discovered so far. I might repeat something you've already posted; I'm posting from my netbook and scrolling up and down the thread to remind myself what has already been said is challenging. :wink:

First - the brcmsmac driver still seems OK. I installed the STA driver from Jockey and rebooted, and the wireless connected straightaway - except that it was still using the brcmsmac driver. The /etc/modprobe.d/blacklist-bcm43.conf file is the same as in Natty, which means that it is not blacklisting brcmsmac, which can't be right. So I added a "blacklist brcmsmac" line and rebooted and the wireless wouldn't work. I did a "sudo modprobe wl", but that didn't bring wireless up. I've removed my blacklist brcmsmac line to get wireless working again and that's as far as I've got for now.

One thought about the brcmsmac driver. I have a N-capable router but I've configured it for G only, mainly because I discovered an issue with an N-capable Atheros wireless chip on another machine. The bcm4313 is N-capable. If you haven't done so already, try reconfiguring your router to G and see if that helps. I'll do some more on this STA driver tomorrow if I find time.

---

### Post by ventrical on 2011-09-19
I am going to try and install this on a Broadcomm 4312 and see what happens :

:here:

0:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

---

### Post by ventrical on 2011-09-19
I had a seamless install on above said computer. Broadcomm STA Wireless driver installed seamlessly.

The hardware jockey came right up after the install after the first re-boot. It installed it and all I had to do was enter my WEP.

Sorry I could not be of more help.

I am about to update now .. so that can change :)

---

### Post by coffeecat on 2011-09-20
I'm really not much further on from 2 days ago - not had enough time. This from a live USB 64-bit with persistence with a bcm4313 card.

Just to clarify what may not have been clear from my previous post. Additional drivers thinks that the STA driver is activated and in use, except that when I boot up, the wireless works fine but with the brcmsmac driver, which so far I have had no problems with. If I "sudo rmmod brcmsmac", wireless goes down and wlan0 disappears from ifconfig output. If I "sudo modprobe wl" nothing happens except that the wl module is loaded. It doesn't seem to do anything - wireless doesn't work and wlan0 is still missing from ifconfig. If I then "sudo modprobe brcmsmac", wireless comes up again and connects spontaneously. 

At the moment I'm doing an update courtesy of the brcmsmac driver to see if that [s]breaks everything[/s] changes anything. :wink:

---

### Post by TheNessus on 2011-09-21
Again, thank you.

I'm afraid I am currently on my Windows 7 rather than on Ubuntu, for smooth internet access. Yesterday it worked flawlessly for almost a whole day until at one point it started dying again, and I had to re-connect every 2 minutes.

What's strange about this bug, however, is that when the internet decided to die on me, it stalls completely - and when I disconnect, it seems to suddenly have a last gasp of air, and pages load completely. That is, if I try to connect to ubuntuforums.org, I get a while nothing page that tries to load, and then I press disconnect, and suddenly it loads. But then of course it is an off-line mode. then it connects to a normal working connection, for a while.

How can I monitor the change? with a graph to see when the connection dies, and what causes it? 

I am considering re-installing the daily release. I refrain from installing previous releases because pre-3.0.0. kernels made my computer freeze completely occasionally due to some kernel issue regarding either wireless, USB or GPU (a known bug that is reportedly fixed since 3.0.0 and I concur as fixed... Oneiric is the first stable work machine I've had since 9.10 bar the internet issue).

I have not yet tested your suggestion about the router.

---

### Post by TheNessus on 2011-09-22
ok, i've had enough.
Sadly, although 11.10 is spectacular, I won't be able to use it until probably a major kernel upgrade or that somehow they will fix the Jockey issue.

question: 
Does Lucid get automatic kernel 3 upgrade? or do I have to tinker with it and hope not to get a kernel panic?

---

### Post by CTenorman on 2011-09-22
I'm experiencing the same problems as above with an Asus 1015pem on Oneiric. None of the suggested fixes work. Much as it pains me, I'm going to have to put win7 on my netbook, I need the wireless to work.

Who do we contact about fixing this, this is a show-stopper issue that a lot more people are going to run into very soon.

---

### Post by ventrical on 2011-09-22
> **TheNessus said:**
> ok, i've had enough.
Sadly, although 11.10 is spectacular, I won't be able to use it until probably a major kernel upgrade or that somehow they will fix the Jockey issue.

question: 
Does Lucid get automatic kernel 3 upgrade? or do I have to tinker with it and hope not to get a kernel panic?

Lucid is rock solid.  I have several installs. It is always smart to have a Lucid install sideXside when beta testing Oneiric or any other distro for that matter. Lucid will install nicely with Win 7 etc.

 Not sure about the kernel upgrade. I think that upgrade is only for Oneiric.

I had big problems with Natty Beta but then I just installed Edubuntu 11.04 on my Dell Inspiron (With Broadcomm wireless) and it works like a charm.

---

### Post by ventrical on 2011-09-22
> **CTenorman said:**
> I'm experiencing the same problems as above with an Asus 1015pem on Oneiric. None of the suggested fixes work. Much as it pains me, I'm going to have to put win7 on my netbook, I need the wireless to work.

Who do we contact about fixing this, this is a show-stopper issue that a lot more people are going to run into very soon.

  I had the same mindset with Natty Narwhal  - no wireless and it was useless to me. But I decided to stay with it - sit back  a bit and wait .. and it appears a lot of problems have been resolved.

---

### Post by CTenorman on 2011-09-22
I'll definitely be patient and keep trying Oneiric. However, it's either one OS or the other as my netbook has a 60 gb SSD, so both OSs won't fit on at once, and the netbook is a critical part of my daily workflow. It's a good lesson for me - when you've finally managed to get your machine stable, make an image of it on your external backup HD so you can recover it if you need to. :)

---

### Post by ventrical on 2011-09-22
> **CTenorman said:**
> I'll definitely be patient and keep trying Oneiric. However, it's either one OS or the other as my netbook has a 60 gb SSD, so both OSs won't fit on at once, and the netbook is a critical part of my daily workflow. It's a good lesson for me - when you've finally managed to get your machine stable, make an image of it on your external backup HD so you can recover it if you need to. :)

Sounds like the right stuff !!

---

### Post by wildmanne39 on 2011-09-23
Hi, I have read this whole thread trying to learn about wireless with 11.10 because I have been working wireless for about three months and I want to know what to expect when 11.10 comes out.

The broadcom card like coffeecat has and just a few others work with the sta driver easily in 11.04, we always have people with most of the broadcom cards install b43, so it will be interesting to see how this all shakes out.

This is the command that you can use to see what card you have even when it say like 4313, according to this command:
```
lspci -nnk | grep -iA2 net
```
which also shows the ehternet connection,
the important numbers are in red:
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01)
That is the actual numbers used to see which driver a certain card uses.

---

### Post by CTenorman on 2011-09-23
Something really weird is going on on my end. After getting Ubuntu back to what I thought was a known-good condition before (natty with full updates), it's stopped connecting to anything. Even if I turn off all security, or install the STA driver, or install the backports-cw module, it simply won't connect to anything. I'm wondering if the hardware isn't borked somehow. For now disregard any previous comments I've made in the post, this may be a hardware problem on my end. I'll do my best to update once I get windows up and running on the machine.

---

### Post by TheNessus on 2011-09-23
> **CTenorman said:**
> Something really weird is going on on my end. After getting Ubuntu back to what I thought was a known-good condition before (natty with full updates), it's stopped connecting to anything. Even if I turn off all security, or install the STA driver, or install the backports-cw module, it simply won't connect to anything. I'm wondering if the hardware isn't borked somehow. For now disregard any previous comments I've made in the post, this may be a hardware problem on my end. I'll do my 
best to update once I get windows up and running on the machine.

when that happened to me on Natty sometimes, I would hard reboot until it worked. takes some 2 or 3 hard reboots. weird.

---

### Post by ventrical on 2011-09-23
Not sure if this will help but I did some homework of some notes I took during  Natty Beta and I recall that I was having Broadcom issues... and so my notes say that I changed  -(change to English US not English Canada) during the log on. And it worked just great!!!  Now .. why exactly this worked ???? I haven't got a clue .. but that is what I did to get the Broadcom Wireless working in Natty. There were some other errors referring to this also. I think it can also be changed in sources etc...

Of course I stand to be corrected but I am declaring the assumption that the proprietary drivers may be restricted in other zones, hence, converting the zone to US solved the problem.So perhaps try again to run those drivers but with your English changed to US. If it is already then of course it is a bigger problem.


Just a side note- I live in Canada but I am on the US-Can border and my city is not included in the install for time zones. I also choose US keyboard .. etc.. and there have been some installs where I have used canada and it has not affected the wireless. But with natty Beta it did.

---

### Post by cariboo on 2011-09-23
I use the Canadian server on my netbook, and I haven't had any problems with the STA driver, other than it not being installed when a new kernel is installed. I still have to manually install the driver every time.

Last night while running powertop --calibrate, I got impatient and restarted the system before it was finished, it turned of wireless and the only way I could get to turn on was to use:

```
sudo rfkill list
```

to find my device, then:

```
rfkill unblock 1
```

Once I had wireless working again, I ran powertop --calibrate again, and it ran with zero problems.

---

### Post by ventrical on 2011-09-23
As I think I stated before that I can use English Canada or English US on Oneiric and not have any problems but with Natty beta I had to use the English US because there was a 'UTF8_US"?? or somthing to this effect that would pop-up when I tried to install the b43 fcutter firmware. That was back 6 months ago. I just thought that maby the LOCALE of some may have a problem with certain driver versions. Once I switched it to  English_US on the login screen then I would get the downloads. Mabey it was just an anomaly in my case.

---

### Post by CTenorman on 2011-09-23
I tried to make wireless work on a stock and fully updated Natty install by buying USB dongles while I waited for my internal wireless to be fixed. We're running wireless N with wpa2 encryption (with WPA1 being insecure now, I can't afford to downgrade).

I tried an ASUS USB-N13, which said it was compatible with linux. Despite considerable effort and various forum fixes to get it working, it wouldn't. The best I could get was a not-totally-reliable g connection.

Then I tried the Belkin N300. This also, despite an incredible amount of fiddling and following instructions on the forum, would not work.

It's taken about 3 hours of searching to find a couple of dongles that have a reasonable chance of working out-of-the-box (TEW-649 and DWA-131) That's a little nuts.

Could we include a section on the forum for "tested hardware"? This would be stuff that has been tried in all configurations and is known to work. Not just new computers, as Ubuntu has on its web site, but accessories like wifi dongles tested to work with the latest standards (like wireless n and wpa2).

Further, I think Ubuntu should be more pro-active in helping users to find hardware that works. My experience (across quite a few machines) is that the wireless often doesn't work. Ubuntu should detect when a wireless card isn't operational or can't connect to a hotspot with minimum throughput standards. It should then suggest to the user "You may be having trouble with your wireless setup. Here are some possible solutions to your problem", and present on-screen several tested wireless cards and dongles that are known to be good. The amount of hassle and headache this would save would be immense. While the wireless should "just work", the reality is that for several years it won't "just work" a lot of the time, and if Ubuntu wants to maximize customer satisfaction, it needs to work for them as it is.

Another suggestion would be to allow users to donate to help get a driver working properly. If I knew that a $10 donation would get Ubuntu working properly either in that release or the next release, I would be very likely to contribute money. Moreover, it would make me feel better about Ubuntu - I would feel like I was making a difference, I would know the problem was transient, and I would feel as though my concerns were being listened to. Users could track the donations toward various cards online and see how many more donations are required to have Ubuntu or someone else devote some resources to fixing the problem.

I always love promoting Ubuntu and the open source community. This would be another way to show other people "hey, even if this isn't working properly now, look what a fantastic system and community we have for fixing this!"

---

### Post by cariboo on 2011-09-23
The Ubuntu Friendly wiki will be the place to check tested hardware once it gets up and running. The wiki is here:

[https://wiki.ubuntu.com/UbuntuFriendly](https://wiki.ubuntu.com/UbuntuFriendly)

---

### Post by ventrical on 2011-09-23
> **cariboo907 said:**
> I use the Canadian server on my netbook, and I haven't had any problems with the STA driver, other than it not being installed when a new kernel is installed. I still have to manually install the driver every time.

Last night while running powertop --calibrate, I got impatient and restarted the system before it was finished, it turned of wireless and the only way I could get to turn on was to use:

```
sudo rfkill list
```to find my device, then:

```
rfkill unblock 1
```Once I had wireless working again, I ran powertop --calibrate again, and it ran with zero problems.

I copied his from a website that had the same issue I was speaking of with Natty, except it is with Linux Mint... so here is what they did to get the wireless fixed:

Unfortunately  I cannot paste it but here is the link:

[http://forums.linuxmint.com/viewtopic.php?f=53&t=57937](http://forums.linuxmint.com/viewtopic.php?f=53&t=57937)

or

---

### Post by CTenorman on 2011-09-23
The Ubuntu friendly site looks good, except it looks as though they're testing systems (laptops, desktops, etc), not components. I think components would be a valuable addition.

I tried what you suggested Ventrical, but it didn't work because I forgot I had a 4313 chip, which the b43 driver doesn't cover (I need the STA or the brcmsmac driver to activate). Thanks for the suggestion though!

---

### Post by cariboo on 2011-09-23
The system testing utility does test the individual components in your system. There is also a wiki page [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") that lists supported wireless devices.

---

### Post by ventrical on 2011-09-23
I'm not ready to give up on this thread yet.

  I had a funny paradox happen with an Acer Aspire 3629, (an older machine with an Atheros Wireless intergration and , guess what,?, I can't get Windows XP to recognize the Atheros card, but, I can install the Broadcom 4313 driver and get my Linsys Speedbooster PCi mini to work. This is the chip (4313) that I had working with Natty.

  I am going to try somthing later and get back to this because I know that  card should be working.   I also remember it had to do with uninstalling something completely and then re-installing and then jockey was able to detect it and install it.

---

### Post by Mykro on 2011-09-23
I'm afraid this really is a stumbling block.  I'm trying out Ubuntu 11.10 from the perspective of a new user, because I want to distribute live CDs and demonstrate it to a group of Windows users.   I'd love them to be able to go home and try it on their own machines.

So I boot Ocelot beta 2 up on a Dell Precision M4300 and get to the Live CD desktop.  Internet doesn't work, and (pretending to be a new user) I don't see anything that might get my internet working.  Note that the empty wireless indicator looks like a piece of pie, and not something that suggests wi-fi!  Lets say I happen across it anyway, and click "Edit Connections".  Aha, a 'Wireless' tab.  I try to Add a Connection, and I see a page of fields for SSID, Mode and MAC addresses. Gah!

Now, we know that's not the right approach without functioning drivers, but a new user wouldn't know that.  They'd get all bogged down in this dialog.

Let's say that I give up on this dialog and go back to the notifications panel.  I discover the "Additional Drivers", spot the "Broadcom STA wireless driver" and install it.  Great!  Now it says all I have to do is reboot and the driver will start working.

Umm.  I'm using the LiveCD.  Our new user just wasted another 10 minutes rebooting to find they're back where they started!

Say I install the driver again, and this time I don't reboot. Because sometimes it works on Windows right - you can install things and ignore the reboot prompt, and it still works.   In fact, if I go into the Additional Drivers a second time, the Broadcom driver is marked as green and activated.  So maybe I don't need to reboot after all!  But no dice.  The wireless is definitely not working (despite the green status). The Broadcom wireless driver really does need a reboot.

At this point about 50% of new users might think to use an ethernet cable.  And 50% of new users will just give up and throw the live CD in the drawer.

I get it - I know the ideological reasons why Ubuntu can't install proprietary drivers by default. But this Broadcom chipset is widespread enough that this problem makes it impossible to close [Bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1").

How can we make this better for Ocelot final?

---

### Post by CTenorman on 2011-09-23
The particularly tricky bit at the moment is that even after installing the broadcom STA driver and rebooting, the driver still doesn't seem to be doing anything on some systems (mine included).

I love linux and Ubuntu, so I'd love to help diagnose this problem any way I can before 11.10 goes final. I suspect a lot of linux die-hards would be willing to pay money to help solve these problems - if we contributed a bit each, together we could amass enough to get some real development behind making sure all the little things just work without tweaking. If I knew that throwing $100, along with other people doing the same, would essentially solve the linux wireless problem, I would do it in a heartbeat, and I bet thousands would as well. I use linux not because I'm cheap but because I believe it's technically superior, more powerful, and more ethical. My time is worth money, and $100 to never worry about wireless again on 99% of machines I would encounter is absolutely worth it to me. Would other people feel the same way?

---

### Post by cariboo on 2011-09-23
> **Mykro said:**
> I'm afraid this really is a stumbling block.  I'm trying out Ubuntu 11.10 from the perspective of a new user, because I want to distribute live CDs and demonstrate it to a group of Windows users.   I'd love them to be able to go home and try it on their own machines.

So I boot Ocelot beta 2 up on a Dell Precision M4300 and get to the Live CD desktop.  Internet doesn't work, and (pretending to be a new user) I don't see anything that might get my internet working.  Note that the empty wireless indicator looks like a piece of pie, and not something that suggests wi-fi!  Lets say I happen across it anyway, and click "Edit Connections".  Aha, a 'Wireless' tab.  I try to Add a Connection, and I see a page of fields for SSID, Mode and MAC addresses. Gah!

Now, we know that's not the right approach without functioning drivers, but a new user wouldn't know that.  They'd get all bogged down in this dialog.

Let's say that I give up on this dialog and go back to the notifications panel.  I discover the "Additional Drivers", spot the "Broadcom STA wireless driver" and install it.  Great!  Now it says all I have to do is reboot and the driver will start working.

Umm.  I'm using the LiveCD.  Our new user just wasted another 10 minutes rebooting to find they're back where they started!

Say I install the driver again, and this time I don't reboot. Because sometimes it works on Windows right - you can install things and ignore the reboot prompt, and it still works.   In fact, if I go into the Additional Drivers a second time, the Broadcom driver is marked as green and activated.  So maybe I don't need to reboot after all!  But no dice.  The wireless is definitely not working (despite the green status). The Broadcom wireless driver really does need a reboot.

At this point about 50% of new users might think to use an ethernet cable.  And 50% of new users will just give up and throw the live CD in the drawer.

I get it - I know the ideological reasons why Ubuntu can't install proprietary drivers by default. But this Broadcom chipset is widespread enough that this problem makes it impossible to close [Bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1").

How can we make this better for Ocelot final?

Please don't use an interim release to demo Ubuntu, there are and will be enough problems even shortly after release to make yourself look silly. When demoing Ubuntu, always use an LTS release, at least it is fairly stable, and is designed to be used by average users. You can show them Oneiric, so they have an idea what is coming in the next LTS release, but you should stress that it is an experimental release, and not recommended for installation by new users.

---

### Post by TheNessus on 2011-09-24
I'm gonna try the 32 bit version of 11.10 and see if I get the same bugs with either internet slowness or not being able to install propriety drivers.

---

### Post by ventrical on 2011-09-24
> **TheNessus said:**
> I'm gonna try the 32 bit version of 11.10 and see if I get the same bugs with either internet slowness or not being able to install propriety drivers.

Thats what I did on my 64bit Acer Extensa 4420!!

32 bit is much easier .. and the speed and efficiency gain isn't really that much.\

btw..  I was unable to replicate how I fixed my broadcom issue with Natty.

---

### Post by CTenorman on 2011-09-24
Ah, I've found the source of my problem - my 1015pem's internal wireless card is toast. After re-installing windows and setting up the driver, it does the exact same thing as in Ubuntu - it sees the network, tries to connect, and simply can't. The machine has connected to the network in the past, and about 6 or 7 machines are using it right now, so I'm pretty sure the router isn't the problem. So it must mean the network card is fried - how odd!!

Sorry if I got anyone researching a problem which doesn't exist - I've just never experienced a wireless card frying out like this before.

Given the netbook's small size I'm looking for a wee adapter that will do the job, and according to this post ([http://ubuntuforums.org/showthread.php?t=1730137]("http://ubuntuforums.org/showthread.php?t=1730137"), the super-micro sized Belkin n150 micro usb should do the job out of the gate in Oneiric.

Again, sorry for the trouble everyone. And thanks for being such a supportive community, it's great to have you all around!

---

### Post by TheNessus on 2011-09-24
ok, 
I have normal (like in WIndows and previous releases) connectivity using native (non-propriety) driver with the 32 bit version. 
i could not, however, install propriety drivers, despite not having the "held packages" error... which is a small improvement.

---

### Post by cariboo on 2011-09-24
What errors do you get when trying to install the proprietary drivers?

---

### Post by TheNessus on 2011-09-24
> **cariboo907 said:**
> What errors do you get when trying to install the proprietary drivers?

no errors, just bugs. Jockey has a green light, says I have Broadcom-sta, but it does not work. I have to uninstall it and reboot in order to have a usable wireless again. When I either install bcm43 or broadcom-sta in synaptics it is the same. blacklisting or whitelisting any drivers doesn't change anything. cli commands to activate drivers do nothing. only non-propriety works (works good only on 32 bit, very slow [on occasions] with 64).

---

### Post by cariboo on 2011-09-24
Can you run:

```
sudo apt-get --reinstall bcmwl-kernel-source
```

and post the output?

---

### Post by TheNessus on 2011-09-25
the-nessus@thenessus-Inspiron-N3010:~$ sudo apt-get --reinstall bcmwl-kernel-source
[sudo] password for the-nessus: 
E: Invalid operation bcmwl-kernel-source

---

### Post by ventrical on 2011-09-25
> **CTenorman said:**
> Ah, I've found the source of my problem - my 1015pem's internal wireless card is toast. After re-installing windows and setting up the driver, it does the exact same thing as in Ubuntu - it sees the network, tries to connect, and simply can't. The machine has connected to the network in the past, and about 6 or 7 machines are using it right now, so I'm pretty sure the router isn't the problem. So it must mean the network card is fried - how odd!!

Sorry if I got anyone researching a problem which doesn't exist - I've just never experienced a wireless card frying out like this before.

Given the netbook's small size I'm looking for a wee adapter that will do the job, and according to this post ([http://ubuntuforums.org/showthread.php?t=1730137](http://ubuntuforums.org/showthread.php?t=1730137), the super-micro sized Belkin n150 micro usb should do the job out of the gate in Oneiric.

Again, sorry for the trouble everyone. And thanks for being such a supportive community, it's great to have you all around!

  It happens more often than not. ESD thermal runaway .. etc..

Some of those cards come without any attennae also ?? and it's no wonder they don't work.

---

### Post by wildmanne39 on 2011-09-25
Hi, try this way please:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Thank you

---

### Post by ventrical on 2011-09-30
I just had some time to experiment on my Dell Inspiron B130 with the Broadcom b4313 wl. I remember now what has to be done. we had some problems with Maveric and beta testing natty. Installing the b43kernel etc.. caused the actual hardware to TURN-OFF and the way to get the driver working was to turn the wireless card back on . The b4313 hardware was prone to this bug. I was able to replicate the problem here on my Natty install by using a pendrive with Oneiric Beta 2 installed , install the b43-kernel-source, and , voila', when I  rebooted after removing the Oneiric pendrive the b4313 was turned off by default.

  On the Dell Inspiron B130 there is an F key <F2> that has a little icon transmitter tower in blue. All that had to be done to get the b4313 driver to work again is to hit the function key and the F2 key (with the tower icon on it) and it was turned back ON.

The downside is that I was not able to get this technique to work with Oneiric.

---

### Post by TheNessus on 2011-10-04
> **wildmanne39 said:**
> Hi, try this way please:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Thank you

same.


update:
recent updates made Jockey succesfuly install Broadcom sta driver. However, upon rebooot, I still use the default open source driver. I don't know how to activate broadcom sta...

Ventrical, that is very interesting. Sadly though since the open source driver now still works when installing the propriety I can't check this out.

---

### Post by wildmanne39 on 2011-10-04
Hi TheNessus please post the results of these commands:
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
dmesg | grep wlan0
```
Thank you

---

### Post by davidryderuk on 2011-10-07
Hi,
I managed to get the wl module working by blacklisting bcma and brcmsmac. Does this work for anyone else?

---

### Post by nmabukhdeir on 2011-10-08
This worked for me, I have a Thinkpad X120e with the optional a/g/b/n wireless card, a Broadcom BCM43224:

1) Install the Broadcom STA driver via jockey (Additional Drivers application).
2) Follow the instructions to blacklist the bcma module and de-blacklist the brcmsmac module as follows:

     > sudo nano /etc/modprobe.d/broadcom-sta-common.conf
3) Change "blacklist brcmsmac" to "# blacklist brcmsmac" (comment it out)
4) Add to new line "blacklist bcma"
5) Check the output of "dmesg" to see if the card was recognized
5) Restart the machine, should work now

Hopefully this helps, if this works for other people please respond so I can submit a bug report.

---

### Post by davidryderuk on 2011-10-08
Hi,
I'm glad your card is working. I think the link I posted may have been a bit confusing though. I found that both the bcma and brcmsmac modules had to be blacklisted to get the wl driver working.

---

