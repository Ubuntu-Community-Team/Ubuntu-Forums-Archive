---
title: "New Install of Ubuntu on Custom Machine"
date: 2015-05-26
forum: New to Ubuntu
---

### Post by josh134 on 2015-05-26
Good Day All,

   I have a custom rig with the following specs:

INTEL I5 Processor
ASUS Maximus V Gene Intel Z77
[COLOR=#000000][FONT=Verdana]EVGA GTX670
[/FONT][/COLOR]Crucial 16GB 8X2 DDR3
Thermalta Smart 750W 
TPLINK 3000MBPS WRLS N PCIE ADAPTER

I've tried the latest version 14 64 bit from a bootable 8 GB USB made via Pendrive Linux. I have the option to boot from usb via EUFI or not UEFI. If I don't boot into UEFI I get a screen that shows me different options via function keys. If I boot into UEFI I get a black screen that gives me the option to try before installing, install, check disc, and one other option. I never get to the point of actual installation because I get the following errors in different order  -

4.303598 ldm_parse_tocblock(): cannot find TOCBLOCK, database may be corrupt

ignoring bgrt: invalid status 0 (expected 1)

acpi ppc proble failed

Does anyone have any suggestions?

Kind Regards,
Josh

---

### Post by grahammechanical on 2015-05-26
I do not know the answer to the error code but I maybe able to clear a couple of things up.

If the motherboard is set for UEFI then you must load the Ubuntu session in UEFI mode and you must install Ubuntu in UEFI mode. If you turn UEFI off or set it to legacy mode then you do not need to load the Ubuntu live session in UEFI mode.

And do not worry about the acpi ppc probe fail error. A lot of us are getting that. It is just a system report that will not stop Linux/Ubuntu from working. This wiki page has some useful information.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

By the way, you should not need to turn secure boot off either.

Regards.

---

### Post by josh134 on 2015-05-27
Thanks for responding. Honestly I am not sure how to determine if my motherboard is set to be default for UEFI. I do have the option to boot into UEFI or not. From what I can tell from the link you provided, if another OS is installed in UEFI then Ubuntu will need to be installed in UEFI. I am planning on installing Ubuntu on its own solid state drive. I'm assuming the previous scenario applies if you're dual booting?

Regards.

---

### Post by tristan16 on 2015-05-28
> **josh134 said:**
> Thanks for responding. Honestly I am not sure how to determine if my motherboard is set to be default for UEFI. I do have the option to boot into UEFI or not. From what I can tell from the link you provided, if another OS is installed in UEFI then Ubuntu will need to be installed in UEFI. I am planning on installing Ubuntu on its own solid state drive. I'm assuming the previous scenario applies if you're dual booting?

Regards.

UEFI is the Unified Extensible Firmware Interface. If you system boots 1 hard drive on UEFI, the entire system boots on UEFI. So yes, it makes sense to install in UEFI even for a dual-boot.

---

### Post by cariboo on 2015-05-28
> **tristan16 said:**
> UEFI is the Unified Extensible Firmware Interface. If you system boots 1 hard drive on UEFI, the entire system boots on UEFI. So yes, it makes sense to install in UEFI even for a dual-boot.

Not necessarily, I have an Asus motherboard that has a combined setting that allows both legacy and UEFI booting at the same time, so in my case I could have both.

---

### Post by josh134 on 2015-05-29
"Solved" I was able to install Ubuntu from a CD. Not sure why I couldn't get it to install from the USB, but I'm not going to loose sleep over it at this point. Thank you all for the suggestions.

---

