---
title: "Slow internet after few mins of use"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by SandiB on 2012-02-27
Hi, as the title says I have been having problems with my internet becoming slow and eventually becoming unresponsive, after just a few mins of browsing. Maybe irrelevant but when I first open browser(chromium) its decent and I've tried doing a speedtest, and it shows speeds at what I normally get but when it starts to slow up I tried it again and it dropped substantially and test only worked after a few attempts.

I recently installed ubuntu 11.10 using usb onto an old refurbed thinkpad X40 that I had lying around but never used as it was painfully slow, to see if would improve it, and if I'm honest I was too scared to install it to my own laptop in case I did something wrong and destroyed my laptop......I really am a beginner.


I want to go ahead and install this on my laptop but if slow internet is the norm, I don't see me going ahead with it, although I really do want to. 

I have looked at some of the other threads that describe similar problems to mine but there seemed to be different solutions to each individual person or I couldn't understand how they went about trying to solve it from the replies.

Looking for some advice, thanks.

---

### Post by LinuxFan999 on 2012-02-27
> **SandiB said:**
> Hi, as the title says I have been having problems with my internet becoming slow and eventually becoming unresponsive, after just a few mins of browsing. Maybe irrelevant but when I first open browser**(chromium)** its decent and I've tried doing a speedtest, and it shows speeds at what I normally get but when it starts to slow up I tried it again and it dropped substantially and test only worked after a few attempts.

I recently installed ubuntu 11.10 using usb onto an old refurbed thinkpad X40 that I had lying around but never used as it was painfully slow, to see if would improve it, and if I'm honest I was too scared to install it to my own laptop in case I did something wrong and destroyed my laptop......I really am a beginner.


I want to go ahead and install this on my laptop but if slow internet is the norm, I don't see me going ahead with it, although I really do want to. 

I have looked at some of the other threads that describe similar problems to mine but there seemed to be different solutions to each individual person or I couldn't understand how they went about trying to solve it from the replies.

Looking for some advice, thanks.
Does this happen in Firefox too?

---

### Post by gandaran on 2012-02-27
wireless or ethernet connection?
if ethernet post the connection information, could be a simple DNS problem.
if the problem is with using wireless post the wireless card and driver info.
> sudo lshw -C network
run command in terminal, post here full output

---

### Post by SandiB on 2012-02-27
Yes, I did start using that but then went for chromium thinking it might just have been the browser that was slow.

> sandib@sandib-ThinkPad-X40:~$ sudo lshw -C network
[sudo] password for sandib: 
  *-network:0             
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:0a:e4:22:ea:1a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:20 memory:d0220000-d023ffff ioport:7000(size=64)
  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 01
       serial: 00:05:4e:4b:aa:58
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-16-generic firmware=N/A ip=192.168.0.7 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
       resources: irq:21 memory:d0200000-d020ffff

---

### Post by wildmanne39 on 2012-02-27
Hi, which one is slow your wireless or wired?
Thanks

---

### Post by SandiB on 2012-02-27
sorry, wireless

---

### Post by wildmanne39 on 2012-02-27
Hi, please try this, just copy and paste for accuracy:

Open a terminal ctrl+alt+t: 
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Then enter your paswword, in the file that opens add a single line:
```
options ath5k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

Make sure to unplug your wired connection.
Thanks

---

### Post by Scott Baker on 2012-02-27
Before we get too much further along, I have what may seem like an odd question. I suspect this is a new installation. Believe it or not, even though you may have checked the box that asked if you wanted to install updates as you were installing Ubuntu, once finished installing, re-boot your machine, go to "update manager" open it and click "check", then watch what pops up. I just finished an install of 11.10 this last weekend on a clients comp. When I checked on updates, the total was just shy of 400!! Remember, this was JUST AFTER installing 11.10. Check to make sure ALL of your updates are current. A lot of the times, this will correct the issues that you can run into. Keep us up to date, and good luck.  [-o<

---

### Post by SandiB on 2012-02-28
@Scott Baker, yes all updates had been installed, got a bit of a shock myself when I saw that there was 380 something updates, just after installing. And there has been a few more updates that have popped up since then.

@Wildmanne I did as you had instructed and have been using the internet for well over an hour with no problem yet, even streaming video which just wasn't possible previously. Hopefully stays this way.

Thanks very much guys for your help, much appreciated. I feel more confident in using this now knowing there's good support out there for noobs like myself. 

Thanks Sandi

---

### Post by wildmanne39 on 2012-02-28
Hi, I am glad I could help, I am sure your wireless will keep working at good speed.

The device you have is almost always fixed by what I asked you to do, that is a very common issue with your wireless.
Enjoy

---

### Post by Scott Baker on 2012-02-28
No problem, Sandi. Best of luck, and welcome to the world of Ubuntu. Hope you enjoy the trip as much as the rest of us.  ):P

---

