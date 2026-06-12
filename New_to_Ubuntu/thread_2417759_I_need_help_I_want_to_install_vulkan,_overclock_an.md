---
title: "I need help I want to install vulkan, overclock and fan control"
date: 2019-04-26
forum: New to Ubuntu
---

### Post by adolfo00 on 2019-04-26
Hi people
I have an ASUS GL702zc with the following specifications

I want to render and play games at high performance with vulkan, but i  cant do it. I installed the driver from amd(the official site), but  looks like that other driver still working even following the  instructions. i afraid that the same occurs with vulkan, but in this  case with opengl/cl and i cant control the fans, i have installed a lot  of programs for this like, lm-sensors, xrander and fancontrol, nothing  works. i want to do overclocking because i think that the freeworld can  do the things better than the private world, vulkan is the reason. Im  waiting for your help


Computer
********


Summary
-------

-```
Computer-
Processor		: AMD Ryzen 5 1600 Six-Core Processor
Memory		: 16424MB (2579MB used)
Machine Type		: Notebook
Operating System		: Linux Mint 19.1 Tessa
User Name		: root (root)
Date/Time		: Fri 26 Apr 2019 08:36:43 PM -04
-Display-
Resolution		: 1920x1080 pixels
OpenGL Renderer		: Radeon RX 580 Series
X11 Vendor		: The X.Org Foundation
-Audio Devices-
Audio Adapter		: HDA-Intel - HDA ATI HDMI
Audio Adapter		: HDA-Intel - HD-Audio Generic
-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Power Button
 Video Bus
 COMPANY USB Device
 COMPANY USB Device
 COMPANY USB Device
 Asus Keyboard
 Asus Keyboard
 Asus Keyboard
 Asus Wireless Radio Control
 ELAN1200:00 04F3:3066 Touchpad
 HDA ATI HDMI HDMI/DP,pcm:3
 HDA ATI HDMI HDMI/DP,pcm:7
 USB2.0 HD UVC WebCam: USB2.0 HD
 Asus WMI hotkeys
 HD-Audio Generic Headphone
 Razer USB Dongle for Razer Lancehead
 Razer USB Dongle for Razer Lancehead
 Razer USB Dongle for Razer Lancehead
-Printers-
No printers found

Operating System
----------------

-Version-
Kernel		: Linux 4.15.0-48-generic (x86_64)
Version		: #51-Ubuntu SMP Wed Apr 3 08:28:49 UTC 2019
C Library		: GNU C Library / (Ubuntu GLIBC 2.27-3ubuntu1) 2.27
Distribution		: Linux Mint 19.1 Tessa
-Current Session-
Computer Name		: killtropc
User Name		: root (root)
Language		:  LC_CTYPE=en_US.UTF-8;LC_NUMERIC=es_CL.UTF-8;LC_TIME=en_US.UTF-8;LC_COLLATE=en_US.UTF-8;LC_MONETARY=es_CL.UTF-8;LC_MESSAGES=en_US.UTF-8;LC_PAPER=es_CL.UTF-8;LC_NAME=es_CL.UTF-8;LC_ADDRESS=es_CL.UTF-8;LC_TELEPHONE=es_CL.UTF-8;LC_MEASUREMENT=es_CL.UTF-8;LC_IDENTIFICATION=es_CL.UTF-8  (en_US)
Home Directory		: /root
-Misc-
Uptime		: 1 hour 43 minutes
Load Average		: 0,89, 1,42, 1,42
Available entropy in /dev/random		: 3892 bits (healthy)

Kernel Modules
--------------

-Loaded Modules-
ccm		: Counter with CBC MAC
bnep		: Bluetooth BNEP ver 1.3
amdgpu		: AMD GPU
amdchash		: Closed hash table
amdttm		: TTM memory manager subsystem (for DRM device)
edac_mce_amd		: AMD MCE decoder
amd_sched		: DRM GPU scheduler
asus_nb_wmi		: Asus Notebooks WMI Hotkey Driver
asus_wmi		: Asus Generic WMI Driver
wmi_bmof		: WMI embedded Binary MOF driver
sparse_keymap		: Generic support for sparse keymaps
arc4		: ARC4 Cipher Algorithm
kvm_amd
kvm
irqbypass		: IRQ bypass manager utility module
r8822be		: Realtek 802.11n PCI wireless core
crct10dif_pclmul		: T10 DIF CRC calculation accelerated with PCLMULQDQ.
snd_usb_audio		: USB Audio
snd_hda_codec_realtek		: Realtek HD-audio codec
crc32_pclmul
snd_hda_codec_generic		: Generic HD-audio codec parser
btusb		: Generic Bluetooth USB driver ver 0.8
ghash_clmulni_intel		: GHASH Message Digest Algorithm, acclerated by PCLMULQDQ-NI
amdkcl		: Module for OS kernel compatible layer
pcbc		: PCBC block cipher algorithm
snd_hda_codec_hdmi		: HDMI HD-audio codec
btrtl		: Bluetooth support for Realtek devices ver 0.1
amd_iommu_v2
snd_usbmidi_lib		: USB Audio/MIDI helper module
uvcvideo		: USB Video Class driver
btbcm		: Bluetooth support for Broadcom devices ver 0.1
snd_hda_intel		: Intel HDA driver
btintel		: Bluetooth support for Intel devices ver 0.1
snd_seq_midi		: Advanced Linux Sound Architecture sequencer MIDI synth.
drm_kms_helper		: DRM KMS helper
mac80211		: IEEE 802.11 subsystem
videobuf2_vmalloc		: vmalloc memory handling routines for videobuf2
snd_hda_codec		: HDA codec core
snd_seq_midi_event		: MIDI byte &lt;-&gt; sequencer event coder
videobuf2_memops		: common memory handling routines for videobuf2
snd_hda_core		: HD-audio bus
videobuf2_v4l2		: Driver helper framework for Video for Linux 2
drm		: DRM shared core routines
videobuf2_core		: Media buffer core framework
snd_rawmidi		: Midlevel RawMidi code for ALSA.
snd_hwdep		: Hardware dependent layer
aesni_intel		: Rijndael (AES) Cipher Algorithm, Intel AES-NI instructions optimized
i2c_algo_bit		: I2C-Bus bit-banging algorithm
bluetooth		: Bluetooth Core ver 2.22
snd_seq		: Advanced Linux Sound Architecture sequencer.
aes_x86_64		: Rijndael (AES) Cipher Algorithm, asm optimized
input_leds		: Input -&gt; LEDs Bridge
joydev		: Joystick device interfaces
videodev		: Device registrar for Video4Linux drivers v2
crypto_simd
glue_helper
nls_iso8859_1
snd_pcm		: Midlevel PCM code for ALSA.
media		: Device node registration for media drivers
snd_seq_device		: ALSA sequencer device management
ecdh_generic		: ECDH generic algorithm
cryptd		: Software async crypto daemon
hid_multitouch		: HID multitouch panels
cfg80211		: wireless configuration support
k10temp		: AMD Family 10h+ CPU core temperature monitor
fb_sys_fops		: Generic file read (fb in system RAM)
snd_timer		: ALSA timer interface
syscopyarea		: Generic copyarea (sys-to-sys)
sysfillrect		: Generic fill rectangle (sys-to-sys)
ccp		: AMD Secure Processor driver
snd		: Advanced Linux Sound Architecture driver for soundcards.
sysimgblt		: 1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)
soundcore		: Core sound module
shpchp		: Standard Hot Plug PCI Controller Driver
wmi		: ACPI-WMI Mapping Driver
asus_wireless		: Asus Wireless Radio Control Driver
mac_hid
sch_fq_codel
parport_pc		: PC-style parallel port driver
ppdev
lp
parport
ip_tables		: IPv4 packet filter
x_tables		: {ip,ip6,arp,eb}_tables backend module
autofs4
btrfs
xor
zstd_compress		: Zstd Compressor
raid6_pq		: RAID6 Q-syndrome calculations
dm_mirror		: device-mapper mirror target
dm_region_hash		: device-mapper region hash
dm_log		: device-mapper dirty region log
hid_asus		: Asus HID Keyboard and TouchPad
hid_generic		: HID generic driver
i2c_piix4		: PIIX4 SMBus driver
usbhid		: USB HID core driver
r8169		: RealTek RTL-8169 Gigabit Ethernet driver
ahci		: AHCI SATA low-level driver
nvme
mii		: MII hardware support library
libahci		: Common AHCI SATA low-level routines
nvme_core
video		: ACPI Video Driver
i2c_hid		: HID over I2C core driver
gpio_amdpt		: AMD Promontory GPIO Driver
hid
gpio_generic		: Driver for basic memory-mapped GPIO controllers

Boots
-----

-Boots-
Fri Apr 26 18:53		: 4.15.0-48-generi
Fri Apr 26 14:59		: 4.15.0-48-generi
Fri Apr 26 09:47		: 4.15.0-48-generi
Fri Apr 26 02:58		: 4.15.0-48-generi
Thu Apr 25 23:56		: 4.15.0-48-generi
Thu Apr 25 23:41		: 4.15.0-48-generi
Thu Apr 25 20:45		: 4.15.0-48-generi
Thu Apr 25 20:11		: 4.15.0-20-generi

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
en_IL		: English locale for Israel
en_IL.utf8		: English locale for Israel
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
es_CL.utf8		: Spanish locale for Chile
C.UTF-8		: C locale

Filesystems
-----------

-Mounted File Systems-
udev	/dev	0,00 % (7,8 GiB of 7,8 GiB)	
tmpfs	/run	0,11 % (1,6 GiB of 1,6 GiB)	
/dev/nvme0n1p2	/	29,89 % (159,7 GiB of 227,7 GiB)	
tmpfs	/dev/shm	2,50 % (7,6 GiB of 7,8 GiB)	
tmpfs	/run/lock	0,08 % (5,0 MiB of 5,0 MiB)	
tmpfs	/sys/fs/cgroup	0,00 % (7,8 GiB of 7,8 GiB)	
/dev/nvme0n1p1	/boot/efi	1,19 % (504,9 MiB of 511,0 MiB)	
tmpfs	/run/user/1000	0,00 % (1,6 GiB of 1,6 GiB)	
tmpfs	/run/user/0	0,00 % (1,6 GiB of 1,6 GiB)	

Display
-------

-Display-
Resolution		: 1920x1080 pixels
Vendor		: The X.Org Foundation
Version		: 1.19.6
Current Display Name		: :0
-Monitors-
Monitor 0		: 1920x1080 pixels
-OpenGL-
Vendor		: Advanced Micro Devices, Inc.
Renderer		: Radeon RX 580 Series
Version		: 4.6.13556 Compatibility Profile Context 19.10.9.418
Direct Rendering		: Yes
-Extensions-
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
DRI3
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
default screen number:    0

Environment Variables
---------------------

-Environment Variables-
LS_COLORS		:  rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
LC_MEASUREMENT		: es_CL.UTF-8
LESSCLOSE		: /usr/bin/lesspipe %s %s
LC_PAPER		: es_CL.UTF-8
LC_MONETARY		: es_CL.UTF-8
LANG		: en_US.UTF-8
SUDO_GID		: 1000
DISPLAY		: :0
COLORTERM		: truecolor
USERNAME		: root
SUDO_COMMAND		: /bin/su
LC_NAME		: es_CL.UTF-8
XDG_SESSION_ID		: c2
USER		: root
PWD		: /home/killtro
HOME		: /root
SUDO_USER		: killtro
LC_ADDRESS		: es_CL.UTF-8
LC_NUMERIC		: es_CL.UTF-8
SUDO_UID		: 1000
MAIL		: /var/mail/root
SHELL		: /bin/bash
TERM		: xterm-256color
SHLVL		: 1
LANGUAGE		: en_US
LC_TELEPHONE		: es_CL.UTF-8
LOGNAME		: root
DBUS_SESSION_BUS_ADDRESS		: unix:path=/run/user/0/bus
XDG_RUNTIME_DIR		: /run/user/0
XAUTHORITY		: /home/killtro/.Xauthority
PATH		: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
LC_IDENTIFICATION		: es_CL.UTF-8
LESSOPEN		: | /usr/bin/lesspipe %s
_		: /usr/bin/hardinfo

Development
-----------

-Scripting Languages-
Gambas3 (gbr3)		: Not found
Python		: 2.7.15
Python2		: 2.7.15
Python3		: 3.6.7
Perl		: 5.26.1
Perl6 (VM)		: Not found
Perl6		: Not found
PHP		: Not found
Ruby		: Not found
Bash		: 4.4.19(1)-release
-Compilers-
C (GCC)		: 7.3.0
C (Clang)		: Not found
D (dmd)		: Not found
Gambas3 (gbc3)		: Not found
Java		: Not found
CSharp (Mono, old)		: Not found
CSharp (Mono)		: Not found
Vala		: Not found
Haskell (GHC)		: Not found
FreePascal		: Not found
Go		: Not found
-Tools-
make		: 4.1
GDB		: (Ubuntu 8.1-0ubuntu3) 8.1.0.20180409-git
strace		: Not found
valgrind		: Not found
QMake		: Not found
CMake		: Not found
Gambas3 IDE		: Not found

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
systemd-network		: systemd Network Management
systemd-resolve		: systemd Resolver
syslog
messagebus
_apt
uuidd
cups-pk-helper		: user for cups-pk-helper service
kernoops		: Kernel Oops Tracking Daemon
rtkit		: RealtimeKit
avahi-autoipd		: Avahi autoip daemon
usbmux		: usbmux daemon
lightdm		: Light Display Manager
dnsmasq		: dnsmasq
saned
nm-openvpn		: NetworkManager OpenVPN
avahi		: Avahi mDNS daemon
colord		: colord colour management daemon
speech-dispatcher		: Speech Dispatcher
pulse		: PulseAudio daemon
hplip		: HPLIP system user
geoclue
killtro		: killtro
nvidia-persistenced		: NVIDIA Persistence Daemon

Groups
------

-Group-
root		: 0
daemon		: 1
bin		: 2
sys		: 3
adm		: 4
tty		: 5
disk		: 6
lp		: 7
mail		: 8
news		: 9
uucp		: 10
man		: 12
proxy		: 13
kmem		: 15
dialout		: 20
fax		: 21
voice		: 22
cdrom		: 24
floppy		: 25
tape		: 26
sudo		: 27
audio		: 29
dip		: 30
www-data		: 33
backup		: 34
operator		: 37
list		: 38
irc		: 39
src		: 40
gnats		: 41
shadow		: 42
utmp		: 43
video		: 44
sasl		: 45
plugdev		: 46
staff		: 50
games		: 60
users		: 100
nogroup		: 65534
systemd-journal		: 101
systemd-network		: 102
systemd-resolve		: 103
input		: 104
crontab		: 105
syslog		: 106
messagebus		: 107
netdev		: 108
mlocate		: 109
ssl-cert		: 110
uuidd		: 111
lpadmin		: 112
rtkit		: 113
avahi-autoipd		: 114
ssh		: 115
bluetooth		: 116
lightdm		: 117
nopasswdlogin		: 118
scanner		: 119
saned		: 120
nm-openvpn		: 121
avahi		: 122
colord		: 123
pulse		: 124
pulse-access		: 125
geoclue		: 126
killtro		: 1000
sambashare		: 127
nvidia-persistenced		: 128

Devices
*******


Processor
---------

-Processors-
Package Information	
AMD Ryzen 5 1600 Six-Core Processor	0	0:0	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	1	0:0	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	2	0:1	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	3	0:1	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	4	0:2	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	5	0:2	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	6	0:4	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	7	0:4	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	8	0:5	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	9	0:5	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	10	0:6	3200,00 MHz	
AMD Ryzen 5 1600 Six-Core Processor	11	0:6	3200,00 MHz	

Memory
------

-Memory-
MemTotal	Total Memory	16424564 KiB	
MemFree	Free Memory	11580576 KiB	
MemAvailable		13499432 KiB	
Buffers		69396 KiB	
Cached		2322644 KiB	
SwapCached	Cached Swap	0 KiB	
Active		2394960 KiB	
Inactive		1931528 KiB	
Active(anon)		1936740 KiB	
Inactive(anon)		278536 KiB	
Active(file)		458220 KiB	
Inactive(file)		1652992 KiB	
Unevictable		16 KiB	
Mlocked		16 KiB	
SwapTotal	Virtual Memory	2097148 KiB	
SwapFree	Free Virtual Memory	2097148 KiB	
Dirty		36464 KiB	
Writeback		0 KiB	
AnonPages		1935088 KiB	
Mapped		590780 KiB	
Shmem		280160 KiB	
Slab		239412 KiB	
SReclaimable		118564 KiB	
SUnreclaim		120848 KiB	
KernelStack		14976 KiB	
PageTables		55668 KiB	
NFS_Unstable		0 KiB	
Bounce		0 KiB	
WritebackTmp		0 KiB	
CommitLimit		10309428 KiB	
Committed_AS		9282204 KiB	
VmallocTotal		-1 KiB	
VmallocUsed		0 KiB	
VmallocChunk		0 KiB	
HardwareCorrupted		0 KiB	
AnonHugePages		0 KiB	
ShmemHugePages		0 KiB	
ShmemPmdMapped		0 KiB	
CmaTotal		0 KiB	
CmaFree		0 KiB	
HugePages_Total		0	
HugePages_Free		0	
HugePages_Rsvd		0	
HugePages_Surp		0	
Hugepagesize		2048 KiB	
DirectMap4k		328284 KiB	
DirectMap2M		9043968 KiB	
DirectMap1G		8388608 KiB	

PCI Devices
-----------

-PCI Devices-
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Root Complex
IOMMU		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) I/O Memory Management Unit
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge (prog-if 00 [Normal decode])
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge (prog-if 00 [Normal decode])
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models  00h-0fh) Internal PCIe GPP Bridge 0 to Bus B (prog-if 00 [Normal  decode])
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models  00h-0fh) Internal PCIe GPP Bridge 0 to Bus B (prog-if 00 [Normal  decode])
SMBus		: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 59)
ISA bridge		: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 6
Host bridge		: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7
Non-Volatile memory controller		: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981 (prog-if 02 [NVM Express])
USB controller		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset USB 3.1 xHCI Controller (rev 02) (prog-if 30 [XHCI])
SATA controller		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset SATA Controller (rev 02) (prog-if 01 [AHCI 1.0])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Device 43b2 (rev 02) (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02) (prog-if 00 [Normal decode])
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
Network controller		: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
VGA compatible controller		: Advanced Micro Devices, Inc. [AMD/ATI]  Ellesmere [Radeon RX 470/480/570/570X/580/580X] (rev c1) (prog-if 00  [VGA controller])
Audio device		: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580]

USB Devices
-----------

-USB Devices-
Linux Foundation 3.0 root hub
A4Tech Co., Ltd.
Linux Foundation 2.0 root hub
Linux Foundation 3.0 root hub
ASUSTek Computer, Inc.
Realtek Semiconductor Corp.
Razer USA, Ltd
IMC Networks
Linux Foundation 2.0 root hub

Printers
--------

-Printers-
No printers found

Battery
-------

-Battery: BAT0-
State		: Not charging
Capacity		: 99 / Normal
Battery Technology		: Li-ion
Manufacturer		: ASUSTeK
Model Number		: ASUS Battery
Serial Number

Sensors
-------

-Sensors-
acpitz/temp1	Temperature	56,00°C	
k10temp/temp1	Temperature	56,50°C	
amdgpu/temp1	Temperature	55,00°C	
amdgpu/in0	Voltage	1,00V	
thermal/thermal_zone0	Temperature	56,00°C	

Input Devices
-------------

-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Power Button
 Video Bus
 COMPANY USB Device
 COMPANY USB Device
 COMPANY USB Device
 Asus Keyboard
 Asus Keyboard
 Asus Keyboard
 Asus Wireless Radio Control
 ELAN1200:00 04F3:3066 Touchpad
 HDA ATI HDMI HDMI/DP,pcm:3
 HDA ATI HDMI HDMI/DP,pcm:7
 USB2.0 HD UVC WebCam: USB2.0 HD
 Asus WMI hotkeys
 HD-Audio Generic Headphone
 Razer USB Dongle for Razer Lancehead
 Razer USB Dongle for Razer Lancehead
 Razer USB Dongle for Razer Lancehead

Storage
-------


DMI
---

-Product-
Name		: GL702ZC
Family		: ROG
Vendor		: ASUSTeK COMPUTER INC. (SEAGATE, [www.seagate.com]("http://www.seagate.com"))
Version		: 1.0
-BIOS-
Date		: 05/10/2018
Vendor		: American Megatrends Inc. (American Megatrends, [www.ami.com]("http://www.ami.com"))
Version		: GL702ZC.305
-Board-
Name		: GL702ZC
Vendor		: ASUSTeK COMPUTER INC. (SEAGATE, [www.seagate.com]("http://www.seagate.com"))
Version		: 1.0
Serial Number		: N0CV1742MB0029575
Asset Tag		: ATN12345678901234567
-Chassis-
Vendor		: ASUSTeK COMPUTER INC. (SEAGATE, [www.seagate.com]("http://www.seagate.com"))
Type		: [10] Notebook
Computer
********


Summary
-------

-Computer-
Processor		: AMD Ryzen 5 1600 Six-Core Processor
Memory		: 16424MB (2579MB used)
Machine Type		: Notebook
Operating System		: Linux Mint 19.1 Tessa
User Name		: root (root)
Date/Time		: Fri 26 Apr 2019 08:36:43 PM -04
-Display-
Resolution		: 1920x1080 pixels
OpenGL Renderer		: Radeon RX 580 Series
X11 Vendor		: The X.Org Foundation
-Audio Devices-
Audio Adapter		: HDA-Intel - HDA ATI HDMI
Audio Adapter		: HDA-Intel - HD-Audio Generic
-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Power Button
 Video Bus
 COMPANY USB Device
 COMPANY USB Device
 COMPANY USB Device
 Asus Keyboard
 Asus Keyboard
 Asus Keyboard
 Asus Wireless Radio Control
 ELAN1200:00 04F3:3066 Touchpad
Version		: 1.0
Serial Number		: HAN0CV158316437
Asset Tag		: No Asset Tag

Memory SPD
----------

-SPD-
Please load the eeprom module to obtain information about memory SPD

Resources
---------

-I/O Ports-
<tt>0000-03af </tt>		: PCI Bus 0000:00
<tt>  0000-001f </tt>		: dma1
<tt>  0020-0021 </tt>		: pic1
<tt>  0040-0043 </tt>		: timer0
<tt>  0050-0053 </tt>		: timer1
Computer
********


Summary
-------

-Computer-
Processor		: AMD Ryzen 5 1600 Six-Core Processor
Memory		: 16424MB (2579MB used)
Machine Type		: Notebook
Operating System		: Linux Mint 19.1 Tessa
User Name		: root (root)
Date/Time		: Fri 26 Apr 2019 08:36:43 PM -04
-Display-
Resolution		: 1920x1080 pixels
OpenGL Renderer		: Radeon RX 580 Series
X11 Vendor		: The X.Org Foundation
-Audio Devices-
Audio Adapter		: HDA-Intel - HDA ATI HDMI
Audio Adapter		: HDA-Intel - HD-Audio Generic
-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Power Button
 Video Bus
 COMPANY USB Device
 COMPANY USB Device
 COMPANY USB Device
 Asus Keyboard
 Asus Keyboard
 Asus Keyboard
 Asus Wireless Radio Control
 ELAN1200:00 04F3:3066 Touchpad
<tt>  0060-0060 </tt>		: keyboard
<tt>  0061-0061 </tt>		: PNP0800:00
<tt>  0062-0062 </tt>		: PNP0C09:00
<tt>    0062-0062 </tt>		: EC data
<tt>  0064-0064 </tt>		: keyboard
<tt>  0066-0066 </tt>		: PNP0C09:00
<tt>    0066-0066 </tt>		: EC cmd
<tt>  0070-0071 </tt>		: rtc0
<tt>  0080-008f </tt>		: dma page reg
<tt>  00a0-00a1 </tt>		: pic2
<tt>  00c0-00df </tt>		: dma2
<tt>  00f0-00ff </tt>		: fpu
<tt>03b0-03df </tt>		: PCI Bus 0000:00
<tt>03e0-0cf7 </tt>		: PCI Bus 0000:00
<tt>  040b-040b </tt>		: pnp 00:03
<tt>  04d0-04d1 </tt>		: pnp 00:03
<tt>  04d6-04d6 </tt>		: pnp 00:03
<tt>  0800-089f </tt>		: pnp 00:03
<tt>    0800-0803 </tt>		: ACPI PM1a_EVT_BLK
<tt>    0804-0805 </tt>		: ACPI PM1a_CNT_BLK
<tt>    0808-080b </tt>		: ACPI PM_TMR
<tt>    0810-0815 </tt>		: ACPI CPU throttle
<tt>    0820-0827 </tt>		: ACPI GPE0_BLK
<tt>  0900-090f </tt>		: pnp 00:03
<tt>  0910-091f </tt>		: pnp 00:03
<tt>  0b00-0b08 </tt>		: piix4_smbus
<tt>  0c00-0c01 </tt>		: pnp 00:03
<tt>  0c14-0c14 </tt>		: pnp 00:03
<tt>  0c50-0c51 </tt>		: pnp 00:03
<tt>  0c52-0c52 </tt>		: pnp 00:03
<tt>  0c6c-0c6c </tt>		: pnp 00:03
<tt>  0c6f-0c6f </tt>		: pnp 00:03
<tt>  0cd0-0cd1 </tt>		: pnp 00:03
<tt>  0cd2-0cd3 </tt>		: pnp 00:03
<tt>  0cd4-0cd5 </tt>		: pnp 00:03
<tt>  0cd6-0cd7 </tt>		: pnp 00:03
<tt>    0cd6-0cd7 </tt>		: smba_idx
<tt>  0cd8-0cdf </tt>		: pnp 00:03
<tt>0cf8-0cff </tt>		: PCI conf1
<tt>0d00-ffff </tt>		: PCI Bus 0000:00
<tt>  d000-efff </tt>		: PCI Bus 0000:03
<tt>    d000-efff </tt>		: PCI Bus 0000:04
<tt>      d000-dfff </tt>		: PCI Bus 0000:07
<tt>        d000-d0ff </tt>		:  <b><small>PCI</small></b>  Realtek Semiconductor  Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
<tt>          d000-d0ff </tt>		:  <b><small>Module</small></b> Realtek 802.11n PCI  wireless core
<tt>      e000-efff </tt>		: PCI Bus 0000:06
<tt>        e000-e0ff </tt>		:  <b><small>PCI</small></b>  Realtek Semiconductor  Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller  (rev 10)
<tt>          e000-e0ff </tt>		:  <b><small>Module</small></b> RealTek RTL-8169  Gigabit Ethernet driver
<tt>  f000-ffff </tt>		: PCI Bus 0000:0c
<tt>    f000-f0ff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]  (rev c1) (prog-if 00 [VGA controller])
-Memory-
<tt>00000000-00000fff </tt>		: Reserved
<tt>00001000-0009ffff </tt>		: System RAM
<tt>000a0000-000fffff </tt>		: Reserved
<tt>  000a0000-000bffff </tt>		: PCI Bus 0000:00
<tt>  000c0000-000dffff </tt>		: PCI Bus 0000:00
<tt>  000f0000-000fffff </tt>		: System ROM
<tt>00100000-09d7ffff </tt>		: System RAM
<tt>09d80000-09ffffff </tt>		: Reserved
<tt>0a000000-db7acfff </tt>		: System RAM
<tt>db7ad000-dcc81fff </tt>		: Reserved
<tt>dcc82000-dccb1fff </tt>		: ACPI Tables
<tt>dccb2000-dcdccfff </tt>		: ACPI Non-volatile Storage
<tt>  dcdae000-dcdaefff </tt>		: MSFT0101:00
<tt>  dcdb2000-dcdb2fff </tt>		: MSFT0101:00
<tt>dcdcd000-dd759fff </tt>		: Reserved
<tt>dd75a000-dd815fff </tt>		: Unknown E820 type
<tt>dd816000-deffffff </tt>		: System RAM
<tt>df000000-dfffffff </tt>		: Reserved
<tt>e0000000-fec2ffff </tt>		: PCI Bus 0000:00
<tt>  e0000000-f01fffff </tt>		: PCI Bus 0000:0c
<tt>    e0000000-efffffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]  (rev c1) (prog-if 00 [VGA controller])
<tt>    f0000000-f01fffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]  (rev c1) (prog-if 00 [VGA controller])
<tt>  f8000000-fbffffff </tt>		: PCI MMCONFIG 0000 [bus 00-3f]
<tt>    f8000000-fbffffff </tt>		: Reserved
<tt>      f8000000-fbffffff </tt>		: pnp 00:00
<tt>  fdf00000-fdffffff </tt>		: Reserved
<tt>  fe100000-fe3fffff </tt>		: PCI Bus 0000:11
<tt>    fe100000-fe1fffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] Family 17h (Models 00h-0fh) USB 3.0 Host Controller  (prog-if 30 [XHCI])
<tt>      fe100000-fe1fffff </tt>		: xhci-hcd
<tt>    fe200000-fe2fffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Platform Security  Processor
<tt>      fe200000-fe2fffff </tt>		:  <b><small>Module</small></b> AMD Secure  Processor driver
<tt>    fe300000-fe301fff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Platform Security  Processor
<tt>      fe300000-fe301fff </tt>		:  <b><small>Module</small></b> AMD Secure  Processor driver
<tt>  fe400000-fe6fffff </tt>		: PCI Bus 0000:03
<tt>    fe400000-fe5fffff </tt>		: PCI Bus 0000:04
<tt>      fe400000-fe4fffff </tt>		: PCI Bus 0000:07
<tt>        fe400000-fe40ffff </tt>		:  <b><small>PCI</small></b>  Realtek Semiconductor  Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
<tt>          fe400000-fe40ffff </tt>		:  <b><small>Module</small></b> Realtek 802.11n PCI  wireless core
<tt>      fe500000-fe5fffff </tt>		: PCI Bus 0000:06
<tt>        fe500000-fe503fff </tt>		:  <b><small>PCI</small></b>  Realtek Semiconductor  Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller  (rev 10)
<tt>          fe500000-fe503fff </tt>		:  <b><small>Module</small></b> RealTek RTL-8169  Gigabit Ethernet driver
<tt>        fe504000-fe504fff </tt>		:  <b><small>PCI</small></b>  Realtek Semiconductor  Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller  (rev 10)
<tt>          fe504000-fe504fff </tt>		:  <b><small>Module</small></b> RealTek RTL-8169  Gigabit Ethernet driver
<tt>    fe600000-fe67ffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] 300 Series Chipset SATA Controller (rev 02) (prog-if  01 [AHCI 1.0])
<tt>    fe680000-fe69ffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] 300 Series Chipset SATA Controller (rev 02) (prog-if  01 [AHCI 1.0])
<tt>      fe680000-fe69ffff </tt>		: <b><small>Module</small></b> AHCI SATA low-level driver
<tt>    fe6a0000-fe6a7fff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] 300 Series Chipset USB 3.1 xHCI Controller (rev 02)  (prog-if 30 [XHCI])
<tt>      fe6a0000-fe6a7fff </tt>		: xhci-hcd
<tt>  fe700000-fe7fffff </tt>		: PCI Bus 0000:12
<tt>    fe700000-fe707fff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
<tt>      fe700000-fe707fff </tt>		: ICH HD audio
<tt>    fe708000-fe708fff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51) (prog-if 01  [AHCI 1.0])
<tt>      fe708000-fe708fff </tt>		: <b><small>Module</small></b> AHCI SATA low-level driver
<tt>  fe800000-fe8fffff </tt>		: PCI Bus 0000:0c
<tt>    fe800000-fe83ffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]  (rev c1) (prog-if 00 [VGA controller])
<tt>    fe840000-fe85ffff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]  (rev c1) (prog-if 00 [VGA controller])
<tt>    fe860000-fe863fff </tt>		:  <b><small>PCI</small></b>  Advanced Micro  Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580]
<tt>      fe860000-fe863fff </tt>		: ICH HD audio
<tt>  fe900000-fe9fffff </tt>		: PCI Bus 0000:01
<tt>    fe900000-fe903fff </tt>		:  <b><small>PCI</small></b>  Samsung Electronics  Co Ltd NVMe SSD Controller SM981/PM981 (prog-if 02 [NVM Express])
<tt>      fe900000-fe903fff </tt>		: nvme
<tt>  fea00000-fea0ffff </tt>		: Reserved
<tt>  feb80000-fec01fff </tt>		: Reserved
<tt>    feb80000-febfffff </tt>		: amd_iommu
<tt>    fec00000-fec003ff </tt>		: IOAPIC 0
<tt>    fec01000-fec013ff </tt>		: IOAPIC 1
<tt>  fec10000-fec10fff </tt>		: Reserved
<tt>    fec10000-fec10fff </tt>		: pnp 00:03
<tt>fec30000-fec30fff </tt>		: Reserved
<tt>  fec30000-fec30fff </tt>		: AMDIF030:00
<tt>    fec30000-fec30fff </tt>		: AMDIF030:00
<tt>fed00000-fed00fff </tt>		: Reserved
<tt>  fed00000-fed003ff </tt>		: HPET 0
<tt>    fed00000-fed003ff </tt>		: PNP0103:00
<tt>fed40000-fed44fff </tt>		: Reserved
<tt>fed80000-fed8ffff </tt>		: Reserved
<tt>  fed81500-fed818ff </tt>		: AMDI0030:00
<tt>fedc0000-fedc0fff </tt>		: pnp 00:03
<tt>fedc2000-fedcffff </tt>		: Reserved
<tt>  fedc5000-fedc5fff </tt>		: AMDI0010:03
<tt>    fedc5000-fedc5fff </tt>		: AMDI0010:03
<tt>fedd4000-fedd5fff </tt>		: Reserved
<tt>fee00000-ffffffff </tt>		: PCI Bus 0000:00
<tt>  fee00000-feefffff </tt>		: Reserved
<tt>    fee00000-fee00fff </tt>		: Local APIC
<tt>      fee00000-fee00fff </tt>		: pnp 00:03
<tt>  ff000000-ffffffff </tt>		: Reserved
<tt>    ff000000-ffffffff </tt>		: pnp 00:03
<tt>100000000-41f37ffff </tt>		: System RAM
<tt>  2a1800000-2a24031d0 </tt>		: Kernel code
<tt>  2a24031d1-2a2e6a6bf </tt>		: Kernel data
<tt>  2a30e2000-2a333dfff </tt>		: Kernel bss
<tt>41f380000-41fffffff </tt>		: RAM buffer
-DMA-
<tt> 4</tt>		: cascade

Network
*******


Interfaces
----------

-Network Interfaces-
enp6s0	0,00MiB	0,00MiB		
lo	0,43MiB	0,43MiB	127.0.0.1	
wlp7s0	3145,83MiB	79,72MiB	192.168.100.4	

IP Connections
--------------

-Connections-
127.0.0.53:53		0.0.0.0:*	udp	
127.0.0.1:631	LISTEN	0.0.0.0:*	tcp	
192.168.100.4:60996	ESTABLISHED	35.155.196.37:443	tcp	
192.168.100.4:36032	ESTABLISHED	35.160.92.193:443	tcp	
192.168.100.4:36786	ESTABLISHED	198.252.206.25:443	tcp	
192.168.100.4:58992	TIME_WAIT	64.233.190.94:443	tcp	
192.168.100.4:50558	TIME_WAIT	64.233.190.128:443	tcp	
192.168.100.4:41976	ESTABLISHED	192.16.58.8:80	tcp	
192.168.100.4:32768	ESTABLISHED	35.155.196.37:443	tcp	
192.168.100.4:56550	TIME_WAIT	172.217.192.19:443	tcp	
192.168.100.4:41996	TIME_WAIT	192.16.58.8:80	tcp	
192.168.100.4:58966	TIME_WAIT	64.233.190.94:443	tcp	
192.168.100.4:35552	TIME_WAIT	13.32.80.47:443	tcp	
192.168.100.4:34194	ESTABLISHED	95.211.246.228:80	tcp	
192.168.100.4:59526	TIME_WAIT	172.217.192.103:443	tcp	
192.168.100.4:41994	ESTABLISHED	192.16.58.8:80	tcp	
192.168.100.4:60998	ESTABLISHED	35.155.196.37:443	tcp	
192.168.100.4:47066	TIME_WAIT	64.233.186.19:443	tcp	
192.168.100.4:60992	ESTABLISHED	35.155.196.37:443	tcp	
192.168.100.4:51296	ESTABLISHED	216.58.222.138:443	tcp	
192.168.100.4:41998	ESTABLISHED	192.16.58.8:80	tcp	
192.168.100.4:49646	ESTABLISHED	185.59.223.153:443	tcp	
192.168.100.4:36864	TIME_WAIT	172.217.192.95:443	tcp	
192.168.100.4:36866	TIME_WAIT	172.217.192.95:443	tcp	
192.168.100.4:47098	TIME_WAIT	64.233.186.19:443	tcp	
192.168.100.4:36672	ESTABLISHED	198.252.206.25:443	tcp	
192.168.100.4:60994	ESTABLISHED	35.155.196.37:443	tcp	
192.168.100.4:53108	ESTABLISHED	192.124.249.8:443	tcp	
192.168.100.4:36030	ESTABLISHED	35.160.92.193:443	tcp	
192.168.100.4:49220	ESTABLISHED	35.160.103.71:443	tcp	
192.168.100.4:54320	TIME_WAIT	172.217.162.78:443	tcp	
192.168.100.4:50158	TIME_WAIT	64.233.190.132:443	tcp	
192.168.100.4:54656	ESTABLISHED	52.27.144.31:443	tcp	
192.168.100.4:57120	TIME_WAIT	172.217.192.138:443	tcp	
192.168.100.4:46230	TIME_WAIT	64.233.186.94:443	tcp	
192.168.100.4:32770	ESTABLISHED	35.155.196.37:443	tcp	
192.168.100.4:41978	ESTABLISHED	192.16.58.8:80	tcp	
192.168.100.4:38678	ESTABLISHED	64.233.186.84:443	tcp	
::1:631	LISTEN	:::*	tcp6	
0.0.0.0:5353		0.0.0.0:*	udp	
0.0.0.0:47705		0.0.0.0:*	udp	
127.0.0.53:53		0.0.0.0:*	udp	
0.0.0.0:68		0.0.0.0:*	udp	
0.0.0.0:631		0.0.0.0:*	udp	
:::5353		:::*	udp6	
:::47852		:::*	udp6	

Routing Table
-------------

-IP routing table-
0.0.0.0 / 192.168.100.1	0.0.0.0	UG	wlp7s0	
169.254.0.0 / 0.0.0.0	255.255.0.0	U	wlp7s0	
192.168.100.0 / 0.0.0.0	255.255.255.0	U	wlp7s0	

ARP Table
---------

-ARP Table-
192.168.100.1	ac:75:1d:66:8b:50	wlp7s0	

DNS Servers
-----------

-Name Servers-
127.0.0.53		: localhost

Statistics
----------

-IP-
<b> </b>		: Forwarding: 2
<b> </b>		: 2338229 total packets received
<b> </b>		: 1 with invalid addresses
<b> </b>		: 0 forwarded
<b> </b>		: 0 incoming packets discarded
<b> </b>		: 2337703 incoming packets delivered
<b> </b>		: 816785 requests sent out
-ICMP-
<b> </b>		: 0 ICMP messages received
<b> </b>		: 0 input ICMP message failed
<b> </b>		: ICMP input histogram:
<b> </b>		: 2 ICMP messages sent
<b> </b>		: 0 ICMP messages failed
<b> </b>		: ICMP output histogram:
<b> </b>		: destination unreachable: 2
-ICMPMSG-
<b> </b>		: OutType3: 2
-TCP-
<b> </b>		: 812 active connection openings
<b> </b>		: 0 passive connection openings
<b> </b>		: 10 failed connection attempts
<b> </b>		: 15 connection resets received
<b> </b>		: 21 connections established
<b> </b>		: 2332478 segments received
<b> </b>		: 811583 segments sent out
<b> </b>		: 3 segments retransmitted
<b> </b>		: 1 bad segments received
<b> </b>		: 1472 resets sent
-UDP-
<b> </b>		: 5201 packets received
<b> </b>		: 2 packets to unknown port received
<b> </b>		: 0 packet receive errors
<b> </b>		: 5204 packets sent
<b> </b>		: 0 receive buffer errors
<b> </b>		: 0 send buffer errors
<b> </b>		: IgnoredMulti: 24
-UDPLITE-
-TCPEXT-
<b> </b>		: 322 TCP sockets finished time wait in fast timer
<b> </b>		: 1 packetes rejected in established connections because of timestamp
<b> </b>		: 714 delayed acks sent
<b> </b>		: Quick ack mode was activated 1813 times
<b> </b>		: 2181052 packet headers predicted
<b> </b>		: 7300 acknowledgments not containing data payload received
<b> </b>		: 5515 predicted acknowledgments
<b> </b>		: TCPLossProbes: 3
<b> </b>		: TCPDSACKOldSent: 214
<b> </b>		: TCPDSACKRecv: 1
<b> </b>		: 143 connections reset due to unexpected data
<b> </b>		: 10 connections reset due to early user close
<b> </b>		: TCPDSACKIgnoredNoUndo: 1
<b> </b>		: TCPRcvCoalesce: 1550166
<b> </b>		: TCPOFOQueue: 6949
<b> </b>		: TCPChallengeACK: 1
<b> </b>		: TCPSYNChallenge: 1
<b> </b>		: TCPAutoCorking: 926
<b> </b>		: TCPOrigDataSent: 15793
<b> </b>		: TCPHystartTrainDetect: 3
<b> </b>		: TCPHystartTrainCwnd: 58
<b> </b>		: TCPKeepAlive: 1761
-IPEXT-
<b> </b>		: InMcastPkts: 84
<b> </b>		: OutMcastPkts: 63
<b> </b>		: InBcastPkts: 24
<b> </b>		: OutBcastPkts: 24
<b> </b>		: InOctets: 3266285470
<b> </b>		: OutOctets: 49895216
<b> </b>		: InMcastOctets: 10795
<b> </b>		: OutMcastOctets: 6163
<b> </b>		: InBcastOctets: 1132
<b> </b>		: OutBcastOctets: 1132
<b> </b>		: InNoECTPkts: 2338229

Shared Directories
------------------

-SAMBA-
printers		: /var/spool/samba
print$		: /var/lib/samba/printers
-NFS-
No NFS exports
```

---

### Post by dino99 on 2019-04-27
Maybe you need to test that ppa, which have the latest vulkan config
> [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

---

