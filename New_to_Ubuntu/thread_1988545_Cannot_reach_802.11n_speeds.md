---
title: "Cannot reach 802.11n speeds"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by roton on 2012-05-27
I've just put a fresh install of Ubuntu 12.04 on my laptop but I cannot get network speeds greater than 20-30Mb (even though my NIC and router support N speeds).
My NIC is a Broadcom BCM4313. I have tried with and without the 'additional drivers' (which I believe use the bcmwl-kernel-source).

Anything else I can try?

---

### Post by alphacrucis2 on 2012-05-27
> **roton said:**
> I've just put a fresh install of Ubuntu 12.04 on my laptop but I cannot get network speeds greater than 20-30Mb (even though my NIC and router support N speeds).
My NIC is a Broadcom BCM4313. I have tried with and without the 'additional drivers' (which I believe use the bcmwl-kernel-source).

Anything else I can try?

What makes you think the wireless part of the connection is limiting the speed?

---

### Post by idoitprone on 2012-05-27
> **roton said:**
> I've just put a fresh install of Ubuntu 12.04 on my laptop but I cannot get network speeds greater than 20-30Mb (even though my NIC and router support N speeds).
My NIC is a Broadcom BCM4313. I have tried with and without the 'additional drivers' (which I believe use the bcmwl-kernel-source).

Anything else I can try?

Is it megabit or megabytes is matter a whole lot

600/8= 75MB/s

tcp/ip stack is expensive so
75/2 = 37.5 MB/s which is the around the normal speed

then you have to deal with ISPs
What is your ISP advertised rate?
The bottleneck should be the ISP is not giving you the fastest connections, so it is the proper speed, I supposed

---

### Post by roton on 2012-05-28
Thanks for the replies.

> **alphacrucis2 said:**
> What makes you think the wireless part of the connection is limiting the speed?

I can get faster speeds on other wireless and wired devices in the network. Wireless devices average about 70Mb and wired is about 100Mb.


> **idoitprone said:**
> Is it megabit or megabytes is matter a whole lot

600/8= 75MB/s

tcp/ip stack is expensive so
75/2 = 37.5 MB/s which is the around the normal speed

then you have to deal with ISPs
What is your ISP advertised rate?
The bottleneck should be the ISP is not giving you the fastest connections, so it is the proper speed, I supposed

It is Mb (so it would be 30Mb/s or 3.75MB/s) and the ISP gives a far greater speed (100Mb). Even if they didn't I should still be able to manage more than 30Mb between computers on the 802.11n network. I have to assume it's a driver issue since 30Mb is where 802.11g speeds max out :(

---

### Post by d4m1r on 2012-05-28
Where are you located? I doubt you are getting a 100mbps connection from your ISP unless you are paying very much each month....Anyway, N speeds can really only be reached on local networks at this point because most people do not have 300mbps connections at home (what N is rated for). To test it, transfer a large file between 1 PC to another and check your transfer speed if speeds are 37.5mb/s then you are getting N speeds.

Also, you could use a PC running Windows to see if this is a Ubuntu issue, or a networking one.

---

### Post by roton on 2012-05-28
> **d4m1r said:**
> Where are you located? I doubt you are getting a 100mbps connection from your ISP unless you are paying very much each month....Anyway, N speeds can really only be reached on local networks at this point because most people do not have 300mbps connections at home (what N is rated for). To test it, transfer a large file between 1 PC to another and check your transfer speed if speeds are 37.5mb/s then you are getting N speeds.

Also, you could use a PC running Windows to see if this is a Ubuntu issue, or a networking one.

UK. Why does everyone keep questioning the speed? I can post a speedtest if necessary :p

As I said I can already get 70Mb using another wireless pc (Windows) so there is no issue with the wifi or isp.

I cannot get more than 30Mb (the limit of 802.11g) with this NIC, although it is rated for 802.11n. Therefore this is either some Ubuntu driver/config issue... or Broadcom accidentally put an "n" in the instruction manual :D

---

### Post by idoitprone on 2012-05-30
> **roton said:**
> UK. Why does everyone keep questioning the speed? I can post a speedtest if necessary :p

As I said I can already get 70Mb using another wireless pc (Windows) so there is no issue with the wifi or isp.

I cannot get more than 30Mb (the limit of 802.11g) with this NIC, although it is rated for 802.11n. Therefore this is either some Ubuntu driver/config issue... or Broadcom accidentally put an "n" in the instruction manual :D

ISP are notorious for short changing their customers

Sigh your chip is broadcom. they cast their linux user to the side alot with their bad drivers.

```
lspci -nnk
```
try changing drivers

perhaps the wl module
[https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module](https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module)

---

### Post by roton on 2012-05-30
> **idoitprone said:**
> ISP are notorious for short changing their customers

Wired:

[IMG]http://speedtest.net/result/1980566629.png[/IMG]

> **idoitprone said:**
> Sigh your chip is broadcom. they cast their linux user to the side alot with their bad drivers.

```
lspci -nnk
```
try changing drivers

perhaps the wl module
[https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module](https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module)

lspci -nk:

```
00:00.0 0600: 8086:0044 (rev 02)
	Subsystem: 144d:c587
	Kernel driver in use: agpgart-intel
00:02.0 0300: 8086:0046 (rev 02)
	Subsystem: 144d:c587
	Kernel driver in use: i915
	Kernel modules: i915
00:1a.0 0c03: 8086:3b3c (rev 05)
	Subsystem: 144d:c587
	Kernel driver in use: ehci_hcd
00:1b.0 0403: 8086:3b56 (rev 05)
	Subsystem: 144d:c587
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 0604: 8086:3b42 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 0604: 8086:3b46 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 0604: 8086:3b48 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 0604: 8086:3b4a (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 0c03: 8086:3b34 (rev 05)
	Subsystem: 144d:c587
	Kernel driver in use: ehci_hcd
00:1e.0 0604: 8086:2448 (rev a5)
00:1f.0 0601: 8086:3b09 (rev 05)
	Subsystem: 144d:c587
	Kernel modules: iTCO_wdt
00:1f.2 0106: 8086:3b29 (rev 05)
	Subsystem: 144d:c587
	Kernel driver in use: ahci
00:1f.3 0c05: 8086:3b30 (rev 05)
	Subsystem: 144d:c587
	Kernel modules: i2c-i801
01:00.0 0280: 14e4:4727 (rev 01)
	Subsystem: 144f:7179
	Kernel driver in use: brcmsmac
	Kernel modules: bcma, brcmsmac
05:00.0 0200: 10ec:8168 (rev 06)
	Subsystem: 144d:c587
	Kernel driver in use: r8169
	Kernel modules: r8169
06:00.0 ff00: 10ec:5209 (rev 01)
	Subsystem: 144d:c587
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor
06:00.1 0805: 10ec:5209 (rev 01)
	Subsystem: 144d:c587
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
3f:00.0 0600: 8086:2c62 (rev 02)
	Subsystem: 8086:8086
3f:00.1 0600: 8086:2d01 (rev 02)
	Subsystem: 8086:8086
3f:02.0 0600: 8086:2d10 (rev 02)
	Subsystem: 8086:8086
3f:02.1 0600: 8086:2d11 (rev 02)
	Subsystem: 8086:8086
3f:02.2 0600: 8086:2d12 (rev 02)
	Subsystem: 8086:8086
3f:02.3 0600: 8086:2d13 (rev 02)
	Subsystem: 8086:8086

```

Thanks for the link. I looked at it but it seems mainly aimed at those which aren't working... May give it a go anyway, just hope it doesn't stop working :p

---

### Post by idoitprone on 2012-05-31
> **roton said:**
> Wired:

[IMG]http://speedtest.net/result/1980566629.png[/IMG]



lspci -nk:

```
00:00.0 0600: 8086:0044 (rev 02)
    Subsystem: 144d:c587
    Kernel driver in use: agpgart-intel
00:02.0 0300: 8086:0046 (rev 02)
    Subsystem: 144d:c587
    Kernel driver in use: i915
    Kernel modules: i915
00:1a.0 0c03: 8086:3b3c (rev 05)
    Subsystem: 144d:c587
    Kernel driver in use: ehci_hcd
00:1b.0 0403: 8086:3b56 (rev 05)
    Subsystem: 144d:c587
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 0604: 8086:3b42 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 0604: 8086:3b46 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 0604: 8086:3b48 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 0604: 8086:3b4a (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 0c03: 8086:3b34 (rev 05)
    Subsystem: 144d:c587
    Kernel driver in use: ehci_hcd
00:1e.0 0604: 8086:2448 (rev a5)
00:1f.0 0601: 8086:3b09 (rev 05)
    Subsystem: 144d:c587
    Kernel modules: iTCO_wdt
00:1f.2 0106: 8086:3b29 (rev 05)
    Subsystem: 144d:c587
    Kernel driver in use: ahci
00:1f.3 0c05: 8086:3b30 (rev 05)
    Subsystem: 144d:c587
    Kernel modules: i2c-i801
01:00.0 0280: 14e4:4727 (rev 01)
    Subsystem: 144f:7179
    Kernel driver in use: brcmsmac
    Kernel modules: bcma, brcmsmac
05:00.0 0200: 10ec:8168 (rev 06)
    Subsystem: 144d:c587
    Kernel driver in use: r8169
    Kernel modules: r8169
06:00.0 ff00: 10ec:5209 (rev 01)
    Subsystem: 144d:c587
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
06:00.1 0805: 10ec:5209 (rev 01)
    Subsystem: 144d:c587
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
3f:00.0 0600: 8086:2c62 (rev 02)
    Subsystem: 8086:8086
3f:00.1 0600: 8086:2d01 (rev 02)
    Subsystem: 8086:8086
3f:02.0 0600: 8086:2d10 (rev 02)
    Subsystem: 8086:8086
3f:02.1 0600: 8086:2d11 (rev 02)
    Subsystem: 8086:8086
3f:02.2 0600: 8086:2d12 (rev 02)
    Subsystem: 8086:8086
3f:02.3 0600: 8086:2d13 (rev 02)
    Subsystem: 8086:8086

```Thanks for the link. I looked at it but it seems mainly aimed at those which aren't working... May give it a go anyway, just hope it doesn't stop working :p

its fine just memorize what driver you where using

```
01:00.0 0280: 14e4:4727 (rev 01) 	Subsystem: 144f:7179 	Kernel driver in use: brcmsmac 	Kernel modules: bcma, brcmsmac
```

you can test the wl driver

```
sudo modprobe -r bcma brcmsmac
sudo modprobe wl
```
to put it back

```
sudo modprobe -r wl
sudo modprobe bcma brcmsmac
```

---

### Post by roton on 2012-05-31
> **idoitprone said:**
> its fine just memorize what driver you where using

```
01:00.0 0280: 14e4:4727 (rev 01) 	Subsystem: 144f:7179 	Kernel driver in use: brcmsmac 	Kernel modules: bcma, brcmsmac
```

you can test the wl driver

```
sudo modprobe -r bcma brcmsmac
sudo modprobe wl
```
to put it back

```
sudo modprobe -r wl
sudo modprobe bcma brcmsmac
```

Thanks for all your help.
I installed the bcmwl-kernel-source package but the wl driver is slower than the brcsmac one :(
Now when I type "sudo modprobe bcma brcmsmac", I am getting:

```
FATAL: Error inserting bcma (/lib/modules/3.2.0-24-generic/kernel/drivers/bcma/bcma.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

edit: After installing and uninstalling the common broadcom drivers (and maybe a few other broadcom related things ;)) and still not getting wireless back I decided to reboot. Now the command works and everything back to normal :p Phew!

---

### Post by idoitprone on 2012-05-31
> **roton said:**
> Thanks for all your help.
I installed the bcmwl-kernel-source package but the wl driver is slower than the brcsmac one :(
Now when I type "sudo modprobe bcma brcmsmac", I am getting:

```
FATAL: Error inserting bcma (/lib/modules/3.2.0-24-generic/kernel/drivers/bcma/bcma.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```edit: After installing and uninstalling the common broadcom drivers (and maybe a few other broadcom related things ;)) and still not getting wireless back I decided to reboot. Now the command works and everything back to normal :p Phew!

my bad. i never had a broadcom and did not realize it was that brain dead
strange? modprobe should be able to find bcma since it brcmsmac depends on it
next time use lsmod to check

let see if the you have to reconfigure that module

print the modinfo of both modules
```
modinfo brcmsmac
modinfo bcma
```nvm i took a look at the modinfo of both of those kernel and there is no way to configure it

there only one more driver to try out it the brcm80211
according to henry
[QUOTE="Henry Ptasinski" <henryp-dY08KVG/lbpWk0Htik3J/w-AT-public.gmane.org>] Greg,

The brcmsmac driver supports full-rate 802.11n/HT operation on 20MHz channels,
and has from the day we released it.  This includes 802.11n/HT rates and
multiple spatial streams, and a number of additional 11n features such as
A-MPDU and RIFS.  Current iperf testing on 20MHz channels with a BCM43224
achieves greater than 70Mbps TCP throughput, using phy rates up to about
130Mbps.
[/QUOTE]
it should support that n standard
[http://lwn.net/Articles/456872/](http://lwn.net/Articles/456872/)
but it has a suspend bug
there are direction to fix it in arch wiki
[https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module](https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module)

this is the last driver to test. BCM4313 is seriously one of the many chips that cause headaches on every linux forums for years. Dawm broadcom

---

### Post by roton on 2012-06-01
> **idoitprone said:**
> my bad. i never had a broadcom and did not realize it was that brain dead
strange? modprobe should be able to find bcma since it brcmsmac depends on it
next time use lsmod to check

let see if the you have to reconfigure that module

print the modinfo of both modules
```
modinfo brcmsmac
modinfo bcma
```nvm i took a look at the modinfo of both of those kernel and there is no way to configure it

there only one more driver to try out it the brcm80211
according to henry

it should support that n standard
[http://lwn.net/Articles/456872/](http://lwn.net/Articles/456872/)
but it has a suspend bug
there are direction to fix it in arch wiki
[https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module](https://wiki.archlinux.org/index.php/Broadcom_wireless#Loading_the_wl_kernel_module)

this is the last driver to test. BCM4313 is seriously one of the many chips that cause headaches on every linux forums for years. Dawm broadcom

Nice find, this looks very promising! Is this the way to install the driver - [http://ubuntuforums.org/showthread.php?t=1617380](http://ubuntuforums.org/showthread.php?t=1617380)? Since it does not seem to be included in 12.04 (though it was in 11.04?).

---

