---
title: "Sound issues"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by Netraxs on 2013-02-13
After hunting down my video card drivers and finally managing skype (previously it was like Max Payne was sitting at this computer, everything was so slow it was impossible to pretty much do anything), I took the tedious task (least I heard it's hard for most) to get the sound to work. The Sound tab in system settings only shows me a Dummy Output. I've tried several workaround and haven't found one that works. I know how to use the terminal pretty well, was using the command prompt in Windows pretty often. So, following the "Conprehensive Sound Promblem Solution" thingy I found that "aplay -l" gives me this: **aplay: device_list:252: no soundcards found...**

Aaaand the "lspci -v" gives me this"
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f0000000-f1ffffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e300 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e100 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at e200 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Giga-byte Technology Device 5006
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f4004000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f2000000-f3ffffff
    Prefetchable memory behind bridge: 000000007ff00000-000000007fffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: leds-ss4200, lpc_ich, intel-rng

00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 80 [Master])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
    Subsystem: Giga-byte Technology GA-8I945PG-RH Mainboard
    Flags: medium devsel, IRQ 11
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde [Radeon HD 7700 Series] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 0429
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f1000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at c000 [size=256]
    [virtual] Expansion ROM at f0000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0
    Subsystem: ASUSTeK Computer Inc. Device aab0
    Flags: bus master, fast devsel, latency 0, IRQ 12
    Memory at f1040000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Flags: bus master, medium devsel, latency 64, IRQ 19
    I/O ports at d000 [size=256]
    Memory at f3000000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at 7ff00000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

``` I'd really like to switch from Windows, and I'm hoping that a hardware issue will be easy to fix :)

---

### Post by Sealbhach on 2013-02-13
OK, well this looks like your sound card

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)     Subsystem: Giga-byte Technology Device a002     Flags: bus master, fast devsel, latency 0, IRQ 10     Memory at f4000000 (64-bit, non-prefetchable) [size=16K]     Capabilities: <access denied>     Kernel modules: snd-hda-intel


Apparently that should work just fine with Ubuntu. See [here]("http://www.ubuntu.com/certification/catalog/component/pci:8086:27D8-AUDIO/").

Maybe your kernel module is not loading for some reason. List the sound modules you have running:

```
lsmod | grep snd
```

and if you don't see snd-hda-intel then load it with

```
sudo modprobe snd-hda-intel
```

A kernel module is like a driver in Windows, it comes already with the kernel so you don't have to download it separately.

.

---

### Post by Netraxs on 2013-02-14
Welp, the ```
lsmod | grep snd
``` shows me absolutely nothing, no output. And the ```
sudo modprobe snd-hda-intel
``` gives me a big, angry list :| ```
3.5.0-23-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
FATAL: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Error running install command for snd
WARNING: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
FATAL: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Error running install command for snd
WARNING: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/core/snd-timer.ko': No such file or directory
FATAL: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Error running install command for snd_pcm
WARNING: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not read '/lib/modules/3.5.0-23-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory

``` I think I am missing the modules since Ubuntu can't find them :/

---

### Post by Netraxs on 2013-02-14
Sorry for bumping, but I need to

---

### Post by Netraxs on 2013-02-14
Well, didn't achieving anything then, I became suspicious that I might've screwed up the modules while doing various workaround. Deleting alsa and sound-something and then trying to reinstall them can do stuff right? Regardless, I decided to do a fresh, clean install of Ubuntu again. The first thing I did is install my graphics drivers, then reboot. After that, I took Sealbach's advice and tried to activate the module. Well first I tried the lsmod command, contrary to before, it showed loaaads of stuff, while previously there was no output at all. Then I was able to get the snd-hda-intel to turn on. Reboot. My eyes went O_O when I heard a sound at the login screen. I tried playing a YT video and my output went crazy, switching between the headphones and speakers. The speakers work fine, but I can barely make out something whilst using the headphones. It's activating\deactivating ~50/s whenever there's a sound input. Least I HAVE sound at all. I can be with the speakers alone, but I'd like my headphones working too :3.

---

### Post by Sealbhach on 2013-02-14
Sounds like you're getting somewhere. Normally you should not have to activate snd-hda-intel at every startup, next bootup don't run the modprobe command and see what happens. It should be already loaded and activated.

I think something went wrong with your last installation which caused the sound modules to fail to install properly.  Now if I were you I would just play around with whatever volume/mixer controls you can find, to get it working the way you like it.

.

---

