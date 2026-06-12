---
title: "Running updates after fresh install greatly slows down browsing / flash videos"
date: 2016-07-01
forum: New to Ubuntu
---

### Post by faraz_k86 on 2016-07-01
I have an old laptop which I only use to watch youtube videos while I am waiting for some process to finish on my main computer.

its an Intel Pentium M 1.8 Ghz, 1GB RAM Toshiba laptop. I have installed Xubuntu 15.04 on it.

Now the problem is that after a fresh install, the system works perfectly. Youtube and flash videos run smoothly, without any jitter or problems. But as soon as I run the updates, browsing becomes slow as anything and it becomes impossible to watch Youtube or any online videos. The videos jitter a lot and video freezes while I can hear the sound.

This has happened twice now. The first time I though it must be the extra apps I installed that must be causing this. So I did a fresh install and only ran the updates. As soon as the updates finished Youtube started acting up again.

So I formatted the drive and did a fresh install again. And have been watching Youtube all day without any problems.

Why does updating cause this?

Is there any reason or workaround for this? Or is it best that I just disable all updates?

Thanks

---

### Post by Impavidus on 2016-07-02
Are you sure you have Xubuntu *15.04*? Because 15.04 is no longer supported. The repositories with the updates have closed, so it can no longer be updated. Better run 16.04. Xubuntu will probably do, but Lubuntu may be better on your specs. Both have 3 years of support.

What graphics hardware have you got in that laptop?

---

### Post by faraz_k86 on 2016-07-02
> **Impavidus said:**
> Are you sure you have Xubuntu *15.04*? Because 15.04 is no longer supported. The repositories with the updates have closed, so it can no longer be updated. Better run 16.04. Xubuntu will probably do, but Lubuntu may be better on your specs. Both have 3 years of support.

What graphics hardware have you got in that laptop?

Hi Impavidus. Thanks for the reply.

Yes, I am positive its 15.04, and I keep getting reminded of updates regularly. Ive taken a screenshot of the updates window:

[url=http://i.imgur.com/GU8QnkA.png]
  [img]http://imgur.com/GU8QnkAl.png[/img]
[/url]

This laptop has an nVidia FX Go5200 graphics.

Below is a hardwareinfo generated report as well if you need to look over it:

```

Computer
********


Summary
-------

-Computer-
Processor		: Intel(R) Pentium(R) M processor 1.80GHz
Memory		: 1544MB (674MB used)
Operating System		: Ubuntu 15.04
User Name		: faraz (Faraz Ahmad Khan)
Date/Time		: Sat 02 Jul 2016 12:13:51 BST
-Display-
Resolution		: 1024x768 pixels
OpenGL Renderer		: Gallium 0.4 on NV34
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: ICH4 - Intel 82801DB-ICH4
-Input Devices-
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 DualPoint Stick
 AlpsPS/2 ALPS DualPoint TouchPad
 Video Bus
 Toshiba input device
-Printers-
No printers found
-SCSI Disks-
ATA SAMSUNG MP0402H
MATSHITA UJDA750 DVD/CDRW

Operating System
----------------

-Version-
Kernel		: Linux 3.19.0-15-generic (i686)
Compiled		: #15-Ubuntu SMP Thu Apr 16 23:32:01 UTC 2015
C Library		: Unknown
Default C Compiler		: GNU C Compiler version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) 
Distribution		: Ubuntu 15.04
-Current Session-
Computer Name		: faraz-TECRA-M2
User Name		: faraz (Faraz Ahmad Khan)
Home Directory		: /home/faraz
Desktop Environment		: XFCE 4
-Misc-
Uptime		: 15 hours, 27 minutes
Load Average		: 0.92, 2.05, 1.49

Kernel Modules
--------------

-Loaded Modules-
michael_mic		: Michael MIC
arc4		: ARC4 Cipher Algorithm
lib80211_crypt_tkip		: lib80211 crypt: TKIP
lib80211_crypt_ccmp		: Host AP crypt: CCMP
rfcomm		: Bluetooth RFCOMM ver 1.11
bnep		: Bluetooth BNEP ver 1.3
btusb		: Generic Bluetooth USB driver ver 0.6
nouveau		: nVidia Riva/TNT/GeForce/Quadro/Tesla
bluetooth		: Bluetooth Core ver 2.20
snd_intel8x0		: Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
snd_ac97_codec		: Universal interface for Audio Codec &apos;97
mxm_wmi		: MXM WMI Driver
ac97_bus
ipw2200		: Intel(R) PRO/Wireless 2200/2915 Network Driver
ttm		: TTM memory manager subsystem (for DRM device)
snd_pcm		: Midlevel PCM code for ALSA.
libipw		: 802.11 data/management/control stack
drm_kms_helper		: DRM KMS helper
drm		: DRM shared core routines
lib80211		: common routines for IEEE802.11 drivers
snd_seq_midi		: Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event		: MIDI byte &lt;-&gt; sequencer event coder
i2c_algo_bit		: I2C-Bus bit-banging algorithm
cfg80211		: wireless configuration support
snd_rawmidi		: Midlevel RawMidi code for ALSA.
snd_seq		: Advanced Linux Sound Architecture sequencer.
pcmcia		: PCMCIA Driver Services
snd_seq_device		: ALSA sequencer device management
snd_timer		: ALSA timer interface
yenta_socket
joydev		: Joystick device interfaces
pcmcia_rsrc
snd		: Advanced Linux Sound Architecture driver for soundcards.
pcmcia_core		: Linux Kernel Card Services
serio_raw		: Raw serio driver
soundcore		: Core sound module
toshiba_acpi		: Toshiba Laptop ACPI Extras Driver
sparse_keymap		: Generic support for sparse keymaps
lpc_ich		: LPC interface for Intel ICH
wmi		: ACPI-WMI Mapping Driver
toshiba_bluetooth		: Toshiba Laptop ACPI Bluetooth Enable Driver
shpchp		: Standard Hot Plug PCI Controller Driver
8250_fintek		: Fintek F812164 module
video		: ACPI Video Driver
mac_hid
parport_pc		: PC-style parallel port driver
ppdev
lp
parport
autofs4
psmouse		: PS/2 mouse driver
firewire_ohci		: Driver for PCI OHCI IEEE1394 controllers
e1000		: Intel(R) PRO/1000 Network Driver
firewire_core		: Core IEEE1394 transaction logic
pata_acpi		: SCSI low-level driver for ATA in ACPI mode
toshsd		: Toshiba PCI Secure Digital Host Controller Interface driver
crc_itu_t		: CRC ITU-T V.41 calculations
pata_isapnp		: low-level driver for ISA PnP ATA

Boots
-----

-Boots-
Fri Jul 1 20:4		: 3..19.0-15-generi|-

Languages
---------

-Available Languages-
en_AG		: English language locale for Antigua and Barbuda
en_AG.utf8		: English language locale for Antigua and Barbuda
en_AU.utf8		: English locale for Australia
en_BW.utf8		: English locale for Botswana
en_CA.utf8		: English locale for Canada
en_DK.utf8		: English locale for Denmark
en_GB.utf8		: English locale for Britain
en_HK.utf8		: English locale for Hong Kong
en_IE.utf8		: English locale for Ireland
en_IN		: English language locale for India
en_IN.utf8		: English language locale for India
en_NG		: English locale for Nigeria
en_NG.utf8		: English locale for Nigeria
en_NZ.utf8		: English locale for New Zealand
en_PH.utf8		: English language locale for Philippines
en_SG.utf8		: English language locale for Singapore
en_US.utf8		: English locale for the USA
en_ZA.utf8		: English locale for South Africa
en_ZM		: English locale for Zambia
en_ZM.utf8		: English locale for Zambia
en_ZW.utf8		: English locale for Zimbabwe

Filesystems
-----------

-Mounted File Systems-
udev	/dev	0.00 % (743.8 MiB of 743.8 MiB)	
tmpfs	/run	3.34 % (145.8 MiB of 150.8 MiB)	
/dev/disk/by-uuid/9ef11159-8431-4ece-9995-bfe9053e77a3	/	14.59 % (30.0 GiB of 35.1 GiB)	
tmpfs	/dev/shm	0.03 % (753.7 MiB of 753.9 MiB)	
tmpfs	/run/lock	0.08 % (5.0 MiB of 5.0 MiB)	
tmpfs	/sys/fs/cgroup	0.00 % (753.9 MiB of 753.9 MiB)	
tmpfs	/run/user/1000	0.03 % (150.7 MiB of 150.8 MiB)	

Display
-------

-Display-
Resolution		: 1024x768 pixels
Vendor		: The X.Org Foundation
Version		: 1.17.1
-Monitors-
Monitor 0		: 1024x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor		: nouveau
Renderer		: Gallium 0.4 on NV34
Version		: 1.5 Mesa 10.5.2
Direct Rendering		: Yes

Environment Variables
---------------------

-Environment Variables-
GNOME_KEYRING_PID
USER		: faraz
LANGUAGE		: en_GB:en
UPSTART_INSTANCE
XDG_SEAT		: seat0
XDG_SESSION_TYPE		: x11
SESSION		: xubuntu
SHLVL		: 0
HOME		: /home/faraz
QT4_IM_MODULE
DESKTOP_SESSION		: xubuntu
XDG_SEAT_PATH		: /org/freedesktop/DisplayManager/Seat0
INSTANCE
DBUS_SESSION_BUS_ADDRESS		: unix:abstract=/tmp/dbus-vaFhrHBe2V
GLADE_MODULE_PATH		: :
GNOME_KEYRING_CONTROL
MANDATORY_PATH		: /usr/share/gconf/xubuntu.mandatory.path
IM_CONFIG_PHASE		: 1
SESSIONTYPE
UPSTART_JOB		: startxfce4
LOGNAME		: faraz
GTK_IM_MODULE
DEFAULTS_PATH		: /usr/share/gconf/xubuntu.default.path
XDG_SESSION_ID		: c1
PATH		: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
GDM_LANG		: en_GB
GLADE_PIXMAP_PATH		: :
XDG_SESSION_PATH		: /org/freedesktop/DisplayManager/Session0
XDG_RUNTIME_DIR		: /run/user/1000
XDG_MENU_PREFIX		: xfce-
LANG		: en_GB.UTF-8
XDG_CURRENT_DESKTOP		: XFCE
XDG_SESSION_DESKTOP		: xubuntu
XAUTHORITY		: /home/faraz/.Xauthority
XMODIFIERS
XDG_GREETER_DATA_DIR		: /var/lib/lightdm-data/faraz
SSH_AUTH_SOCK		: /run/user/1000/keyring/ssh
GLADE_CATALOG_PATH		: :
SHELL		: /bin/bash
GDMSESSION		: xubuntu
UPSTART_EVENTS		: started xsession
GPG_AGENT_INFO		: /run/user/1000/keyring/gpg:0:1
UPSTART_SESSION		: unix:abstract=/com/ubuntu/upstart-session/1000/764
XDG_VTNR		: 7
QT_IM_MODULE
PWD		: /home/faraz
XDG_CONFIG_DIRS		: /etc/xdg/xdg-xubuntu:/usr/share/upstart/xdg:/etc/xdg:/etc/xdg
XDG_DATA_DIRS		: /usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share
CLUTTER_IM_MODULE
JOB		: dbus
SESSION_MANAGER		: local/faraz-TECRA-M2:@/tmp/.ICE-unix/1267,unix/faraz-TECRA-M2:/tmp/.ICE-unix/1267
DISPLAY		: :0.0

Users
-----

-Users-
root		: root
daemon		: daemon
bin		: bin
sys		: sys
sync		: sync
games		: games
man		: man
lp		: lp
mail		: mail
news		: news
uucp		: uucp
proxy		: proxy
www-data		: www-data
backup		: backup
list		: Mailing List Manager
irc		: ircd
gnats		: Gnats Bug-Reporting System (admin)
nobody		: nobody
systemd-timesync		: systemd Time Synchronization
systemd-network		: systemd Network Management
systemd-resolve		: systemd Resolver
systemd-bus-proxy		: systemd Bus Proxy
syslog
messagebus
uuidd
avahi		: Avahi mDNS daemon
dnsmasq		: dnsmasq
whoopsie
avahi-autoipd		: Avahi autoip daemon
kernoops		: Kernel Oops Tracking Daemon
pulse		: PulseAudio daemon
rtkit		: RealtimeKit
saned
usbmux		: usbmux daemon
speech-dispatcher		: Speech Dispatcher
colord		: colord colour management daemon
hplip		: HPLIP system user
lightdm		: Light Display Manager
faraz		: Faraz Ahmad Khan

Devices
*******


Processor
---------

-Processor-
Name		: Intel(R) Pentium(R) M processor 1.80GHz
Family, model, stepping		: 6, 13, 6 (Pentium III/Pentium III Xeon/Celeron)
Vendor		: Intel
-Configuration-
Cache Size		: 2048kb
Frequency		: 1800.00MHz
BogoMIPS		: 3590.86
Byte Order		: Little Endian
-Features-
FDIV Bug		: no
HLT Bug		: no
F00F Bug		: no
Coma Bug		: no
Has FPU		: yes
-Cache-
Cache information not available
-Capabilities-
fpu		: Floating Point Unit
vme		: Virtual 86 Mode Extension
de		: Debug Extensions - I/O breakpoints
pse		: Page Size Extensions (4MB pages)
tsc		: Time Stamp Counter and RDTSC instruction
msr		: Model Specific Registers
pae		: Physical Address Extensions
mce		: Machine Check Architeture
cx8		: CMPXCHG8 instruction
sep		: Fast System Call (SYSENTER/SYSEXIT)
mtrr		: Memory Type Range Registers
pge		: Page Global Enable
mca		: Machine Check Architecture
cmov		: Conditional Move instruction
clflush		: Cache Line Flush instruction
dts		: Debug Store
acpi		: Thermal Monitor and Software Controlled Clock
mmx		: MMX technology
fxsr		: FXSAVE and FXRSTOR instructions
sse		: SSE instructions
sse2		: SSE2 (WNI) instructions
ss		: Self Snoop
tm		: Thermal Monitor
pbe		: Pending Break Enable
bts		: Branch Trace Store
est		: Enhanced SpeedStep
tm2		: Thermal Monitor 2

Memory
------

-Memory-
Total Memory		: 1544056 kB
Free Memory		: 123392 kB
MemAvailable		: 837580 kB
Buffers		: 88284 kB
Cached		: 748092 kB
Cached Swap		: 448 kB
Active		: 759588 kB
Inactive		: 580184 kB
Active(anon)		: 331672 kB
Inactive(anon)		: 186264 kB
Active(file)		: 427916 kB
Inactive(file)		: 393920 kB
Unevictable		: 0 kB
Mlocked		: 0 kB
High Memory		: 659208 kB
Free High Memory		: 27936 kB
Low Memory		: 884848 kB
Free Low Memory		: 95456 kB
Virtual Memory		: 1569788 kB
Free Virtual Memory		: 1569020 kB
Dirty		: 0 kB
Writeback		: 0 kB
AnonPages		: 502956 kB
Mapped		: 191588 kB
Shmem		: 14544 kB
Slab		: 51900 kB
SReclaimable		: 39600 kB
SUnreclaim		: 12300 kB
KernelStack		: 2256 kB
PageTables		: 6464 kB
NFS_Unstable		: 0 kB
Bounce		: 0 kB
WritebackTmp		: 0 kB
CommitLimit		: 2341816 kB
Committed_AS		: 2086204 kB
VmallocTotal		: 122880 kB
VmallocUsed		: 41132 kB
VmallocChunk		: 76720 kB
AnonHugePages		: 81920 kB
CmaTotal		: 0 kB
CmaFree		: 0 kB
HugePages_Total		: 0
HugePages_Free		: 0
HugePages_Rsvd		: 0
HugePages_Surp		: 0
Hugepagesize		: 2048 kB
DirectMap4k		: 77816 kB
DirectMap2M		: 835584 kB

PCI Devices
-----------

-PCI Devices-
Host bridge		: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
PCI bridge		: Intel Corporation 82855PM Processor to AGP Controller (rev 21) (prog-if 00 [Normal decode])
USB controller		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
PCI bridge		: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
ISA bridge		: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
IDE interface		: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
Multimedia audio controller		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
Modem		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
VGA compatible controller		: NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1) (prog-if 00 [VGA controller])
Network controller		: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
FireWire (IEEE 1394)		: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] (prog-if 10 [OHCI])
Ethernet controller		: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
CardBus bridge		: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
CardBus bridge		: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
System peripheral		: Toshiba America Info Systems SD TypA Controller (rev 03)

USB Devices
-----------


Printers
--------

-Printers-
No printers found

Battery
-------

-No batteries-
No batteries found on this system

Sensors
-------


Input Devices
-------------

-Input Devices-
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 DualPoint Stick
 AlpsPS/2 ALPS DualPoint TouchPad
 Video Bus
 Toshiba input device

Storage
-------

-SCSI Disks-
ATA SAMSUNG MP0402H
MATSHITA UJDA750 DVD/CDRW

DMI
---

-BIOS-
Date		: 02/14/2008
Vendor		: TOSHIBA (www.toshiba.com)
Version		: Version 1.60
-Board-
Name		: Portable PC
Vendor		: TOSHIBA (www.toshiba.com)

Resources
---------

-I/O Ports-
<tt>0000-0cf7 </tt>		: PCI Bus 0000:00
<tt>  0000-001f </tt>		: dma1
<tt>  0020-0021 </tt>		: pic1
<tt>  0040-0043 </tt>		: timer0
<tt>  0050-0053 </tt>		: timer1
<tt>  0060-0060 </tt>		: keyboard
<tt>  0061-0061 </tt>		: PNP0800:00
<tt>  0064-0064 </tt>		: keyboard
<tt>  0070-0071 </tt>		: rtc0
<tt>  0080-008f </tt>		: dma page reg
<tt>  00a0-00a1 </tt>		: pic2
<tt>  00c0-00df </tt>		: dma2
<tt>  00f0-00ff </tt>		: PNP0C04:00
<tt>    00f0-00ff </tt>		: fpu
<tt>  0170-0177 </tt>		: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    0170-0177 </tt>		: ata_piix
<tt>  01e0-01e7 </tt>		: pnp 00:04
<tt>  01f0-01f7 </tt>		: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    01f0-01f7 </tt>		: ata_piix
<tt>  0376-0376 </tt>		: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    0376-0376 </tt>		: ata_piix
<tt>  0378-037a </tt>		: parport0
<tt>  037b-037f </tt>		: parport0
<tt>  03c0-03df </tt>		: vesafb
<tt>  03f6-03f6 </tt>		: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    03f6-03f6 </tt>		: ata_piix
<tt>  03f8-03ff </tt>		: serial
<tt>  0480-048f </tt>		: pnp 00:04
<tt>  04d0-04d1 </tt>		: pnp 00:04
<tt>  0680-06ff </tt>		: pnp 00:04
<tt>  0778-077a </tt>		: parport0
<tt>0cf8-0cff </tt>		: PCI conf1
<tt>0d00-ffff </tt>		: PCI Bus 0000:00
<tt>  1000-10ff </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
<tt>    1000-10ff </tt>		: Intel 82801DB-ICH4
<tt>  1400-14ff </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
<tt>  1800-187f </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
<tt>  1880-18bf </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
<tt>    1880-18bf </tt>		: Intel 82801DB-ICH4
<tt>  18c0-18df </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
<tt>    18c0-18df </tt>		: uhci_hcd
<tt>  bfa0-bfaf </tt>		: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    bfa0-bfaf </tt>		: ata_piix
<tt>  c000-cfff </tt>		: PCI Bus 0000:02
<tt>    c000-c0ff </tt>		: PCI CardBus 0000:03
<tt>    c400-c4ff </tt>		: PCI CardBus 0000:03
<tt>    c800-c8ff </tt>		: PCI CardBus 0000:05
<tt>    cc00-ccff </tt>		: PCI CardBus 0000:05
<tt>    cf40-cf7f </tt>		: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
<tt>      cf40-cf7f </tt>		: Intel(R) PRO/1000 Network Driver
<tt>  d800-d803 </tt>		: ACPI PM1a_EVT_BLK
<tt>  d804-d805 </tt>		: ACPI PM1a_CNT_BLK
<tt>  d808-d80b </tt>		: ACPI PM_TMR
<tt>  d810-d815 </tt>		: ACPI CPU throttle
<tt>  d820-d820 </tt>		: ACPI PM2_CNT_BLK
<tt>  d828-d82f </tt>		: ACPI GPE0_BLK
<tt>  d830-d833 </tt>		: iTCO_wdt
<tt>  d860-d87f </tt>		: iTCO_wdt
<tt>  d880-d89f </tt>		: pnp 00:04
<tt>  d8a0-d8bf </tt>		: pnp 00:04
<tt>  e000-e07f </tt>		: pnp 00:04
<tt>  e080-e0ff </tt>		: pnp 00:04
<tt>  e400-e47f </tt>		: pnp 00:04
<tt>  e480-e4ff </tt>		: pnp 00:04
<tt>  e800-e87f </tt>		: pnp 00:04
<tt>  e880-e8ff </tt>		: pnp 00:04
<tt>  ec00-ec7f </tt>		: pnp 00:04
<tt>  ec80-ecff </tt>		: pnp 00:04
<tt>  eeac-eeac </tt>		: pnp 00:04
<tt>  eeb0-eebf </tt>		: pnp 00:04
<tt>  eec0-eeff </tt>		: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
<tt>    eec0-eeff </tt>		: pnp 00:04
<tt>  ef80-ef9f </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
<tt>    ef80-ef9f </tt>		: uhci_hcd
<tt>  efe0-efff </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
<tt>    efe0-efff </tt>		: uhci_hcd
-Memory-
<tt>00000000-00000fff </tt>		: reserved
<tt>00001000-0009fbff </tt>		: System RAM
<tt>0009fc00-0009ffff </tt>		: reserved
<tt>000a0000-000bffff </tt>		: PCI Bus 0000:00
<tt>  000a0000-000bffff </tt>		: Video RAM area
<tt>000c0000-000cffff </tt>		: Video ROM
<tt>000d0000-000dffff </tt>		: PCI Bus 0000:00
<tt>000e0000-000eedff </tt>		: reserved
<tt>000eee00-000eefff </tt>		: ACPI Non-volatile Storage
<tt>000ef000-000fffff </tt>		: reserved
<tt>  000f0000-000fffff </tt>		: System ROM
<tt>00100000-5ffbffff </tt>		: System RAM
<tt>  01000000-016f16b5 </tt>		: Kernel code
<tt>  016f16b6-01a9177f </tt>		: Kernel data
<tt>  01b79000-01c3ffff </tt>		: Kernel bss
<tt>5ffc0000-5ffcffff </tt>		: reserved
<tt>  5ffc0000-5ffcffff </tt>		: pnp 00:00
<tt>5ffd0000-5ffdffff </tt>		: ACPI Tables
<tt>5ffe0000-5fffffff </tt>		: reserved
<tt>  5ffe0000-5fffffff </tt>		: pnp 00:00
<tt>80100000-fed9ffff </tt>		: PCI Bus 0000:00
<tt>  80100000-801003ff </tt>		: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
<tt>    80100000-801003ff </tt>		: ehci_hcd
<tt>  80100400-801007ff </tt>		: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>  80100800-801009ff </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
<tt>    80100800-801009ff </tt>		: Intel 82801DB-ICH4
<tt>  80100a00-80100aff </tt>		: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
<tt>    80100a00-80100aff </tt>		: Intel 82801DB-ICH4
<tt>  84000000-8bffffff </tt>		: PCI Bus 0000:02
<tt>    84000000-87ffffff </tt>		: PCI CardBus 0000:03
<tt>    88000000-8bffffff </tt>		: PCI CardBus 0000:05
<tt>  8c000000-8c000fff </tt>		: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
<tt>    8c000000-8c000fff </tt>		: yenta_socket
<tt>  90000000-93ffffff </tt>		: PCI CardBus 0000:03
<tt>  94000000-94000fff </tt>		: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
<tt>    94000000-94000fff </tt>		: yenta_socket
<tt>  98000000-9bffffff </tt>		: PCI CardBus 0000:05
<tt>  d0000000-dfffffff </tt>		: PCI Bus 0000:01
<tt>    d0000000-dfffffff </tt>		: NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1) (prog-if 00 [VGA controller])
<tt>  e0000000-efffffff </tt>		: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
<tt>  fce00000-fcefffff </tt>		: PCI Bus 0000:02
<tt>    fce00000-fce03fff </tt>		: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] (prog-if 10 [OHCI])
<tt>    fce04000-fce047ff </tt>		: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] (prog-if 10 [OHCI])
<tt>      fce04000-fce047ff </tt>		: Driver for PCI OHCI IEEE1394 controllers
<tt>    fce04800-fce049ff </tt>		: Toshiba America Info Systems SD TypA Controller (rev 03)
<tt>      fce04800-fce049ff </tt>		: Toshiba PCI Secure Digital Host Controller Interface driver
<tt>    fcec0000-fcedffff </tt>		: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
<tt>      fcec0000-fcedffff </tt>		: Intel(R) PRO/1000 Network Driver
<tt>    fceff000-fcefffff </tt>		: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
<tt>      fceff000-fcefffff </tt>		: Intel(R) PRO/Wireless 2200/2915 Network Driver
<tt>  fd000000-fdffffff </tt>		: PCI Bus 0000:01
<tt>    fd000000-fdffffff </tt>		: NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1) (prog-if 00 [VGA controller])
<tt>feda0000-fedbffff </tt>		: reserved
<tt>  feda0000-fedbffff </tt>		: pnp 00:00
<tt>fedc0000-ffafffff </tt>		: PCI Bus 0000:00
<tt>ffb00000-ffbfffff </tt>		: reserved
<tt>  ffb00000-ffbfffff </tt>		: pnp 00:00
<tt>ffc00000-ffe7ffff </tt>		: PCI Bus 0000:00
<tt>ffe80000-ffffffff </tt>		: reserved
<tt>  ffe80000-ffffffff </tt>		: pnp 00:00
-DMA-
<tt> 1</tt>		: parport0
<tt> 4</tt>		: cascade

```

---

### Post by &amp;KyT$0P# on 2016-07-02
What if you update everything except Firefox?
(Note that this is only a test.  Outdated Firefox is insecure has publicly known vulnerabilities!)

---

### Post by Impavidus on 2016-07-02
OK, on your mirror the updates for 15.04 may still be present, but in any case they are no longer maintained. No new updates have been added since January. So even if you update, you'll still have outdated software.

I think you use open source drivers for your graphics. For nvidia the proprietary drivers are usually better. That may improve things a bit. You can install them via settings -> extra drivers (or something like that, I'm translating back from my system). But I think you should first get Xubuntu 16.04. Make sure you read the release notes: [http://xubuntu.org/news/xubuntu-16-04-release/](http://xubuntu.org/news/xubuntu-16-04-release/)

---

### Post by faraz_k86 on 2016-07-03
> **Impavidus said:**
> OK, on your mirror the updates for 15.04 may still be present, but in any case they are no longer maintained. No new updates have been added since January. So even if you update, you'll still have outdated software.

I think you use open source drivers for your graphics. For nvidia the proprietary drivers are usually better. That may improve things a bit. You can install them via settings -> extra drivers (or something like that, I'm translating back from my system). But I think you should first get Xubuntu 16.04. Make sure you read the release notes: [http://xubuntu.org/news/xubuntu-16-04-release/](http://xubuntu.org/news/xubuntu-16-04-release/)

Thanks, I tried installing the nVidia legacy drivers for my card. Downloaded the .run file from their website, followed instructions but got an error. Here is the log generated:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jul  3 04:52:07 2016
installer version: 1.0.7

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  OpenGL header files                : true
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.39.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/3.19.0-15-generic/build'
-> Kernel output path: '/lib/modules/3.19.0-15-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/3.19.0-15-gener
   ic/build SYSOUT=/lib/modules/3.19.0-15-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
   echo >&2;							\
   echo >&2 "  ERROR: Kernel configuration is invalid.";		\
   echo >&2 "         include/generated/autoconf.h or include/config/auto.conf 
   are missing.";\
   echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix
   it.";	\
   echo >&2 ;							\
   /bin/false)
   mkdir -p /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f ./scripts/Makefile.build obj=/tmp/selfgz5241/NVIDIA-Linux-x86-173.14
   .39-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.9/include  -I./arch/x8
   6/include -Iarch/x86/include/generated/uapi -Iarch/x86/include/generated  -I
   include -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./incl
   ude/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -Iub
   untu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs 
   -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-
   format-security -std=gnu89 -m32 -msoft-float -mregparm=3 -freg-struct-return
   -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulat
   e-outgoing-args -Wa,-mtune=generic32 -ffreestanding -DCONFIG_AS_CFI=1 -DCONF
   IG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_CRC32=1 -DCO
   NFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -fno-delete-nul
   l-pointer-checks -O2 --param=allow-store-data-races=0 -Wframe-larger-than=10
   24 -fstack-protector -Wno-unused-but-set-variable -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -fno-var-tracking-assignments -pg -Wdeclaration-af
   ter-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -Werro
   r=implicit-int -Werror=strict-prototypes -Werror=date-time -DCC_HAVE_ASM_GOT
   O -I/tmp/selfgz5241/NVIDIA-Linux-x8
   6-173.14.39-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -
   Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VE
   RSION_STRING=\"173.14.39\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)" -c -o /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/.tmp
   _nv.o /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c
   In file included from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:16:0,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/conftest.h:42:2: 
   error: #error acpi_walk_namespace() conftest failed!
    #error acpi_walk_namespace() conftest failed!
     ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/conftest.h:43:2: 
   error: #error acpi_os_wait_events_complete() conftest failed!
    #error acpi_os_wait_events_complete() conftest failed!
     ^
   In file included from include/linux/bitops.h:36:0,
                    from include/linux/kernel.h:10,
                    from include/linux/sched.h:17,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   ./arch/x86/include/asm/bitops.h: In function â&#128;&#152;set_bitâ&#128;&#153;:
   ./arch/x86/include/asm/bitops.h:53:61: warning: pointer of type â&#128;&#152;void *â&#128;&#153;
   used in arithmetic [-Wpointer-arith]
    #define CONST_MASK_ADDR(nr, addr) BITOP_ADDR((void *)(addr) + ((nr)>>3))
                                                                ^
   ./arch/x86/include/asm/bitops.h:43:49: note: in definition of macro â&#128;&#152;BITOP
   _ADDRâ&#128;&#153;
    #define BITOP_ADDR(x) "+m" (*(volatile long *) (x))
                                                    ^
   ./arch/x86/include/asm/bitops.h:76:6: note: in expansion of macro â&#128;&#152;CONST_M
   ASK_ADDRâ&#128;&#153;
       : CONST_MASK_ADDR(nr, addr)
         ^
   ./arch/x86/include/asm/bitops.h: In function â&#128;&#152;clear_bitâ&#128;&#153;:
   ./arch/x86/include/asm/bitops.h:53:61: warning: pointer of type â&#128;&#152;void *â&#128;&#153;
   used in arithmetic [-Wpointer-arith]
    #define CONST_MASK_ADDR(nr, addr) BITOP_ADDR((void *)(addr) + ((nr)>>3))
                                                                ^
   ./arch/x86/include/asm/bitops.h:43:49: note: in definition of macro â&#128;&#152;BITOP
   _ADDRâ&#128;&#153;
    #define BITOP_ADDR(x) "+m" (*(volatile long *) (x))
                                                    ^
   ./arch/x86/include/asm/bitops.h:114:6: note: in expansion of macro â&#128;&#152;CONST_
   MASK_ADDRâ&#128;&#153;
       : CONST_MASK_ADDR(nr, addr)
         ^
   ./arch/x86/include/asm/bitops.h: In function â&#128;&#152;change_bitâ&#128;&#153;:
   ./arch/x86/include/asm/bitops.h:53:61: warning: pointer of type â&#128;&#152;void *â&#128;&#153;
   used in arithmetic [-Wpointer-arith]
    #define CONST_MASK_ADDR(nr, addr) BITOP_ADDR((void *)(addr) + ((nr)>>3))
                                                                ^
   ./arch/x86/include/asm/bitops.h:43:49: note: in definition of macro â&#128;&#152;BITOP
   _ADDRâ&#128;&#153;
    #define BITOP_ADDR(x) "+m" (*(volatile long *) (x))
                                                    ^
   ./arch/x86/include/asm/bitops.h:187:6: note: in expansion of macro â&#128;&#152;CONST_
   MASK_ADDRâ&#128;&#153;
       : CONST_MASK_ADDR(nr, addr)
         ^
   In file included from include/linux/list.h:6:0,
                    from include/linux/preempt.h:10,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:35,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:19,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/linux/list.h: In function â&#128;&#152;list_delâ&#128;&#153;:
   include/linux/poison.h:22:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON1  ((void *) 0x00100100 + POISON_POINTER_DELTA)
                                               ^
   include/linux/list.h:108:16: note: in expansion of macro â&#128;&#152;LIST_POISON1â&#128;&#153;
     entry->next = LIST_POISON1;
                   ^
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/list.h:109:16: note: in expansion of macro â&#128;&#152;LIST_POISON2â&#128;&#153;
     entry->prev = LIST_POISON2;
                   ^
   include/linux/list.h: In function â&#128;&#152;hlist_delâ&#128;&#153;:
   include/linux/poison.h:22:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON1  ((void *) 0x00100100 + POISON_POINTER_DELTA)
                                               ^
   include/linux/list.h:626:12: note: in expansion of macro â&#128;&#152;LIST_POISON1â&#128;&#153;
     n->next = LIST_POISON1;
               ^
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/list.h:627:13: note: in expansion of macro â&#128;&#152;LIST_POISON2â&#128;&#153;
     n->pprev = LIST_POISON2;
                ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from ./include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/asm-generic/qrwlock.h: In function â&#128;&#152;queue_write_trylockâ&#128;&#153;:
   include/asm-generic/qrwlock.h:93:35: warning: comparison between signed and 
   unsigned integer expressions [-Wsign-compare]
             cnts, cnts | _QW_LOCKED) == cnts);
                                      ^
   include/linux/compiler.h:159:40: note: in definition of macro â&#128;&#152;likelyâ&#128;&#153;
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
   In file included from include/linux/list.h:6:0,
                    from include/linux/preempt.h:10,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:35,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:19,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/linux/rculist.h: In function â&#128;&#152;list_del_rcuâ&#128;&#153;:
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/rculist.h:132:16: note: in expansion of macro â&#128;&#152;LIST_POISON2â
   &#128;&#153;
     entry->prev = LIST_POISON2;
                   ^
   include/linux/rculist.h: In function â&#128;&#152;list_replace_rcuâ&#128;&#153;:
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/rculist.h:178:14: note: in expansion of macro â&#128;&#152;LIST_POISON2â
   &#128;&#153;
     old->prev = LIST_POISON2;
                 ^
   include/linux/rculist.h: In function â&#128;&#152;hlist_del_rcuâ&#128;&#153;:
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/rculist.h:346:13: note: in expansion of macro â&#128;&#152;LIST_POISON2â
   &#128;&#153;
     n->pprev = LIST_POISON2;
                ^
   include/linux/rculist.h: In function â&#128;&#152;hlist_replace_rcuâ&#128;&#153;:
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/rculist.h:366:15: note: in expansion of macro â&#128;&#152;LIST_POISON2â
   &#128;&#153;
     old->pprev = LIST_POISON2;
                  ^
   In file included from include/linux/utsname.h:5:0,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/linux/sched.h: In function â&#128;&#152;object_is_on_stackâ&#128;&#153;:
   include/linux/sched.h:2709:41: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in
   arithmetic [-Wpointer-arith]
     return (obj >= stack) && (obj < (stack + THREAD_SIZE));
                                            ^
   In file included from include/linux/list.h:6:0,
                    from include/linux/preempt.h:10,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:35,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:19,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/linux/list_bl.h: In function â&#128;&#152;hlist_bl_delâ&#128;&#153;:
   include/linux/poison.h:22:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON1  ((void *) 0x00100100 + POISON_POINTER_DELTA)
                                               ^
   include/linux/list_bl.h:106:12: note: in expansion of macro â&#128;&#152;LIST_POISON1â
   &#128;&#153;
     n->next = LIST_POISON1;
               ^
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/list_bl.h:107:13: note: in expansion of macro â&#128;&#152;LIST_POISON2â
   &#128;&#153;
     n->pprev = LIST_POISON2;
                ^
   include/linux/rculist_bl.h: In function â&#128;&#152;hlist_bl_del_rcuâ&#128;&#153;:
   include/linux/poison.h:23:44: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in 
   arithmetic [-Wpointer-arith]
    #define LIST_POISON2  ((void *) 0x00200200 + POISON_POINTER_DELTA)
                                               ^
   include/linux/rculist_bl.h:76:13: note: in expansion of macro â&#128;&#152;LIST_POISON
   2â&#128;&#153;
     n->pprev = LIST_POISON2;
                ^
   In file included from include/uapi/linux/stddef.h:1:0,
                    from include/linux/stddef.h:4,
                    from ./include/uapi/linux/posix_types.h:4,
                    from include/uapi/linux/types.h:13,
                    from include/linux/types.h:5,
                    from include/uapi/linux/capability.h:16,
                    from include/linux/capability.h:15,
                    from include/linux/sched.h:15,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   ./arch/x86/include/asm/uaccess.h: In function â&#128;&#152;copy_from_userâ&#128;&#153;:
   ./arch/x86/include/asm/uaccess.h:712:26: warning: comparison between signed 
   and unsigned integer expressions [-Wsign-compare]
     if (likely(sz < 0 || sz >= n))
                             ^
   include/linux/compiler.h:159:40: note: in definition of macro â&#128;&#152;likelyâ&#128;&#153;
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
   ./arch/x86/include/asm/uaccess.h: In function â&#128;&#152;copy_to_userâ&#128;&#153;:
   ./arch/x86/include/asm/uaccess.h:730:26: warning: comparison between signed 
   and unsigned integer expressions [-Wsign-compare]
     if (likely(sz < 0 || sz >= n))
                             ^
   include/linux/compiler.h:159:40: note: in definition of macro â&#128;&#152;likelyâ&#128;&#153;
    # define likely(x) __builtin_expect(!!(x), 1)
                                           ^
   In file included from include/linux/dma-mapping.h:9:0,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from ./arch/x86/include/asm/pci.h:121,
                    from include/linux/pci.h:1450,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:102,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/linux/scatterlist.h: In function â&#128;&#152;sg_virtâ&#128;&#153;:
   include/linux/scatterlist.h:220:35: warning: pointer of type â&#128;&#152;void *â&#128;&#153; us
   ed in arithmetic [-Wpointer-arith]
     return page_address(sg_page(sg)) + sg->offset;
                                      ^
   In file included from ./arch/x86/include/asm/dma-mapping.h:44:0,
                    from include/linux/dma-mapping.h:82,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from ./arch/x86/include/asm/pci.h:121,
                    from include/linux/pci.h:1450,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:102,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/asm-generic/dma-mapping-common.h: In function â&#128;&#152;dma_map_pageâ&#128;&#153;:
   include/asm-generic/dma-mapping-common.h:78:48: warning: pointer of type â&#128;&#152;
   void *â&#128;&#153; used in arithmetic [-Wpointer-arith]
     kmemcheck_mark_initialized(page_address(page) + offset, size);
                                                   ^
   In file included from ./arch/x86/include/asm/hardirq.h:5:0,
                    from include/linux/hardirq.h:8,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:103,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/linux/irq.h: In function â&#128;&#152;irq_reg_writelâ&#128;&#153;:
   include/linux/irq.h:851:36: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in ar
   ithmetic [-Wpointer-arith]
      gc->reg_writel(val, gc->reg_base + reg_offset);
                                       ^
   include/linux/irq.h:853:28: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in ar
   ithmetic [-Wpointer-arith]
      writel(val, gc->reg_base + reg_offset);
                               ^
   include/linux/irq.h: In function â&#128;&#152;irq_reg_readlâ&#128;&#153;:
   include/linux/irq.h:860:37: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in ar
   ithmetic [-Wpointer-arith]
      return gc->reg_readl(gc->reg_base + reg_offset);
                                        ^
   include/linux/irq.h:862:29: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in ar
   ithmetic [-Wpointer-arith]
      return readl(gc->reg_base + reg_offset);
                                ^
   In file included from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:0:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv-linux.h: At to
   p level:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv-linux.h:126:2:
   error: #error "struct file_operations compile test likely failed!"
    #error "struct file_operations compile test likely failed!"
     ^
   In file included from include/linux/vgaarb.h:34:0,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:130,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/video/vga.h: In function â&#128;&#152;vga_mm_râ&#128;&#153;:
   include/video/vga.h:220:24: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in ar
   ithmetic [-Wpointer-arith]
     return readb (regbase + port);
                           ^
   include/video/vga.h: In function â&#128;&#152;vga_mm_wâ&#128;&#153;:
   include/video/vga.h:225:23: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in ar
   ithmetic [-Wpointer-arith]
     writeb (val, regbase + port);
                          ^
   include/video/vga.h: In function â&#128;&#152;vga_mm_w_fastâ&#128;&#153;:
   include/video/vga.h:231:43: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used in ar
   ithmetic [-Wpointer-arith]
     writew (VGA_OUT16VAL (val, reg), regbase + port);
                                              ^
   In file included from ./arch/x86/include/asm/string.h:2:0,
                    from include/linux/string.h:17,
                    from ./arch/x86/include/asm/page_32.h:34,
                    from ./arch/x86/include/asm/page.h:13,
                    from ./arch/x86/include/asm/thread_info.h:11,
                    from include/linux/thread_info.h:54,
                    from ./arch/x86/include/asm/preempt.h:6,
                    from include/linux/preempt.h:18,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:35,
                    from include/linux/time.h:5,
                    from include/uapi/linux/timex.h:56,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:19,
                    from include/linux/utsname.h:5,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/linux/highmem.h: In function â&#128;&#152;zero_user_segmentsâ&#128;&#153;:
   include/linux/highmem.h:201:16: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used i
   n arithmetic [-Wpointer-arith]
      memset(kaddr + start1, 0, end1 - start1);
                   ^
   ./arch/x86/include/asm/string_32.h:325:46: note: in definition of macro â&#128;&#152;m
   emsetâ&#128;&#153;
    #define memset(s, c, count) __builtin_memset(s, c, count)
                                                 ^
   include/linux/highmem.h:204:16: warning: pointer of type â&#128;&#152;void *â&#128;&#153; used i
   n arithmetic [-Wpointer-arith]
      memset(kaddr + start2, 0, end2 - start2);
                   ^
   ./arch/x86/include/asm/string_32.h:325:46: note: in definition of macro â&#128;&#152;m
   emsetâ&#128;&#153;
    #define memset(s, c, count) __builtin_memset(s, c, count)
                                                 ^
   In file included from include/acpi/platform/acenv.h:172:0,
                    from include/acpi/acpi.h:56,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:209,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/acpi/platform/aclinux.h: At top level:
   include/acpi/platform/aclinux.h:52:2: error: #error "Please don't include <a
   cpi/acpi.h> directly, include <linux/acpi.h> instead."
    #error "Please don't include <acpi/acpi.h> directly, include <linux/acpi.h>
   instead."
     ^
   In file included from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv-linux.h:210:0,
                    from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:
   include/acpi/acpi_drivers.h:98:43: warning: â&#128;&#152;struct acpi_pci_rootâ&#128;&#153; decla
   red inside parameter list
    struct pci_bus *pci_acpi_scan_root(struct acpi_pci_root *root);
                                              ^
   include/acpi/acpi_drivers.h:98:43: warning: its scope is only this definitio
   n or declaration, which is probably not what you want
   In file included from /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv/nv.c:13:0:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv-linux.h:217:4:
   warning: "NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT" is not defined [-Wundef]
      (NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT == 6)
       ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv-linux.h:219:8:
   warning: "NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT" is not defined [-Wundef]
    #elif (NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT == 7)
           ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv-linux.h:225:2:
   error: #error "NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT value unrecognized!"
    #error "NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT value unrecognized!"
     ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv-linux.h:230:4:
   warning: "NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT" is not defined [-W
   undef]
      (NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT == 1)
       ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv-linux.h:233:8:
   warning: "NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT" is not defined [-W
   undef]
    #elif (NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT == 0)
           ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c: In function
   â&#128;&#152;nv_kern_ioctlâ&#128;&#153;:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c:2646:26: war
   ning: comparison between signed and unsigned integer expressions [-Wsign-com
   pare]
                if (arg_size < (sizeof(*ci) * num_nv_devices))
                             ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c: In function
   â&#128;&#152;nv_kern_unlocked_ioctlâ&#128;&#153;:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c:2749:30: err
   or: â&#128;&#152;struct fileâ&#128;&#153; has no member named â&#128;&#152;f_dentryâ&#128;&#153;
        return nv_kern_ioctl(file->f_dentry->d_inode, file, cmd, i_arg);
                                 ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c: In function
   â&#128;&#152;nv_kern_compat_ioctlâ&#128;&#153;:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c:2758:30: err
   or: â&#128;&#152;struct fileâ&#128;&#153; has no member named â&#128;&#152;f_dentryâ&#128;&#153;
        return nv_kern_ioctl(file->f_dentry->d_inode, file, cmd, i_arg);
                                 ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c: In function
   â&#128;&#152;nv_kern_unlocked_ioctlâ&#128;&#153;:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c:2750:1: warn
   ing: control reaches end of non-void function [-Wreturn-type]
    }
    ^
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c: In function
   â&#128;&#152;nv_kern_compat_ioctlâ&#128;&#153;:
   /tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.c:2759:1: warn
   ing: control reaches end of non-void function [-Wreturn-type]
    }
    ^
   scripts/Makefile.build:257: recipe for target '/tmp/selfgz5241/NVIDIA-Linux-
   x86-173.14.39-pkg1/usr/src/nv/nv.o' failed
   make[3]: *** [/tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/src/nv/nv.
   o] Error 1
   Makefile:1394: recipe for target '_module_/tmp/selfgz5241/NVIDIA-Linux-x86-1
   73.14.39-pkg1/usr/src/nv' failed
   make[2]: *** [_module_/tmp/selfgz5241/NVIDIA-Linux-x86-173.14.39-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   Makefile:239: recipe for target 'module' failed
   make[1]: *** [module] Error 1
   makefile:54: recipe for target 'module' failed
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by faraz_k86 on 2016-07-03
> **halogen2 said:**
> What if you update everything except Firefox?
(Note that this is only a test.  Outdated Firefox is insecure has publicly known vulnerabilities!)

I did not want to risk another reinstall of the entire system. So I downloaded the 16.04 LTS Ubuntu and ran youtube from the LiveCD.

Got the same problem, the playback was jittery and very laggy. So I'm definitely not touching any updates

---

### Post by mörgæs on 2016-07-03
We are dealing with a weak graphics processor so best is to install the lightest operative system possible. Ubuntu itself is heavy, and it does not surprise me that the system is slow.

I suggest that you begin with a fresh install of a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Command_Line_Install:_12.04_and_later") 16.04 followed by all updates.  After that please open Software & Updates and click the Additional Drivers tab. Are there any drivers listed here?

---

### Post by Impavidus on 2016-07-03
As I wrote in post #2, use Xubuntu or even better Lubuntu 16.04. Ubuntu is not going to work. Keep in mind that a live disk is always a bit more laggy than the installed system. You can only install the proprietary drivers on an installed system. Try installing them with "additional drivers", not from source code, which is the hard way.

So I agree with mörgæs.

---

### Post by faraz_k86 on 2016-07-03
> **mörgæs said:**
> We are dealing with a weak graphics processor so best is to install the lightest operative system possible. Ubuntu itself is heavy, and it does not surprise me that the system is slow.

I suggest that you begin with a fresh install of a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Command_Line_Install:_12.04_and_later") 16.04 followed by all updates.  After that please open Software & Updates and click the Additional Drivers tab. Are there any drivers listed here?

Hi. I have tried Lubuntu on this as well and the same problem exists. After the minimal install and after running updates youtube becomes laggy and jittery. Any online video becomes unwatchable. The system in itself is very fast and responsive everywhere else, file system, word processing etc, but with youtube no. I have even tried Ubuntu mate 32 bit (which they state is for slow processors).

But the problem is with updates not the distro as even now I am using Xubuntu 15.04 without the updates and the system is working perfectly, browsing is fast and streaming videos is smooth, but as soon as I run the updates, online streaming and youtube becomes unwatchable. 

There is nothing in additional drivers related to the graphics card, just something unknown. I have attached the screenshot.

[ATTACH=CONFIG]269922[/ATTACH]

---

### Post by &amp;KyT$0P# on 2016-07-03
> **faraz_k86 said:**
> I did not want to risk another reinstall of the entire system. 
Even in a live CD environment you can test upgrading anything that doesn't require a restart, which is pretty much everything except the kernel.

By not only not updating anything but also using an outdated version of Ubuntu, you are leaving your entire OS with many security holes and vulnerabilities, some publicly known.  Linux is not immune to malware.

---

### Post by faraz_k86 on 2016-07-03
> **halogen2 said:**
> Even in a live CD environment you can test upgrading anything that doesn't require a restart, which is pretty much everything except the kernel.

By not only not updating anything but also using an outdated version of Ubuntu, you are leaving your entire OS with many security holes and vulnerabilities, some publicly known.  Linux is not immune to malware.

agreed. I just installed ubuntu mate 16.04. Granted its not as fast as xubuntu 15.04 but ill manage

---

### Post by mörgæs on 2016-07-04
Is it slow in all browsers?

---

### Post by faraz_k86 on 2016-07-04
> **mörgæs said:**
> Is it slow in all browsers?

No, its actually performing really well. Dont know why. Maybe Ubuntu Mate installed the proper driver for my graphics.

I still havent run any updates though. Its just a fresh install of 16.04

---

### Post by mörgæs on 2016-07-04
Then you are at risk of an attack. It's OK for just watching Youtube but don't enter your password or other personal information into a system which has not been updated for several months.

---

### Post by faraz_k86 on 2016-07-04
> **mörgæs said:**
> Then you are at risk of an attack. It's OK for just watching Youtube but don't enter your password or other personal information into a system which has not been updated for several months.

Since I already went ahead and installed 16.04, I'll go ahead with the other updates as well while my installation is fresh. Worst case would be me reinstalling a fresh install anyway.

I'm sure this has something to do with my graphics. Is there a way to find out if I am using the correct driver. 

In hardInfo the card is being identified correctly but then again its not the legacy driver by nVidia (at least it wasnt in Xubuntu) but maybe Ubuntu Mate installed the correct driver as during installation I was asked if I want to install proprietary drivers.

How do I find out if it is the correct driver from nVidia.?

Thanks

---

### Post by &amp;KyT$0P# on 2016-07-04
Look at "Additional Drivers" section of "Software & Updates" settings.  It will list all hardware that can use proprietary drivers and tell you what drivers you're currently using, as well as offer the options of any other drivers that can be used.

---

