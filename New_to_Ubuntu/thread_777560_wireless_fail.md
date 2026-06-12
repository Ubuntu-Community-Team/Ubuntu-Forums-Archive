---
title: "wireless fail"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mrweektor on 2008-05-01
hey guys, i hate to post such a simple question, but I'm having wireless issues.

Obviously not right now... because i'm on windows, but for some reason my ubuntu boot (fiesty) won't connect.

My abode was recently set up with a new router and it's working flawlessly for me on windows.

I'm pretty new to linux so all i've done is just typed the key into the password window that pops up once you attempt to connect, like 30 times.

I've also tried it under different settings but, the only one that makes sense is 128bit WEP w/ open.

The settings I use in XP are for Open authentication, WEP encryption and I have the password right in front of me so I doubt i've typed it in wrong every time.

what else can i try to get this figured out?

thnx ladies & gents
-week

---

### Post by Ichido on 2008-05-01
Always Check that the correct Drivers are being loaded.
Does your PC(fiesty) 'see' any networks?
I had to use "Open" WEP with only MAC Address Filtering.

---

### Post by wadelewis4 on 2008-05-01
What kind of wireless adapter are you using? Is it PCI or USB? I've had wireless problems with USB wireless devices, I got a generic one once from my ISP that would see the wireless networks but would not connect - and it got really hot to the touch (but it worked perfectly in Windows XP). I think it was a netopia - it was blueish-grayish-purple and quasi-transparent - the size of a standard thumb-drive. I also tried installing a Belkin USB adapter on the same computer - it works fine, though occasionally after leaving the computer unattended for hours overnight, I have to restart the computer to reestablish a connection. It's odd, but chances are if you have a similar device troubling you, getting a PCI wireless adapter would help you out

---

### Post by mrweektor on 2008-05-01
it sees the networks. in fact when I type run iwconfig i get:

```
eth1      IEEE 802.11g  ESSID:"L****l"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:6B:62:A4   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-32 dBm  Noise level=-33 dBm
          Rx invalid nwid:0  Rx invalid crypt:128  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:120   Missed beacon:0
```

i would expect that the correct drivers are installed because it works at school, which is an unencrypted network and it previously worked here(sometimes) before the new router which... was also unencrypted. soooo if that has something to do with the inability to connect to WEP encryption then... i'll see what i can do.

thnx
-week

//edit
lol, k i need to turn off the smilies, it's messing w/ my report... ah quote tags... right... damn, that didn't work either... ah yes code tags FTW.
@wadelewis4: and no this is on a notebook, integrated wireless. sony vaio vgn-n110G... it even has a switch on the side to turn the wireless on and off (which did cause some confusion when i first got it and it wasn't seeing the network!)

---

### Post by mrweektor on 2008-05-01
k looked around the forums a bit and found [this thread]("http://ubuntuforums.org/showthread.php?t=767204&highlight=wireless+drivers").

so i ran lshw and here's the output.

```
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:5a:a7:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:da000000-da000fff irq:18
```

---

### Post by mrweektor on 2008-05-01
i accidently used the back button and it double posted. my bad.

---

### Post by sneeks on 2008-05-01
just a hunch,but in gutsy i changed the encryption to wpa-psk and hey presto all was well,with wep all i had was problems and dropped connections,or no connection,also changed channel from auto to a set one as this helped a lot.
hope this helps.
sneeks.

---

