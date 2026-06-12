---
title: "Sound Gone In Update"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-10-15
I just did the new update and it totaly screwed my graphics and sound up. I fixed the graphics using envyng but I have no idea how to get my sound back . It just tells me I have no devices to control. I remember this happening before but I can not remember how to fix it. Please help.

---

### Post by dustint83 on 2008-10-15
thats one thing i cant stand about linux, you really have to be careful what you update otherwise you will overwrite your settings and end up reinstalling the entire OS in the long run. maybe not these people thats been using linux for 20 years, but for the common user updating always causes more problems than it fixes

i had this problem happen to me about 2 weeks ago, lost sound and i even had my pulseaudio files backed up incase something went wrong, restoring them didnt do a thing. wasnt worth the headache so i reinstalled the OS and turned automatic updates OFF!

make sure you read through the updates instead of just installing them as they appear, if you dont NEED it, dont install it

---

### Post by bobnutfield on 2008-10-15
> **DarkSaga70 said:**
> I just did the new update and it totaly screwed my graphics and sound up. I fixed the graphics using envyng but I have no idea how to get my sound back . It just tells me I have no devices to control. I remember this happening before but I can not remember how to fix it. Please help.

Open a terminal and type:

```
lspci | grep Audio
```

This is just to see how the system is recognizing your card.

---

### Post by DarkSaga70 on 2008-10-15
I don't know why they do it the way they do but either way it needs fixed and I know I do not have to redo the whole OS to fix this.

---

### Post by DarkSaga70 on 2008-10-15
riddle@darksaga:~$ lspci | grep Audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
riddle@darksaga:~$ 
 
This is what i get

---

### Post by bobnutfield on 2008-10-15
OK, so you do have a recognizable sound card.  It may not work, but try this:

> sudo /etc/init.d/alsa-utils reset

---

### Post by DarkSaga70 on 2008-10-15
NOpe that didn't do it. Damn I hate this

---

### Post by bobnutfield on 2008-10-15
Type:

> aplay -l

See if your soundcard comes up.

---

### Post by DarkSaga70 on 2008-10-15
i get this


aplay: device_list:205: no soundcards found...
riddle@darksaga:~$

---

### Post by bobnutfield on 2008-10-15
OK, looks like the update did not pick up the modules necessary for your sound card.  Was this update an update to the new 2.6.24-21 keernel?  If it was, then try this:

> find /lib/modules/`uname -r` | grep snd

If it returns no results, then try this.

> sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic

If there are any missing modules, this will get them.  You must reboot after running this.

---

### Post by DarkSaga70 on 2008-10-15
You Sir are king of The Beans!!!! Thank you so much!!!

---

### Post by bobnutfield on 2008-10-15
My pleasure, glad you got it working. You might want to make note of this fix in case a future update gives you the same trouble.  Just in case, you will want to know your sound module is snd_via82xx.

---

### Post by carofiro on 2008-10-15
I did all those things and did not have any modules to be added, however my sound still does not work.  When I use

carolyn@dell-desktop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
that is what I get

 but 

carolyn@dell-desktop:~$ aplay -l
aplay: device_list:205: no soundcards found...

and trying to install other modules shows the whole library, then when I try to install missing modules it says it is installing 0 packages etc etc.

How am I supposed to know that an update is needed or not?  When I got my computer it had over 800 I was supposed to install.  These were just updating kernels and had very little description on them.

---

### Post by bobnutfield on 2008-10-15
> **carofiro said:**
> I did all those things and did not have any modules to be added, however my sound still does not work.  When I use

carolyn@dell-desktop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
that is what I get

 but 

carolyn@dell-desktop:~$ aplay -l
aplay: device_list:205: no soundcards found...

and trying to install other modules shows the whole library, then when I try to install missing modules it says it is installing 0 packages etc etc.



How am I supposed to know that an update is needed or not?  When I got my computer it had over 800 I was supposed to install.  These were just updating kernels and had very little description on them.

Your problem may be different.  Open a terminal and confirm that the sound modules are indeed loaded:

> sudo lsmod

Look for modules that begin with snd

---

### Post by carofiro on 2008-10-15
I have several that start with snd:

snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
button                  9232  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                      6916  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
evdev                  13056  9 
snd_page_alloc         11400  1 snd_pcm


I think that is most of them... there were many more but these are the ones starting with snd

---

### Post by bobnutfield on 2008-10-15
OK, well I believe (could be wrong) that your sound card uses the snd-hda-intel module.  If you have not yet tried it, open a terminal and type:

> sudo modprobe snd-hda-intel

as I do not see it in your listing (though it might be there, just not posted)

> alsamixer

This will look a little like an equalizer.  Make sure that none of the channels are muted, particularly Master and PCM.  You navigate with the arrow keys, and mute and unmute with the space bar.

Then, go to System>Preferences>Sound and make sure your sound device is shown in the box toward the bottom.

---

### Post by carofiro on 2008-10-15
I get this warning :

carolyn@dell-desktop:~$ sudo modprobe snd-hda-intel 
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.24-21-generic/updates/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-21-generic/updates/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

This is so weird, is there a way to revert to what I had before the updates?

---

### Post by bobnutfield on 2008-10-15
Post the results of:

> lspci -v

I want to double check what module your sound card uses.

---

### Post by carofiro on 2008-10-15
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at eff8 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, fast devsel, latency 0
	Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: fe700000-fe7fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe400000-fe6fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: fe300000-fe3fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=32]
	Memory at fe9fb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 022f
	Flags: medium devsel, IRQ 10
	Memory at fe9fb700 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]

02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fe3ff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at fe3ff500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at fe3ff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at fe3ff700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at de00 [size=256]
	Capabilities: <access denied>

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at fe7ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by bobnutfield on 2008-10-15
Well, I was correct, that card uses the snd-hda-intel module.  Just one more, just to make sure it is loaded:

> sudo lsmod | grep snd_hda_intel

Type it just as it looks, or copy and paste.  If it comes up that it is loaded correctly, you may have to uninstall and reinstall Alsa.

---

### Post by carofiro on 2008-10-15
carolyn@dell-desktop:~$ sudo lsmod | grep snd_hda_intel
carolyn@dell-desktop:~$ 


thats all that happens.  Nothing.

---

### Post by bobnutfield on 2008-10-15
What does alsamixer show you?

> alsamixer

Do you have any devices shown in System>Preferences>Sound?

---

### Post by carofiro on 2008-10-15
alsamixer: function snd_ctl_open failed for default: No such file or directory
carolyn@dell-desktop:~$ 


Didn't work either.  I checked my synaptic package manager for alsa and there are plenty of source and driver packages that aren't installed.

---

### Post by bobnutfield on 2008-10-15
OK, that is what I thought, just wanted to be sure.  I believe it is safe to say you will need to reinstall alsa.  You would do it this way:

> sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

This will uninstall and reinstall, all in the same command.  You will need to reboot afterward to get the modules loaded.  This recommendations comes from the community sound troubleshooting guide.  I believe this will fix it for you.

---

### Post by ChildOfMana on 2008-10-15
Looks like bobnutfield is on his way (hopefully) to helping you find a permanent solution to your problem.

However, as a *temporary* measure you could try loading an earlier kernel (say, 2.6.24-19). This can be achieved by selecting it from your GRUB menu at boot (or pressing *Esc* when GRUB loads if you have your menu set to hidden).

If your lack of sound is due to a problem with the latest kernel version then this should do the trick for now... at least until you find a permanent solution.

---

### Post by Lorelei- on 2008-10-15
> **bobnutfield said:**
> OK, that is what I thought, just wanted to be sure.  I believe it is safe to say you will need to reinstall alsa.  You would do it this way:



This will uninstall and reinstall, all in the same command.  You will need to reboot afterward to get the modules loaded.  This recommendations comes from the community sound troubleshooting guide.  I believe this will fix it for you.

I'm having the same problem and have tried all the fixes suggested here with no luck.

Any other ideas? For now I may just go back to the previous kernel as its starting to seriously get on my nerves that none of the fixes seem to make any dent into the problem >.<

---

### Post by bobnutfield on 2008-10-15
> **Lorelei- said:**
> I'm having the same problem and have tried all the fixes suggested here with no luck.

Any other ideas? For now I may just go back to the previous kernel as its starting to seriously get on my nerves that none of the fixes seem to make any dent into the problem >.<

There seem to be a lot of people who have experienced the loss of sound after this upgraded kernel.  But, I am afraid that what I have suggested in these posts is the sum total of the fixes that I know.  They have worked for me many times in the past.  Hopefully, someone else will chime in who may have more knowledge.

---

### Post by Lorelei- on 2008-10-15
> **bobnutfield said:**
> There seem to be a lot of people who have experienced the loss of sound after this upgraded kernel.  But, I am afraid that what I have suggested in these posts is the sum total of the fixes that I know.  They have worked for me many times in the past.  Hopefully, someone else will chime in who may have more knowledge.

Thank you for the suggestions, they at least gave me something to try.

For those who are interested, this is a current bug on Launchpad so perhaps direct ideas for fixes there?

---

### Post by bobnutfield on 2008-10-15
> **Lorelei- said:**
> Thank you for the suggestions, they at least gave me something to try.

For those who are interested, this is a current bug on Launchpad so perhaps direct ideas for fixes there?

I have Hardy on my desktop, but I run Intrepid on my laptop.  I didn't have the issue, but I did not know about the bug.  That would certainly explain why so many have had sound issues.

---

### Post by carofiro on 2008-10-15
I uninstalled alsa and reinstalled just like you said, and I rebooted and it still doesn't work.  I could go with the temporary fix for now and wait for an update that could fix the bug.  It's not a terrible emergency to get it fixed so if its a new bug I can wait for a solution.

---

### Post by carofiro on 2008-10-15
Also thank you so much for your help anyway, Bob!  I really appreciate it.  I am pretty new to linux so even fixes that don't work teach me a lot about my computer :)

---

### Post by Lorelei- on 2008-10-15
> **bobnutfield said:**
> I have Hardy on my desktop, but I run Intrepid on my laptop.  I didn't have the issue, but I did not know about the bug.  That would certainly explain why so many have had sound issues.

bug appears to be new-ish. I was going to submit one myself given that I'd seen 3 people on here with the same problem as me plus at least another 2 on #ubuntu but someone had beaten me to it. Heh.

---

### Post by Lorelei- on 2008-10-15
> **carofiro said:**
> Also thank you so much for your help anyway, Bob!  I really appreciate it.  I am pretty new to linux so even fixes that don't work teach me a lot about my computer :)

I ditto this. I'm also a newbie, so things like this help me learn.

---

### Post by bobnutfield on 2008-10-15
Well, if the previous poster is correct and it is indeed a bug that others are suffering from, it will be fixed soon.  In the meantime, you can use the previous kernel and sound should work just fine from that.

---

### Post by Lorelei- on 2008-10-15
previous kernel works just fine. and there's a post I started with how to boot from it and set it as default for the moment. 

fingers crossed that the bug gets solved soon! from the looks of the update & install support category, its a fairly widespread bug too affecting both sound & graphics.

---

### Post by Andy Moon on 2008-10-18
Hello,

Im using an Inspiron 1525 laptop, and same audio device as carofiro : Intel Corporation 82801H (ICH8 Family)

Reinstalling the audio driver fixed my problem. [The procedure is explained on dell unbuntu wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade"), as I wrote in this post :

> **Andy Moon said:**
> 
Here's a summary of how it worked in my case, if that can help others :

_Computer : _
Inspirion 1525
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

_OS :_
Ubuntu Hardy 8.04
Kernel Linux 2.6.24-19-generic UPGRADED TO 2.6.24-21-generic => that's when I encountered the sound problem
[U]
The problem[/U]

After I upgraded to kernel 2.4.24-21, I had no sound anymore. Some symptoms :
there was a red warning flag on my sound icon tray
no driver found by ubuntu, as revealed by the shell command 
"aplay -l" (result was something like :  device_list:221: no soundcard found...)


_What solved my problem_

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

Quotes from that page :
```
Description: No sound after upgrade from Ubuntu 7.10 or upgrade to kernel 2.4.24-17
Systems Affected: Inspiron E1505n, 1420n and 1525n.
```
=>this procedure also fixes the problem after upgrade to kernel 2.4.24.-21


Follow the instructions given in the second part, titled _"If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic"_. 

Shall fix it for you too ;)

Cheers,

Andy

---

### Post by carofiro on 2008-10-26
Sorry this is delayed for the thanks, but it worked great!  I should know better to also check out my laptop specific problems (I have the exact same computer) on Dell as well.

---

