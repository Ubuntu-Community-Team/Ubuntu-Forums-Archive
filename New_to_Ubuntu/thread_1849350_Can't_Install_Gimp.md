---
title: "Can't Install Gimp"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by gemma.laming on 2011-09-24
Hi everybody,
I have just re-installed Ubuntu 10.04

Sadly I cannot install the Gimp, which was on the last installation of Ubuntu - but not this. Now I find that trying to install via the terminal window does not work, and I cannot install it from the Software centre. 

Has anybody got any ideas as to what I can do? 

Thanks. 

BTW three are several other programs I would like to install, but cannot find a way to do this despite their being listed in the Software centre.

---

### Post by Frogs Hair on 2011-09-24
Run the two commands below to see if you are connecting to your software sources and try again. ```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Slim Odds on 2011-09-24
It really helps to know what the symptom of the failure is. What error message to you get?

---

### Post by gemma.laming on 2011-09-24
Thanks Frog's Hair,
when trying the first suggestion,  I got the same problem as when I tried to update the system using the update manager, and it came back with the result: 
 
"An error occurred during the signature verification. The repository isnot updated  (etc) "

I am vey hesitant to want to upgrade, I had enough problems when I moved from Ubuntu 9 to Ubuntu 10 and I have no wish to repeat that experience! What does the upgrade do? Does that mean that I then have Ubuntu 10,10 instead of 10,04? I would prefer to re-install Ubuntu 10,04 from the CD than upgrade.  Sorry.

---

### Post by Slim Odds on 2011-09-24
> **gemma.laming said:**
> Thanks Frog's Hair,
when trying the first suggestion,  I got the same problem as when I tried to update the system using the update manager, and it came back with the result: 
 
"An error occurred during the signature verification. The repository isnot updated  (etc) "

I am vey hesitant to want to upgrade, I had enough problems when I moved from Ubuntu 9 to Ubuntu 10 and I have no wish to repeat that experience! What does the upgrade do? Does that mean that I then have Ubuntu 10,10 instead of 10,04? I would prefer to re-install Ubuntu 10,04 from the CD than upgrade.  Sorry.

Upgrade does not mean what you think that it does. It updates your packages. Update just gets a list of the latest packages. The terminology could be a bit better. Dist-upgrade is the one that does what you thought.

---

### Post by gemma.laming on 2011-09-24
Thanks Slim Odds,
well that is where it all starts, nothing happened at all. Having downloaded it, the package Gimp is not available. 

I tried through the software centre, the terminal window and downloading it from the Gimp website, but nothing has worked.

It worked in the past, seamlessly. I got used to what I consider "hacking" which is using the computer code in the terminal window when I started, so I do have a little understanding of what *should* happen. Actually, what should happen is that it installs. I am having exactly the same problem with Filezilla, it does something and then nothing. No file, no error, no program. I really don't know what is going on!


Gem

---

### Post by gemma.laming on 2011-09-24
Thanks for the reassurance, Frog's

I did the upgrade bit, and it came back " 0 packets upraded, 0 packets newly installed, 0 to ditch, 0 not upgraded" 

in short, nothing has happened with either operation.  What am I doing wrong??!

---

### Post by gemma.laming on 2011-09-24
Would it make sense to re-install the OS entirely?  I was hoping to use the fast internet connection at the library to clear all this trouble up - and I am now in a bigger mess than when I started. Or so it seems. 

Is it possible to save programs like Gimp on a USB stick to install at home? Thanks

---

### Post by Frogs Hair on 2011-09-24
Did you try to install Gimp again after updating your system ? If it the package is still unavailable it may be a server problem , Which are often temporary .

---

### Post by gemma.laming on 2011-09-24
The updating failed, and sent back error messages, and has ever since I re-installed Ubuntu on my new hard disc. Does this mean anything?  I really appreciate the help by the way, I would be running around in circles otherwise!

---

### Post by Frogs Hair on 2011-09-24
Run the first command again and if errors occur , copy & paste the output here in code tags using the # symbol of the reply tool bar .

---

### Post by gemma.laming on 2011-09-24
I have to go off-line now, as the library is closing. I am very disappointed that I could not install the software I needed, nor could I update the machine. It remains a great pity that Ubuntu is not more user friendly.

---

### Post by ajgreeny on 2011-09-24
It sounds to me as though you are not connected at all.  Try the command ```
ping -c 5 www.google.com
``` and report what you see.

---

### Post by Slim Odds on 2011-09-24
It's quite possible that the problem is the libraries firewall.

---

### Post by gemma.laming on 2011-09-24
Good morning everybody.

Thankyou for your responses. AJ Greeny, I pinged as you suggested, the response was 5 packets transmitted, 5 received, 0% packet loss, time 4004ms.

Plus some code that means nothing. I have a slow internet connection thanks to Vodafone whose idea of out of bundle internet speeds means 15kb/s. I am afraid that had I known it would be this slow, I would not have taken out the contract!  Which is why I was at the local library - so that I could use their wireless system. 

Does this help any?

---

### Post by gemma.laming on 2011-09-24
Note: that "quick reply" took Vodafone nearly 10 seconds to process (!!)

---

### Post by gemma.laming on 2011-09-24
Just so that you know, that "quick reply" took nearly 10 seconds to post (!!)

---

### Post by gemma.laming on 2011-09-24
Slim Odds,
this is for me one of the biggest problems with Ubuntu: can you please tell me what "Library Firewalls" are - and further, why am I experiencing this problem now, when in the past I have not? I have run Lucid for quite a while now, and never had this problem, it seems strange that something should crop up like this - and what is more, cause trouble on such a panoramic scale.

---

### Post by Blasphemist on 2011-09-24
Please see this from the apt-get documentation.
> Maintenance commands
```
apt-get update
```
Run this command after changing /etc/apt/sources.list or /etc/apt/preferences . For information regarding /etc/apt/preferences, see PinningHowto. Run this command periodically to make sure your source list is up-to-date. This is the equivalent of "Reload" in Synaptic or "Fetch updates" in Adept.
```
apt-get upgrade
```
This command upgrades all installed packages. This is the equivalent of "Mark all upgrades" in Synaptic.
As you can see this is the same as choosing to reload the package information and mark all software you have to be upgraded if one is available. This does not include doing a distribution upgrade as noted earlier. Again from the documentation.
> ```
apt-get dist-upgrade
```
The same as the above, except add the "smart upgrade" checkbox. It tells APT to use "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary.
 "apt-get dist-upgrade" does not perform distribution upgrade. See [[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) upgrading] for more information.

So still no unwanted distribution upgrade. This is the link to the documentation. [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

As mentioned above, you can keep from doing this "hacking" and use synaptic, the ubuntu package manager GUI. Here is the link to its documentation. [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

You can run synaptic, reload the package information and look at the bottom of the window to see if it has any errors that need fixed. You haven't posted any error information but you can fix those errors in synaptic. See the documentation.

---

### Post by gemma.laming on 2011-09-25
Thankyou Blasphemist,
your exhaustive reply will take me some time to digest. I have looked at the link about AptGet/Howto and realized that it is a little more complex than first meets the eye. I think I need some serious training in software engineering if I am to grasp the full impact of your suggestions. This is not for beginners like me. I was trying to solve a problem, not unwrap twenty more.

Perhaps 11 am and three strong mugs of coffee will have clobbered my poor braincells into some sort of submission whereby I can begin to unravel the complexities of the arguents.

Or it is time I bought Windows 95 and started again?

[Edit added: I was unaware of Frog's response because it was on a following page, which was not obvious at first glance. I only realized there had been a subsequent response later. That is one reason why I had not responded to his suggestion. I will see what I can do to remedy this later this morning. In the mean time, I need to corral my braincells so that they form something a little more useful than the intellectual equivalent of cotton wool.]

---

### Post by gemma.laming on 2011-09-25
Blasphemous,
I appreciated your response, but find the articles you have directed me to well beyond my abilities.

If this is supposed to be easy to use, I am sorry, but this then demonstrates that in all my years of using Ubuntu there is one issue that has dogged my progress with it.  Put simply, Ubuntu is not for beginners, or those who are not software profesionals.

In short, the problems I have had with ubuntu *FROM THE START* are the problems that are facing me now. That in two years of development, Ubuntu has not been made any easier to use, whatsoever. From my perspective, it is harder.

What I want to do is install several small programs, things I was able to do with only a modest degree of trouble in the past - but now to install them I am faced with a mountain of problems that really go well beyond my abilities to deal with.

There are many other issues beyond this, but these problems are small in comparison - problems such as getting a modest printer or scanner to work with the computer. Not big problems, but problems that have made Ubuntu the unfriendly OS it is.

---

### Post by gemma.laming on 2011-09-25
> **Frogs Hair said:**
> Run the first command again and if errors occur , copy & paste the output here in code tags using the # symbol of the reply tool bar .

{Edit: could you tell me what the purpose of the # tag is, please? I am sorry if this shows that I am not competent enough to use Ubuntu, but that has been my problem from the start. Sorry. Should I install Windows? I am being serious.]

Thankyou Frog's Hair,
I am sorry not to have responded earlier, I was not aware that the discussion had run to two pages. By then the time I had at the library was already running short, and my problems had escalated in scale beyond the point where I was comfortable with dealing with them. 

The Command apt-get update gave the following: (it is in Dutch, sorry) 

E: Kon het vergrendelingsbestand '/var/lib/apt/lists/lock' niet openen - open (13: Permission denied)
E: Kon de lijst-map niet vergrendelen

[Not able ot open this file]

May I ask why it is on this occasion that my OS will not open this file, when in the past it was happy to do so?

The command apt-get upgrade gave the following: 

E: Kon het vergrendelingsbestand '/var/lib/dpkg/lock' niet openen - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I would like to ask why I am experiencing these problems with a fresh install of Ubuntu.  As mentioned in my first post this morning, Ubuntu is now harder to use than when I began with Ubuntu 8 two years ago. I face not fewer problems but more. It is deeply frustrating and I can see why people veer away from Linux.

I am sorry if you are offended by this sort of negativity, but it has been my experience of not being skilled enough to perform the simplest tasks with this OS. 

Would a clean install help here? This is a fresh install of Ubuntu, and if this would solve the problem, it would be the easier thing to do (!)

---

### Post by gemma.laming on 2011-09-25
> **Blasphemist said:**
> Please see this from the apt-get documentation.

As you can see this is the same as choosing to reload the package information and mark all software you have to be upgraded if one is available. This does not include doing a distribution upgrade as noted earlier. Again from the documentation.

So still no unwanted distribution upgrade. This is the link to the documentation. [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

As mentioned above, you can keep from doing this "hacking" and use synaptic, the ubuntu package manager GUI. Here is the link to its documentation. [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

You can run synaptic, reload the package information and look at the bottom of the window to see if it has any errors that need fixed. You haven't posted any error information but you can fix those errors in synaptic. See the documentation.

Blasphemist:
whilst your reply was appreciated, as previously mentioned, it goes well beyond my abilities to deal with this. I simply have not a clue where to start with this sort of technical interface. 

If this is supposed to be easy to use, then I need a degree in Ubuntu software development. 

Which I do not intend studying for now.

Should I re-install Ubuntu with a clean install? Would that solve the problem?

---

### Post by gemma.laming on 2011-09-25
I am now doing a fresh install of Ubuntu. if this does not solve the problem, then my problems with Ubuntu will remain.

---

### Post by westie457 on 2011-09-25
> **gemma.laming said:**
> {Edit: could you tell me what the purpose of the # tag is, please? I am sorry if this shows that I am not competent enough to use Ubuntu, but that has been my problem from the start. Sorry. Should I install Windows? I am being serious.]

Thankyou Frog's Hair,
I am sorry not to have responded earlier, I was not aware that the discussion had run to two pages. By then the time I had at the library was already running short, and my problems had escalated in scale beyond the point where I was comfortable with dealing with them. 

The Command apt-get update gave the following: (it is in Dutch, sorry) 

E: Kon het vergrendelingsbestand '/var/lib/apt/lists/lock' niet openen - open (13: Permission denied)
E: Kon de lijst-map niet vergrendelen

[Not able ot open this file]

May I ask why it is on this occasion that my OS will not open this file, when in the past it was happy to do so?

The command apt-get upgrade gave the following: 

E: Kon het vergrendelingsbestand '/var/lib/dpkg/lock' niet openen - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I would like to ask why I am experiencing these problems with a fresh install of Ubuntu.  As mentioned in my first post this morning, Ubuntu is now harder to use than when I began with Ubuntu 8 two years ago. I face not fewer problems but more. It is deeply frustrating and I can see why people veer away from Linux.

I am sorry if you are offended by this sort of negativity, but it has been my experience of not being skilled enough to perform the simplest tasks with this OS. 

Would a clean install help here? This is a fresh install of Ubuntu, and if this would solve the problem, it would be the easier thing to do (!)

Hello.

Apologies for this it is a long post.

The purpose of the # is to show when something has to be typed into a Terminal, that is a command: eg sudo apt-get upgrade. it is also used to paste the output from a terminal command that has a lot of text. The # produces ```
 tags which keep the text formatting from the terminal and makes it easier to read. Another example is [CODE]lshw
``` this command has a lot of text and is a nightmare to read without the formatting as this will show.
First without the tags.


graham@Hope-This-Works-Properly:~$ lshw
WARNING: you should run this program as super-user.
hope-this-works-properly  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2004MiB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0200000-d027ffff ioport:5088(size=8) memory:c0000000-cfffffff memory:d0300000-d033ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0280000-d02fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:d0340000-d0343fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:7000(size=4096) memory:84a00000-84bfffff ioport:84c00000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:6000(size=4096) memory:84600000-847fffff ioport:84800000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:84200000-843fffff ioport:84400000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=4096) memory:d0000000-d00fffff ioport:84000000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:19 memory:d0000000-d0003fff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:50a0(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:50c0(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5400(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0544000-d05443ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d0100000-d01fffff ioport:80000000(size=67108864)
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 02
                serial: 00:16:d4:e4:75:dd
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:21 memory:d0100000-d0101fff
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:d0102000-d0102fff ioport:2000(size=256) ioport:2400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
                resources: memory:d0103000-d010307f
           *-generic
                description: SD Host controller
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:17 memory:d0103400-d01034ff
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
                resources: memory:d0103800-d010387f
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:17 memory:d0103100-d01031ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:5440(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5420(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:9f:c3:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-11-generic firmware=508.1084 ip=192.168.0.100 multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
And now with the tags```
graham@Hope-This-Works-Properly:~$ lshw
WARNING: you should run this program as super-user.
hope-this-works-properly  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2004MiB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0200000-d027ffff ioport:5088(size=8) memory:c0000000-cfffffff memory:d0300000-d033ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0280000-d02fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:d0340000-d0343fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:7000(size=4096) memory:84a00000-84bfffff ioport:84c00000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:6000(size=4096) memory:84600000-847fffff ioport:84800000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:84200000-843fffff ioport:84400000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=4096) memory:d0000000-d00fffff ioport:84000000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:19 memory:d0000000-d0003fff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:50a0(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:50c0(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5400(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0544000-d05443ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d0100000-d01fffff ioport:80000000(size=67108864)
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 02
                serial: 00:16:d4:e4:75:dd
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:21 memory:d0100000-d0101fff
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:d0102000-d0102fff ioport:2000(size=256) ioport:2400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
                resources: memory:d0103000-d010307f
           *-generic
                description: SD Host controller
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:17 memory:d0103400-d01034ff
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
                resources: memory:d0103800-d010387f
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:17 memory:d0103100-d01031ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:5440(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5420(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:9f:c3:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-11-generic firmware=508.1084 ip=192.168.0.100 multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

The error you got when trying to run the apt-get command was caused by not putting sudo at the front.
You wrote ```
apt-get upgrade
```when it should have been ```
sudo apt-get upgrade
```
The sudo bit is necessary when installing things as you are writing to system files which are locked from accidental access. The system does try to protect itself from nasties and also relies on the user for some commonsense.

Hope this explains some things for you.

---

### Post by gemma.laming on 2011-09-25
Thankyou Westie for your response.

I have just re-installed Ubuntu on my disc and am experiencing the same problems as before. Your extended piece on the hash tag helps with hash tags, and explains a great deal about hash tags. Unfortunately, my problem is *not with hash tags*.

Whilst being useful on the forum, it still leaves me unable to install the Gimp. 
Without that and a few other things, Ubuntu and its forum are wholly useless to me as I cannot do my work. My work with this machine is already severely limited by my inability to install such elemental items as printers or scanners. It is a great pity that the compilers of Ubuntu software have not concentrated on making their operating system easier to use. 

I will now be returning to my old hard drive so that I can use the programs that were installed on it there with a previous installation of Ubuntu. This I regard as unsatisfactory, but given that I am not a computer expert, is the only way I can have an (almost) usable computer.

---

### Post by Elfy on 2011-09-25
Please run this and then paste the _whole of the output_ - we need to see what's happening

```
sudo apt-get update &&sudo apt-get upgrade
```

As far as printers and scanners go - that can indeed be pot luck if you happen to have hardware that's not supported. 

If you are having this much trouble using linux then perhaps you should use windows until such time as it gives you less trouble. 

Good luck.

---

### Post by gemma.laming on 2011-09-25
Forest Pixie,
I have just re-installed my old hard drive. Whilst not perfect, it at least allows me to continue with my work.

When the time comes that this disc really does not work, then I will try your suggestion, but in all likelyhood I will be taking the time not to learn more about Ubuntu but of how to install Windows on my computer instead. 

For beginners, it is a far better solution.

At least now I can get back to my html and css coding in peace. That at least I can do. Were ubuntu so easy to use, then this whole conversation would have been unnecessary.

---

### Post by Paqman on 2011-09-25
The first thing to do if you're having trouble reaching any of the repos is to scan for a new one. Open up Software Sources and where it shows what download server you're using change it and pick the option to "select best server" (or similar, i'm going from memeory here). 

It will scan all the possible servers and try and find one that you can connect to at a good speed. If you can't connect to any, then the problem is not on the package manager's side, but is your connection.

---

### Post by gemma.laming on 2011-09-25
Thankyou Paqman
I went to the library yesterday so that I could use a better internet connection (+-300kb/s) but found that the same problem existed there. I had thought, like you, that it was the speed (should I say lack of speed?  This is Vodafone in the 21st century!)

I have retro-fitted my old hard drive, which has all the required programs fitted. Until that finally dies, I have the time to get Windows (of some description) installed on it so that I can go further without all the problems I have had with Ubuntu over the last years.

---

### Post by WasMeHere on 2011-09-25
Gemma,

Instead of leaving linux, maybe it would be a good idea for you to install a system that includes Gimp and other software, that you need. There are 'DVD' live disc iso images that install Linux Mint, which is based on Ubuntu, and can be updated or extended the same way as Ubuntu. If you are used to Gnome, I suggest that you go to your library and download

'linuxmint-11-gnome-dvd-32bit.iso'

and make a live DVD or live USB. Otherwise you can try one of the other versions for example the LXDE light-weight desktop.

Mint is quite easy to install and manage (my daughter prefers it while I stay with Ubuntu). The DVD version is particularly good for you, since you have a slow internet connection at home.

Have fun
Olle

*Edit: Added in the DVD version: 'full multimedia support, VLC, Gimp, Giver, Tomboy, LibreOffice-Base, Java, Samba, additional fonts, backgrounds, themes, icons, and everything that makes Linux Mint a complete, out of the box, operating system'*

---

### Post by Blasphemist on 2011-09-25
I agree that mint may be easier for an inexperienced user. I left a cd of mint with my sister, no high level user for sure, and she installed it and uses it now. She hasn't even needed to ask any questions. 

I do however think downloading the dvd will be a challenge here. If you do try it at the library or anywhere else, try doing it via torrent as that is always much quicker for me. [http://www.linuxmint.com/edition.php?id=82](http://www.linuxmint.com/edition.php?id=82)

Mainly, I think it is time for a few deep breaths. I don't think you give yourself enough credit. If you write HTML and CSS you are perfectly well capable of solving issues that may come up. The link I provided on using synaptic gives you instruction on solving package issues in a GUI. You can do that. Just breathe deeply, look at what the system tells you, evaluate the problem and learn the solution. Just as you would do in creating html and css.

---

### Post by Slim Odds on 2011-09-25
> **gemma.laming said:**
> Slim Odds,
this is for me one of the biggest problems with Ubuntu: can you please tell me what "Library Firewalls" are - and further, why am I experiencing this problem now, when in the past I have not? I have run Lucid for quite a while now, and never had this problem, it seems strange that something should crop up like this - and what is more, cause trouble on such a panoramic scale.

gemma,

I'm not sure what "problem" that you are referring to with Ubuntu. It works perfectly well. When users, such as yourself, have issues there is usually another problem not related to Ubuntu itself.

Linux (of which Ubuntu is a distribution based on the Debian family) has very good networking support. The majority of web servers in the world run Linux, so that should tell us something.

How a computer connects to the Internet and how traffic travels is a fairly complex issue. The "library firewall" that I was talking about manages how computers connect into and out of the local network in that library. It's possible that they are simply not allowing access to the repository that you are trying to get to.

As was mentioned by someone, run "sudo apt-get update && sudo apt-get upgrade" and post the entire output so that we can see what the problem might be.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by gemma.laming on 2011-09-25
Firstly I would like to thank everybody who contributed to this thread. I have not responded individually as several of you have responded on one topic, this being the subject of Linux Mint.

**Olle:** I did try Mint at one time, it had a nice name. That in itself is enough for me. Unfortunately, I could not partition a disc in the way that it needed, so that was that. I have also tried Linux Gem (no guessing why I chose that one!) but whilst it did work, it made a mess of much of my stored data and took months to sort out. So, Ubuntu it was, and  for the last eighteen months, has been my OS. 

I do have a Mac, and I find it harder to use than Linux in day to day usage -but and it is a VERY BIG BUT - I can use printers and scanners. I can print more than one page, without having to buy a new printer. That sort of detail is the sort of thing I sometimes need despite being one of the few businesses that uses digital invoicing and suchlike.

**Blasphemist: **I am afraid that this issue, along with the many others that trouble me with this installation have required more than just a few deep breaths. When the jasmine tea comes out, you know that a copywriter is getting serious. I am using the disc now that had my old installation on it, which did (to a degree) work. The problems of printers, installing software and other miscellaneous problems (like the ones that cropped up with the updates) have all contributed to my being unable to use this effectively. If I want to do anything like this in Ubuntu, it generally takes me a week (or sometimes longer) to work my way through the problem to the best of my ability, and at the end of a mountain of hard work, coding, installing, de-installing and goodness knows what, arrive at the place I started in. Only thankful that the system still worked. 

In short, I am content with my shortcomings, know them well enough to understand that when I ahve a problem in Ubuntu, it is usually beyond my abilities to deal with. I know where my strengths are - and speaking five languages adequately goes to prove my point. But ubuntu is not one of them. Sorry.

**Slim Odds: **I do not agree with you on this. The problems are in my case an inability to install printers which have backends (or whatever they wanted) that worked with Linux, and had special software that would allow them to work. I tried my damndest to get it to work, and after a week went to the local library and printed out what I needed there. Until I bought my mac, that is what I had to do. There is a problem with my update (I don't know the exact wording, but there is an inability to unlock something or other. I have neither the time nor the energy to go into this).  

**For your sake I have run sudo apt-get update** - you will have to shove it through a translator if you don't speak Dutch. Sorry. 

Ophalen:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid Release.gpg [189B]
Ophalen:2 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/main Translation-nl [113kB]
Geraakt [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-nl   
Ophalen:3 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/universe Translation-nl [57,7kB]
Ophalen:4 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-nl [26,1kB]
99% [2 Translation-nl bzip2 0B] [Wachtend op de kopteksten] [Wachtend op de kopbzip2: (stdin) is not a bzip2 file.
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/main Translation-nl       
42% [3 Translation-nl bzip2 0B] [Wachtend op de kopteksten] [Wachtend op de kopbzip2: (stdin) is not a bzip2 file.
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/universe Translation-nl   
13% [4 Translation-nl bzip2 0B] [Wachtend op de kopteksten] [Wachtend op de kopbzip2: (stdin) is not a bzip2 file.
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-nl 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates Release.gpg                 
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-nl
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-nl
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-nl
Ophalen:5 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-backports Release.gpg [198B]      
Geraakt [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                             
Genegeerd [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-nl           
Geraakt [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                 
Geraakt [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                           
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-nl
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-nl
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release 
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-nl
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-proposed Release.gpg
Geraakt [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-nl
Ophalen:6 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-nl [96,5kB]
Ophalen:7 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-nl [26,1kB]
38% [6 Translation-nl bzip2 0B] [Wachtend op de kopteksten]bzip2: (stdin) is not a bzip2 file.
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-nl
8% [7 Translation-nl bzip2 0B] [Wachtend op de kopteksten] [Wachtend op de koptbzip2: (stdin) is not a bzip2 file.
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-nl
Ophalen:8 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-nl [61,9kB]
16% [8 Translation-nl bzip2 0B] [Wachtend op de kopteksten] [Wachtend op de kopbzip2: (stdin) is not a bzip2 file.
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-nl
Ophalen:9 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid Release [57,2kB]                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates Release    
Ophalen:10 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-backports Release [38,5kB]       
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid Release                           
Fout [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-backports Release                      
  
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages          
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-proposed Release
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/main Packages   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/restricted Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/main Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/restricted Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/universe Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/multiverse Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/main Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/restricted Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/main Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/restricted Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/universe Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/multiverse Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-updates/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-proposed/restricted Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-proposed/main Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-proposed/multiverse Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-proposed/universe Packages
395B opgehaald in 5s (70B/s)   
W: GPG-fout: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid Release: De volgende ondertekeningen waren ongeldig: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Er is een fout opgetreden bij het controleren van de handtekeningen. De pakketbron is niet bijgewerkt en de vorige indexbestanden zullen worden gebruikt. GPG-fout: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) lucid-backports Release: De volgende ondertekeningen waren ongeldig: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Ophalen van [http://nl.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release](http://nl.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release)  is mislukt

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
E: dpkg werd onderbroken; u dient 'sudo dpkg --configure -a' met de hand in te voeren om dit te corrigeren. 

[B]The sudo apt-get upgrade gave the following result: 

[/B]E: dpkg werd onderbroken; u dient 'sudo dpkg --configure -a' met de hand in te voeren om dit te corrigeren. [B]

Warning: this is for my current disc, not the one I am having problems with. However I think the outcomes were identical which might prove your point; I am not expert enough to know the difference! If you want, I can swap discs in the morning and see what happens then. 

[/B]Gentlemen, I am extremely tired, and very frustrated with all this. The energy this takes out of me is considerable. This is the time when I am relieved that all the messing around with the OS has not rendered permanent damage to the system. 

Thankyou for your help.

---

### Post by Slim Odds on 2011-09-25
> **gemma.laming said:**
> <cut>
**Slim Odds: **I do not agree with you on this. The problems are in my case an inability to install printers which have backends (or whatever they wanted) that worked with Linux, and had special software that would allow them to work. I tried my damndest to get it to work, and after a week went to the local library and printed out what I needed there. Until I bought my mac, that is what I had to do. There is a problem with my update (I don't know the exact wording, but there is an inability to unlock something or other. I have neither the time nor the energy to go into this).  
<cut>

I was speaking specifically about networking, which is where you seemed to be having issues.

---

### Post by Slim Odds on 2011-09-25
```
dpkg was interrupted, you must "sudo dpkg - configure-a 'to enter by hand to correct it.
```

Did you do what it says?

---

### Post by gemma.laming on 2011-09-26
Slim odds:
"I was talking about networking where you seem to be having problems" - sir! that is only the latest of a whole string of problems. That, in short, is the problem. It is not one problem, but many, and all focus on my inability to program computers in the way that you have to program Ubuntu.

Further to this, you then say "did you do what it says" - how can I do this when I do not know what to do, where to do it, with which commands in which space. I am wholly at a loss on this one and I refer you to the previous paragraph!

In short, Ubuntu is for serious professional computer programmers. Not ordinary people like me.  Sorry, you have proved your case against me.

---

### Post by BlinkinCat on 2011-09-26
> **gemma.laming said:**
> 
In short, Ubuntu is for serious professional computer programmers. Not ordinary people like me.  Sorry, you have proved your case against me.

Sorry for your problems Gemma, but Ubuntu is definitely for "ordinary people". I consider myself a 67 year old newbie who very much enjoys Ubuntu and obtaining the help one needs from time to time in these forums - I hope you get your problems sorted out - :)

---

### Post by WasMeHere on 2011-09-26
I understand that you have really tried, but maybe you would need a little 'hands on help' by someone nearby. (I guess from your system output language, that you live at least 1000 km from me, so I'm not the right guy to do it.)

Once you get across the threshold, that seems high now, you would probably be doing quite well by yourself or with help via the internet.

My scanner and wireless LAN device work out-of-the-box and my printer is made by a company that offers linux printer drivers to be downloaded. Linux used to be difficult, but every year Ubuntu and Mint get much easier to use.

Maybe the best thing for you is to

1. save whatever private data you have from your new disk and then
2. use the whole disk installing Ubuntu or Linux Mint
3. adding new programs using Synaptic should be safe
4. backup your system

*"A **fresh install** and a **backup** so that you can easily get back to a working system, if you manage to break it"*

---

### Post by Paqman on 2011-09-26
> **gemma.laming said:**
> 
Further to this, you then say "did you do what it says" - how can I do this when I do not know what to do, where to do it, with which commands in which space.

Don't worry, it's not at all obvious what to do with that command, and the previous poster didn't really offer a lot of help.

Most computer systems offer a command line where you can enter text commands to make the computer do things. Your Mac and Ubuntu use pretty much the same one, and simple commands from one often work on the other.

To access Ubuntu's command line, hit Ctrl-T, or open up Terminal from the menus. Then copy and paste (or type in) the command the system suggested:
```
sudo dpkg --configure -a
```
You'll need to enter your user password. Nothing will happen when you press the keys, that's normal, just type it in anyway. Hopefully this will fix whatever is broke in your package manager. If it doesn't, or if it spits out errors, please copy the whole error message from the terminal and paste it into a reply here and we'll take a look.

And no, Ubuntu is not just for ubernerds. Although like any computer system it can seem that way when trying to fix things that go wrong with it.

---

### Post by Zill on 2011-09-26
> **gemma.laming said:**
> ...**For your sake I have run sudo apt-get update** - you will have to shove it through a translator if you don't speak Dutch. Sorry...
While everyone here *wants* to help you, please be aware that this is an English language forum and, although your English is obviously impeccable, some of us do not understand Dutch.  You may therefore find that the folk on the [Dutch Ubuntu forums]("http://forum.ubuntu-nl.org/") may be of more assistance in understanding the exact error messages you receive from your system.

I must disagree with your comment that "In short, Ubuntu is for serious professional computer programmers. Not ordinary people like me.".  You most definitely *do not* need to be a computer programmer to use Ubuntu, any more than you need to be a mechanic to drive a car.  You do, however, need to understand how the controls work to "drive" your computer to do what you wish.

One of the fundamentals of this is knowing *how* to install new applications on your PC.  The "apt-get" system is a terminal-based method which simply uses the command "sudo apt-get install packagename".  As long as your apt-get sources.list file is correct this should quickly install your required application and any necessary dependencies.  If you receive error messages then you just need to *read* what they say and take the action they recommend.  If you don't understand exactly what to do then post the error to either/both this forum and/or the Dutch forum and someone will advise.  Note that if you do post such information you should use the "#" code tags in your forum post (as discussed earlier in this thread) as this makes the error info much easier to read than burying it in the general thread text.  To do this just highlight the error info and then click on the "#" code button, which then automatically adds the code tags at the beginning and end of the selected text.

The terminal command-line way of installing software is a simple method and, as such, is often used on these forums as it is far easier to give a short command here than to try to explain exactly what to point and click in a GUI.  Having said that, Ubuntu *does* provide GUI's that install software, simply by point and click.  The two main examples are the "Ubuntu Software Center" and "Synaptic Package Manager".  While the *appearance* of these two graphical applications is different, they are both simply front-ends to the command-line apt-get system and do exactly the same thing.  Just look in your menu(s) and give these applications a try.  You were provided with a link earlier that explained how to use Synaptic - it really is worth reading that as this does make installing software extremely easy.

Don't give up.  Installing software in Ubuntu is actually far simpler (and safer!) than in Windows.  Once you have done this you will discover the magic of Linux and never want to return to Windows.

One final thought...  Please ensure that you have a reliable internet connection while you are installing anything - if it is not then you are inviting trouble, whether on Linux or Windows!

---

### Post by Slim Odds on 2011-09-26
> **Paqman said:**
> Don't worry, it's not at all obvious what to do with that command, and the previous poster didn't really offer a lot of help.

Most computer systems offer a command line where you can enter text commands to make the computer do things. Your Mac and Ubuntu use pretty much the same one, and simple commands from one often work on the other.

To access Ubuntu's command line, hit Ctrl-T, or open up Terminal from the menus. Then copy and paste (or type in) the command the system suggested:
```
sudo dpkg --configure -a
```You'll need to enter your user password. Nothing will happen when you press the keys, that's normal, just type it in anyway. Hopefully this will fix whatever is broke in your package manager. If it doesn't, or if it spits out errors, please copy the whole error message from the terminal and paste it into a reply here and we'll take a look.

And no, Ubuntu is not just for ubernerds. Although like any computer system it can seem that way when trying to fix things that go wrong with it.

Maybe you should read some of the previous posts.

He already opened a terminal and typed:```
sudo apt-get update && sudo apt-get upgrade
```So is it to much to ask that he might be able to figure out that
```
sudo dpkg --configure -a
```might also be input via the very same terminal.

I'm all for some hand holding in these forums but sometimes there is only so much you can do.

I guess I'll have to be more helpful next time.

---

### Post by gemma.laming on 2011-09-26
Slim Odds,
I am sorry but it was not obvious. I am happy that you feel it no longer necessary to hold my hand in this affair; I have found this and several other issues quite beyond me. 

@Zill I wish you well with everything you do. I am English but run a Dutch system so that the spreadsheets work in the appropriate manner for my business. That is why I posted things here,that is all. I agree with you about the command line input of sudo apt-get, however to me it was quite a frightening experience. Having managed it a few times, then it no longer worked which is why I was here. So I re-installed my old hard drive so I have the Gimp until this drive finally dies on me. Not perfect, but this is not a perfect world.

---

