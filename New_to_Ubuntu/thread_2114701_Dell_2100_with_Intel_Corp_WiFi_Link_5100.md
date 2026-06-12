---
title: "Dell 2100 with Intel Corp WiFi Link 5100"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by Loopy4Dodge on 2013-02-10
Heyy,

Brand spankin' new to the forum, and have only tried Ubuntu without success a couple times before.  Want it to work!  System runs with it, and Microsoft is crashing the computer multiple times a day (windows xp sp3).  Should be stable, but I can't figure out what's  wrong and cannae be bothered.

So, issue?  I have a Dell Latitude 2100, ran 10.04.4 on it before (lucid), but the problem was the wifi adapter: Intel Corp WiFi Link 5100.  Am currenhtly running 12.0.4 LTS--but it's cumbersome and takes a while to boot and open programs--XP is still on other half of drive.

I plan to boot from my USB and overwrite my entire drive with 10.04.4 (backups already done--don't want to play with GParted--K.I.S.S.).  Thing is, I don't know how to get a hold of the drivers and proprietary program to run the Intel Corp WiFi Link 5100 wireless card--and I don't want to download a build for a different computer with a different processor.

So--what do I do?  Where can I get the software for this 5100 card after I install 10.04.4? (tried before a couple years ago, and failed miserably...)

THANKS!  And Yee haw for communities like this...

-Loopy4Dodge

---

### Post by cariboo on 2013-02-11
Support for 10.04 desktop ends in April of this year, and much has changed in those 3 years since it was released. I'd suggest you download the iso for 12.04 (available [here]("http://releases.ubuntu.com/precise/")), and install that. 

What you have to keep in mind that drivers for most devices, except those on the very bleeding edge, are included with the kernel package, and unless they are closed source, aren't available as a separate package. Intel has been very good in supporting open source, so by installing the current LTS release, the drivers will more than likely be automagically installed for you.

Actually after writing the above, I did some research, and it seems your device should work with Lucid. I'd suggest you boot from the Live CD, and once at the desktop, open a terminal, and type the following command:

```
sudo lshw -C network > network.txt
```

what the command does is create a text file with a listing of you network hardware similar to this:

```
 sudo lshw -C network
[sudo] password for cariboo: 
  *-network               
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 11
       serial: 00:1b:11:b2:63:65
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 memory:deefc000-deefffff ioport:df00(size=256) memory:deec0000-deedffff
```

I don't have a wireless device on this system, but you should see your wired and wireless devices in the output.

Once you have created the text file called network.txt, copy it to your windows partition, and paste the output in your next post.

---

