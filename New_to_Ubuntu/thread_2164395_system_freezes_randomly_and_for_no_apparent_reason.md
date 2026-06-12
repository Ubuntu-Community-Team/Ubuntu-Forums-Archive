---
title: "system freezes randomly and for no apparent reason"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by al.adab on 2013-07-31
hello, 

this is affecting a Thinkpad T42 + Xubuntu 12.04. 

have run various flavours of Ubuntu on this machine for almost a decade now, hardly had any issue. Now, all of a sudden (and possibly after a recent update), Xubuntu freezes randomly though frequently. Sometimes I hardly have the time to do anything at all after turning on the machine and loading Xubuntu - other times (like now), I manage to work for an hour or two before it freezes. But sooner or later it does freeze...

I've just re-installed Xubuntu 12.04 (thought it might solve things) and a) the machine froze during the installation routine, b) it still freezes as often as before. 

I'm also wondering if it might be time I replaced my T42...could it be a hardware problem? The machine doesn't seem to overheat and the fan is working fine as usual. How can I find out? 

Thanks a million for your help.

---

### Post by al.adab on 2013-07-31
...sorry, i just wanted to add that - when it freezes - there seems to be nothing i can do other than press the main power switch to force the machine to turn off. I tried the ctrl-alt-delete or ctrl-alt-f1/f2 commands but it didn't work. It's a total freeze, in other words: keyboard, mouse, everything gets stuck....

---

### Post by slw210 on 2013-07-31
What are the full specifications on your Thinkpad T42?

---

### Post by al.adab on 2013-07-31
here you go - there's probably a lot of stuff you won't need, sorry

```
~$ lshw
WARNING: you should run this program as super-user.
t42                       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.6
          size: 1700MHz
          capacity: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:c0100000-c01fffff memory:e0000000-e7ffffff
           *-display
                description: VGA compatible controller
                product: RV350 [Mobility Radeon 9600 M10]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:11 memory:e0000000-e7ffffff ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:c0000000-c00003ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:4000(size=20480) memory:c0200000-cfffffff memory:e8000000-efffffff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:b0000000-b0000fff ioport:4c00(size=256) ioport:4800(size=256) memory:cc000000-cfffffff memory:c8000000-cbffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:b1000000-b1000fff ioport:4400(size=256) ioport:4000(size=256) memory:ec000000-efffffff memory:c4000000-c7ffffff
           *-network:0
                description: Ethernet interface
                product: 82540EP Gigabit Ethernet Controller (Mobile)
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 03
                serial: 00:10:c6:ce:fa:aa
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 mingnt=255 multicast=yes port=twisted pair
                resources: irq:11 memory:c0240000-c025ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:e8000000-e800ffff
           *-network:1
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wlan0
                version: 01
                serial: 00:05:4e:50:ca:5d
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.2.0-51-generic firmware=N/A latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
                resources: irq:11 memory:c0210000-c021ffff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1860(size=16) memory:40000000-400003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:18c0(size=64) memory:c0000c00-c0000dff memory:c0000800-c00008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
  *-scsi:0
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
```

---

### Post by al.adab on 2013-08-01
could it have something to do with the Radeon driver(s)? if it could, any thought about what can be done about it? If Xubuntu 12.04 has got nothing to do about it, I guess it's the display or the motherboard or...

hope someone can help. thanks.

---

### Post by dino99 on 2013-08-01
sorry im not used with xubuntu; but you might find something usefull logged. At first glance im thinking about a possible compiz crash for such trouble; reset it to default.

> dconf reset -f /org/compiz/

and possibly clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit
also glance at the sources.list (no "exotic" entries like untrusted ppas for example)

---

### Post by matt_symes on 2013-08-01
Hi

Can you pin point any change that happened when it occured ?

Do you still get the same issue when running from a live cd/usb ?

As you reinstalled xubuntu and still have the issue, i would suspect/eliminate hardware in the first instance.

What hardware tests have you run ?

EDIT: Can you shutdown by getting to a console ?

Can you shutdown using the magic key combination (alt + sysreq .....) ?

Kind regards

---

### Post by tgalati4 on 2013-08-01
Thinkpads with ATI Radeon graphics chips develop problems over time.  The graphics chip delaminates from the motherboard causing a hard lockup.  You had a good run at 10 years.  You can search youtube for ways of resoldering the chip, but success is low.  Back up your data and start looking for another machine.

Try booting from a Live CD of an older distro.  If your machine stays up for several days, then it could be software-related.  If it locks up while running the Live CD, then you can be reasonably sure that the motherboard has worn out.

---

### Post by al.adab on 2013-08-01
thanks all for your kind advice - i tried a *dconf reset -f /org/compiz/ * though don't really know if it's worked. I understand that it's an old machine and it did lock up while running the live CD so...i'm looking into getting an X230 anyway, but in the meantime would like to try and keep this for as long as I can and as a second machine. So let me answer the questionnaire first :) 
[I]
Can you pin point any change that happened when it occured ?[/I] 
No, I can't. Couldn't see any change in (for example) the screen. In fact, every time it freezes, the screen (colours, light intensity, etc) remains exactly as it is when the pc is working. 
[I]
Do you still get the same issue when running from a live cd/usb ?[/I]
It happened once, the second time it didn't, as it didn't the third time I run it (after that I proceeded to install Xubuntu). 

A*s you reinstalled xubuntu and still have the issue, i would suspect/eliminate hardware in the first instance.*
*What hardware tests have you run ?*
None. Wouldn't know where to start from. 

*EDIT: Can you shutdown by getting to a console ?*
No. Have to use the power button. 

*Can you shutdown using the magic key combination (alt + sysreq .....) ? *
As above. Power button only. 

Will post more if I see any change.

---

### Post by matt_symes on 2013-08-01
Hi

@tgalati4[SIZE=3] [SIZE=2]may have the answer. It sounds like he may have come across this issue in the past.

You can run the usual suit of tests for memory, hard drive, temps etc, but if it is the issue tgalati4 suspects it is then it may be a bigger issue to fix it.

Have you looked in the log files to see if there is anything in them ?

Does the CAPS LOCK keyboard LED flash when the system has hung ? This would suggest a kernel crash.

Does it freeze if you boot into the BIOS and leave that running (leave it overnight or even longer) ?

Kind regards[/SIZE][/SIZE]

---

### Post by Portaro on 2013-08-01
Is an 12.04 , verify if you have installed mesa-utils if not install please, i have a very similar problem with your on 12.04 the only can i do and in part solve my problem is install **mesa-utils.**

In other past posts i relate this problem and in true i dont find the right answer, i try for me and find that mesa-utils help in the graphic performance and probably this is the original problem.

In 13.04 my both pcs that need this "medicine" on 12.04 dont freezes anymore, but / except if you use a pc with battery in short cases the pc freezes in seconds but is very rare , on 13.04.

---

### Post by al.adab on 2013-08-03
so it would appear @tgalati4 is actually right - i haven't run any test for memory, etc, but it did freeze after booting into the BIOS. No flashing of the CapsLock detected. Funny enough, today it hasn't frozen once, and the poor machine has been working way over its capacity and with the fan often working full blast...weird...

---

### Post by al.adab on 2013-08-06
is it possible that it's got to do with the *3.2.0-51-generic* kernel (for any reason, bugs, etc, after all it all started going belly-up after a recent update) and would it be worth trying "downgrade" Xubuntu 12.04 to an earlier kernel? 

it's likely this machine is fried by now, i'd just like to give it a try in the hope it's not *that* fried :) could you please advise on a) which kernel to choose, b) how to safely do the "downgrading" thing on terminal? 

thanks again.

---

### Post by al.adab on 2013-08-06
is it possible that it's got to do with the *3.2.0-51-generic* kernel (for any reason, bugs, etc, after all it all started going belly-up after a recent update) and would it be worth trying "downgrade" Xubuntu 12.04 to an earlier kernel? 

it's likely this machine is fried by now, i'd just like to give it a try in the hope it's not *that* fried :) could you please advise on a) which kernel to choose, b) how to safely do the "downgrading" thing on terminal? 

thanks again.

---

### Post by al.adab on 2013-08-06
thanks tons Portaro, i've just seen your post and downloaded the *mesa-utils* let's see how it goes

---

### Post by al.adab on 2013-08-06
downloading *mesa-utils* hasn't made any difference, i'm afraid. I'm not clear on keeping Xubuntu 12.04 while reversing the latest kernel update(s), so could anyone tell me what to do (in case, as i suggested above) it might be a bug, etc. thanks

---

### Post by andybrassell on 2013-09-14
Hi,

Complete noob here and this is my first ever post however I am currently running a falling to pieces HP G5000 (2x1.73GH Intel processors + 900MB Ram) and I think that I have found a rather suitable work around for 12.04's full system crash / freeze issue (full sys freeze with no mouse movement or caps key light).

Originally my fresh 12.04 install was crashing within half an hour of boot therefore I tried 13.04 and Xbuntu 12.04 only to find the same problem. As such I installed 12.04 again fresh and worked on the basis that my system being low spec might be an issue. I therefore installed Mate 1.6 and began using this desktop environment. Then as freezes continued I installed linux kernel 3.11.0-031100-generic. Then I read somewhere that compiz  and chrome may both be in part to blame and as freezes continued I decided to completely purge these 2 packages. 

This then is where it gets interesting. For if I now log into my Mate 1.6 desktop I have a completely stable session. However you can gaurantee thai if I log into a gnome session or xfce session my system will neeed a hard reboot in at least half an hour. (Incidentally I have noticed that nautilus crashes just prior to freezes in gnome therefore perhaps the mate file manager is mitigating this issue in a mate session). 

Anyway I have been running for 8 days now almost freeze free. I say almost as attempting to log out, restart or switch user in mate still brings on a full freeze but I think this might be a mate bug and its easily avoided. Also I installed virtual box only to discover that a running VM or VM installation also brings on a full freeze however I believe that this might either be a sepoarate bug or just due to my low spec.

In short therefore if you are suffering the 12.04 full sys freeze bug you might want to try installing Mate 1.6, upgrading kernel to 3.11.0-031100-generic and purging compiz as this is giving me a completely stable system. (providing I dont restart or log out in the session indicator).


P.S I have also installed a cpu scailing app and as soon as I log into my mate session I manually set the cpu to run at its highest level. Also if your system freezes and your worried about your hard disks you should hold down Alt and PrintScreen and then whilst doing so press the following sequence of keys for 2 seconds each:

R, E, I, S, U, B,

This will force your system to restart without the need for a hard reboot. (Also if this doesn't work the first time keep trying the sequence as it really works).


I know how infuriating this can get so I hope this helps. Also sorry if I can't elaborate more technically but I really am a noob.

---

