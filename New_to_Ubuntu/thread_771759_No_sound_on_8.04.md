---
title: "No sound on 8.04"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-04-27
Well it seems that some times I have sound and then other times I don't. My sound isn't on mute. My speakers are on. To get sound back I got to restart my computer and it is back then some times it just goes away again. I am using an old dell with their sound card and speakers, nothing fancy. I know it isn't my speakers or computer since it worked fine on 7.10

Does anyone know what the problem is and how I can get sound to work all the time?

---

### Post by riven0 on 2008-04-27
The next time you have this problem, try this command: **sudo /etc/init.d/alsa-utils restart**

If it comes back after that, it's possible there is something interfering with your sound device.

---

### Post by 1scorpio on 2008-04-27
> **riven0 said:**
> The next time you have this problem, try this command: **sudo /etc/init.d/alsa-utils restart**

If it comes back after that, it's possible there is something interfering with your sound device.
same problem diff machine. what will this command do

---

### Post by riven0 on 2008-04-27
> **1scorpio said:**
> same problem diff machine. what will this command do

It restarts the alsa sound device. If there is a conflict with another program, it may need a restart. It's a start, but I have a feeling you may have a different problem. Also, you may want to post the output of this command to determine your sound card: **lspci -v**

---

### Post by ImThatNerd on 2008-04-28
> **riven0 said:**
> It restarts the alsa sound device. If there is a conflict with another program, it may need a restart. It's a start, but I have a feeling you may have a different problem. Also, you may want to post the output of this command to determine your sound card: **lspci -v**

Here I did this:

```
ryan@ryan-desktop:~$ sudo /etc/init.d/alsa-utils restart
[sudo] password for ryan: 
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
ryan@ryan-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
	Subsystem: Dell Unknown device 0127
	Flags: bus master, fast devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 0127
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0127
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0127
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0127
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0127
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at ffa00800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ff800000-ff9fffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 0127
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: Dell Unknown device 0127
	Flags: medium devsel, IRQ 11
	I/O ports at dc80 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Dell Unknown device 0127
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d800 [size=256]
	I/O ports at dc40 [size=64]
	Memory at ffa00400 (32-bit, non-prefetchable) [size=512]
	Memory at ffa00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:08.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02) (prog-if 00 [Generic])
	Subsystem: Dell Unknown device 0001
	Flags: bus master, fast devsel, latency 64, IRQ 16
	Memory at ff8ff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecf0 [size=16]
	Capabilities: <access denied>

ryan@ryan-desktop:~$ 


```

I noticed I didn't have sound again so I tried to bring up terminal and the window showed up but it didn't load. I tried bringing up other apps like preferred applications and the window popped up but nothing else loaded. Then both the top and bottom bars froze and I couldn't click anything so I had to restart. Anyways when I got back on I did what I said above. Going to see how long sound lasts. :mad:

P.S. What does that mean in your sig? Just incase someone tells me to do it I know not to and I know what will happen.

---

### Post by riven0 on 2008-04-28
> **ImThatNerd said:**
> Here I did this:

I noticed I didn't have sound again so I tried to bring up terminal and the window showed up but it didn't load. I tried bringing up other apps like preferred applications and the window popped up but nothing else loaded. Then both the top and bottom bars froze and I couldn't click anything so I had to restart. Anyways when I got back on I did what I said above. Going to see how long sound lasts. :mad:

P.S. What does that mean in your sig? Just incase someone tells me to do it I know not to and I know what will happen.

Sounds like you may have more problems than just the sound. If you're running Compiz, it may help to disable that. 

It looks like your card is the generic Intel AC 97 card. So see if Alsa is recognizing your soundcard. What is the card and chip model listed when you do: **sudo alsamixer** ? Also, it's a good idea to make sure the sound is not disabled in BIOS, as that is generally the most common sound problem.


As for the warning in my sig; there has been some malicious people going around telling people to: sudo rm -rf / which basically means:

sudo = administrator privileges

rm = remove

-rf = recursively and forcefully, without warning

/ = the entire operating system. 

Also, it's generally not a good idea to forcefully remove anything, unless it's something in your home directory.

---

### Post by Bodsda on 2008-04-28
alsa probably isnt the issue due to pulseaudio being the default sound device for hardy iirc

the problem could be onbaord sound interfering with sound card. i would suggest running this

```
asoundconf list
```

this will show all sound cards, if there is more then 1 work out which one is your onboard and which one is sound card by using 

```
lspci
```

then 

```
asoundconf set-default-card 'type the result of your card from first command here'
```

---

