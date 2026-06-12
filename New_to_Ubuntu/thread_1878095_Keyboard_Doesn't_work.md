---
title: "Keyboard Doesn't work"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by Garland Fox on 2011-11-09
I need help on control of keyboard.

When I boot into 11.10 , the keyboard will not respond until I unplug the usb and plug it back in.

Dual boot windows 7 and 11.10 - It does not mess up in windows.

---

### Post by Mark Phelps on 2011-11-09
Same thing happened to me -- except it first appeared to be a cordless mouse problem.  After installing 11.10 (clean install) and booting into it, was suddenly unable to select windows and move them.  Changed to a corded mouse and it worked better.  Rebooted, and the corded mouse no longer worked.

Changed to an older USB keyboard -- mouse worked.  Changed back to the cordless mouse, it too, worked.

So basically, it was a new problem with a USB keyboard that I have been using for years, without problems across a half-dozen different Windows and Ubuntu versions.

Sorry, apart from changing keyboards, don't have a solution -- to this, yet another new 11.10 problem.

---

### Post by Garland Fox on 2011-11-11
Thanks for the info

---

### Post by dgermer on 2011-11-12
I am having a similar problem but found out, that I could unplug and replug the keyboard.
This is not a problem with the keyboard in my case, I try to figure out why this happens:
my logs are like this:
Nov 12 10:39:37 daniel-desktop kernel: [41553.533465] PM: Preparing system for mem sleep
Nov 12 13:13:31 daniel-desktop kernel: [41553.715981] Freezing user space processes ... (elapsed 0.01 seconds) done.
Nov 12 13:13:31 daniel-desktop kernel: [41553.731741] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Nov 12 13:13:31 daniel-desktop kernel: [41553.747732] PM: Entering mem sleep
Nov 12 13:13:31 daniel-desktop kernel: [41553.747797] Suspending console(s) (use no_console_suspend to debug)
...
Nov 12 13:13:31 daniel-desktop kernel: [41553.757726] serial 00:04: disabled
Nov 12 13:13:31 daniel-desktop kernel: [41553.757735] i8042 kbd 00:03: wake-up capability enabled by ACPI
Nov 12 13:13:31 daniel-desktop kernel: [41553.758131] ata_piix 0000:00:1f.5: PCI INT B disabled
Nov 12 13:13:31 daniel-desktop kernel: [41553.763732] ACPI handle has no context!
Nov 12 13:13:31 daniel-desktop kernel: [41553.795680] ehci_hcd 0000:00:1d.0: PCI INT A disabled
Nov 12 13:13:31 daniel-desktop kernel: [41553.795698] ehci_hcd 0000:00:1a.0: PCI INT A disabled
Nov 12 13:13:31 daniel-desktop kernel: [41554.064092] HDA Intel 0000:00:1b.0: PCI INT A disabled
Nov 12 13:13:31 daniel-desktop kernel: [41554.064118] ACPI handle has no context!
...
Nov 12 13:13:31 daniel-desktop kernel: [41555.439326] pcieport 0000:00:1c.4: wake-up capability disabled by ACPI
Nov 12 13:13:31 daniel-desktop kernel: [41555.439337] r8169 0000:02:00.0: PME# disabled
Nov 12 13:13:31 daniel-desktop kernel: [41555.439347] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Nov 12 13:13:31 daniel-desktop kernel: [41555.439359] i8042 kbd 00:03: wake-up capability disabled by ACPI
Nov 12 13:13:31 daniel-desktop kernel: [41555.439384] xhci_hcd 0000:04:00.0: setting latency timer to 64
Nov 12 13:13:31 daniel-desktop kernel: [41555.439435] Switched to NOHz mode on CPU #3
Nov 12 13:13:31 daniel-desktop kernel: [41555.439849] sd 0:0:0:0: [sda] Starting disk
Nov 12 13:13:31 daniel-desktop kernel: [41555.439962] sd 1:0:0:0: [sdb] Starting disk
Nov 12 13:13:31 daniel-desktop kernel: [41555.441155] serial 00:04: activated
Nov 12 13:13:31 daniel-desktop kernel: [41555.441328] Extended CMOS year: 2000
Nov 12 13:13:31 daniel-desktop kernel: [41555.491529] firewire_core: skipped bus generations, destroying all nodes
...
Nov 12 13:13:31 daniel-desktop kernel: [41555.691370] usb 1-1.4: reset full speed USB device number 4 using ehci_hcd
Nov 12 13:13:31 daniel-desktop kernel: [41555.697834] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input12
Nov 12 13:13:31 daniel-desktop kernel: [41555.749945] No ACPI video bus found
Nov 12 13:13:31 daniel-desktop kernel: [41555.749948] PM: resume of drv:i915 dev:0000:00:02.0 complete after 310.900 msecs
Nov 12 13:13:31 daniel-desktop kernel: [41555.787938] btusb 1-1.4:1.0: no reset_resume for driver btusb?
Nov 12 13:13:31 daniel-desktop kernel: [41555.787942] btusb 1-1.4:1.1: no reset_resume for driver btusb?
Nov 12 13:13:31 daniel-desktop kernel: [41555.991260] firewire_core: rediscovered device fw0
...
Nov 12 13:13:31 daniel-desktop kernel: [41556.786692] ata2.01: failed to resume link (SControl 0)
Nov 12 13:13:31 daniel-desktop kernel: [41559.461192] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
...
Nov 12 13:13:31 daniel-desktop kernel: [41559.491246] PM: Finishing wakeup.
...
Nov 12 13:13:31 daniel-desktop kernel: [41559.491246] Restarting tasks ... done.
Nov 12 13:13:31 daniel-desktop acpid: client 921[0:0] has disconnected
Nov 12 13:13:31 daniel-desktop acpid: client connected from 921[0:0]
Nov 12 13:13:31 daniel-desktop acpid: 1 client rule loaded
Nov 12 13:13:31 daniel-desktop kernel: [41559.540498] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
...
Nov 12 13:13:32 daniel-desktop pulseaudio[1661]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Nov 12 13:13:32  pulseaudio[1661]: last message repeated 2 times
Nov 12 13:13:32 daniel-desktop pulseaudio[10814]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Nov 12 13:13:33  pulseaudio[10814]: last message repeated 2 times
...
Nov 12 13:13:33 daniel-desktop NetworkManager[847]: <info> wake requested (sleeping: yes  enabled: yes)
Nov 12 13:13:33 daniel-desktop NetworkManager[847]: <info> waking up and re-enabling...
...
Nov 12 13:13:49 daniel-desktop dbus[796]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov 12 13:13:49 daniel-desktop dbus[796]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 12 13:13:49 daniel-desktop avahi-daemon[827]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::8e89:a5ff:fe1b:7f76.
...
Nov 12 13:15:53 daniel-desktop kernel: [41701.787966] usb 2-1.1: USB disconnect, device number 3
Nov 12 13:17:01 daniel-desktop CRON[21488]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 13:19:12 daniel-desktop kernel: [41900.055365] usb 2-1.1: new low speed USB device number 4 using ehci_hcd
Nov 12 13:19:12 daniel-desktop mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Nov 12 13:19:12 daniel-desktop kernel: [41900.159182] input: MLK Wireless Desktop as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input13
Nov 12 13:19:12 daniel-desktop kernel: [41900.159235] generic-usb 0003:046A:0100.0003: input,hidraw0: USB HID v1.00 Keyboard [MLK Wireless Desktop] on usb-0000:00:1d.0-1.1/input0
Nov 12 13:19:12 daniel-desktop kernel: [41900.165171] input: MLK Wireless Desktop as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input14
Nov 12 13:19:12 daniel-desktop kernel: [41900.165253] generic-usb 0003:046A:0100.0004: input,hiddev0,hidraw1: USB HID v1.00 Mouse [MLK Wireless Desktop] on usb-0000:00:1d.0-1.1/input1
Nov 12 13:19:12 daniel-desktop mtp-probe: bus: 2, device: 4 was not an MTP device

In the logs You can see that I send my Desktop to sleep (Suspend) and then startet it again but the keyboard did not respond. I then removed the PS/2 keyboard and switched back to my wireless keyboard (unplugged the usb-dongle and replugged it)

any other things? I will post if I find out more...

---

### Post by Mark Phelps on 2011-11-12
I too, don't think this is a keyboard problem -- but yet ANOTHER problem with 11.10.  This same keyboard has worked flawlessly for years.  And, after I replaced it, I plugged it into another PC -- and it works fine there.  

The difference?  The other PC is NOT running Ubuntu 11.10.

---

### Post by verymadpip on 2011-11-12
I don't think this is new.

[http://ubuntuforums.org/showthread.php?t=1485671](http://ubuntuforums.org/showthread.php?t=1485671)

I could be wrong.  I have been before & I fully expect to be again.

---

### Post by Garland Fox on 2011-11-14
I am not sure I could call this solved yet, but the keyboard does seem to be slowly improving over time in 11.10.
Wife has not had to unplug/replug in the last day or so - problem intermittent at this time instead of  continuous malfunction.
Go figure...
Thanks...
By the way... 10.04 acted similar when we first installed it.
Same end result--slow improvement?
thx again

---

### Post by Garland Fox on 2011-11-27
> **Garland Fox said:**
> I am not sure I could call this solved yet, but the keyboard does seem to be slowly improving over time in 11.10.
Wife has not had to unplug/replug in the last day or so - problem intermittent at this time instead of  continuous malfunction.
Go figure...
Thanks...
By the way... 10.04 acted similar when we first installed it.
Same end result--slow improvement?
thx again

Slowly improved.
No problems in last 7 or 8 days.
Maybe an update fixed it.
Marking it solved.

---

### Post by pquest on 2012-02-28
I am still having this problem. Keyboard is a Logitech G19. It never works at all. Even if I unplug it and plug it back in.

---

