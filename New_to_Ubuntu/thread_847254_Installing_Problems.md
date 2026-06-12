---
title: "Installing Problems"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Crucial Death on 2008-07-02
Hey everyone,

I've downloaded 8.04's iso and burned it onto a CD. I booted it and selected to run it without installing, and it hang on the loading screen... splash screen? Anyway, I changed it so it shows as text rather than a a bar going sideways. It hang at this message:

[ 178.739138] b43legacy -phy0: Broadcom 4301 WLAN found

I tried selecting the Install option, and it hang at the same place, I think. Can't remember very well now. Any help would be appreciated, if you need me to fetch some more information I'd be glad to.

Thanks.

---

### Post by theravenproject on 2008-07-02
Sounds like you may have a faulty disc-I would try re-burning it this time at a very slow speed...there is an option at the main menu screen that says check cd for defects-you can use that as well to make sure.  Ithink reburning a proper copy should solve this though

---

### Post by phidia on 2008-07-02
Trying booting with the noapic boot option. See the [boot options guide]("https://help.ubuntu.com/community/BootOptions") from the community doc pages.
Basically though when you get to the screen where you can choose install from press the F6 key and then type this > noapic acpi=offin that line.
Hope that helps.

---

### Post by meindian523 on 2008-07-02
Also,Broadcom wireless cards are known to be pretty much "pieces of silicon" with atleast Ubuntu,and most probably with other distros too,because everyone uses more-or-less the same kernel.Follow theravenproject's advice and before that,do a md5sum on it to verify the integrity of your download.

---

### Post by Crucial Death on 2008-07-02
Thanks for the replies everyone!

Yeah theravenproject and meindian535, I had already done an md5sum hash check before I burned it and I also checked the CD from the Ubuntu boot screen and both tests came out positive. Thanks for your advice though =)

I'll try that, and tell you about the result as soon as I can, phidia.

Thanks again!

**[COLOR="DarkRed"]Update:[/COLOR]**

I tried phidia's advice and it hung on the same message:

[  0.000000] b43legacy-phy0 Broadcom 4301 WLAN found

The only different being that it showed up much earlier and with different numbers at the beginning.

Here's my system's specs:

CPU: Intel Q6600
Motherboard: ASUS Maximus Formula
GPU: Nvidia 9600 GT
Souncard: SupremeFX II (incl. with mobo)
Wireless Card: Broadcom 802.11b Network Adapter - is what Windows Vista's Device Manager calls it, I'll try to get a real brand/model

---

### Post by Crucial Death on 2008-07-02
Anyone with any information, kindly share it.

Thanks.

---

### Post by phidia on 2008-07-02
The output you are posting (WLAN found) doesn't seem like an error message.
Can you open another tty? Press Alt+Ctrl+F1 or try F2 through F7 with Alt+Ctrl.
If you get a commandline type dmesg to see where it is actually stopping.

---

### Post by Crucial Death on 2008-07-02
Thank you for that but I'm not entirely sure what you mean exactly.
Here's what I did though:
I booted from CD and got to the Ubuntu Installation screen. I then selected Try Without Installing. After pressing F6 I deleted 'quiet' and 'splash' from the Boot Parameters box. I then added 'priority=low' (and later repeated with 'noapic acpi=off' as well as 'priority=low'). This yielded in the same message being displayed at the end. Because the last message seems not to be erratic, I have taken pictures of what the screen says, I can't post them up right now because I don't have a way of removing them from the SD card at the moment. Also, at the end, when it hung at the aforementioned phrase, I attempted Alt+Ctrl+<insert F1-F7> and it did nothing - no command prompt or anything came up. I also tried to type in dmesg and pressing enter and nothing happened then either. 
Did you mean for me to do something else instead?
Any information I can get for you?
I'd like to thank you for all your help, it is much appreciated!

---

### Post by Crucial Death on 2008-07-02
I am not bumping into this thread... no siree! :twisted:

---

### Post by meindian523 on 2008-07-03
Nopes,phidia meant find a console if you can,and if you can,type dmesg and see where it's stopping.Since you didn't get a console,it's no use typing dmesg and pressing Enter without a prompt.Also,please bump only after about 24 hours.You have to remember that your advisors are in different time zones than you.

---

### Post by Crucial Death on 2008-07-03
Hey,

-------------------------------------------------------------
To meindian523, sorry, won't happen again - I didn't know of any defined rules for bumping, I've never used forums before... only read from them. Also, I knew typing it wouldn't do anything since it doesn't let you actually type anything, I just posted it... well I don't know why I did it or why I posted that I did it, but I did it :) hehe
-------------------------------------------------------------

I was thinking about my problem. Even though the md5sum hash check came out positive and the CD says it is fine on its self check, could it still be faulty?

Other than that I was wondering if the way around this would be to go into text mode installation? Obviously I am new to Linux and wouldn't have a clue where to start if that is the case. Anyway, if anyone can help me, that would be cool!

This is as much context as I can provide for the problem I have in a definite order, it is without using 'noapic acpi=off' since that gave me similar results, if giving you the context from that would help, then tell me so and I will provide it:

```
scsi 4:0:0:0: Attached scsi generic sg1 type 5
b44.c:v2.0
Driver 'sr' needs updating - please use bus_type methods
sr0: sci3-mmc drive: 40x/40x writer dvd-rom cd/rw xa/form2 cdda tray
Uniform CD-ROM driver revision: 3.20
b44: Invalid MAC address found in EEPROM
b44 ssb0:1: Problem fetching invariants of chip, aborting.
b44: probe of ssb0:1 failed with error -22
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
Registering uniofs 1.4
Uniofs: debugging is not enabled
loop: module loaded
Squashfs: Version 3.3 (2007/10/31) Phillip Lougher
Done.
Begin: Running /scripts/init-bottom...
Done.
*Setting preliminary keymap...          [OK]
*Setting restricted drivers...          [OK]
*Setting system clock
*Starting basic networking...           [OK]
*Starting kernel event manager...       [OK]
*Loading hardware drivers...
input: PC Speaker as /devices/platform/pcspkr/input/input3
pci_hotplug: PCI Hot Plug PCI Core Version: 0.5
input: Power Button (FF) as /devices/virtual/input/input4
ACPI:  Power Button (FF) [PWRF]
input: Power Button (CM) as /devices/virtual/input/input5
ACPI:  Power Button (CM) [PWRB]
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
iTCO_vendor_support: vendor-support=0
ACPI: PCI Interrupt 0000:04:00.04[A] -> GSI 18 (level, low) -> IRQ 18
sky2 0000:04:00.0: v1.20 addr 0xfeafc000 irq 18 Yukon-EC Ultra (0 xb4) rev 3
sky2 eth0: addr 00:1e:8c:7b:45:80
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
sky2 0000:02:00.0: v1.20 addr 0xfe8fc000 irq 17 Yukon-EC Ultra (0    xb4) rev 3
sky2 eth1: addr 00:1e:8c:7b:4b:b8
iTCO_wdt: Intel TCO Watchdog Timer Driver v1.02 (26-Jul-2007)
iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0860)
iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
b43legacy-phy-0:Broadcom 4301 WLAN found
```

I included all of that because there seems to be some erratic behavior other than the fact that it halts.

Thanks for any help.

---

### Post by meindian523 on 2008-07-03
> **Crucial Death said:**
> Hey,

-------------------------------------------------------------
To meindian523, sorry, won't happen again - I didn't know of any defined rules for bumping, I've never used forums before... only read from them. Also, I knew typing it wouldn't do anything since it doesn't let you actually type anything, I just posted it... well I don't know why I did it or why I posted that I did it, but I did it :) hehe
-------------------------------------------------------------

I was thinking about my problem. Even though the md5sum hash check came out positive and the CD says it is fine on its self check, could it still be faulty?

Nopes,md5 does a bitwise check,if even one bit is wrong the md5 hash fails.So,if md5 checks out,there's no problem with the CD.

> **Crucial Death said:**
> 
Other than that I was wondering if the way around this would be to go into text mode installation? Obviously I am new to Linux and wouldn't have a clue where to start if that is the case. Anyway, if anyone can help me, that would be cool!

You could do that,but I've no experience with the alternate installer(the text-mode installation you are talking about)Maybe phidia or someone else can help you out on that if nothing else works out.

> **Crucial Death said:**
> 
This is as much context as I can provide for the problem I have in a definite order, it is without using 'noapic acpi=off' since that gave me similar results, if giving you the context from that would help, then tell me so and I will provide it:

```

Driver 'sr' needs updating - please use bus_type methods
b44: Invalid MAC address found in EEPROM
b44 ssb0:1: Problem fetching invariants of chip, aborting.
b44: probe of ssb0:1 failed with error -22
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
b43legacy-phy-0:Broadcom 4301 WLAN found
```

I cut out the portions which I felt were normal,but honestly,I can't say anything about these either,I'm a total hardware n00b.

---

