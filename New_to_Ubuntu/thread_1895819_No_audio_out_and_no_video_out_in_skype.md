---
title: "No audio out and no video out in skype"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by pierreu1 on 2011-12-15
This is a new attempt at setting my system to use Skype.

Initially, I had no video out, but had everything else working.

I got help, but now I have no video out and no audio out.

Here is the [thread]("http://ubuntuforums.org/showthread.php?p=11536458#post11536458").

I went into system profiler and benchmark and copied the following in order to find a solution, but please direct me as to what I should do to help you find out where my system is now, so you can presumably get it to work. I hope this helps.

Thanks.

-Loaded Modules-
nls_utf8
isofs
binfmt_misc
parport_pc		: PC-style parallel port driver
ppdev
dm_crypt		: device-mapper target for transparent encryption / decryption
snd_usb_audio		: USB Audio
snd_hda_codec_si3054		: Si3054 HD-audio modem codec
snd_usbmidi_lib		: USB Audio/MIDI helper module
snd_hda_codec_realtek		: Realtek HD-audio codec
arc4		: ARC4 Cipher Algorithm
snd_hda_intel		: Intel HDA driver
iwl3945		: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
snd_hda_codec		: HDA codec core
snd_hwdep		: Hardware dependent layer
snd_seq_midi		: Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi		: Midlevel RawMidi code for ALSA.
iwlcore		: iwl core
gspca_sn9c20x		: GSPCA/SN9C20X USB Camera Driver
gspca_main		: GSPCA USB Camera Driver
snd_atiixp_modem		: ATI IXP MC97 controller
snd_seq_midi_event		: MIDI byte &lt;-&gt; sequencer event coder
videodev		: Device registrar for Video4Linux drivers v2
snd_via82xx_modem		: VIA VT82xx modem
snd_intel8x0m		: Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7013; NVidia MCP/2/2S/3 modems
mac80211		: IEEE 802.11 subsystem
snd_ac97_codec		: Universal interface for Audio Codec &apos;97
snd_seq		: Advanced Linux Sound Architecture sequencer.
ac97_bus
pcmcia		: PCMCIA Driver Services
snd_pcm		: Midlevel PCM code for ALSA.
joydev		: Joystick device interfaces
snd_timer		: ALSA timer interface
snd_seq_device		: ALSA sequencer device management
ipt_REJECT		: Xtables: packet &quot;rejection&quot; target for IPv4
ipt_LOG		: Xtables: IPv4 packet logging to syslog
xt_limit		: Xtables: rate-limit match
xt_tcpudp		: Xtables: TCP, UDP and UDP-Lite match
ipt_addrtype		: Xtables: address type match for IPv4
xt_state		: ip[6]_tables connection tracking state match module
yenta_socket
cfg80211		: wireless configuration support
psmouse		: PS/2 mouse driver
tifm_7xx1		: TI FlashMedia host driver
ip6table_filter		: ip6tables filter table
ip6_tables		: IPv6 packet filter
nf_nat_irc		: IRC (DCC) NAT helper
nf_conntrack_irc		: IRC (DCC) connection tracking helper
nf_nat_ftp		: ftp NAT helper
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack_ftp		: ftp connection tracking helper
snd		: Advanced Linux Sound Architecture driver for soundcards.
tifm_core		: TI FlashMedia core driver
pcmcia_rsrc
serio_raw		: Raw serio driver
nf_conntrack
iptable_filter		: iptables filter table
soundcore		: Core sound module
ip_tables		: IPv4 packet filter
x_tables		: {ip,ip6,arp,eb}_tables backend module
pcmcia_core		: Linux Kernel Card Services
snd_page_alloc		: Memory allocator for ALSA system.
sparse_keymap		: Generic support for sparse keymaps
lp
parport
usbhid		: USB HID core driver
i915		: Intel Graphics
hid
drm_kms_helper		: DRM KMS helper
drm		: DRM shared core routines
i2c_algo_bit		: I2C-Bus bit-banging algorithm
firewire_ohci		: Driver for PCI OHCI IEEE1394 controllers
sdhci_pci		: Secure Digital Host Controller Interface PCI driver
firewire_core		: Core IEEE1394 transaction logic
e100		: Intel(R) PRO/100 Network Driver
sdhci		: Secure Digital Host Controller Interface core driver
crc_itu_t		: CRC ITU-T V.41 calculations
video		: ACPI Video Driver


+

operating system info (just in case)


-Version-
Kernel		: Linux 2.6.38-13-generic (i686)
Compiled		: #52-Ubuntu SMP Tue Nov 8 16:48:07 UTC 2011
C Library		: Unknown
Default C Compiler		: GNU C Compiler version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
Distribution		: Ubuntu 11.04
-Current Session-
Computer Name		: Pierre-Vancouver
User Name		: pierre2 (pierre1)
Home Directory		: /home/pierre2
Desktop Environment		: GNOME 2.32.1
-Misc-
Uptime		: 1 day, 13 hours and 27 minutes
Load Average		: 0.27, 0.23, 0.46

---

### Post by pierreu1 on 2011-12-20
This was solved at [http://ubuntuforums.org/showthread.php?t=1895867](http://ubuntuforums.org/showthread.php?t=1895867)

---

