---
title: "sounds familiar- soundblaster soundless"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-08-15
I have an integrated sound card and a Creative soundblaster live card and a logitech webcam. I now have so many setting to choose from in the preference options I am running in circles.
I would like all my applications to run on the soundblaster card

Here are my aplay and lspci results what does it all mean?

-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
Subdevices: 32/32
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
Subdevice #2: subdevice #2
Subdevice #3: subdevice #3
Subdevice #4: subdevice #4
Subdevice #5: subdevice #5
Subdevice #6: subdevice #6
Subdevice #7: subdevice #7
Subdevice #8: subdevice #8
Subdevice #9: subdevice #9
Subdevice #10: subdevice #10
Subdevice #11: subdevice #11
Subdevice #12: subdevice #12
Subdevice #13: subdevice #13
Subdevice #14: subdevice #14
Subdevice #15: subdevice #15
Subdevice #16: subdevice #16
Subdevice #17: subdevice #17
Subdevice #18: subdevice #18
Subdevice #19: subdevice #19
Subdevice #20: subdevice #20
Subdevice #21: subdevice #21
Subdevice #22: subdevice #22
Subdevice #23: subdevice #23
Subdevice #24: subdevice #24
Subdevice #25: subdevice #25
Subdevice #26: subdevice #26
Subdevice #27: subdevice #27
Subdevice #28: subdevice #28
Subdevice #29: subdevice #29
Subdevice #30: subdevice #30
Subdevice #31: subdevice #31
card 1: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
Subdevices: 8/8
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
Subdevice #2: subdevice #2
Subdevice #3: subdevice #3
Subdevice #4: subdevice #4
Subdevice #5: subdevice #5
Subdevice #6: subdevice #6
Subdevice #7: subdevice #7
card 1: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
Subdevices: 1/1
Subdevice #0: subdevice #0


-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
Subsystem: Dell Unknown device 01d2
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: efd00000-efefffff
Prefetchable memory behind bridge: 00000000ec000000-00000000edffffff
Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: Dell Unknown device 01d2
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
Memory behind bridge: efc00000-efcfffff
Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
Subsystem: Dell Unknown device 01d2
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
Subsystem: Dell Unknown device 01d2
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
Subsystem: Dell Unknown device 01d2
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
Subsystem: Dell Unknown device 01d2
Flags: bus master, medium devsel, latency 0, IRQ 20
I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
Subsystem: Dell Unknown device 01d2
Flags: bus master, medium devsel, latency 0, IRQ 17
Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
I/O behind bridge: 0000c000-0000cfff
Memory behind bridge: efb00000-efbfffff
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
Subsystem: Dell Unknown device 01d2
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Dell Unknown device 01d2
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
I/O ports at fe00 [size=8]
I/O ports at fe10 [size=4]
I/O ports at fe20 [size=8]
I/O ports at fe30 [size=4]
I/O ports at fea0 [size=16]
Memory at c4000000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
Subsystem: Dell Unknown device 01d2
Flags: medium devsel, IRQ 9
I/O ports at ece0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] (prog-if 00 [VGA controller])
Subsystem: ATI Technologies Inc Unknown device 0602
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at ec000000 (64-bit, prefetchable) [size=32M]
Memory at efde0000 (64-bit, non-prefetchable) [size=64K]
I/O ports at dc00 [size=256]
Expansion ROM at efe00000 [disabled] [size=128K]
Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
Subsystem: ATI Technologies Inc Unknown device 0603
Flags: bus master, fast devsel, latency 0
Memory at efdf0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>

03:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
Flags: bus master, medium devsel, latency 64, IRQ 19
Memory at efbfe800 (32-bit, non-prefetchable) [size=2K]
I/O ports at cc80 [size=128]
Capabilities: <access denied>

03:03.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0
Subsystem: Creative Labs SBLive! 5.1 Model SB0100
Flags: bus master, medium devsel, latency 64, IRQ 22
I/O ports at cc20 [size=32]
Capabilities: <access denied>

03:03.1 Input device controller: Creative Labs SB Live! Game Port (rev 0
Subsystem: Creative Labs Gameport Joystick
Flags: bus master, medium devsel, latency 64
I/O ports at cc18 [size=8]
Capabilities: <access denied>

03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
Subsystem: Dell Unknown device 01ab
Flags: bus master, medium devsel, latency 64, IRQ 21
Memory at efbff000 (32-bit, non-prefetchable) [size=4K]
I/O ports at cc40 [size=64]
Capabilities: <access denied>
__________________

---

### Post by bobnutfield on 2008-08-15
If possible, the easiest thing to do would be to disable the onboard sound BIOS settings.  Some BIOSes do not have that option, and if not, you may have to disable it by removing the modules that support it.  Type:

> sudo lsmod | grep snd

to see which modules for sound are loaded.  The driver for the onboard card is the snd-hda-intel module.  That is a very commonly used module, but I do not believe the Soundblaster card uses it.

---

### Post by Midgetprawn on 2008-08-15
OK here is the output from [sudo lsmod | grep snd 
]

Soundblaster uses emu10k1

I have set it as my sound preference but all I get is hiss
 and no sound!!

snd_usb_audio          83936  1 
snd_usb_lib            18432  1 snd_usb_audio
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           146880  4 snd_emu10k1_synth
snd_hda_intel         344728  2 
snd_ac97_codec        101028  1 snd_emu10k1
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_pcm                78596  5 snd_usb_audio,snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  3 snd_emu10k1,snd_hda_intel,snd_pcm
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10500  4 snd_usb_audio,snd_emux_synth,snd_emu10k1,snd_hda_intel
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  4 snd_usb_lib,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  29 snd_usb_audio,snd_usb_lib,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_dummy,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
usbcore               146028  9 snd_usb_audio,snd_usb_lib,pwc,speedtch,usbatm,usbhid,ehci_hcd,uhci_hcd

---

### Post by bobnutfield on 2008-08-15
Well, both modules are fully loaded.  If you have not tried to disable the on=board sound in the BIOS, I would try that first.  I have only once in the past removed the module supporting my on-board sound in favor of using a PCI card, and it worked, but that was many years ago.  I also believe that possibly blacklisting the snd-hda-intel module may work as well.  These are just possible suggestions, but I would let a few others post before doing that to see if there are others who may be able to suggest something for suitable.

---

### Post by HittingSmoke on 2008-08-15
I have the same problem with my Audigy card. Alsa installs the Emu10k1 driver and when I use it I get a loud hissing with just a hint of my music buried underneath it. I did some digging and on the Alsa web site it says Audigy and newer cards use the Emu10k2 driver and if it wasnt available for my OS I'd have to compile one.  I dont know how to compile... or much of anything about Linux for that matter and my post about it went unanswered so I just enabled my onboard Realtek and it works fine other than no surround.

I decided I would just stick with my onboard until I get a bit more comfortable tweaking with Linux, compiling and such.

---

### Post by bobnutfield on 2008-08-15
> **HittingSmoke said:**
> I have the same problem with my Audigy card. Alsa installs the Emu10k1 driver and when I use it I get a loud hissing with just a hint of my music buried underneath it. I did some digging and on the Alsa web site it says Audigy and newer cards use the Emu10k2 driver and if it wasnt available for my OS I'd have to compile one.  I dont know how to compile... or much of anything about Linux for that matter and my post about it went unanswered so I just enabled my onboard Realtek and it works fine other than no surround.

I decided I would just stick with my onboard until I get a bit more comfortable tweaking with Linux, compiling and such.

This may well be the problem.  Here is a link on installing drivers from ALSA.  Compiling is not really difficult.  You do not have to be a coder to know how to do it.  It is really just making sure you have the gcc compiler installed, which, again is as simple as installing it from Synaptic.

[http://tldp.org/HOWTO/Alsa-sound-4.html]("http://tldp.org/HOWTO/Alsa-sound-4.html")

---

### Post by HittingSmoke on 2008-08-15
Thanks a lot! Ill try this out later this evening when I have some time and post the results. The guide seems a little bit confusing from skimming over it but I should be able to work through it and be all the wiser after.

Thanks again.

---

### Post by trash on 2008-09-10
> **bobnutfield said:**
> Well, both modules are fully loaded.  If you have not tried to disable the on=board sound in the BIOS, I would try that first.  I have only once in the past removed the module supporting my on-board sound in favor of using a PCI card, and it worked, but that was many years ago.  I also believe that possibly blacklisting the snd-hda-intel module may work as well.  These are just possible suggestions, but I would let a few others post before doing that to see if there are others who may be able to suggest something for suitable.

I disabled the sound in the bios but would get kernel panics everytime i tried to play anything. So then i blacklisted snd_ac97_codec but it keeps loading anyway as well as snd_emu10k1.. and still no sound coming out of my soundblaster card.

---

