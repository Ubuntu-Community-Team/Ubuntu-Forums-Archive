---
title: "No sound via HDMI AMD Radeon HD 7670 Ubuntu 13.04 64bit"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by 0N3 on 2013-04-26
I recently did fresh install of Ubuntu 13.04 64bit and was able to play sound via HDMI using the open source drivers. The only problem is there is no hardware acceleration via those drivers and they also make my fan spin constantly even if left idle for hours. The AMD graphics drivers I have installed is version 13.4 AMD legacy driver. I have edited the kernel parameters like:

[COLOR=#333333][FONT=Ubuntu Beta]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and changed it to:

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"  (This method worked with the open source drivers but not with the closed source drivers)

Any help appreciated :-)[/FONT][/COLOR]

---

### Post by DuckHook on 2013-04-26
Please provide HW info. At a minimum, do:```
lspci -vk | egrep -iA13 "vga|audio"
```

Your boot parameter won't work because the *radeon.audio* parameter is specific to the open-source *radeon* driver whereas you now have closed-source *fglrx* installed. Sound is likely being piped through your motherboard sound chip instead of your video card, but impossible to know without proper HW info.

---

### Post by 0N3 on 2013-04-26
Heres the output:


00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at c1210000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c1100000-c11fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
--
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT [Radeon HD 7670M] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device fb22
	Flags: bus master, fast devsel, latency 0, IRQ 55
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at c0040000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci


01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c0020000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


07:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c1100000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: alx

Thanks for quick reply

---

### Post by DuckHook on 2013-04-26
Let's try simple things first. In sound settings, do you have a HDMI output option? If so, select it, then reboot. Sound Settings is available by right clicking speaker icon at top right.

BTW, why did you install amd-legacy drivers?

---

### Post by 0N3 on 2013-04-26
There is no HDMI option in sound settings. I had an awful time with the drivers available in the repos and the opensource driver my fan won't stop spinning constantly even if left idle for more then an hour. Laptop becomes a little discomforting to use after 10 mins of the noise of the fan. I did take the laptop aprt and clean the fan there was hardly any dust in it. It does stop spinning when using the closed source drivers from AMD.

---

### Post by DuckHook on 2013-04-26
Yes, radeon driver is not known for efficient power management. However, next steps may not work with amd-legacy, so I must keep your expectations low. Please post results of:```
aplay -l
```

---

### Post by 0N3 on 2013-04-26
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Whats the difference between the drivers offered via Software & Updates > Additional Drivers and the AMD legacy drivers?  (Neither would give me sound)
Im trying the legacy to see if they would work is all.

---

### Post by DuckHook on 2013-04-26
There it is. HDMI is card 1, device 3. OS recognizes it. Just a matter of piping audio output to this device.

We could start monkeying around with config files, but I would like you to try the simplest measures first. Is there a BIOS setting in your MB to disable onboard audio? Sometimes, doing so will force OS to go to remaining sound HW which is your HDMI. If that doesn't work then will try other things.

Re: different drivers.

All proprietary drivers are problematic in that they aren't supported by the Linux community: you have only one source of support and that's the card vendor. If they drop support for certain cards (due to kernel or Xorg upgrades), as they frequently have, then it's just too-bad-so-sad.

The newer drivers are designed for the newer cards, and the legacy driver for ancient cards. It was my understanding that the problem with the legacy driver is that it won't work with the newest version of Xorg, but you've managed to get it working with 13.04 so my info is clearly wrong. In any case, newer drivers presumably have bug fixes and better features, but this is not always the case, and anyways, since they are proprietary, there is often no way to tell if a newer driver (which tends to push GPU envelope) is not, in fact less stable. Since it is working for you let's try sticking with it for now.

BTW, as my signature line reminds: if you haven't already done so, back up all important data before monkeying with graphics drivers. A bad install could leave you with no access to your computer.

---

### Post by 0N3 on 2013-04-27
I have uninstalled and purged the legacy driver and installed the driver via Software Updates > Additional Drivers do you want the outputs of the above commands again?

---

### Post by DuckHook on 2013-04-27
Yes. please. But only after rebooting, to let driver take effect. Also, did you try disabling motherboard sound chip in BIOS?

---

### Post by 0N3 on 2013-04-27
Nothing in the BIOS to disable it unfotunately :(

First Output: [COLOR=#000000][FONT=Ubuntu Mono]lspci -vk | egrep -iA13 "vga|audio"[/FONT][/COLOR]

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at c1210000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c1100000-c11fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
--
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT [Radeon HD 7670M] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device fb22
	Flags: bus master, fast devsel, latency 0, IRQ 55
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at c0040000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci


01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c0020000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


07:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c1100000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: alx



Second Output: [COLOR=#000000][FONT=Ubuntu Mono]aplay -l

[/FONT][/COLOR]**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by DuckHook on 2013-04-27
Just a posting tip... wrap output in code tags to make it easier to read. Just highlight the output (one for each command) and use hash tag at top of reply box to format it. You can also use the following syntax (CODE)output(/CODE) where the round brackets are replaced by square ones. Output will be much easier to read. I provide an example of the result below.

1. Next step is to install *Pulseaudio Volume Control* to see if it can see and set the proper output. In a terminal, do:```
sudo apt-get install pavucontrol
```2. Then open dash, type "pulse" and select the app: *Pulseaudio Volume Control*.
3. Select *Output Devices* tab. Do you see two devices there and is HDMI audio one of them? (You must make sure that the "Show" field at bottom is set to "All Output Devices".) If so, click the green check mark which "selects as fallback". You may have to unlock it with password first.
4. Make sure HDMI is not muted (little speaker button) and volume controls are not set at "silence", but at a volume you can hear.
5. Make sure that HDMI is selected in the "Port:" field.
6. Test sound by playing something.

---

### Post by 0N3 on 2013-04-27
Had that installed I tried it to no avail it is only showing my speakers under all output devices :(

---

### Post by 0N3 on 2013-04-27
Here's a screenshot ...

---

### Post by 0N3 on 2013-04-27
I don't know if this helps anyway but here's screenshot of alsamixer.

---

### Post by DuckHook on 2013-04-27
In that case, it gets harder and more and more out of my league. Do:```
aplay -L
```note: it's a capital "L" this time. This lists the modes for both of your cards. Post back output.

---

### Post by 0N3 on 2013-04-27
Output of aplay -L

```
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC269VB Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions

```

---

### Post by DuckHook on 2013-04-27
Let's do a speaker test with:```
speaker-test -c 2 -r 48000 -D hw:1,3
```Make sure you have speakers attached to your HDMI interface and they are not muted. This should generate irritating pink noise (static). <Ctrl>+<c> will stop the test.

<edit>
note semicolon changed to colon
</edit>

---

### Post by 0N3 on 2013-04-27
I have to pop out now for work I will post back in a few hours with the result thanks for your time and effort much appreciated

---

### Post by DuckHook on 2013-04-27
> **0N3 said:**
> I have to pop out now for work I will post back in a few hours with the result thanks for your time and effort much appreciated

...and I need to shut down for the night to get some beauty rest. Have early morning appointment and will try to look in again tomorrow aft (N/A time). Hang in there and hopefully, we will get problem solved.

---

### Post by 0N3 on 2013-04-27
Here's the output of 
```
[COLOR=#000000][FONT=Ubuntu Mono]
speaker-test -c 2 -r 48000 -D hw:1,3[/FONT][/COLOR]
```

```
speaker-test 1.0.25


Playback device is hw:1,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -19,No such device



```

---

### Post by 0N3 on 2013-04-27
Solved!! The problem was ALSA had to go install ALSA Daily builds and reboot and bingo it worked

```
[https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)

Downloaded the [oem-audio-hda-daily-dkms_0.201304261252~raring1_all.de]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201304261252~raring1_all.deb")b
```

---

### Post by DuckHook on 2013-04-27
Good for you! Glad you got it working. Hopefully, Ubuntu will have the newest Alsa build incorporated into their distros soon.

---

### Post by eddiejames on 2013-04-28
Thank You for the hdmi audio info. works great on my sapphire 5450 card.. now if I could only get 3d acceleration.. looking to change back to ubuntu from linux mint

---

### Post by 0N3 on 2013-04-28
Hi Eddiejames glad it helped you.

This tutorial installs the latest AMD catalyst driver its a script gives you the option to install hardware acceleration.

[http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)

---

### Post by rob4Christ on 2013-05-11
Thanks guys!   Alsa update did the trick..

---

### Post by mfcardio on 2013-09-29
> **0N3 said:**
> Solved!! The problem was ALSA had to go install ALSA Daily builds and reboot and bingo it worked

```
[https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)

Downloaded the [oem-audio-hda-daily-dkms_0.201304261252~raring1_all.de]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201304261252~raring1_all.deb")b
```



I can't install the ALSA, when I try it asks me to  insert Ringtail DVD. What is that. Thanks for the help

---

### Post by mcongom on 2013-12-01
Hi everybody!! I had the same problem, tried all the solutions above, but still no sound. Can anybody help me? Thanks a lot!

---

### Post by emperorofnight on 2013-12-02
Hello, I'm having the same problem alsa is installed, alsa mixer shows the spdif unmuted, PulseAudio detected and configured my HDMI sound out and shows the animated vu bars when playing something but still can't hear a thing. Any ideas?

---

### Post by verymadpip on 2013-12-02
> **mfcardio said:**
> I can't install the ALSA, when I try it asks me to  insert Ringtail DVD. What is that. Thanks for the help

Look at your software sources & uncheck the CD rom option.

---

