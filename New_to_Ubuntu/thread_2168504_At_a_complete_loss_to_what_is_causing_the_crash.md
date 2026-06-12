---
title: "At a complete loss to what is causing the crash"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by christiegrinham on 2013-08-18
My computer keeps crashing in a strange manner. It doesn't stop, it just becomes extremely slow. As in, it takes 30 seconds to move the mouse from one side of the screen to another.
I built the computer myself around an ASUS P6X58D-E Motherboard.
I use it for pro-audio so I tend to run the lowlatency kernel. Here is a dump of the syslog of when it crashes:

```
Aug 17 20:50:41 christie-desktop pulseaudio[2039]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 17 20:50:41 christie-desktop pulseaudio[2039]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-EDIROL_UA-101_ZU24693-00-UA101" card_name="alsa_card.usb-EDIROL_UA-101_ZU24693-00-UA101" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-EDIROL_UA-101_ZU24693-00-UA101" card_name="alsa_card.usb-EDIROL_UA-101_ZU24693-00-UA101" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-EDIROL_UA-101_ZU24693-00-UA101" card_name="alsa_card.usb-EDIROL_UA-101_ZU24693-00-UA101" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-EDIROL_UA-101_ZU24693-00-UA101" card_name="alsa_card.usb-EDIROL_UA-101_ZU24693-00-UA101" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 17 20:50:42 christie-desktop pulseaudio[2039]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-EDIROL_UA-101_ZU24693-00-UA101" card_name="alsa_card.usb-EDIROL_UA-101_ZU24693-00-UA101" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 17 20:50:43 christie-desktop pulseaudio[2039]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 17 20:50:43 christie-desktop pulseaudio[2039]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-EDIROL_UA-101_ZU24693-00-UA101" card_name="alsa_card.usb-EDIROL_UA-101_ZU24693-00-UA101" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 17 20:50:43 christie-desktop pulseaudio[2039]: [pulseaudio] module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1e.0/0000:07:01.2/usb3/3-4/3-4:1.0/sound/card2 (alsa_card.usb-EDIROL_UA-101_ZU24693-00-UA101) more often than 5 times in 10s
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449104] irq 19: nobody cared (try booting with the "irqpoll" option)
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449112] Pid: 103, comm: irq/19-uhci_hcd Tainted: PF          O 3.8.0-28-lowlatency #20-Ubuntu
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449115] Call Trace:
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449125]  [<ffffffff810efefd>] __report_bad_irq+0x3d/0xe0
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449130]  [<ffffffff810f03c2>] note_interrupt+0x1c2/0x210
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449134]  [<ffffffff810ee3f0>] ? irq_thread_fn+0x50/0x50
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449138]  [<ffffffff810ee915>] irq_thread+0x145/0x160
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449142]  [<ffffffff810ee2f0>] ? irq_finalize_oneshot+0xf0/0xf0
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449146]  [<ffffffff810ee7d0>] ? irq_thread_check_affinity+0xa0/0xa0
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449150]  [<ffffffff8107fb80>] kthread+0xc0/0xd0
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449153]  [<ffffffff8107fac0>] ? kthread_create_on_node+0x120/0x120
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449159]  [<ffffffff816e1eec>] ret_from_fork+0x7c/0xb0
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449162]  [<ffffffff8107fac0>] ? kthread_create_on_node+0x120/0x120
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449164] handlers:
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449167] [<ffffffff810edd40>] irq_default_primary_handler threaded [<ffffffff81505e50>] usb_hcd_irq
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449174] [<ffffffff810edd40>] irq_default_primary_handler threaded [<ffffffff81505e50>] usb_hcd_irq
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449179] [<ffffffff810edd40>] irq_default_primary_handler threaded [<ffffffff81505e50>] usb_hcd_irq
Aug 17 20:56:33 christie-desktop kernel: [ 1027.449183] Disabling IRQ #19
Aug 17 20:56:33 christie-desktop kernel: [ 1027.527934] usb 3-4: USB request error -18: unknown error
Aug 17 20:56:33 christie-desktop kernel: [ 1027.548581] usb 3-4: USB request error -18: unknown error
```

This is ruining my production computer so if anybody could help I would be so grateful

---

### Post by TheFu on 2013-08-18
Thanks for the relevant logs!

Looks like the audio card module is not being found. Have you tried reinstalling the software?
If that didn't help, could the card have gotten loose in the socket?  Try re-seating the card.

If that doesn't help, can you try the card in a different slot?
Last, I'd try a new card (identical if possible) in multiple slots?

This could turn out to be anything - software, kernel, cables, power supply, broken MB.

The USB errors wouldn't worry me, unless this is a USB audio device.

---

### Post by christiegrinham on 2013-08-18
Hi there, thanks for the reply! I forgot to mention this is actually a USB audio device. It is an Edirol UA-101. I'll try some of what you said and report back. 
I am using a 3m USB cable, do you think this might be part of the problem?

---

### Post by Yellow Pasque on 2013-08-19
```
irq 19: nobody cared (try booting with the "irqpoll" option)
```

I suggest you try booting with the irqpoll option ;)
Edit /etc/default/grub and change this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"

Save, quit, and run 
```
sudo update-grub
```
Reboot. Pray.

---

### Post by christiegrinham on 2013-08-20
What does the irqpoll option do?

---

### Post by Vladlenin5000 on 2013-08-20
* Subscribed *

---

### Post by sandyd on 2013-08-20
> **christiegrinham said:**
> What does the irqpoll option do?

basically gets systems with broken firmware running.
Does this by scanning all the irq handlers for an interrupt when its not handled

---

### Post by christiegrinham on 2013-08-21
I've not noticed a crash in the last couple of days after changing to a shorter USB cable. I will keep this thread updated if it happens again though.

---

