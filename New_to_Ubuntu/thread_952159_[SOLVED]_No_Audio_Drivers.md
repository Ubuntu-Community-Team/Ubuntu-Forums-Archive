---
title: "[SOLVED] No Audio Drivers?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by waldo_phill on 2008-10-18
Hello Everyone,

I am new to the whole Linux scene I just installed xubuntu on a very old PC yesterday (Compaq Presario 5202). When attempting to run Amarok I recieve an error message "xine was unable to initialize any audio drivers." Can anyone point me in the right direction?

Thanks

---

### Post by kilroy423 on 2008-10-19
Find out what audio devices you have.  Try ```
lspci
``` and see if you can find anything in there.  Once you find what hardware you have then you will have to search google and see if anyone has drivers or if there is a kernel module that is compatible.

some other places to look might be:
```

dmesg
cat /var/log/messages
cat /var/log/syslog

```

---

### Post by waldo_phill on 2008-10-19
when running 

Code:

lspci 

it does not list my sound card. Its an integrated sound card. But there are no options for it in the BIOS. Any ideas? 
However, upon start-up my speakers will beep

---

### Post by waldo_phill on 2008-10-20
bump :(

---

### Post by kilroy423 on 2008-10-21
Could you post the output of lspci?  Do you happen to know the model# and type?

---

### Post by waldo_phill on 2008-10-22
The output is:

00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:03.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
00:04.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 45)
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:14.3 Bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

the integrated sound is suppose to be an ESS 1866

Thanks for the help

---

### Post by wolfen69 on 2008-10-22
if you can, just pick up an old soundblaster pci card from craigslist.org

i've seen them for $5. or go to a computer fair/swap meet. the time you could spend trying to get this going isn't worth it.

---

### Post by aimpau on 2008-10-22
Compaq Presario is a laptop, not a PC.

Anyways, try:

```

sudo apt-get install oss-compat

```

This would install drivers that would enable non-alsa legacy audio drivers.

---

### Post by ardvark71 on 2008-10-23
> **waldo_phill said:**
> The output is:

00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:03.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
00:04.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 45)
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:14.3 Bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

the integrated sound is suppose to be an ESS 1866

Thanks for the help

Hi...

It may be a long shot but you may want to check your CMOS to see if the sound chip has been disabled. If not, then it's possible that the chip simply "died" or became defective. I had that happen to an ESS chipset in a Toshiba Satellite notebook I once had.

If nothing else you can research a PCMCIA sound card that is fully compatible with Ubuntu. Does anyone here know of one?

Best Regards...

---

### Post by waldo_phill on 2008-10-27
Thanks for everyone's help...I ended up getting a sound card and it worked fine.

---

