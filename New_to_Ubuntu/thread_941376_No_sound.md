---
title: "No sound"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by ibznorange on 2008-10-08
Ive been wittling down the issues with ubuntu as Im frankly just done morally with windows and the monopoly.

Anyways, everything now works flawlessly, except sound

lspci gives me

```
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
```

Sysinfo has 2 lines posted under Hardware/soundcard/multimedia controller

```
intel corporation 82801ji (ICH10 family) HD audio controller
subsytem: Asustek computer inc. unknown device 82fe
```

under system/prefrences/sound it shows 2 devices under default mixer tracks, HDA Intel (alsa mixer) and realtek alc888(OSS mixer)

if im not mistaken, it should be an alc883 though from what google tells me

for all options (sound events, music and movies, audio conferencing) when i test with autodetect, OSS-open sound system, or pulseaudio i get 
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.
```

with alc883 digital,(see, alc883 here as well :shrug:), alc883 analog, and ALSA - advanced linux sound architecture, i get
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.
```

Sound works A OK in XP. I rreeaaally wanna stick with this, but im a musician, and a music listening type, so i cant if i dont have my sound running. HELP SAVE A CONVERT

oh and yes, i did search around, quite alot first. Im a bit of a forumite elsewhere so i know how it goes. Nothing ive read has helped so far

---

### Post by rybaxs on 2008-10-08
Try to open audio player,check the controls maybe it is mute, sometimes player have a global effect in changing volume control.. can you hear the Ubuntu intro sounds?

---

### Post by rolnics on 2008-10-08
When I first install Ubuntu for some reason my sound stops working and I find that the reason is my digital output is checked. Unchecking that resolves it for me.

To find your digital output, open you volume control via the icon (right click) and click the output tab, then uncheck the digital output.

---

### Post by lordfrikk on 2008-10-08
> **rolnics said:**
> When I first install Ubuntu for some reason my sound stops working and I find that the reason is my digital output is checked. Unchecking that resolves it for me.

To find your digital output, open you volume control via the icon (right click) and click the output tab, then uncheck the digital output.

Yep, that solved it for me as well. I have old SB Audigy.:)

---

### Post by ibznorange on 2008-10-08
Already messed with the volumes, including alsamixer ;)

Im a linux noob but im generally capable of figuring things out, if nothing else by looking up old threads.

Hrm. ill check out the digital output thing when i get home. I'll keep you posted.

---

### Post by ibznorange on 2008-10-08
Welp, problemo. There isnt any output tab on my volume control

---

### Post by ibznorange on 2008-10-08
update:

didnt think to check with the different device mixer tracks. the above errors are with 
HDA Intel (OSS Mixer)

With Realtek ALC888 (ALSA Mixer)
i get the following errors

autodetect, OSS:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Internal data flow error.
```

ALC883 Digital:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.
```

ALC883 Analog, ALSA:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.
```

PulseAudio Sound Server:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused
```

:confused:
[edit]
Dmesg gives me this
```

[   51.567533] sysfs: duplicate filename 'pcspkr' can not be created
[   51.567535] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   51.567538] Pid: 3113, comm: modprobe Tainted: P        2.6.24-19-generic #1
[   51.567539] 
[   51.567540] Call Trace:
[   51.567549]  [<ffffffff80303b88>] sysfs_add_one+0xb8/0xf0
[   51.567551]  [<ffffffff803041a0>] create_dir+0x60/0xb0
[   51.567555]  [<ffffffff80304221>] sysfs_create_dir+0x31/0x50
[   51.567558]  [<ffffffff8034a092>] kobject_get+0x12/0x20
[   51.567560]  [<ffffffff8034a6a3>] kobject_add+0xb3/0x200
[   51.567563]  [<ffffffff8034a888>] kobject_register+0x28/0x50
[   51.567567]  [<ffffffff803bf121>] bus_add_driver+0x91/0x220
[   51.567572]  [<ffffffff80263c5e>] sys_init_module+0x18e/0x1a90
[   51.567579]  [<ffffffff80251bf0>] param_get_int+0x0/0x20
[   51.567584]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[   51.567588] 
[   51.567589] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
[   51.567593] Pid: 3113, comm: modprobe Tainted: P        2.6.24-19-generic #1
[   51.567594] 
[   51.567595] Call Trace:
[   51.567597]  [<ffffffff8034a739>] kobject_add+0x149/0x200
[   51.567599]  [<ffffffff8034a888>] kobject_register+0x28/0x50
[   51.567602]  [<ffffffff803bf121>] bus_add_driver+0x91/0x220
[   51.567605]  [<ffffffff80263c5e>] sys_init_module+0x18e/0x1a90
[   51.567612]  [<ffffffff80251bf0>] param_get_int+0x0/0x20
[   51.567615]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[   51.567619] 
[   51.684024] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   51.685061] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   51.717395] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   52.717435] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:586: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   53.719837] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x100f0000
[   55.061297] lp: driver loaded but no devices found
[   55.135686] Adding 9936160k swap on /dev/sdc5.  Priority:-1 extents:1 across:9936160k
[   55.682188] EXT3 FS on sdc1, internal journal
[   57.179007] ip_tables: (C) 2000-2006 Netfilter Core Team
[   57.494750] No dock devices found.
[   58.594026] ppdev: user-space parallel port driver
[   58.807072] audit(1223523432.856:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5377 profile="/usr/sbin/cupsd" namespace="default"
[   67.920102] r8169: eth0: link up
[   67.920113] r8169: eth0: link up
[   68.035261] Bluetooth: Core ver 2.11
[   68.035397] NET: Registered protocol family 31
[   68.035403] Bluetooth: HCI device and connection manager initialized
[   68.035410] Bluetooth: HCI socket layer initialized
[   68.043851] Bluetooth: L2CAP ver 2.9
[   68.043856] Bluetooth: L2CAP socket layer initialized
[   68.094388] Bluetooth: RFCOMM socket layer initialized
[   68.094546] Bluetooth: RFCOMM TTY layer initialized
[   68.094549] Bluetooth: RFCOMM ver 1.8
[   70.120576] NET: Registered protocol family 17
[   75.372239] printk: 191 messages suppressed.
[   76.314035] NET: Registered protocol family 10
[   76.314316] lo: Disabled Privacy Extensions
[   86.347071] eth0: no IPv6 routers present
[ 2242.932625] printk: 5 messages suppressed.
[ 2271.710357] UDF-fs: No VRS found
[ 2271.766084] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2271.771654] ISOFS: changing to secondary root

```

---

### Post by ibznorange on 2008-10-09
OK updated to Ibex beta. Same stuff, except ALSA and PulseAudio just say testing perpetually. However, OSS mixer says
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.
```

[edit]

Killing gnome sound manager took care of that, now im just back to an internal data flow error :squint:

[edit] fresh boot, all the alc883/888 options are gone, im down to ALSA, OSS, PulseAudio, and Autodetect :confused:

[moreedit] Further probing reveals that NO sound modules are loaded :/

how would i load those up? Still a n00b lol

---

### Post by ibznorange on 2008-10-09
Ok, problem. modprobe snd_hda_intel (which from all google searches should be running, and is not) yields 
```
WARNING: Could not open '/lib/modules/2.6.27-6-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.27-6-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.27-6-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.27-6-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.27-6-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory

```

---

### Post by sarthorks on 2008-10-10
I was having this problem that although system sounds were working fine, i couldnt get Movie Player or Rhythmbox to play audio for me quite a lot of times and I woould have to reboot. VLC Player would always play songs for me.

I went to System->Sound Preferences and selected Autodetect for Music and Movies, and hey presto everything's working fine now!

---

### Post by ibznorange on 2008-10-13
yeah but ive got nothing duder, no system sounds, nada. No programs play sound.the only tonez i get are system beeps, and those arent as fun as my music

---

### Post by ibznorange on 2008-10-20
bump.

still nothing guys

---

### Post by bluestix on 2008-10-31
Hey

I have the same problem.


My sound worked fine for the last 6 months up until today. 

Today when I turned on my comp there was no sound.


I will let you know if I get anywhere.

---

### Post by enbuyukfener on 2008-11-03
Same problem here. Multitude of errors similar to OP's after upgrading from Hardy to Intrepid. Mind you, sound was not working ideally in Hardy either but at least the only problem back then was that sometimes only one app (or application type) was able to use sound at a time.

---

### Post by popie on 2008-11-03
I'm trying to help a friend with the same problem. He had some sound when he first installed, I think through a USB headset. Now nothing. 

Even the internal laptop speakers don't work playing DVDs, CDs, MP3s, Teamspeak, or test tones in sound preferences...

Is there some way to completely reset the sound settings back to defaults?

He's on Hardy v8.04.

---

### Post by enbuyukfener on 2008-11-05
popie:

Sorry, not sure, however, doing a "sudo alsa force-reload" from a terminal solved the problem for me. I still have the problem where only one app or app type can use sound at a time :(

---

### Post by samrugger on 2008-11-12
Not sure if this will help, although when I was having this issue anything was worth a shot...

I had the same errors listed above using Realtek HD onboard sound ALC888.  MOBO is an Asus P5LP-LE.  Racked my brain, what little there is, until something told me to check the BIOS setup.  Audio was set to "Auto", changed that to "Enabled" and the sky opened up to the glorious sounds of Ubuntu (and finally my music)...

All works now, very well.  Using PulseAudio Sound Server w/ Realtek ALC888 (OSS Mixer) for default mixer.

Good luck!

---

### Post by cooperised on 2008-11-25
I had a very similar set of errors to the OP here (running Intrepid).  Sound worked fine on installation a week ago, something's broken since.  Tried "sudo alsa force-reload" as suggested by enbuyukfener, and that fixed it :) - anyone any idea what might be causing it?  Sorry I went straight for a solution instead of diagnosing the problem, if it happens again I'll get dmesg output etc.

---

### Post by ged5 on 2008-11-26
I had no sound or sound with one app only. Then I found the "sudo alsa force-reload" and that fixed it till I re-booted  when it was all bad again.

Then I found another post where someone suggested disabling onboard sound in the bios. That fixed it and I think that could be the problem with a lot of us noobs cause most mobo's have onboard sound and most of us upgrade to a decent sound card. 

In my bios the entry was under

Integrated Peripherals
On Chip PCI Device
On Chip Audio Controller  -   change to Disabled

Ged

---

### Post by Qinkai on 2008-12-01
I had no sound on my machine just a crackling sound but got it fixed check this thread

[http://ubuntuforums.org/showthread.p...94#post6183194](http://ubuntuforums.org/showthread.p...94#post6183194)

---

### Post by moli on 2009-02-21
ok, 'sudo alsa force-reload' worked for me too. 
ubuntu really needs a complete sound system rework and rationalizing.
i've lost sound from one day to the other, my integrated soundchip went away. even under winxp, but still i think the problem is the super-intelligent front-presence-audio-magic-****. i somehow disabled something in the driver softwares and stuck with no sound at all. when i plug something into the front i can turn off my amplifier, i'm smart, able, dextrous enough to do that.
anyway so i've installed my soundblasterlive card and got sound in banshee but not in mplayer/alsa. in the sound config menu i got a 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.' error when tried autodetect/alsa/oss only specific soundblaster device worked.

---

### Post by fred_99 on 2009-05-08
> **enbuyukfener said:**
> 

Sorry, not sure, however, doing a "sudo alsa force-reload" from a terminal solved the problem for me. I still have the problem where only one app or app type can use sound at a time :(

Solved the problem for me as well. Thanks!

My problem was by the way that when I left work, I just paused VLC. Sometimes, when I got back the next day, no sound. I had to reboot to make it work again. Not anymore ;-)

Fred

---

### Post by user2037 on 2009-06-24
Still no sound on this end. ALSA stopped working with 9.04. As of today OSS also doesn't work as well. The ALSA sound test in Sound Preferences says it is playing, but there is no audio. OSS sound test produces "audiotestsrc wave=sine... Could not open audio device for playback".

"sudo alsa force-reload" produces:
```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/progers/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/progers/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

```

Lspci says the sound device is "Intel Corporation 82801JI (ICH10 Family) HD Audio Controller".

EDIT: Issue has been resolved. Turns out it was related to a Linuxant modem driver getting in the way. It was a kernel-version specific driver. After re-installing the kernel-version-agnostic version and checking the ALSA volume both ALSA and OSS are working again.

---

### Post by goog64 on 2009-06-28
I had the same errors listed above using Realtek HD onboard sound ALC888. MOBO is an Asus P5LP-LE. Racked my brain, what little there is, until something told me to check the BIOS setup. Audio was set to "Auto", changed that to "Enabled" and the sky opened up to the glorious sounds of Ubuntu (and finally my music)...

I have no sound whatsoever. How does one "check the BIOS setup"?

---

### Post by ibznorange on 2009-06-29
> **goog64 said:**
> I had the same errors listed above using Realtek HD onboard sound ALC888. MOBO is an Asus P5LP-LE. Racked my brain, what little there is, until something told me to check the BIOS setup. Audio was set to "Auto", changed that to "Enabled" and the sky opened up to the glorious sounds of Ubuntu (and finally my music)...

I have no sound whatsoever. How does one "check the BIOS setup"?

that would be where your computer says "press del to enter setup" (or f2, or escape, or such depending on your computer. odds are, that is not the problem. in my experience, including both of my sound issues, as well as 4 friends all using hd intel audio chips, the issue can be resolved by recompiling alsa from scratch. if you need a hand, with that, shoot me a pm and ill get you sorted

---

### Post by prish on 2011-08-22
try this command in terminal

alsa force reload

---

