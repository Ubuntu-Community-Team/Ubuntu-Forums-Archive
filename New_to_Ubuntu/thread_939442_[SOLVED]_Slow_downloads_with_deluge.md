---
title: "[SOLVED] Slow downloads with deluge"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by janes604 on 2008-10-05
Hi I'm having some trouble with deluge. My downloads speed have dropped to less then 15kibs. I used to get over 300 and if i boot back into windows and run utorrent  i still get those speeds.
 
I know my Isp is not throttling me   and i have a 10 mb connection with a 1m up 

I have searched all over but none of the solutions seem to work 

I have:
opened the port in Ubuntu and in router (65530)
i have  tried various combinations of setting my download speed and upload speed along with decreased # of connection 
nothing seems to fix this any help would be great 


TIA

---

### Post by pytheas22 on 2008-10-05
Can you download normal files at high speeds--for instance if you download an ISO from the Ubuntu website, does it go faster than 15KB/s?  If not, perhaps you simply have issues with your network driver.  In that case, post the output of:
```

lshw -C Network
lspci -nn
```

so that we can see if there's a better driver for you to use.

Also, utorrent runs very well in wine.  You may want to try that to see if speeds are also bad there, since you say utorrent works on the same machine in Windows.

---

### Post by janes604 on 2008-10-05
hope this helps 


lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
00:06.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b9] (rev a1)
00:07.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03bb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0e.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0e.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:0f.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a3)
00:12.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a3)
00:13.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a3)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a3)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a3)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0378] (rev a3)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a3)
00:18.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a3)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7900 GS] [10de:0292] (rev a1)
04:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev c0)
0a:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7900 GS] [10de:0292] (rev a1)
darkside604@darkside604-desktop:~$

---

### Post by pytheas22 on 2008-10-05
How are you connected to the Internet--wirelessly or via ethernet?  Also, please post the output of:
```

lshw -C Network
```

That will tell us which driver you're using.

And please let us know whether you can download normal files from websites at higher speeds.  This is important to know.

---

### Post by janes604 on 2008-10-05
all other downloads are normal
  i am connected via my dlink wbr 1310 router and cable modem (ethernet)
 
and as requested 

PCI (sysfs)  

thanks for the help

---

### Post by pytheas22 on 2008-10-05
If other downloads are normal, the problem may be exclusive to Deluge.  Please try installing wine by typing:
```

sudo apt-get install wine
```

Then download the utorrent .exe file from [http://www.utorrent.com/download.php](http://www.utorrent.com/download.php) and save it to your desktop.  Right-click on the icon and select "Open with WINE Windows Emulator" (or whatever sounds closest to that).  It will open and you can load torrents, etc.  Are download speeds equally poor there, using the same settings that you have for utorrent in Windows.

Also, the 'lshw -C Network' output that you provided wasn't what I was looking for--I should have explained it, but after you type that command, you have to wait a few seconds, and you'll get longer output that will look similar to:

```
 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:19:21:85:0d:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.46 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

Please post that information here, as that's what contains what we need to know.

---

### Post by janes604 on 2008-10-06
I am completing the utorrent install and will post the results in a moment 

the lshw -C Network command say i should run as a Super user how do i do that ?


thanks again



Update

I have installed utorrent and have the download speed seem to be a bit better   about 20- 40 kb  also  utorrent tells me that one of the torrents im downloading in deluge is done.... 

i can't seem to get that command to act as you would like

---

### Post by pytheas22 on 2008-10-06
For the command, just type:
```

lshw -C Network
```

then wait a few seconds.  After a maximum of five seconds, the "Warning: you should run this as superuser" and "PCI:SYS" messages will disappear, and you should see output like what I posted above as an example.

Also, if your speeds are improved under utorrent, then I'd blame Deluge itself as the culprit.  You may want to keep running utorrent with a really popular file (the Ubuntu CD ISOs usually have hundreds of seeders and will download very fast, so that's a good file to experiment with) to see what its maximum speed is.

---

### Post by janes604 on 2008-10-06
i did exactly as  u described and it does each step as you said but them just reverts back to the command line prompt uer@userblah blah

any suggestions?

---

### Post by pytheas22 on 2008-10-06
hmmm, that's strange.  What happens if you type:
```

sudo lshw -C Network
```

and then wait a few seconds?  It should not take more than a few seconds to get the full output.  I've never heard of the behavior you're describing before.

---

### Post by janes604 on 2008-10-06
Same thing 

darkside604@darkside604-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
darkside604@darkside604-desktop:~$ sudo lshw -C Network
[sudo] password for darkside604: 
darkside604@darkside604-desktop:~$

---

### Post by pytheas22 on 2008-10-06
That's weird.  I'm not sure what else to suggest.

But at this point, I'm not sure that it matters.  Since you say that you've been able to get significantly better torrent download speeds in utorrent than in Deluge, and you can download normal Web files at full speed, I think it's fair to conclude that there's most likely not a driver problem.  As I said, I think the best thing to do now is to try sharing in utorrent  some really popular torrents with lots of seeders that should give you high download speeds and see if you can reach the same maximum speeds that you see in Windows.

Also, if you want to try a third client option, Ubuntu comes with a default torrent client called Transmission, which you can find under Applications>Internet.  I've never had much luck with it (it seems to have NAT issues) and it doesn't have any but the most basic features, but it also might give you better speeds than Deluge.

---

### Post by gandaran on 2008-10-06
> I have:
opened the port in Ubuntu and in router (65530)
are you running any firewall, like firestarter or gufw?
opening 65530 port is not enough, deluge needs a lot of open ports for fast downloads.

---

### Post by TenPlus1 on 2008-10-06
Try setting "Max Connectoin Attempts" to 12 and see how that helps...  It worked for me...

---

### Post by janes604 on 2008-10-06
GOOD MORNING AND FIRST OFF THANKS TO EVERYONE FOR THERE HELP !!

 seems u torrent has reverted to the same state as deluge SLOW download 5-10kb


Yes i am running a firewall- "fire starter" 

i also changed  max connections to 12 ...no luck with that.

Side note ---> the port i open yesterday #65530 seems to be closed again  as deluge is saying no incoming connections

this was the command i used - is it correct ?

 sudo iptables -A INPUT -p tcp --dport 65530:65535 -j ACCEPT


Thanks agian

---

### Post by gandaran on 2008-10-06
then I recommend you remove firestarter and install gufw [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)
you can setup deluge in the programs tab [http://img67.imageshack.us/my.php?image=example2pq6.png](http://img67.imageshack.us/my.php?image=example2pq6.png)

---

### Post by janes604 on 2008-10-06
So i have updated my firewall and thigns seem sto be good now thanks all i hope this one is solved

---

