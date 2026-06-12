---
title: "Installing Wireless Drivers... once and for all!"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-11-23
This has been my real nightmare ever since I switched to Linux. The first time, with the newly installed system, it took me one week to get wireless working. I don't know how I did it anymore.

The second time, there was a Kernel update. I don't know what I did, but I somehow managed to ruin the new Kernel in my computer. It didn't boot anymore. I had to use the old Kernel for a long time.

Now, this morning, I upgraded to 8.10. Time to install the Wireless Drivers, but I still have no idea how it is done, and I'm afraid of doing what I did the second time.

So I ask you here, can you please explain to me so I can finally do it without coming here every time, how I can get my wireless up and running?

...and can you please give me the "for dummies" version? <.<

---

### Post by Toshibawarrior on 2008-11-23
A little info is needed first.

What's your computer model?

What's your wireless card model?

What kernel are you using?...

Once I have this info I might be able to help you. If it's an Atheros wi-fi, it shouldn't be that hard to fix...

:popcorn:

---

### Post by marshall.robert on 2008-11-23
well, first we need to find out your wireless card details, model, chipset, who makes it etc

also, sometimes a good thing to do is reinstall ubuntu, not upgrade. upgrades always break things for me...

---

### Post by Michael.Godawski on 2008-11-23
First let's have a look what your wireless device is.

Please post the result of these commands:

```
sudo lshw -C network
lspci
```

---

### Post by Haruki-kun on 2008-11-23
> **Toshibawarrior said:**
> A little info is needed first.

What's your computer model?

What's your wireless card model?

What kernel are you using?...

Once I have this info I might be able to help you. If it's an Atheros wi-fi, it shouldn't be that hard to fix...

:popcorn:

This is an Acer Computer, and it's an Atheros. As for the Kernel, I'm not sure.

What's the the terminal command to find it out? Someone told me once, I believe....

---

### Post by Ryadt on 2008-11-23
Try to see if your card is present in System > Administration > Hardware Drivers. If it is enable it.

---

### Post by Haruki-kun on 2008-11-23
There's one that says "Support for Atheros 802.11 Wireless LAN Cards". And it's enabled.

---

### Post by Haruki-kun on 2008-11-23
>  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:74:73:e9
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:76:09:5f:9a:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


This is the result.

---

### Post by ugm6hr on 2008-11-23
Read (and follow) this: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

In 8.10, you should not have problems with future kernel upgrades either.

---

### Post by Toshibawarrior on 2008-11-23
Yup, everyone here pretty much covered anything i could say. I also have an Atheros card and the "Support for Atheros 802.11 Wireless LAN Cards" works great for me. Let us know how it works for ya!

---

### Post by Haruki-kun on 2008-11-23
I cannot find ath5k being blacklisted anywhere, and the terminal isn't finding it either. What else could it be?

---

### Post by ugm6hr on 2008-11-23
> **Toshibawarrior said:**
> Yup, everyone here pretty much covered anything i could say. I also have an Atheros card and the "Support for Atheros 802.11 Wireless LAN Cards" works great for me. Let us know how it works for ya!

The AR242X (AR5007) requires the newer ath5k driver (or a madwifi patch).

Hence the need for the backports module.

---

### Post by ugm6hr on 2008-11-23
> **Haruki-kun said:**
> I cannot find ath5k being blacklisted anywhere, and the terminal isn't finding it either. What else could it be?

It should not be blacklisted.

Did you install the backports module??

[ath5k backports module (Intrepid)]("apt:linux-backports-modules-intrepid")
If this link gives you a "not found" error, follow the advice [here]("http://ubuntuforums.org/showpost.php?p=4030951&postcount=16") to get to the Software Sources, and select the Updates tab, and make sure the "unsupported, backports" box is ticked. Close and Reload when prompted.

Then click the [link]("apt:linux-backports-modules-intrepid") again.

After that - go back to Software Sources and untick "unsupported, backports", close and reload again to prevent further backports being updated.

---

### Post by Haruki-kun on 2008-11-23
> **ugm6hr said:**
> Did you install the backports module??

I did, just now. The site you linked asked me to look for ath5k being blacklisted ant comment it, but I couldn't find it anywhere.

Anyway, yes, I just installed the backports module. Wireless still not working, though.

---

### Post by nothingspecial on 2008-11-23
Once and for all =

Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/	madwifi-hal-0.10.5.6-r3875-20081105.tar.gz	

```
Unzip it

```
tar -xvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz 	
```


navigate to the extracted file


```
cd madwifi-hal-0.10.5.6-r3875-20081105
```

If you`ve not got the tools necessary for compiling get them
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it

```
sudo make
```

```
sudo make install
```

load the module

```
sudo modprobe ath_pci
```

make it load every time you boot
```

gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file

```
ath_pci
```

save
exit 
reboot

Do not delete the madwifi directory you have downloaded, save it somewhere, in a file in your home directory named madwifi for  example. Every time you get a kernel update it will break. It is very easy to fix.

If you have placed it in your home directory in a file called madwifi then

```
cd ~/madwifi/madwifi-hal-0.10.5.6-r3875-20081105
```

Then

```
make clean

``````
make
```
```
sudo make install
```  every time you get a kernel update.

---

### Post by ugm6hr on 2008-11-23
> **Haruki-kun said:**
> I did, just now. The site you linked asked me to look for ath5k being blacklisted ant comment it, but I couldn't find it anywhere.

Anyway, yes, I just installed the backports module. Wireless still not working, though.

Did you blacklist these?
```
blacklist ath_hal
blacklist ath_pci
```

ath5k should not be blacklisted (hence the need to unblacklist it with # signs if it is).

None of that matters unless the backports module is installed though.

Since it now is... reboot now.

Then the driver should appear in the Hardware Drivers (or possibly automatically enabled).

Good luck.

---

### Post by Haruki-kun on 2008-11-23
> **ugm6hr said:**
> Did you blacklist these?
```
blacklist ath_hal
blacklist ath_pci
```

ath5k should not be blacklisted (hence the need to unblacklist it with # signs if it is).

None of that matters unless the backports module is installed though.

Since it now is... reboot now.

Then the driver should appear in the Hardware Drivers (or possibly automatically enabled).

Good luck.

That's the problem. It's there. I did blacklist those two, and I rebooted the system, and the wireless network is still not appearing.

---

### Post by ugm6hr on 2008-11-23
> **Haruki-kun said:**
> That's the problem. It's there. I did blacklist those two, and I rebooted the system, and the wireless network is still not appearing.

Unusual...

What is output from:
```
modprobe -l *ath*
```

And repeat:
```
lshw -class network
```

If the ath5k driver isn't listed (or ath5k.ko), then the module obviously isn't loading at boot.  This may be something to do with the upgrade rather than fresh install.

Nevertheless, you should be able to manually load it by:
```
echo ath5k | sudo tee -a /etc/modules
```
Followed by a reboot again.

---

### Post by Haruki-kun on 2008-11-23
> **ugm6hr said:**
> Unusual...

What is output from:
```
modprobe -l *ath*
```
It is:
> /lib/modules/2.6.27-7-generic/volatile/ath_hal.ko
/lib/modules/2.6.27-7-generic/volatile/ath_pci.ko
/lib/modules/2.6.27-7-generic/volatile/ath_rate_amrr.ko
/lib/modules/2.6.27-7-generic/volatile/ath_rate_minstrel.ko
/lib/modules/2.6.27-7-generic/volatile/ath_rate_onoe.ko
/lib/modules/2.6.27-7-generic/volatile/ath_rate_sample.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.27-7-generic/updates/ath5k.ko
/lib/modules/2.6.27-7-generic/updates/ath9k.ko


> And repeat:
```
lshw -class network
```
I get:
> WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:74:73:e9
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.11 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:22:c4:6e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:4c:3b:6b:b1:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


I'll try the manual thing in a sec.

EDIT: Manual didn't work either. :(

---

### Post by ugm6hr on 2008-11-24
OK.

Sorry - I had to go to bed, and am off to work now....

But, you do not need to load the module manually - it is loading automatically (see the list of modules).

You can reverse this by editing /etc/modules and adding a # in front of ath5k (since it is not needed).

It appears that ath_pci and ath_hal **are** being loaded though.  Which means you have not correctly blacklisted them.

Nevertheless, the driver allocated to your wifi is now ath5k.  Which is progress...  (compare with your prior lshw on page 1).  But it is "DISABLED" - do you have a hardware or BIOS switch to turn wifi on and off?

I would suggest you try / double-check:
You have blacklisted correctly ath_pci and ath_hal
Unselect the Hardware Drivers Atheros support
Turn on hardware switch

After that - I'm out of ideas with this route (backports module).  There are other ways to do this (similar to with Hardy), but the backports module is the ideal route, since it will not break with future updates.

ath5k should be default in Jaunty - so there's hope for the future!

---

### Post by Haruki-kun on 2008-11-24
> **ugm6hr said:**
> OK.

Sorry - I had to go to bed, and am off to work now....

But, you do not need to load the module manually - it is loading automatically (see the list of modules).

You can reverse this by editing /etc/modules and adding a # in front of ath5k (since it is not needed).

It appears that ath_pci and ath_hal **are** being loaded though.  Which means you have not correctly blacklisted them.

Nevertheless, the driver allocated to your wifi is now ath5k.  Which is progress...  (compare with your prior lshw on page 1).  But it is "DISABLED" - do you have a hardware or BIOS switch to turn wifi on and off?

I would suggest you try / double-check:
You have blacklisted correctly ath_pci and ath_hal
Unselect the Hardware Drivers Atheros support
Turn on hardware switch

After that - I'm out of ideas with this route (backports module).  There are other ways to do this (similar to with Hardy), but the backports module is the ideal route, since it will not break with future updates.

ath5k should be default in Jaunty - so there's hope for the future!

*checked*
There is a button, but it's never worked on Linux. Either way, I gave it a try, still no wireless.

I don't know about ath_pci and ath_hal. I'm sure I blacklisted them exactly as the link you gave me said, and I just checked it over. They are blacklisted the same way.

> blacklist ath_pci
blacklist ath_hal

Unselecting the Hardware Drivers Atheros Support: I think this might be it, but I'm not sure. What should be enabled and what should be disabled?

---

### Post by Haruki-kun on 2008-11-25
*thread bump*

Does anyone have any ideas?

I already downloaded and installed the Windows drivers, and it's still not working. What should I do now?

---

### Post by ugm6hr on 2008-11-26
> **Haruki-kun said:**
> I already downloaded and installed the Windows drivers, and it's still not working. What should I do now?

It's difficult to know exactly why your wifi isn't working.

The comments in this thread might help: [http://ubuntuforums.org/showthread.php?t=967654](http://ubuntuforums.org/showthread.php?t=967654)

It appears that some people have found they have disable / re-enable the device after upgrading to 8.10, while a fresh install solves the issue.

---

### Post by Haruki-kun on 2008-11-26
Alright. Thank you very much for your help. I will attempt a fresh install, then.

---

### Post by SDSL on 2009-05-18
> **nothingspecial said:**
> Once and for all =

Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/    madwifi-hal-0.10.5.6-r3875-20081105.tar.gz    

```Unzip it

```
tar -xvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz     
```navigate to the extracted file


```
cd madwifi-hal-0.10.5.6-r3875-20081105
```If you`ve not got the tools necessary for compiling get them
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```Then compile it

```
sudo make
``````
sudo make install
```load the module

```
sudo modprobe ath_pci
```make it load every time you boot
```

gksudo gedit /etc/modules
```then copy and paste this to the bottom of that file

```
ath_pci
```save
exit 
reboot

Do not delete the madwifi directory you have downloaded, save it somewhere, in a file in your home directory named madwifi for  example. Every time you get a kernel update it will break. It is very easy to fix.

If you have placed it in your home directory in a file called madwifi then

```
cd ~/madwifi/madwifi-hal-0.10.5.6-r3875-20081105
```Then

```
make clean

``````
make
``````
sudo make install
```  every time you get a kernel update.

hello, i just recently upgraded to Ubuntu karmic 9.10
and i lost my wireless driver.. 
trying your notes but here what i get
```

user@user:~/Desktop/madwifi-hal-0.10.5.6-r4016-20090429$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.30-5-generic/build SUBDIRS=/home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-5-generic'
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath/if_ath.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath/if_ath_radar.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath/if_ath_hal_extensions.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath/if_ath_pci.o
  LD [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath/ath_pci.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_hal/ah_os.o
  HOSTCC  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_hal/uudecode
  UUDECODE /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_hal/i386-elf.bin
  UNMANGLE /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_hal/i386-elf.hal.o
  LD [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_hal/ath_hal.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/amrr/amrr.o
  LD [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/minstrel/minstrel.o
  LD [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/onoe/onoe.o
  LD [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/sample/sample.o
  LD [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/net80211/if_media.o
  CC [M]  /home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.o
cc1: warnings being treated as errors
/home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.c: In function 'skb_print_message':
/home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.c:132: error: the frame size of 1072 bytes is larger than 1024 bytes
make[3]: *** [/home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.o] Error 1
make[2]: *** [/home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429/net80211] Error 2
make[1]: *** [_module_/home/user/Desktop/madwifi-hal-0.10.5.6-r4016-20090429] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-5-generic'
make: *** [modules] Error 2
user@user:~/Desktop/madwifi-hal-0.10.5.6-r4016-20090429$ 

```

I'm not sure what to do, your help is much appreciated 
thanks

---

### Post by SDSL on 2009-05-18
nevermind, i was able to get it work using the trunk version
this one
[http://snapshots.madwifi-project.org/madwifi-trunk/madwifi-trunk-r4022-20090513.tar.gz](http://snapshots.madwifi-project.org/madwifi-trunk/madwifi-trunk-r4022-20090513.tar.gz)

for reference: i reached this post from here
[http://www.debianhelp.org/node/14777](http://www.debianhelp.org/node/14777)

thank you all

---

### Post by WinterMadness on 2009-05-18
you need to know what wireless card you have, and youll need to get the driver for it. it has to be the xp driver too, and then you simply load it with ndiswrapper in the terminal. if you dont want to use the terminal, install ndiswrapper and then install ndisgtk

---

### Post by Roadbloc on 2009-05-18
[http://ubuntuforums.org/showthread.php?t=1138528](http://ubuntuforums.org/showthread.php?t=1138528)



this is my thred about it. i hope it helps.

---

