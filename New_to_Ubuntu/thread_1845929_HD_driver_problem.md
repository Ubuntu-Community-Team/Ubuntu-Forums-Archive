---
title: "HD driver problem?"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by maskiepop on 2011-09-18
I might have an HD driver problem. I have a relatively new desktop x64 pc, that I configured as a dual boot -- win7 & ubuntu 10.10. I have a 320 GB Hitachi HD that I connect to another desktop PC via USB --  an x86 PC, likewise a dual boot -- win7 & ubuntu 10.10. The x86 pc can read and write to the Hitachi hd; the x64 pc can't.

Is it a driver problem? Where can I get this driver. I have been all over the net for this. 

TIA

---

### Post by coffeecat on 2011-09-18
I have a USB SATA docking station which has worked with every combination of OS and machine I have tried it with, with one exception: one particular release of Ubuntu a year or more ago on my Sony laptop. It has worked with subsequent releases of Ubuntu on that laptop, and other USB hard drive devices worked on the Sony laptop with that version of Ubuntu. All I can conclude is that there was some obscure conflict between the kernel USB driver, the enclosure firmware, perhaps the hard drive firmware, and the computer's ACPI. Perhaps you are seeing something similar.

Try this. Attach the USB drive to each machine in turn, switch it on and then run this from the terminal:

```
dmesg | tail
```

Post the output of each. You can highlight the output in the terminal, right-click -> copy, and then paste it into your post. Then we can compare the two.

Have you tried other USB hard drives with the x64 machine?

---

### Post by maskiepop on 2011-09-19
Thanks for your reply coffeecat.
Below are the dmesg outputs from the x32 (ubuntu 10.04) and the x64 (ubuntu 10.10):

Re your other question, the answer is yes. I have another HD external drive that I can connect to both machines.

dmesg tail (x32 Ubuntu 10.04)
================================

[  205.138386] scsi 7:0:0:0: Direct-Access     Hitachi  HTS545032B9A300       PQ: 0 ANSI: 2 CCS
[  205.139009] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  205.143062] sd 7:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[  205.143861] sd 7:0:0:0: [sdb] Write Protect is off
[  205.143866] sd 7:0:0:0: [sdb] Mode Sense: 28 00 00 00
[  205.143869] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  205.146360] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  205.146367]  sdb: sdb1 sdb2
[  205.170310] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  205.170317] sd 7:0:0:0: [sdb] Attached SCSI disk

dmesg tail (X64 Ubuntu 10.10)
=============================

[   44.095956] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x5
[   44.095956] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x25
[   44.095956] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x10
[   44.095956] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x6
[   44.095956] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x2
[   44.095956] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x3
[   44.095957] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x4
[   44.095958] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x5
[   44.095960] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x25
[   44.096583] ALSA hda_codec.c:1471: hda_codec_cleanup_stream: NID=0x2

---

### Post by coffeecat on 2011-09-19
The dmesg output from the 64-bit machine is certainly not what you should be seeing after attaching a USB drive. As far as I can make out ALSA is nothing to do with attaching a USB drive. I tried googling "hda_codec_cleanup_stream" and found a couple of incomplete bug reports, but nothing to help.

> **maskiepop said:**
> I have another HD external drive that I can connect to both machines.

Ah. But does it work with both machines? That's the thing. :) I think that's what you mean, but you need to clarify. We need to determine whether it's just this drive that's the problem with the x64 machine, or all drives.

---

### Post by maskiepop on 2011-09-20
> **coffeecat said:**
> ... I think that's what you mean, but you need to clarify. We need to determine whether it's just this drive that's the problem with the x64 machine, or all drives.

Hi coffeecat,

There is another external HD that I attach to the x64 machine, for backing up the x64. That works on both machines. Did you want me to show the dmesg for that as well? I may not have understood correctly what you wanted me to do regarding that.

And, maybe, I should emphasize that both the Win7 and the Ubuntu 10.10 running on the x64 ***_cannot_*** read the Hitachi HD. Bearing that in mind, is it still valid for me to assume that it is a driver problem? What exactly is it that triggers an OS to detect that there is an HD attached to the system via a USB port, such that it begins looking for a driver to associate with it?

---

### Post by coffeecat on 2011-09-20
> **maskiepop said:**
> There is another external HD that I attach to the x64 machine, for backing up the x64. That works on both machines. Did you want me to show the dmesg for that as well?

No, you don't need to run dmesg on the other HD - I simply wanted to compare the dmesg output for the affected hard drive on both machines. By the way, I may not have mentioned that the dmesg output on the 32-bit machine was fine. The other - well :-k.

> **maskiepop said:**
> And, maybe, I should emphasize that both the Win7 and the Ubuntu 10.10 running on the x64 ***_cannot_*** read the Hitachi HD. Bearing that in mind, is it still valid for me to assume that it is a driver problem?

That I didn't realise. Most intriguing. I'd assumed this was an Ubuntu problem. If it affects Windows as well, looking at drivers is unlikely to help. This sounds like some sort of weird hardware incompatibility between the Hitachi and the 64-bit machine.

It's late here, and if I continue, I'm just going to start getting incoherent. You've noticed already?! :) I'll come back to this thread tomorrow when I'm fresher.

---

