---
title: "phoenix bios beep codes"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by scholzilla on 2008-05-20
My computer issues forth 7 piercing beeps upon bootup. I [checked here]("http://www.pchell.com/hardware/beepcodes.shtml#phoenix") to interpret what these beeps might signify, but I don't see a match. I definitely don't hear a "pattern" such as 1 beep - 2 beeps - 1 beep, though maybe the pattern is too fast to get my ears around. It also doesn't happen every time I bootup, which makes it difficult to parse. Any notions? Thanks.

---

### Post by PinkFloyd102489 on 2008-05-20
Check that the processor is seated, RAM is seated, everything is ventilated, cable connections.

It could be virtually anything. I'll try to find what it means.



EDIT: I found this. It has a crapload more codes than your link did.

[http://www.bioscentral.com/beepcodes/phoenixbeep.htm](http://www.bioscentral.com/beepcodes/phoenixbeep.htm)

---

### Post by scholzilla on 2008-05-20
Thanks for the response. This is a laptop so I'm not really sure I want to climb the learning curve by opening it up to check these things. I appreciate your looking into this for me and the link as well. This is an amd64 machine and runs pretty hot. I keep the vents free of obstruction but maybe it's getting too hot in there.

---

### Post by forestpixie on 2008-05-20
I have a recollection that 7 beeps is ram - but i'm tired and ready for bed, should be easy enough to check ram on a laptop - easier than a desktop anyway - much lighter to pick up and turn over.

---

### Post by scholzilla on 2008-05-26
I'm still getting what sound like 7 shrill beeps upon start-up. I've checked the Phoenix BIOS beep codes linked to above, but see nothing relevant. Gnome system log spits out the following, and I was hoping someone brighter than I would be able to see the diagnosis within (for example, the line that says "root hub lost power"?):

```
May 26 18:35:39 Darwin -- MARK --
May 26 18:35:39 Darwin kernel: [  739.508953] swsusp: Marking nosave pages: 000000000009d000 - 0000000000100000
May 26 18:35:39 Darwin kernel: [  739.508960] swsusp: Basic memory bitmaps created
May 26 18:35:39 Darwin kernel: [  739.508963] Syncing filesystems ... done.
May 26 18:35:39 Darwin kernel: [  739.508995] Freezing user space processes ... (elapsed 0.00 seconds) done.
May 26 18:35:39 Darwin kernel: [  739.509754] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
May 26 18:35:39 Darwin gnome-power-manager: (matt) Resuming computer
May 26 18:35:39 Darwin kernel: [  739.602776] Shrinking memory...  ^H-^H\^H|^Hdone (28912 pages freed)
May 26 18:35:39 Darwin kernel: [  740.094394] Freed 115648 kbytes in 0.49 seconds (236.01 MB/s)
May 26 18:35:39 Darwin kernel: [  740.094397] Suspending console(s)
May 26 18:35:39 Darwin kernel: [  740.119475] ACPI: PCI interrupt for device 0000:05:09.2 disabled
May 26 18:35:39 Darwin kernel: [  740.166441] ACPI: PCI interrupt for device 0000:00:14.2 disabled
May 26 18:35:39 Darwin kernel: [  740.182404] ACPI: PCI interrupt for device 0000:00:13.2 disabled
May 26 18:35:39 Darwin kernel: [  740.198326] ACPI: PCI interrupt for device 0000:00:13.1 disabled
May 26 18:35:39 Darwin kernel: [  740.198380] ACPI: PCI interrupt for device 0000:00:13.0 disabled
May 26 18:35:39 Darwin kernel: [  740.198719] Disabling non-boot CPUs ...
May 26 18:35:39 Darwin kernel: [  740.318161] CPU 1 is now offline
May 26 18:35:39 Darwin kernel: [  740.318164] SMP alternatives: switching to UP code
May 26 18:35:39 Darwin kernel: [  740.319586] CPU1 is down
May 26 18:35:39 Darwin kernel: [  740.319821] swsusp: critical section: 
May 26 18:35:39 Darwin kernel: [  740.386158] swsusp: Need to copy 108436 pages
May 26 18:35:39 Darwin kernel: [   40.803258] Enabling non-boot CPUs ...
May 26 18:35:39 Darwin kernel: [   40.815212] SMP alternatives: switching to SMP code
May 26 18:35:39 Darwin kernel: [   40.815966] Booting processor 1/2 APIC 0x1
May 26 18:35:39 Darwin kernel: [   40.826646] Initializing CPU#1
May 26 18:35:39 Darwin kernel: [   40.903660] Calibrating delay using timer specific routine.. 3192.23 BogoMIPS (lpj=6384473)
May 26 18:35:39 Darwin kernel: [   40.903667] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 26 18:35:39 Darwin kernel: [   40.903670] CPU: L2 Cache: 512K (64 bytes/line)
May 26 18:35:39 Darwin kernel: [   40.903672] CPU 1/1 -> Node 0
May 26 18:35:39 Darwin kernel: [   40.903675] CPU: Physical Processor ID: 0
May 26 18:35:39 Darwin kernel: [   40.903676] CPU: Processor Core ID: 1
May 26 18:35:39 Darwin kernel: [   40.903766] AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
May 26 18:35:39 Darwin kernel: [   40.904345] CPU1 is up
May 26 18:35:39 Darwin kernel: [   40.907668] Clockevents: could not switch to one-shot mode: lapic is not functional.
May 26 18:35:39 Darwin kernel: [   40.907673] Could not switch to high resolution mode on CPU 1
May 26 18:35:39 Darwin kernel: [   40.954603] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
May 26 18:35:39 Darwin kernel: [   40.975015] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
May 26 18:35:39 Darwin kernel: [   41.014978] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
May 26 18:35:39 Darwin kernel: [   41.015034] usb usb1: root hub lost power or was reset
May 26 18:35:39 Darwin kernel: [   41.015143] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
May 26 18:35:39 Darwin kernel: [   41.031024] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
May 26 18:35:39 Darwin kernel: [   41.808524] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0305000-c03057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May 26 18:35:39 Darwin kernel: [   41.822412] ACPI: PCI Interrupt 0000:05:09.2[A] -> GSI 20 (level, low) -> IRQ 20
May 26 18:35:39 Darwin kernel: [   42.578432] hda: UDMA/100 mode selected
May 26 18:35:39 Darwin kernel: [   42.581992] hdb: UDMA/33 mode selected
May 26 18:35:39 Darwin kernel: [   42.642020] Restarting tasks ... <6>usb 1-6: USB disconnect, address 3
May 26 18:35:39 Darwin kernel: [   42.643595] done.
```

I don't know if it matters, but I get them only sporadically and they happen both if I restart and when I come out of hibernation.

---

### Post by lazyart on 2008-05-27
What's the make and model of the laptop?  Have you checked the manufacturers site?

---

### Post by scholzilla on 2008-05-27
It's a Gateway MT6452 laptop. I checked gateway's frustrating site to no avail. Had a lovely "chat" with an automated response system that responded with a series of non sequiturs. It is worth noting that I did not have this issue before upgrading to Hardy, and the issue began the after the first boot-up with Hardy. Could be coincidental, but seems unlikely.

---

