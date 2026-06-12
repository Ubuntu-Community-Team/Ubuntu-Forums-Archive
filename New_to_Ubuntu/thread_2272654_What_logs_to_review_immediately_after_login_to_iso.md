---
title: "What logs to review immediately after login to isolate inconsistent behavior"
date: 2015-04-08
forum: New to Ubuntu
---

### Post by robertzito on 2015-04-08
What is the duration from the time you log in into Ubuntu 12.04 to the time Ubuntu becomes available for use? 
late 
An example is once you enter your password and hit enter I  see my desktop background only after a duration of time the icons and my desktop items become visible and Ubuntu is ready for use.

There are times that the duration from log in and just my background being visible to the time that desktop items and icons, I think it is called launcher. There are times that the duration from when I log in to the availability of launcher and desktop items are instantaneous and other times it takes a several seconds, but very noticeable delay.

From a Ubuntu system understanding is this considered something else rather than boot up because the log in screen is available or is this considered system?

I am trying to see what logs I can review and see what is contributing to the delay and tweak so it is always that immediate look and feel and if this is considered boot up or post boot up?

Immediately once the system becomes available I run a GUI program called Ksystemlog and these are all the warnings in my syslog:

These are all the "Warning" messages.

**04/08/15 02:37:50 AM MyUbuntu kernel  [   34.618509] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)**
[B]
04/08/15 02:37:50 AM MyUbuntu kernel  [   34.618520] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)[/B]
[B]
04/08/15 02:37:50 AM MyUbuntu kernel  [   34.618525] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)[/B]
[B]
04/08/15 02:37:51 AM MyUbuntu kernel  [   37.200720] rts5139: module is from the staging directory, the quality is unknown, you have been warned.[/B]
[B]
04/08/15 02:37:52 AM MyUbuntu NetworkManager[888] <warn> failed to allocate link cache: (-12) Object not found[/B]
[B]
04/08/15 02:37:52 AM MyUbuntu NetworkManager[888] <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...[/B]
[B]
04/08/15 02:37:52 AM MyUbuntu NetworkManager[888] <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...[/B]
[B]
04/08/15 02:37:52 AM MyUbuntu NetworkManager[888] <warn> Trying to remove a non-existant call id.[/B]
[B]
04/08/15 02:37:53 AM MyUbuntu ModemManager[824] <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0': not supported by any plugin[/B]
[B]
04/08/15 02:37:53 AM MyUbuntu ModemManager[824] <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0': not supported by any plugin[/B]
[B]
04/08/15 02:37:55 AM MyUbuntu NetworkManager[888] <warn> dnsmasq not available on the bus, can't update servers.[/B]
[B]
04/08/15 02:37:55 AM MyUbuntu NetworkManager[888] <warn> DNS: plugin dnsmasq update failed[/B]
[B]
04/08/15 02:37:55 AM MyUbuntu dnsmasq[1502] warning: no upstream servers configured[/B]
[B]
04/08/15 02:37:56 AM MyUbuntu NetworkManager[888] <warn> dnsmasq appeared on DBus: :1.13[/B]
[B]
04/08/15 02:38:42 AM MyUbuntu NetworkManager[888] <warn> (wlan0): DHCPv6 request timed out.[/B]
[B]
04/08/15 02:39:05 AM MyUbuntu gnome-session[5690] WARNING: Could not parse desktop file gnome-user-share.desktop or it references a not found TryExec binary

[U]Here are the errors

[/U][/B]_**04/08/15 02:37:50 AM MyUbuntu kernel  [    0.206368] ACPI: Using IOAPIC for interrupt routing**_
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.212219] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.228703] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.228758] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.228810] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.228860] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 *11 12 14 15)[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.228911] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.228960] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.229010] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *7[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [    0.229061] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)[/B][/U]
[U][B]
04/08/15 02:37:50 AM MyUbuntu kernel  [   35.010880] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro[/B][/U]
[U][B]
04/08/15 02:37:55 AM MyUbuntu NetworkManager[888] <error> [1428475075.150525] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not 
found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name[/B][/U]

---

### Post by mastablasta on 2015-04-08
dmesg will show error messages.

also kernel.log

otherwise bootchart should show where system get's "stuck".: [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

