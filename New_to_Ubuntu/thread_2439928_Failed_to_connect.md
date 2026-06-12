---
title: "Failed to connect"
date: 2020-04-03
forum: New to Ubuntu
---

### Post by pierro974 on 2020-04-03
Hello guys,

I am very new with Ubuntu and I have some issues from the start and can't seem to find the solution anywhere.

I have a Lenovo B590 and installed Ubuntu from a USB flash drive. The installation seemed to be fine.

However when I start my laptop, after I type in my login and password I get the following message from the command line :

0 packages can be updated
0 updates are security updates.

Failed to connect to [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts). Check your Internet connection or proxy settings

I have tried many things especially to try to fix the network as I believe the problem is mostly because of the internet connection. 
One of the few command that works is **sudo lshw -C network** and it shows *network DISABLED for both Wireless interface and Ethernet.

Also on some of the videos I found some people seem to have access to a mouse and I do not have one on my screen. 

Can someone please tell me how to fix this ?

Thank you,

---

### Post by threezee on 2020-04-03
I could be way off-track here but have to ask. Which version of ubuntu did you install? And was it a server or desktop edition?

---

### Post by pierro974 on 2020-04-03
It is a laptop and I believe the version of Ubuntu is the 18.04.4 LTS version 

I believe the main issue is that I cannot activate the WIFI so most of the actions are not permitted.

---

### Post by CelticWarrior on 2020-04-03
> **pierro974 said:**
> It is a laptop and I believe the version of Ubuntu is the 18.04.4 LTS version 

Ubuntu 18.04 is fine as in "should work" but I would use newer anyway. Ubuntu 20.04 is about to be released and is very stable already -and- it may already support your WiFi device out of the box -and-, unlike 18.04, it automatically installs Nvidia drivers.

> I believe the main issue is that I cannot activate the WIFI so most of the actions are not permitted.

Not really but it surely makes the things you need to do harder.
So...
If you have an alternative internet connection like Ethernet (cable) or even USB tethering using your phone then 1) install all updates and 2) open Additional Drivers and install the recommended Nvidia drivers (required for optimal performance).
The next step is troubleshooting the WiFi which is likely just a matter of installing drivers. Again, an alternative internet connection is sort of needed.

---

### Post by pierro974 on 2020-04-04
I tried connecting it to the Ethernet cable and the same messages appear.

---

### Post by CelticWarrior on 2020-04-04
Just in case, open UEFI ("BIOS") settings and disable Secure Boot.
And, again, if nothing else works, use USB tethering from your phone.

---

### Post by TheFu on 2020-04-04
One problem at a time, per thread, please.

Please post the command and output of:
[B]
sudo lshw -C network
[/B]
That command will show both wifi and wired information so we can decide which is easier to get working.

No way should a non-developer/non-tester run 20.04 yet.  Not everyone has the same level of adventure. The risks just aren't worth it.

---

### Post by pierro974 on 2020-04-04
I tried to open the UEFI and disable Secure Boot with that : **sudo mokutil --disable-validation**[COLOR=#333333][FONT=&quot].

And that does not even work when I type in the password it does not do anything or says invalid character :(

Is there another way to disable Secure Boot or am I doing something wrong ?[/FONT][/COLOR]

---

### Post by pierro974 on 2020-04-04
[COLOR=#000000]Result of : [/COLOR]**sudo lshw -C network**[COLOR=#000000]

*WIFI network DISABLED  

*Ethernet network DISABLED[/COLOR]

---

### Post by TheFu on 2020-04-04
Should see something like this:
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 03
       serial: 0c:9d:xx:xx:xx:xx
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.4.0-k duplex=full firmware=0. 6-1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:29 memory:f6600000-f661ffff ioport:d000(size=32) memory:f6620000-f6623fff
```

If not, then check that the devices aren't disabled in the BIOS.

---

### Post by pierro974 on 2020-04-05
When [FONT=Ubuntu Mono, monospace][COLOR=#000000]sudo lshw -C network[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]I get *-network DISABLED[/COLOR][/FONT]
[FONT=Ubuntu Mono, monospace][COLOR=#000000]description: Wireless interface[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]*-network DISABLED[/COLOR][/FONT]
[FONT=Ubuntu Mono, monospace][COLOR=#000000]description: Ethernet interface[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]I tried restarting it connected with the Ethernet cable nothing changed. And also tried the [/COLOR][/FONT][B]sudo mokutil --disable-validation


[/B][COLOR=#333333]Still no results so far[/COLOR]

---

### Post by CelticWarrior on 2020-04-05
A few mandatory comments:

[LIST]
[*]UEFI is what replaced BIOS a long time ago. For all intended purposes here the terms are interchangeable. Knowing that you were asked (twice) to open the UEFI ("BIOS") settings either to disable Secure Boot (just in case) and to check whether or not one or both network devices are disabled there (they shouldn't be, obviously, but if they are that would automatically explain why they sow up as disabled).
[*]Twice you were asked to provide the results of a command and twice you didn't post the complete, full, output of that command. Please do it once and for all by selecting everything in the terminal, copying with CTRL+SHIFT+C or with rigth-click > Copy and paste it in your post inside code tags as exemplified in post #10 by TheFu. We already know they're disable, **we need to know what they are **in order to give you advice.
[/LIST]

---

### Post by pierro974 on 2020-04-06
I did try to access the UEFI or BIOS settings to disable the Secure Boot but when I type the password it says invalid character even though I tried multiple times (and I know they are the right characters).

Sorry the mouse is not available or access to my desktop so I had to type everything, hopefully there are not errors. 
Here is the full output of the command **sudo lshw -C network:**

*-network DISABLED
 description: Wireless Interface
 product: BCM4313 802.11bgn Wireless Network Adapter
 vendor: Broadcom Inc. and subsidiaries
 physical id: 0
 bus info: pci@0000:02:00.0
 logical name: wlp2s0b1
 version: 01
 serial: a4:17:31:bc:f1:2d
 width: 64 bits
 clock: 33Mhz
 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
 configuration: broadcast=yes driver=brcmscmac driverversion=4.15.0-76-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
 resources: irq:17 memory:f0500000-f0503fff
*network DISABLED
 description: Ethernet interface
 product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
 vendor: Realtek Semiconductor Co., Ltd.
 physical id: 0
 bus info: pci@0000:03:00.0
 logical name: enp3s0
 version: 07
 serial: 3c:97:0e:76:2e:b7
 size: 10Mbit/s
 capacity: 1Gbit/s
 width: 64 bits
 clock: 33Mhz
 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt-fd 1000bt 1000bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes driver=r8169 driversion=2.3LK-NAPI duplex=half latency=O link=no multicast=yes port=MII speed= 10Mbit/s
 resources: ir:19 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff

---

### Post by CelticWarrior on 2020-04-06
So, here are the very bad news:

If you can't open UEFI settings you're pretty much screwed. The WiFi (Broadcom) needs drivers and Secure Boot disabled but the Ethernet (Realtek) shouldn't need either. They are very likely disabled in the firmware (UEFI) and need to be enabled there, it can't be done from the OS (Ubuntu, Windows, etc.).

If UEFI ("BIOS") is password protected you MUST know that password (and, of course, it has nothing to do with your user's password to start a session in Ubuntu or Windows). You shouldn't have forgot such password if set by you because now you're effectively locked out of your computer in what concerns firmware settings. If the password was set by someone else please ask them.

---

### Post by pierro974 on 2020-04-06
I tried this for accessing the BIOS settings ([https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS))
Type **sudo mokutil --disable-validation**
 Then choose a password of 8 or 10 characters 
 Restart pressing a random key so
 I am on the right page where it says change secure boot
 But when I type the password it does not work. 

The password was not set by someone else as I am the only user. 

If you are saying I am pretty much screwed, should I completely reinstall the Ubuntu version so it could work then ?

---

### Post by TheFu on 2020-04-06
> **pierro974 said:**
> 
Sorry the mouse is not available or access to my desktop so I had to type everything, hopefully there are not errors. 
Here is the full output of the command **sudo lshw -C network:**

if you can't get into the Bios to enable those capabilities, we are stuck.  You'll need to hunt down the motherboard manual and see how to reset that password. Sometimes removing the CMOS battery or moving a jumper to short the memory of the CMOS. This is how the settings get put back to the factory reset values.

i hope you didn't type all that.  Every unix system can "redirect" the output from 1 command to a file.  

```
sudo lshw -C network | tee /tmp/net.log
```
That will show the output on the screen as it also stores it into that file.  Then we can take the file to another system and post it here or elsewhere.  There are hundreds of little things/techniques like this. 
Learn more:  [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)

---

### Post by CelticWarrior on 2020-04-06
I think you're not getting it... At all. 

BIOS/UEFI settings are accessed **BEFORE** any OS loads, not *from *the OS. There's a key you must press immediately after powering on and that varies depending on the vendor and model. Please check your user's manual.

Mokutil is a tool for self-signing unsigned drivers that otherwise would be prevented from loading with Secure Boot enabled. That's why we recommended disabling it, for convenience. But signing drivers is obviously not enough if the device is disabled in BIOS/UEFI.

---

### Post by TheFu on 2020-04-06
> **CelticWarrior said:**
>  
BIOS/UEFI settings are accessed **BEFORE** any OS loads, not *from *the OS. There's a key you must press immediately after powering on and that varies depending on the vendor and model. Please check your user's manual.


+1.   Bios is the firmware for the motherboard/computer, before any OS gets loaded.  i'm unaware of any way to access it once an OS has loaded.

---

### Post by pierro974 on 2020-04-07
I was not getting it indeed, I thought it was a command to access the BIOS. 

I will look into that as I tried when the computer starts and there are no option or keys to press in order to access it.

Apparently not many have used this laptop to access the BIOS.

---

### Post by sdsurfer on 2020-04-07
> Apparently not many have used this laptop to access the BIOS.

Just Googled your model, restart the computer and before it boots up, press F1. I found just tapping the BIOS key (for you, F1) as it boots works best, some say wait until you see the logo. This should get you into the BIOS. From the start it sounds like the hardware for Wireless and Ethernet are just not enabled.

---

### Post by pierro974 on 2020-04-07
You were right, this time I started the computer. I was able to enter the BIOS settings and disabled the Secure Boot.

In Network:

Wake On Lan [AC Only]
UEFI IPv4 Network Stack [Enabled]
UEFI IPv6 Network Stack [Enabled]
UEFI PXE Boot Priority [IPv4 First]
Wireless LAN Radio [On]

Tried turning it on again after disabling the secure boot still same answer for the networks...

---

