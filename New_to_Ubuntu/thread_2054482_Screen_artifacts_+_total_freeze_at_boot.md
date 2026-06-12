---
title: "Screen artifacts + total freeze at boot"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Mrnumber3isme on 2012-09-07
For some unknown reason, every once in a while, when I turn my system on, everything looks like it's going well until I get to the Ubuntu splash screen before the login screen. at that point, the screen slowly develops artifacts until the entire screen has faded to random pixels. If I use the old windoze "Ctrl +Alt + Del" trick to reboot, the artifacts completely disappear, and are replaced with a Ubuntu loading bar. previously, this trick has fixed the issue, and allowed me to log in as normal, but today, I fought with my computer for 45+ minutes trying to work around this problem. Eventually, I went into BIOS and just took a look over my settings to see if anything might have changed, but everything looked good. the only change I made was to turn silent boot mode off so I can watch the status screen as I boot, and now the problem appears to have gone away. but as I mentioned, this happens every once in a while. maybe 4 or 5 times a month. I would simply try a reload of Ubuntu, but at the moment (Thanks to my little brother) my disc tray is broken, and I cannot seem to boot my machine from an old external dvd drive. any thoughts?

---

### Post by Bashing-om on 2012-09-07
Mrnumber3isme;

  Hi ! ; 
      I experienced a similar situation. I do not know that this is THE solution, but, may be worth trying.
 edit (make backup first) /etc/rc.local and add "sleep 5" (with out the quotes).

I had the thought that every once in a while Upstart was too quick in loading up while some booting process had not completed.

  I also did some other alterations on my boot process, but I think the pause  command in rc.local resolved my situation. 

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by Mrnumber3isme on 2012-09-07
Okay. just ran into the same problem again. I was fighting for a good 15 minutes or so, booting on and off, trying to get to the login screen. since I disabled quiet boot mode earlier, I tried enabling it again, and the machine booted right up with no problems. I really don't want to have to cycle my settings like this every time I want to turn the computer on. Perhaps BIOS is corrupt?

---

### Post by Mrnumber3isme on 2012-09-07
For someone who has been happily using Linux since windoze ME came out, I'm feeling a lot like a noob here. this is the output from rc.local. where should I add the sleep command?

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

---

### Post by khelben1979 on 2012-09-07
Have you checked for dust inside the case? Things like that can cause some serious software freezing because of overheating. I recommend you take a look!

---

### Post by Bashing-om on 2012-09-07
Apologize for not thinking through ( guilty of assuming).

Just place sleep 5 before the "exit 0"

save the file... see what happens in the next few days.

[INDENT]regards <==BDQ 
[/INDENT]

---

### Post by Mrnumber3isme on 2012-09-08
There could likely be dust. I haven't taken the thing apart since I first bought it (Used from a pawn shop. ugh.) I've inserted the command, and I'm about to take her apart to blast the evil dust invaders. thank you for your patience with me

---

### Post by Mrnumber3isme on 2012-09-08
So far, after following both hardware and software solutions, this thing is running like a champ again. I've gone through ten shutdown and bootup cycles trying to force the artifacts to come back, and they still haven't come back. for now, I think I can dare to call this one solved. thank you, guys.

---

### Post by Bashing-om on 2012-09-08
ahey, you are more then welcome ! Remember, we are all in this together.

                                                                                BDQ

---

### Post by Mrnumber3isme on 2012-09-09
Uh oh. scratch my last post. sure enough, a day has gone by, and even with adding the sleep command, and doing battle with the evil dust bunnies from another dimension, the problem has come back. darn. Eventually I plan on upgrading to a newer computer, but for the time being, I'd like to keep this thing working. any other ideas? perhaps increasing the sleep time? ten seconds, maybe?

---

### Post by idoitprone on 2012-09-09
> **Mrnumber3isme said:**
> Uh oh. scratch my last post. sure enough, a day has gone by, and even with adding the sleep command, and doing battle with the evil dust bunnies from another dimension, the problem has come back. darn. Eventually I plan on upgrading to a newer computer, but for the time being, I'd like to keep this thing working. any other ideas? perhaps increasing the sleep time? ten seconds, maybe?

```

lspci -nnk

uname -a
```

---

### Post by Bashing-om on 2012-09-09
I feel for you.

  Let us presume a problem with splash... what about going back to the text login (remove /quiet and splash/ in grub file) ...try that for a while (with sleep 5 still existing, 5 is a long long time to the computer)...

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Mrnumber3isme on 2012-09-11
Here is my output from lspci -nnk

thomas@thomas-laptop:~$ lspci -nnk
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
    Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
    Kernel modules: shpchp
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
    Kernel modules: shpchp
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
    Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a08] (rev 03)
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
05:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
05:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1
06:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Kernel driver in use: ndiswrapper
    Kernel modules: ssb

---

### Post by Mrnumber3isme on 2012-09-11
and my output from uname -a

thomas@thomas-laptop:~$ uname -a
Linux thomas-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

Bashing, I'm about to try removing the gui login. wish me luck

---

### Post by Mrnumber3isme on 2012-09-11
Well. removed "quiet" and "Splash" from boot/grub/grub.cfg.
it looked like a classic text-only boot screen for a while, but it still went to a gui login screen. worked perfect the first time, though, so I suppose no worries for now, but I'll be watching it over the next few days.

---

### Post by Hadaka on 2012-09-11
Hi, just out of curiosity please post the output of

```
lpci -nnk | grep -iA3 0280 
```thanks

ahhh..never mind. I see you have the diswrapper thingy
you need b43 for your broadcom 4306 card. The wireless
driver loads just before login window, and I "think" not
having the correct driver is causing the problem, works
sometimes, and trashes the screen others.

---

### Post by idoitprone on 2012-09-12
> **Mrnumber3isme said:**
> Well. removed "quiet" and "Splash" from boot/grub/grub.cfg.
it looked like a classic text-only boot screen for a while, but it still went to a gui login screen. worked perfect the first time, though, so I suppose no worries for now, but I'll be watching it over the next few days.

I remember there was an ati driver bug that freezes upon boot.

The fix was to remove the splash screen.

athougth I am surprise that the open source driver had this issue 

  the open source ati drivers should be stable

---

### Post by Bashing-om on 2012-09-12
come to remind me of it ... I had the ati card freeze up in version 9.04 (or so) .. I swapped cards to resolve (needed better graphics card anyway). That system has been solid ever since (10.04 ATT ...wife wants to keep her computer as she has it !).

[INDENT]BDQ
[/INDENT]

---

### Post by Mrnumber3isme on 2012-09-23
Well, more than a week later, I believe I can mark this as solved. Thank you all for your help in solving this issue.

---

### Post by Bashing-om on 2012-09-23
Good thing ! Are you still running without splash ?


                   regards <==BDQ

---

### Post by Mrnumber3isme on 2012-09-25
Yes. I would prefer to use splash, because let's face it, we all love flashy stuff, but I'd rather have a computer that boots up.

---

### Post by Bashing-om on 2012-09-25
I can relate. But, like you, it is functionality before beauty! Plus, I want to see/know what my system is doing, so, I run with text messages enabled, would gladly change my bootup color screens for informative messages!

  Glad you are up and running! ==> BDQ

---

