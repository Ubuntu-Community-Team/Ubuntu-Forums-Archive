---
title: "Compaq Presario C500 Wireless question"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by duckfeet on 2008-07-31
The reason I'm posting here in beginners is because I'm clueless: it's working fine on ethernet cable, but I don't really know where to begin: I have wired hookups on mine, and this lady asked if I'd give this a wack, and I said I'd post on here.  She has 8.04 newly installed, w/built in wireless card, which worked fine on XP, but she had first switched to Kubuntu, then loaded Ubuntu, so it's no longer working, and I don't really know where to start...I have been reading the forums, seeing if there's any basic stuff, but I'm not sure if the downloads are correct for this computer or not...Reading the instructions, it did say to include iwconfig, and ishw -C network, so here goes: thanks in advance, as usual, you'all are who I turn to...

jacki@jacki-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jacki@jacki-laptop:~$ 



jacki@jacki-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:a2:fa:94
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.104 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:0b:3f:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
jacki@jacki-laptop:~$

---

### Post by StageCraft on 2008-07-31
It says that there is a network interface, is that working? and was the interface working in Kubuntu? The description at the start is a little unclear.

I know this sounds basic but is are fwcutter and restricted drivers installed?

---

### Post by duckfeet on 2008-07-31
I'm sorry I hadn't answered sooner: I finally fell asleep, and figured that probably I hadn't put enough information in.  It was someone else's laptop, and they had just put Kubuntu on, and apparently they had no problems connecting, then she said "the Icon just diappeared" and that was the end of it.  So she gave it over to me.  I kind of explained to her that linux is  designed for people who want to work on their *own* computers, and I think she may actually reinstall Windows over this...which actually might be her wisest course...as I spend a lot of time on these forums learning how to take care of my own computer, and am obviously way in beginner mode myself..

But my Ubuntu setup is happily *wired* so I haven't ran into of these wireless problems, until now...but anyway, now she has Unbuntu 8.04 installed, and all I knew to do was to check around on Networks, and see if anything made sense...and nothing did, so if perhaps you--or someone--could just run down to me what I need to check, and where it is, I would be glad--and grateful--to do that...

I don't *think* the interface is working, but I'm not sure what you are asking...what would I need to look for?

I do appreciate the help...this is sort of a thankless project, and you'all have never failed to help me keep plugging away, and I guess I thought maybe I could do the same for her...but if ever there was a case of "blind leading the blind..." this is it.  I even picked up a copy of "Ubuntu For Non-Geeks" but it doesn't have much on this...

geff


> **StageCraft said:**
> It says that there is a network interface, is that working? and was the interface working in Kubuntu? The description at the start is a little unclear.

I know this sounds basic but is are fwcutter and restricted drivers installed?

---

### Post by johwel on 2008-08-01
Hi there,

Some advise from my wireless experience.
I think the wlan0 interface needs to scan. Try the following:

To get the Gnome network manager running:

```

sudo NetworkManager start

```

or if it is already running but for some reason not showing:

```

sudo NetworkManager restart

```

```

sudo iwconfig wlan0 scanning
sudo iwconfig wlan0 ap any

```

Then run iwconfig again to see if an access point has been assigned. If so, u can most likely connect. If it shows "invalid", we are not so lucky.

To fix this problem permanently, u have to inspect a file called iwl3945 in /etc/modules.d/network/rules.d if I remember correctly. There must be a parameter for scanning. Please note that I'm not at my Ubuntu laptop at the moment, but can check tonight.:popcorn:

---

### Post by falcon61102 on 2008-08-01
Being that she just installed she is probably going to have to load new drivers for her card.  It's a common Broadcom problem.  Here is a HowTo that walks you through it.  If you get any errors or get stuck, let me know and I'll help you through it.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

I'm on my way out the door, otherwise I wouldn't just drop a link and go but I figured this could get you started.  Like I said, any questions just post up here and they'll get answered.

---

### Post by duckfeet on 2008-08-01
Thankyou so much: this is exactly what I wanted, which was sort of basic stuff, and my own experience in other areas was that she probably would be needing drivers too, but this way we have something to start with.  I'm seeing her in the morning, and I'll make a copy of this, and we'll see if we can't at least get started in a better way...

I think my excitement over Ubuntu the last few weeks had made her not realize that I actually *like* spending hours fiddling around, downloading stuff, and finding out how this all works...I think she thoght it was just a free replacement for Windows...it is, but we gotta sort of learn, too, how to take care of it...my fault...

Anyway,  again thankyou for help, this'll get us started...

geff

---

### Post by techshack on 2012-02-19
> **duckfeet said:**
> the reason i'm posting here in beginners is because i'm clueless: It's working fine on ethernet cable, but i don't really know where to begin: I have wired hookups on mine, and this lady asked if i'd give this a wack, and i said i'd post on here.  She has 8.04 newly installed, w/built in wireless card, which worked fine on xp, but she had first switched to kubuntu, then loaded ubuntu, so it's no longer working, and i don't really know where to start...i have been reading the forums, seeing if there's any basic stuff, but i'm not sure if the downloads are correct for this computer or not...reading the instructions, it did say to include iwconfig, and ishw -c network, so here goes: Thanks in advance, as usual, you'all are who i turn to...

Jacki@jacki-laptop:~$ iwconfig
lo        no wireless extensions.

Eth0      no wireless extensions.

Wmaster0  no wireless extensions.

Wlan0     ieee 802.11g  essid:""  
          mode:managed  channel:0  access point: Not-associated   
          tx-power=0 dbm   
          retry min limit:7   rts thr:off   fragment thr=2346 b   
          link quality:0  signal level:0  noise level:0
          rx invalid nwid:0  rx invalid crypt:0  rx invalid frag:0
          tx excessive retries:0  invalid misc:0   missed beacon:0

jacki@jacki-laptop:~$ 



jacki@jacki-laptop:~$ lshw -c network
warning: You should run this program as super-user.
  *-network               
       description: Network controller
       product: Bcm94311mcg wlan mini-pci
       vendor: Broadcom corporation
       physical id: 0
       bus info: Pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33mhz
       capabilities: Bus_master cap_list
       configuration: Driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: Rtl-8139/8139c/8139c+
       vendor: Realtek semiconductor co., ltd.
       Physical id: 8
       bus info: Pci@0000:08:08.0
       logical name: Eth0
       version: 10
       serial: 00:16:d4:a2:fa:94
       width: 32 bits
       clock: 33mhz
       capabilities: Bus_master cap_list ethernet physical
       configuration: Broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.104 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network disabled
       description: Wireless interface
       physical id: 1
       logical name: Wlan0
       serial: 00:1a:73:0b:3f:75
       capabilities: Ethernet physical wireless
       configuration: Broadcast=yes multicast=yes wireless=ieee 802.11g
jacki@jacki-laptop:~$



dittto.....i have the same problem...firt i installed ubuntu...but it shwed no wireless networking...thn i thought to switch on to kubuntu....but the condition is same as in ubuntu....i didn't expected this....alas...:(

---

### Post by CharlesA on 2012-02-19
This is an old thread, if you are having the same problem, please create a new thread.

Thanks.

---

