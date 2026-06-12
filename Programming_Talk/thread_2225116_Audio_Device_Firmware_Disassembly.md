---
title: "Audio Device Firmware Disassembly"
date: 2014-05-19
forum: Programming Talk
---

### Post by ToFue on 2014-05-19
Hi there,

I could use some help or advice in approach techniques or research tips concerning usb device firmware and I haven't attempted anything like this before.

I was hoping to copy a bios from a usb device, specifically from my podxt pro, for code disassembly. It's an old and buggy device (corrupted somewhere) and there's no publicly listed api. I was wanting to tinker with its software (since the cpu is reported to be in the ARM family), and also play at making my own front end.

How would I go about this - would I have better luck 'intercepting' a firmware update through Line6's locked-down client java-based updater (seems messy)? Also is there anything I should be aware of, like specific USB protocol read addresses, or should I rely on the OS knowledge of the device driver? I assume that the OS driver would omit reporting addresses that could reveal the device's core system... am I wrong?

Since the device isn't supported anymore and it's for my own education, I would think this wouldn't be categorized as piracy (if it is i'll perform this in a country in which this doesn't apply, if that helps o.O )? 

I suppose I'm also interested in firewire devices as well, with similar question (I have a profire 2626).

Any tips would be great, thanks!

~tofue

---

### Post by ofnuts on 2014-05-20
Normally all these devices use well known USB protocol (mass storage or Media Transfer). I don't think there is anything in the USB protocol to read random firmware addresses. AFAIK your only hope is that the BIOS shows up as some hidden file system. But there is no need to for the manufacturer to be able to read the installed firmware (firmware version can be reported by using a different USB device identifier). So you best bet is to get the firmware from some update.

---

### Post by ToFue on 2014-05-20
Ahh, thank you for that!

---

