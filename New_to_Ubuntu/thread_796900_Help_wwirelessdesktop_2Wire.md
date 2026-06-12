---
title: "Help w/wireless/desktop 2Wire"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by tngcritters on 2008-05-16
Hey:
Hardy detects the networks and many others around here. But (the but just had to be there) it won't connect. I have been reading the forums and will try un-encrypting of the router tonight or in the morning.

I have the 2Wire wireless modem from pacbell. with several pcs on the network and a printer. (the printer will be another issue once I get the internet connection solved).

My wireless card is working.

in the terminal when I type in ifconfig I get
not only wlan0 but also wlan0:avahi (the last one has the ip address)

Any suggestions? 
I am duel booting with ms xp media edition on a HP Pavilion Slimline.

I'm new to Ubuntu but not new to pcs.

TngCritters

You can either email me or post here...
[email]tngcritters@gmail.com[/email]

Thank you!!!!!

---

### Post by oliviacond on 2008-05-16
try manually connect.
click on wireless icon, and select "Connect to other wireless network"

---

### Post by rpwdh on 2008-05-16
Hello,

I'm not sure what kind of card you have but here's what worked on my laptop's Broadcom. hopefully I don't forget anything!

I connected to my router with a wire and installed ndiswrapper by running Synaptic Package Manager (System>Administration). You can type the name into the search bar. Then run Update Manager (System>Administration). 
It prompted me by asking if I wanted to install the card and have it "search and fetch" firmware.

It was all automated after that. Really simple.

I hope I haven't forgotten a step, if so, I'm sure someone will fill in the blanks.

Let us know how you made out!

---

### Post by tngcritters on 2008-05-18
> **oliviacond said:**
> try manually connect.
click on wireless icon, and select "Connect to other wireless network"

Didn't work...

Thanks.

I will keep on trying!!

---

### Post by tngcritters on 2008-05-18
> **rpwdh said:**
> Hello,

I'm not sure what kind of card you have but here's what worked on my laptop's Broadcom. hopefully I don't forget anything!
!

Me too..not know what kind of card...my daughter took the numbers from me and looked it up and said it came from China..and is a generic, no name brand. 
here are the first numbers she used... 00:14:A5:BA:

as for the router its SBC's 2Wire wireless.

I will be trying what you suggested next! but not sure when, trying to do this between kids, work, dogs, and eating...opps forgot sleep!

Keep fingers crossed!! I hope to reply from the Ubuntu!!

---

### Post by sam_delta on 2008-05-18
you can know the chipset of your wireless card by posting the output of the command 
```
lspci
```
go into aplications>accessories>terminal, and type the command of above, post the output'

thx, sam

---

### Post by tngcritters on 2008-05-19
okay..I connected to with a cable and I was automatic on-line..did a bunch of updates etc. 

I d/l (thought I did anyway) the ndiswrapper and I was never asked to install it. I then put the router back in the living room (centrally located to all pc's). And I'm back to where I was when not hooked up to the cable.

I looked up what I have in my pc as way of wireless...
Gemtek v 1.0.4.0
a wireless LAN 802.11 b/g
also said it is a usb wireless (I have an external antenna but the card is internal)...other info on the wireless is the corp name.. Ralink Technology Corp.

I need to get back on line in Ubuntu!! I had a little taste of what it can do and want to explore more!

---

### Post by Shazaam on 2008-05-19
If you could please run the code that sam_delta posted and post the output here it would be greatly appreciated. We need to know more about your cards chipset.
Here is a google search result for Ralink...
[http://www.google.com/search?hl=en&as_q=&as_epq=Ralink+wireless&as_oq=linux&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=&as_epq=Ralink+wireless&as_oq=linux&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)
And the Ralink page....
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by tngcritters on 2008-05-19
> **Shazaam said:**
> If you could please run the code that sam_delta posted and post the output here it would be greatly appreciated. We need to know more about your cards chipset.
Here is a google search result for Ralink...
[http://www.google.com/search?hl=en&as_q=&as_epq=Ralink+wireless&as_oq=linux&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=&as_epq=Ralink+wireless&as_oq=linux&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)
And the Ralink page....
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

okay...here it is...it takes me a bit when using one pc ;o) at least my little drives work on both! :)

+++++++++++++++++++++++++++++

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2) 
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2) 
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2) 
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2) 
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2) 
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2) 
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2) 
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2) 
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3) 
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3) 
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3) 
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) 
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) 
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) 
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) 
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) 
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem 


Thanks for any help!

She

---

### Post by Shazaam on 2008-05-19
Hmm, it didn't show up under pci. Odd.
I realize it's a chore but could you run this code and post the results?
```
lsusb
```

---

### Post by ugm6hr on 2008-05-19
Bizarre...

lspci doesn't list either a wired or wireless card.  When you connected with a wire, presumably it was an ethernet (RJ45) cable?

Give us the output of all the following (if transferring with USB, easier all at once):
```
lshw -C network
ifconfig
iwconfig
iwlist scan
lsusb
```

All commands case sensitive (i.e capital C).

---

### Post by tngcritters on 2008-05-19
> **Shazaam said:**
> Hmm, it didn't show up under pci. Odd.
I realize it's a chore but could you run this code and post the results?
```
lsusb
```

yep I will!

She

---

### Post by tngcritters on 2008-05-19
> **Shazaam said:**
> Hmm, it didn't show up under pci. Odd.
I realize it's a chore but could you run this code and post the results?
```
lsusb
```

This is with the lsusb code:

Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 005: ID 15a9:0004   
Bus 001 Device 004: ID 0781:7101 SanDisk Corp.  
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External) 
Bus 001 Device 002: ID 046d:08cc Logitech, Inc.  
Bus 001 Device 001: ID 0000:0000

---

### Post by ugm6hr on 2008-05-19
> **tngcritters said:**
> This is with the lsusb code:

Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 005: ID 15a9:0004   
Bus 001 Device 004: ID 0781:7101 SanDisk Corp.  
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External) 
Bus 001 Device 002: ID 046d:08cc Logitech, Inc.  
Bus 001 Device 001: ID 0000:0000

Not there either.

Do you have a hardware or BIOS switch for the wifi card?

---

### Post by tngcritters on 2008-05-19
> **ugm6hr said:**
> Bizarre...

lspci doesn't list either a wired or wireless card.  When you connected with a wire, presumably it was an ethernet (RJ45) cable?

Give us the output of all the following (if transferring with USB, easier all at once):
```
lshw -C network
ifconfig
iwconfig
iwlist scan
lsusb
```

All commands case sensitive (i.e capital C).

When I was able to connect it was with a cat cable and I didn't have to do anything...it was there. 
weird how it can detect about 5 wireless's in the area (2 are unsecured and 3 need keys)

lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Wireless interface 
       physical id: 3 
       logical name: wlan0 
       serial: 00:14:a5:ba:30:09 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 


eth0      Link encap:Ethernet  HWaddr 00:18:f3:9a:f9:6b   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:23 Base address:0x6000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:3288 (3.2 KB)  TX bytes:3288 (3.2 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:14:a5:ba:30:09   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wlan0:avahi Link encap:Ethernet  HWaddr 00:14:a5:ba:30:09   
          inet addr:169.254.4.122  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-BA-30-09-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:"2WIRE389"   
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:D0:9E:FA:24:29    
          Tx-Power=27 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     No scan results

---

### Post by tngcritters on 2008-05-19
Hey I'm in Ubuntu right now...
And no I didn't get the wireless to work. Soooo...I moved the router to this room along with the network printer and all that goes with it and found a short cat cable in my pc stash. Yep I'm wired for internet now. 

Now on to my next quest...my monitors resolution! YIKES! the windows are off the grid sort of speak! I will address this issue later..first going to research my monitor and video card! :)

I want to thank all who tried to help. Sorry my pc was not cooperating.

Happy Ubuntu

Sheila

---

### Post by ugm6hr on 2008-05-20
Sorry I couldn't solve this.

Good luck with the monitor issue!

---

