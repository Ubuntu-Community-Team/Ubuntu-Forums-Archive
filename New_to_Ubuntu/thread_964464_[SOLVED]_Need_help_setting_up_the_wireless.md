---
title: "[SOLVED] Need help setting up the wireless"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by E. Mark Mitchell on 2008-10-30
LONG POST, I KNOW, I'M SORRY.  But I wanted to get as much initial data to the experts as possible, to help forestall as many lengthy back-and-forth data exchanges as I can.

I must find a way to get my laptop wireless working.  I had it going with a fix that utilized wicd, and that was working out great, but a recent Ubuntu update seems to have wiped out wicd's ability to interpret the wireless card's data: it keeps saying there are no wireless networks in the area, when my wife's laptop reads the 4 or 5 ones normally detectable in our apartment just fine.  I'm currently connected with a network cable, but this solution is clearly not a long-term preference.  I need to get my wireless accessible again.

Anyway, so I need the usual newbie's assistance in getting my wireless working.  I'm not a complete goob as a user, but my facility with raw Linux is minimal at best, so explanations and instructions are going to have to be step-by-step, just to be sure I'm not missing something.

I've run the "apt-get update" and "apt-get upgrade" and the only thing resembling an error that it tells me is that the wicd signature can't be verified because the public key is not available.  I'm not sure, but it doesn't sound like a catastrophic failure message to me.

From previous attempts to get this fixed, I know some of the data you'll need:

putting in "cat /etc/issue" gets me:
Ubuntu 8.04.1 \n \l

putting in "uname -a" gets me:
Linux little-sparky 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

And yes, I named my computer "little-sparky," so sue me.

I don't seem to have the System/Administration menu option for Hardware Drivers any longer; that's a little disturbing, actually.  But it means I can't check again on the system to see if my proprietary drivers for my Atheros wireless chipset are engaged or not.  I didn't know when this got taken out; little bit worrying.

Anyway, to move on to some of the questions that were asked during my initial attempt to get my system working:

putting in "sudo ifconfig " gets me:
eth0      Link encap:Ethernet  HWaddr 00:1b:38:ff:2f:e3  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::21b:38ff:feff:2fe3/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:23591 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:22171 errors:0 dropped:0 overruns:3 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:27772839 (26.4 MB)  TX bytes:2773975 (2.6 MB) 
          Interrupt:22 Base address:0x1000 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1653 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1653 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:86860 (84.8 KB)  TX bytes:86860 (84.8 KB) 

putting in "sudo ethtool eth0 " gets me:
Settings for eth0: 
	Supported ports: [ TP MII ] 
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes 
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes 
	Speed: 100Mb/s 
	Duplex: Full 
	Port: MII 
	PHYAD: 32 
	Transceiver: internal 
	Auto-negotiation: on 
	Supports Wake-on: pumbg 
	Wake-on: d 
	Current message level: 0x00000007 (7) 
	Link detected: yes 

putting in "sudo mii-tool " gets me:
eth0: negotiated 100baseTx-FD, link ok 

putting in "sudo mii-diag " gets me:
Using the default interface 'eth0'. 
Basic registers of MII PHY #32:  1100 782d 0000 0000 01e1 45e1 0001 0000. 
 The autonegotiated capability is 01e0. 
The autonegotiated media type is 100baseTx-FD. 
 Basic mode control register 0x1100: Auto-negotiation enabled. 
 You have link beat, and everything is working OK. 
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control. 
   End of basic transceiver information. 

putting in "sudo lshw -C network " gets me:
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list 
       configuration: latency=0 
  *-network 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 1 
       bus info: pci@0000:02:01.0 
       logical name: eth0 
       version: 10 
       serial: 00:1b:38:ff:2f:e3 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s 

putting in "lspci | grep Ethernet " gets me:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 

See, now, I don't know what any of that really means, is the thing.  Many of the responses are quite different from what I got the first time I put in those commands, back in July when I got the wireless connection working the first time, so I know something's different.  However, I don't know what to make of it, because while I'm a pretty good user, I'm a crappy programmer.

All right.

LONG POST, I KNOW, I'M SORRY.  But I wanted to get as much initial data to the experts as possible, to help forestall as many lengthy back-and-forth data exchanges as I can.

---

### Post by bumanie on 2008-10-31
Look at this thread [http://ubuntuforums.org/showthread.php?t=964321]("http://ubuntuforums.org/showthread.php?t=964321")- it may help. If not I set up an AR242x yesterday using ndis wrapper; [Follow this]("http://ubuntuforums.org/archive/index.php/t-766169.html") to get ndiswrapper working with that card.

---

### Post by E. Mark Mitchell on 2008-10-31
Thanks for the attempt, but I'm having troubles with both of them.

I tried to follow the ndiswrapper instructions, but my skills aren't enough, and every time I tried to unpack the tar file, the terminal just kind of froze, and I couldn't get a command prompt back again.  I told you, I'm a newbie and not a programmer, and the instructions were vague enough that I seem to have messed up in trying to follow them.

I mean, I had to ignore the whole thing about the "Hardware Drivers" thing because that selection no longer shows up in my Administration menu, anyway.

And I couldn't even follow the discussion about backports or madwifi drivers or anything.  I mean, really, I really need step by step directions.  If you can link me to that, and it doesn't futz up at some point, by all means, I'll be happy to follow it.

---

### Post by bumanie on 2008-11-01
Yes... It's all a bit daunting when one is new. No problem ..
Go to terminal and do following code, this will install the c compiler needed to compile the tar.gz file > sudo apt-get install build-essentialThen go to synaptic package manager and type ndiswrapper into the search function - there should be three things listed - check and click apply to download. When you have done that, let me know and I will continue with the rest of the procedure.

---

### Post by E. Mark Mitchell on 2008-11-02
Done and done, good sir or madam.

May I say, I appreciate your step-by-step assistance... precisely what I need.  I hope it won't put you out too much.

---

### Post by ardvark71 on 2008-11-02
> **E. Mark Mitchell said:**
> 
And yes, I named my computer "little-sparky," so sue me.


Hi...

Why the reactive comment? :confused:

So long as your system isn't a fire danger, I don't see anything wrong. ;)

Best Regards...

---

### Post by E. Mark Mitchell on 2008-11-03
> **ardvark71 said:**
> Hi...

Why the reactive comment? :confused:

So long as your system isn't a fire danger, I don't see anything wrong. ;)

Best Regards...

Heh.  Perhaps a little bit defensive about choosing a bit of a whimsical name.  I personally like it, but I suppose I was forestalling mockery with that one.  :D

---

### Post by E. Mark Mitchell on 2008-11-08
bump for attention...

---

### Post by ugm6hr on 2008-11-08
Do you recall how you originally installed the drivers?

Looks like you are running the 32-bit (i686) Ubuntu Hardy.  Some people used ndiswrapper, and other found they could get the madwifi drivers compiled with a fix.

Either way, any kernel update will probably break your wifi - hence the problem.

This is a good How-To link (see the first piece of advice for 32-bit): 
[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)
Make sure that ath_pci is not blacklisted, and ndiswrapper is removed from etc/modules.

Out of interest, your wifi is more easily fixed with Intrepid (8.10)...
Read this: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

---

### Post by E. Mark Mitchell on 2008-11-08
> **ugm6hr said:**
> Do you recall how you originally installed the drivers?
I followed a procedure from... I think it may have been on this board.  I can look it up if you like, but it'll take time I don't have tonight.
> Looks like you are running the 32-bit (i686) Ubuntu Hardy.  Some people used ndiswrapper, and other found they could get the madwifi drivers compiled with a fix.

Either way, any kernel update will probably break your wifi - hence the problem.
Ah.  Well, good to know that, I guess.  In an academic sense, at least.
> This is a good How-To link (see the first piece of advice for 32-bit) - EDIT: Now-outdated - see later post: 
[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)
I'll give that a shot when I have more time.
> Make sure that ath_pci is not blacklisted, and ndiswrapper is removed from etc/modules.
Um... how do I do that?  It kind of has the same effect as adults talking in the Peanuts cartoons...
> Out of interest, your wifi is more easily fixed with Intrepid (8.10)...
Read this: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)
So... are you saying that's what you would recommend?  The Release Notes say a bunch of things, asks me to install a bunch of things... and if you've read above, you know I'm not nearly that capable.

Bumanie above was taking the right tack with me, but seems to have dropped away.

---

### Post by ugm6hr on 2008-11-09
> **E. Mark Mitchell said:**
> I followed a procedure from... I think it may have been on this board.  I can look it up if you like, but it'll take time I don't have tonight.
I would strongly suggest you "subscribe" to, and save somewhere you can find in the future, any advice or how-to you follow, since future breakages can be anticipated (e.g. by kernel upgrades), and are more easily fixed if you know what worked the first time.

> I'll give that a shot when I have more time.
Actually - this is (similar &) better: [http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)
Just one modification for one line (the one that looks similar - and will give you an error): EDIT: Tutorial updated with correct info:
```
wget -O driver.tar.gz http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```
I would anticipate that should work, dependent on what other modifications you have made to your installation (i.e how you installed the first time).  See note below.

> Um... how do I do that?  It kind of has the same effect as adults talking in the Peanuts cartoons...
```
gksudo gedit /etc/modprobe.d/blacklist
```
And delete any line that says *ath_pci*
```
gksudo gedit /etc/modules
```
And remove any line that says *ndiswrapper*

> So... are you saying that's what you would recommend?  The Release Notes say a bunch of things, asks me to install a bunch of things... and if you've read above, you know I'm not nearly that capable.
It's up to you.  Intrepid may have new problems for your hardware - but the wifi will work **following a fresh install** with a simple:
```
sudo aptitude install linux-backports-modules-intrepid
```
For more detail - see here: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by E. Mark Mitchell on 2008-11-17
> **ugm6hr said:**
> I would strongly suggest you "subscribe" to, and save somewhere you can find in the future, any advice or how-to you follow, since future breakages can be anticipated (e.g. by kernel upgrades), and are more easily fixed if you know what worked the first time.

Actually - this is (similar &) better: [http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)
Just one modification for one line (the one that looks similar - and will give you an error):
```
wget -O driver.tar.gz http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```
I would anticipate that should work, dependent on what other modifications you have made to your installation (i.e how you installed the first time).  See note below.


```
gksudo gedit /etc/modprobe.d/blacklist
```
And delete any line that says *ath_pci*
```
gksudo gedit /etc/modules
```
And remove any line that says *ndiswrapper*
Okay.  Okay.  Let's see.

I've got this thread subscribed, and any other thread that helps me, I'll be happy to use, too.

It seemed to work; certainly, a lot of things did happen when I put in the various commands.  I would presume something is working, but I don't know how to check it.

And I checked the blacklist, and I checked the modules.  So, done and done.

Now, I'm not sure what else to do.  On the link you linked to above had some FAQs suggesting ways to check the scanning of networks, etc., and I still can't seem to detect any networks.  Suggestions?

---

### Post by acreech on 2008-11-17
> **E. Mark Mitchell said:**
>  and I still can't seem to detect any networks.  Suggestions?

I have an Atheros AR5007EG card that I use on a 32 bit system. I have found that the following way is the only way that I can get my card to work. 


```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 

```

restart or reboot the computer after you try these and that is how I get mine to work.

---

### Post by ugm6hr on 2008-11-18
> **E. Mark Mitchell said:**
> Now, I'm not sure what else to do.  On the link you linked to above had some FAQs suggesting ways to check the scanning of networks, etc., and I still can't seem to detect any networks.  Suggestions?

Presumably, you have rebooted?  Did you receive any errors during the process?

In System->Administration->Hardware Drivers, make sure the "Support for Atheros Wifi" is not enabled.

Then check the following to see if the driver is installed:
```
lshw -class network
```

---

### Post by E. Mark Mitchell on 2008-11-18
> **ugm6hr said:**
> Presumably, you have rebooted?  Did you receive any errors during the process?

In System->Administration->Hardware Drivers, make sure the "Support for Atheros Wifi" is not enabled.

Then check the following to see if the driver is installed:
```
lshw -class network
```

I came back on to say "REBOOT! I'M AN IDIOT!" and found you'd already suggested the reboot.  It's a very basic thing I should have realized, but damn it, I had all that browsing to do!

Okay!  Now I can see the local wireless routers in the Network Settings program!  One Step Closer!  But not quite active yet...

I can select our home network, put in our router's WPA key and... well, it tries to connect, it does that little bar bouncing from side to side thing that Ubuntu does... but doesn't seem to connect successfully.  Hm.  May need more diagnostics.  Still, one step closer, and all that...

I don't have a Hardware Drivers option under my System>Administration pull-down any longer, as I noted in that gigantic long first post.  I'm still concerned about that; every instruction set seems to think I should have it, and since I don't, that worries me.

Anyway, I ran the test you suggested, and this is what it gave me...

> WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:26:8f:1f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:ff:2f:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

Does that tell you anything about the results?  I think I follow some of it...

---

### Post by E. Mark Mitchell on 2008-11-18
> **acreech said:**
> I have an Atheros AR5007EG card that I use on a 32 bit system. I have found that the following way is the only way that I can get my card to work. 


```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 

```

restart or reboot the computer after you try these and that is how I get mine to work.

I think I'm going in a different direction at the moment, but I'll keep your option in mind if this doesn't seem to work out...  thanks!

---

### Post by acreech on 2008-11-18
There have been other posts suggesting that you change you wireless router settings from WPA and WPA2 to just WPA2. Apparantly it could be make a difference. You might also check to see if your wireless router has "Mac Filtering" enabled. It will only allow listed machines to connect. 

just a couple things to look at. They were the final straws for me to get my wireless working.

---

### Post by ugm6hr on 2008-11-18
> **E. Mark Mitchell said:**
> Does that tell you anything about the results?  I think I follow some of it...

Looks like the driver is correctly loaded now.

The fact that you can see your access point is good.

Perhaps try turning your WPA security off, and trying to connect.  That will at least confirm things are working correctly.

If that works, consider swapping Network Manager with Wicd - that somethimes works in this scenario.

---

### Post by E. Mark Mitchell on 2008-11-24
> **ugm6hr said:**
> Looks like the driver is correctly loaded now.

The fact that you can see your access point is good.

Perhaps try turning your WPA security off, and trying to connect.  That will at least confirm things are working correctly.

If that works, consider swapping Network Manager with Wicd - that somethimes works in this scenario.

My father has my computer on his network; I'll give it a shot when I'm down there Wednesday night for the holiday.  That'll be the test that things are working properly.

Then it's home and probably Wicd.  It's not like I'm unfamiliar with the program <sigh>  And yes, I'm subscribed to this thread for the next time this happens...   :P

---

### Post by E. Mark Mitchell on 2008-11-27
Okay, so I'm typing this wireless at my parents' place.  It works!  Now I just have to get it working at home.  My wife uses WiFi Radar on her laptop, and she didn't have the same problem as I did.  I'll try one thing or another when I get home, and keep y'all posted.

I'm 90% there, and I have you folks to thank for it.  Particularly ugm6hr.  Thank you!  It's help like this that makes Linux something I recommend to people, even when I have problems with it.

---

### Post by E. Mark Mitchell on 2008-11-29
I'm very pleased to report that wicd worked!  I'm wireless again.

Thanks to you all.  What can I do on here to show my thanks?  Is there some kind of rep system?

---

### Post by ugm6hr on 2008-11-29
> **E. Mark Mitchell said:**
> Thanks to you all.  What can I do on here to show my thanks?  Is there some kind of rep system?

Glad to hear you're sorted again.  And you're welcome.

There is an "official" thanking procedure, just so you know about it:
[http://ubuntuforums.org/showpost.php?p=4576145&postcount=16](http://ubuntuforums.org/showpost.php?p=4576145&postcount=16)
Look at The symbols labelled "7" - there is a Thanks feature.  The button used to be a blue ribbon (as in that picture), but it's now a slightly odd looking red ribbon (in same location).

Also - just so you know, there has been a kernel update today.

Each kernel update will require you to repeat the compilation of your driver (copied from [http://ubuntuforums.org/showthread.php?t=792158 ):](http://ubuntuforums.org/showthread.php?t=792158 ):)
```
cd ~/madwifi-*
sudo make clean
make
sudo make install
sudo modprobe ath_pci
```

---

### Post by perspectoff on 2008-11-29
These simple instructions worked for me the first time:

(excerpted from KubuntuGuide at [http://www.kubuntuguide.org](http://www.kubuntuguide.org) ):

Atheros Wireless cards may work automatically with the new kernel, after installing the following package:
 sudo apt-get install madwifi-tools 

The Atheros 802.11 b/g integrated card on my laptop did not work, however, until I installed the drivers manually.

*Download the latest [[http://snapshots.madwifi.org/](http://snapshots.madwifi.org/) 'snapshot' driver from Madwifi]. When I was doing it, the version was:
 madwifi-hal-0.10.5.6-current.tar.gz
*Extract the files
*Make sure your linux headers and build-essential packages are installed:
 sudo apt-get install build-essential
 sudo apt-get install linux-headers-$(uname -r)
*Unload any drivers already running.
 ifconfig ath0 down
 ifconfig wifi0 down
*Change to the directory where you extracted the driver.
 cd <directory_where_driver_unzipped>
*From that directory, run the installation scripts:
 cd scripts
 ./madwifi-unload
 ./find-madwifi-modules.sh $(uname -r)
 cd ..
*Complete the installation by compiling the source and installing it.
 make
 make install
*Add the installed drivers to your system.
 modprobe ath_pci

Following this, Network Manager was able to see the wireless card and I was able to configure everything else (WEP / WPA key, etc.) from there.

Complete instructions are available at [[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) MadWifi UserDocs].

---

### Post by CrimsnDragn on 2008-12-11
> **acreech said:**
> I have an Atheros AR5007EG card that I use on a 32 bit system. I have found that the following way is the only way that I can get my card to work. 


```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 

```

restart or reboot the computer after you try these and that is how I get mine to work.

haven't tried it yet but I have a basic noob question. A part of the instruction dictates you to 

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

how can you do that when you're not connected to a network? aren't you like telling it to download a zip file or something?

---

### Post by E. Mark Mitchell on 2008-12-15
Hate to be a bother, but I just finally got around to doing some of the recent updates, including an update to wicd, and now I got nothing once again.

It can see my network in the area, but when I try and click connect to my home network, it just immediately says it can't connect.  I've checked the login data, and that appears to be correct.  It's just suddenly up and stopped connecting.

I pulled out the old network cable and did the whole madwifi reset thing, but no dice; still nonfunctional.  Thoughts?

---

### Post by CrimsnDragn on 2008-12-16
what's your wireless card? i use AR5007 and i can't even *detect* anything, and i can't turn on the wireless on my computer with the wirelss button...

---

### Post by E. Mark Mitchell on 2008-12-16
> **CrimsnDragn said:**
> what's your wireless card? i use AR5007 and i can't even *detect* anything, and i can't turn on the wireless on my computer with the wirelss button...

All my data is in my first post, basically.

My problem now is possibly new.  Anyone with wicd expertise?

---

### Post by chudder on 2008-12-20
> **acreech said:**
> I have an Atheros AR5007EG card that I use on a 32 bit system. I have found that the following way is the only way that I can get my card to work. 


```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 

```

restart or reboot the computer after you try these and that is how I get mine to work.

I tried this, I also have an Atheros wireless component.  I don't know if it's the same number but I tried the string of commands and it didn't work.

Here is my output:

```
chud@Lappy30X6:~$ sudo -s
[sudo] password for chud: 
root@Lappy30X6:~# echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
root@Lappy30X6:~# apt-get install ndiswrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ndiswrapper-modules-1.9 for regex 'ndiswrapper*'
Note, selecting linux-image-2.6.27-7-generic instead of ndiswrapper-modules-1.9
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Lappy30X6:~# 
root@Lappy30X6:~# wget ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
--2008-12-20 20:30:00--  ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
           => `Wireless_Atheros.zip'
Resolving ftp.work.acer-euro.com... 193.0.238.152
Connecting to ftp.work.acer-euro.com|193.0.238.152|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /notebook/aspire_4710/driver ... done.
==> SIZE Wireless_Atheros.zip ... 2787341
==> PASV ... done.    ==> RETR Wireless_Atheros.zip ... done.
Length: 2787341 (2.7M)

100%[======================================>] 2,787,341   12.3K/s   in 2m 37s  

2008-12-20 20:32:40 (17.3 KB/s) - `Wireless_Atheros.zip' saved [2787341]

root@Lappy30X6:~# 
root@Lappy30X6:~# unzip Wireless*
Archive:  Wireless_Atheros.zip
   creating: Atheros/
  inflating: Atheros/HR2H01WW.zip    
root@Lappy30X6:~# cd Atheros
root@Lappy30X6:~/Atheros# unzip HR*
Archive:  HR2H01WW.zip
  inflating: data1.cab               
  inflating: data1.hdr               
  inflating: data2.cab               
  inflating: ISSetup.dll             
  inflating: layout.bin              
  inflating: net5211.cat             
  inflating: net5211.inf             
  inflating: Notes.txt               
  inflating: setup.exe               
  inflating: setup.ini               
  inflating: setup.inx               
  inflating: setup.iss               
  inflating: SilentInstall.bat       
  inflating: _Setup.dll              
  inflating: ar5211.sys              
root@Lappy30X6:~/Atheros# ndiswrapper -i net5211.inf
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
root@Lappy30X6:~/Atheros# echo 'ndiswrapper' >> /etc/modules
root@Lappy30X6:~/Atheros# apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common

```

granted I haven't tried restarting yet but I'm going to shortly.

thanks for your help

---

### Post by ugm6hr on 2008-12-21
> **chudder said:**
> I tried this, I also have an Atheros wireless component.  I don't know if it's the same number but I tried the string of commands and it didn't work.

This will not work if you don't have the identical wifi card.

Also, in order to install ndiswrapper, you need to be online with a wried connection at the time.

I would suggest you start a new thread of your own with relevant hardware details - as here: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

---

