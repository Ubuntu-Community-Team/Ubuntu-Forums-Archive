---
title: "Linksys Wireless card only gets 1 Mbps, but 54 Mbps on Windows"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by GreyArea2 on 2008-10-30
I have a Linksys wireless PCI card that I am not able to identify. On Windows, I easily get 54.0 Mbps. On Ubuntu, that drops to a sorry 1 Mbps. Obviously, I'll never be able to upgrade to 8.10 at this rate, so I need help - badly.

Please note that I am a total, absolute noob. I have been using Ubuntu for a while, but most of that has been just using the web and typing stuff. Assume I know nothing technical about computers and you'll stand the best chance of helping me.

Thanks!

---

### Post by GreyArea2 on 2008-10-30
Sorry to double post, but I need to keep this thread visible, or I'll never get an answer.

Anyone?

---

### Post by DoubleMcLovin on 2008-10-30
lets start by opening a terminal window, and typing 
```
lspci -nn
```

and posting its results here.

And you shouldn't worry about double posting to bump within reason. That is outlined in the Do's and Dont's sticky in this forum.

---

### Post by ctarwater on 2008-10-30
I had the same problem when I first started with Ubuntu about 6 months ago and this is the only solution I found that worked.

I forget exactly where I came across this, but here it is:
create a file containing this:

#!/bin/sh -e
#
# Fixes rt2500 speed problem
#

if [ "$IFACE" = "wlan0" ] ; then
 iwconfig wlan0 rate 54M
fi


name it "ralink-fix" (without the quotations), make it executable (an option when you save the file), and put it in the directory "/etc/network/if-up.d/" .

(I had to create the file in my "home" directory and move the file using root access via the terminal: "sudo mv ralink-fix /etc/network/if-up.d/" (again, no quotations)

---

### Post by Zero7 on 2008-10-30
I had same problem with rtl8185 (Airlink) card and I balcklisted rtl8180 driver it was using. Then I used ndiswrapper toconfigure the card with Win98 driver and it is back to 54mbps with 100% qulaity. It used to connect at 54mbps most of the times but quality used to be 7 to 15%

---

### Post by GreyArea2 on 2008-10-30
ctarwater's fix worked, and I now see 54 Mbps - fortunately creating text files is one thing I do know how to do in Ubuntu. Sadly, my internet seems no faster. I still get download speeds measured in bytes per second. I was hoping for kilobytes, at least.

Worse, I seem to have nuked my Ubuntu install by interrupting the upgrade to 8.10. The entire update program consistently dies in a flurry of error messages. Is there any way to repair a broken Ubuntu install? I really, really don't want to start from scratch.

Incidentally, DoubleMcLovin, here are the results of the lspci -nn command; hopefully they make more sense to you then they do to me.

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
00:07.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03bb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [GeForce 8800 GTS] [10de:0193] (rev a2)
02:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2360] (rev 02)
03:06.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
03:08.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev c0)

---

### Post by DoubleMcLovin on 2008-10-31
indeed it does.
```
03:06.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```

Thats your network card. Which is what I wanted to get started on this.

To fix your install you should be able to reboot the computer, then wait for the grub loading message and hit "esc" key to enter the boot options. Boot into the recovery console and there should be an option to fix broken packages. That should do the trick for ya while I work out a solution to your card.

EDIT::

Could you also post the results of
```
iwconfig
```
and
```
ifconfig
```

for me.

---

### Post by GreyArea2 on 2008-10-31
Thanks for the help! I'll go try the recovery fix you suggested, and report back.

EDIT: Didn't work - when I first set up a dual boot with Ubuntu and Vista, I installed EasyBCD on the later, since I couldn't figure out how to edit the Grub boot menu. Thus, Grub is no longer my boot manager, and thus, I need another way into the recovery console. Is there any way to do this?

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Hauer"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:A8:D1:E0   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=51/100  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:d7:a5:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62100 (62.1 KB)  TX bytes:62100 (62.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:10:e4:2e:62  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:10ff:fee4:2e62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18588835 (18.5 MB)  TX bytes:1771471 (1.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-10-E4-2E-62-65-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by DoubleMcLovin on 2008-10-31
Ok, I've been working on your problem, I think I found a solution, though a little technical so if you encounter errors please dont hesitate to post them here. 
Start by running the following in a terminal:

```
sudo apt-get install build-essentials
```

Followed by each of these lines 1 at a time.
```
cd ~
mkdir ~/rt2500
cd ~/rt2500
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -zxvf rt2500-cvs-daily.tar.gz
cd rt2500-cvs*/Module
make
sudo modprobe -r rt2500pci
echo 'blacklist rt2500pci' | sudo tee -a /etc/modprobe.d/blacklist
sudo make install
echo 'rt2500' | sudo tee -a /etc/modules
```


after which, type:
```
sudo gedit /etc/network/interfaces
```

you will want to first save that file as interfaces.back or something similar (you should be able to just go to File-->Save As)

Then delete it all and paste this in its place:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "******"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="*********"
pre-up ifconfig ra0 up
```

Solution courtesy of ernstblaauw on these message boards.

---

### Post by GreyArea2 on 2008-10-31
Thanks again, I'll try this when I get home. As for my install... is there any way to fix this without Grub? I'm still stuck in some bizarre limbo between 8.04 and 8.10.

---

### Post by DoubleMcLovin on 2008-10-31
if you log into a root terminal instead of the GUI you can use the command:
```
apt-get check
```
which if it reports anything broken should be followed by
```
apt-get install -f
```

---

### Post by GreyArea2 on 2008-10-31
Disaster! After following all of your instructions to the letter, my connection has slid back to 1 Mb/s! Worse, my signal strength, which used to be in the nineties, has dropped into the fifties, and has not recovered despite two reboots. It took me fifteen seconds just to load my home page, Google. And my updater is still on the blink, giving me errors no matter what I do. My interpretation of what it's telling me is that I'm stuck in some kind of software limbo between 8.04 and 8.10. And all because of a bad network connection.

I know you're doing your best, but I have to be honest, I'm really not optimistic at this point. Still, I'm open to anything. I'm going to see if I can get the updater to respond. Maybe if I do what it wants, I'll get back to normal.

EDIT: Well, that wasn't such a good idea. I right royally screwed my entire system, so I've installed 8.10 fresh. Good news: I'm looking at a solid 48 mbps right from the get-go. Bad news: graphics card drivers don't work. *sigh*

---

### Post by TNE26 on 2008-12-19
Hi. Im sorry for thread revival, but i followed the suggestions to get the LAN card working on the previous page, and now i have no connection at all. I did exactly what told, and it suddently didnt work. Is there any way of reverting to previous settings?

Help please!! I dont want to reinstall Ubuntu from scratch :(

Edit: Im (almost) a complete noob to ubuntu! So bear with me. Im pretty good at computers usually, but i have no long-termed experience with Ubuntu.

---

