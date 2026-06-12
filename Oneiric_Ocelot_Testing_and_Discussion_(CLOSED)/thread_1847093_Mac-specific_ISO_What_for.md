---
title: "Mac-specific ISO? What for?"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 8_Bit on 2011-09-20
Can someone explain why there is an ISO on the daily build live CD only for Intel Macs?
[http://cdimage.ubuntu.com/daily-live/20110919/](http://cdimage.ubuntu.com/daily-live/20110919/)

Why wouldn't the regular PC version work?

I've installed past versions of Ubuntu (10.10 and 11.04) successfully on a Macbook before, using the regular x64 AMD discs. Is there something different about Oneiric that necessitates creating a specific ISO just for Macs?

Well either way, I did just burn the ISO, and tried it out. Black screen with flashing underscore.
Doesn't appear to work.

---

### Post by lucazade on 2011-09-20
> **8_Bit said:**
> Can someone explain why there is an ISO on the daily build live CD only for Intel Macs?
[http://cdimage.ubuntu.com/daily-live/20110919/](http://cdimage.ubuntu.com/daily-live/20110919/)

Why wouldn't the regular PC version work?

I've installed past versions of Ubuntu (10.10 and 11.04) successfully on a Macbook before, using the regular x64 AMD discs. Is there something different about Oneiric that necessitates creating a specific ISO just for Macs?

Well either way, I did just burn the ISO, and tried it out. Black screen with flashing underscore.
Doesn't appear to work.

because it is not for Intel Macs (i386/64) but for old PowerPC Macs (PPC)

---

### Post by dino99 on 2011-09-20
> **8_Bit said:**
> Can someone explain why there is an ISO on the daily build live CD only for Intel Macs?
[http://cdimage.ubuntu.com/daily-live/20110919/](http://cdimage.ubuntu.com/daily-live/20110919/)

Why wouldn't the regular PC version work?

I've installed past versions of Ubuntu (10.10 and 11.04) successfully on a Macbook before, using the regular x64 AMD discs. Is there something different about Oneiric that necessitates creating a specific ISO just for Macs?

Well either way, I did just burn the ISO, and tried it out. Black screen with flashing underscore.
Doesn't appear to work.

You just need to take time to read & pay attention:

Mac (PowerPC) and IBM-PPC (POWER5) desktop CD
    For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines.
    Warning: This image is oversized (which is a bug) and will not fit onto a standard 700MiB CD. However, you may still test it using a DVD, a USB drive, or a virtual machine.

---

### Post by 8_Bit on 2011-09-20
I am NOT talking about the PPC version! I'm talking about THIS:

[64-bit Mac (AMD64) desktop CD]("http://cdimage.ubuntu.com/daily-live/20110919/oneiric-desktop-amd64+mac.iso")  Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead. This image is adjusted to work properly on Mac systems.

Clearly I am not the one that needs to pay attention.

---

### Post by kaldor on 2011-09-20
> **8_Bit said:**
> I am NOT talking about the PPC version! I'm talking about THIS:

[64-bit Mac (AMD64) desktop CD]("http://cdimage.ubuntu.com/daily-live/20110919/oneiric-desktop-amd64+mac.iso")  Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead. This image is adjusted to work properly on Mac systems.

Clearly I am not the one that needs to pay attention.

I've wondered this too. Both amd64 and the "Mac" amd64 versions loaded fine when I tried them on a MacBook. I didn't see any differences.

---

### Post by lucazade on 2011-09-20
In Ubuntu 10.10, we changed the normal amd64 CD images to dual-boot on either BIOS or UEFI systems (UEFI, "Unified Extensible Firmware Interface", is a different kind of firmware found on many newer systems). This was done using a technique known as a "multi-catalog" CD - it contains two boot images, and the specification says that the firmware is supposed to pick the one it can best use.

Unfortunately, even though Macs use a variant of EFI (an earlier version of what's now called UEFI), they apparently can't cope with multi-catalog CDs, and simply refuse to boot them. This left us in rather a quandary: we needed to support UEFI systems, but we didn't want to drop support for Macs either. I therefore created the amd64+mac CD images, which are exactly the same as the amd64 images except that they only support BIOS booting. Macs are happy to boot these in their BIOS emulation mode.

(In fact, the name amd64+mac is a slight misnomer, because it later turned out that some systems other than Macs suffer from a similar problem - but I felt that a more technically accurate naming such as amd64+nouefi would be more likely to confuse than enlighten.)

While I would love to return to shipping just amd64 images rather than both amd64 and amd64+mac, at the moment there is no prospect of reunifying them unless somebody figures out how to make a multi-catalog CD image that Macs can boot. If you're an expert on this, please do contact me by e-mail.

[http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image](http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image)

---

