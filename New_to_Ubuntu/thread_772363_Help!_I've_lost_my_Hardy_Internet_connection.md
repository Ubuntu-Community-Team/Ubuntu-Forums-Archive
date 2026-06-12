---
title: "Help! I've lost my Hardy Internet connection"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Roger D on 2008-04-28
Hi

Been getting on fine with Hardy - a real step forward. Then decided it would be nice to try and get my Edimax USB wireless stick working - I'd been connecting to the Internet via an Ethernet cable. The Edimax USB stick used to work with Dapper, but was 'killed' by an upgrade. 

On the advice of the supplier of the USB stick I edited the blacklist file - basically unblacklisting rt73usb (I think this is the driver supplied in Hardy) and blacklisting rt73 (I think this is the driver I'd previously installed for my USB stick).

There was some progress, my Networking Setting changed to show a wireless connection -see attachments. Something then went wrong - it may have something to do with me  trying to unlock the wireless connection - but anyway, the net result is that I've no network connection of any description. Restoring my blacklist file hasn't helped.

I'm sure there's something wrong with Networking Settings - the images shouldn't be 'dimmed out' like this, should they?

All help much appreciated.

Roger D

---

### Post by Nxion on 2008-04-28
Open a terminal window and type:

```
lspci
```

And post the results here.

Also run:

```
iwconfig
```

And post that here as well.

---

### Post by Roger D on 2008-04-28
Thanks for the speedy response. Here's  the output to lspci:

roger@roger-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
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
03:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
roger@roger-desktop:~$ 


And here's iwconfig:

roger@roger-desktop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

roger@roger-desktop:~$ 


If I could just get my Ethernet cable connection working again I'd be grateful.

Roger D

---

### Post by Nxion on 2008-04-28
When you plug in your ether net cable what happens ? Are you able to get an address ?

try this:

```
sudo /etc/init.d/network restart
```

Make sure the cable is plugged in.

What happens ?

---

### Post by amubu on 2008-04-28
i have the same problem 
when i press 

sudo /etc/init.d/network restart
says 

sudo: /etc/init.d/network: command not found

i run from a LiveCD cause me grub is broken (error 17)
no internet when installing also.

funny thing is when i put static IP of my neighborhood he has problem cause someone got his IP

---

### Post by Roger D on 2008-04-28
OK. I did a re-start without my cable plugged in, but with USB stick plugged in - as it always has been. I had no Internet connection, and plugging in the cable made absolutely no difference to anything.

With the cable plugged in  I ran sudo /etc/init.d/network restart, and got the message 'command not found'

Any ideas?

---

### Post by amubu on 2008-04-28
Roger your Ethernet connection works without usb plugged in?
i guess not/ but how can you publish lspci and iwconfig results?
i misunderstood with Hardy did you get any internet connection (before usb stick) or not?

i need help also its possible i have the same problems. 

i use a laptop with a dizzy ac adapter to write to you (30 minutes on every 1 hour) so its very difficult for me to find other posts to solve my desktop problem (grub error).

i repeat that funny thing is when i put static IP of my neighborhood he has problem cause someone got his IP.

you can check it you roger also.

so even if other computers see that i have their ip and with the same cable in this laptop i have internet, when i ping 82.211.81.158 i get 0% successful packets and i have no internet at all. 
you think is a hardy bug problem?
Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

---

### Post by Roger D on 2008-04-28
Sorry, but don't understand a lot of this. I'm able to post to the forum because I'm running two computers - my old Dapper computer, with a working Internect connection, and my new PC, where my wired Ethernet connection used to work, but has ceased working since I tried to get my wireless connection working.

I very much hope this isn't a Hardy bug. As I understand things, all this Internet connection and wireless stuff was supposed to be much easier with the Hardy Network Manager.

Roger D

---

### Post by Nxion on 2008-04-28
> **Roger D said:**
> 
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




This here means that the wireless is working. It is seeing a access point somewhere. 

The more I read you mention that you are using a live disk fot the time being because you can't boot your machine because of a grub error correct ?

---

### Post by Roger D on 2008-04-29
No. I can boot my machine; it's just that my internet connection no longer works, either with a cable or with wireless.

I've tried using a Hardy Live CD, and both wireless and cable work, so my hardware's OK

By the way. I'm using my second Dapper PC to connect to the Forum.

Roger D

---

### Post by Boyohazard on 2008-04-29
When you boot the machine can you choose an older linux-kernel to boot? (You may have to press Esc to get the menu up first)

I'm thinking you may have to roll back and re-upgrade

---

### Post by Roger D on 2008-04-29
Yes, I'm beginning to think I may have to start again, perhaps with a fresh installation, rather than an upgrade. But that seems a pretty desperate step, it will involve quite a bit of work, and what do I do if this happens again? I keep telling myself  there can't be much wrong as my cable connection did work originally.

Roger D

---

### Post by Boyohazard on 2008-04-29
I am 100% certain there's a way to fix this without resorting to a re-install. Unfortunately I don't have the experience with Linux to help you out.

I did something similar; I lost my Internet connection after installing VMWare and I had to manually remove a lot of the vmware files to get it working again.

Sounds like a configuration error somewhere, that's why I suggest the roll back. You can then check if everything works before opting to upgrade, should be less work then a complete re-install.

---

### Post by Roger D on 2008-04-29
Thanks for the advice. Do you mean a roll-back to Dapper. That's OK with me, but how do I do it?

---

### Post by Boyohazard on 2008-04-29
No when you boot up do you have an option menu visible? I don't think it comes up by default you may have to press escape.

You should see a normal boot with linux 2.6.18 (I think) and below that another one with 2.6.17. You may even have a few if you have upgraded from Dapper.

Boot up and let us know if your Internet is back, we can then take it from there.

---

### Post by Roger D on 2008-04-29
OK, pressed ESC, got:

2.6.24-16-38
2.6.24-16-38 (recovery mode)
2.6.15-51-38
2.6.15-51-38 (recovery mode)

Not much choice. Not sure what to do

---

### Post by Boyohazard on 2008-04-29
Boot 2.6.15-51-38

---

### Post by Roger D on 2008-04-29
Been getting some helpful advice from the company who sold me the USB stick. By enabling roaming, I've managed to get the cable connection working - for this relief, much thanks. It also appears that the problem with the USB stick is all down to an error in dev - a result of the upgrade process. There's a bug report out on this 183968. Hopefully, when this is resolved I'll be able to edit my dev file and get wireless working.

Roger D

---

### Post by Boyohazard on 2008-04-29
Excellent news. I have been giving your situation some further thought and might have an alternative solution for you.

You could create a dedicated /home partition (see [_Psychocats - Home partition_]("http://www.psychocats.net/ubuntu/separatehome") and re-install Hardy.

However if the problem lies with your USB stick and /dev then it won't help you much but worth keeping in mind.

---

### Post by Roger D on 2008-04-29
Many thanks - I'll bear that is mind. When this is all sorted, I'll  post the result.

---

