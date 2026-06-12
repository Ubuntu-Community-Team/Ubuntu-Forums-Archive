---
title: "Generic Desktop PC and can't get the speakers to work"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by PureRicanGringo on 2008-09-04
I have tried both usb speakers and standard stereo jack speakers. Is there a typical reason for this not to work?

---

### Post by shad0w_walker on 2008-09-04
How are you testing the speakers?

---

### Post by PureRicanGringo on 2008-09-04
> **shad0w_walker said:**
> How are you testing the speakers?

I have tried different websites that have audio. Honestly I had not put a whole lot of thought into how to test now that you mention it. What do you suggest?

---

### Post by halitech on 2008-09-04
open a terminal and post the info back here from```
aplay -l
```

---

### Post by shad0w_walker on 2008-09-04
It is entirely possible that the audio on the websites is coming from flash (I assume one of the sites would be youtube?) and that may well be the issue instead of the speakers. If you don't mind an annoying tone, you can try out the speakers by doing this:

Goto System > Preferences > Sound

Select the Test button for the first drop down selection.

If it's working it should produce a constant tone.

---

### Post by PureRicanGringo on 2008-09-04
> **halitech said:**
> open a terminal and post the info back here from```
aplay -l
```

So, does this mean that there is no card or that the system doesn't see the one that is there?

> aplay: device_list:205: no soundcards found...


---

### Post by halitech on 2008-09-04
that means the system doesn't have a suitable module lodaed to make your sound card work. Still in the terminal, post the output of```
lspci
```

---

### Post by PureRicanGringo on 2008-09-04
> **shad0w_walker said:**
> It is entirely possible that the audio on the websites is coming from flash (I assume one of the sites would be youtube?) and that may well be the issue instead of the speakers. If you don't mind an annoying tone, you can try out the speakers by doing this:

Goto System > Preferences > Sound

Select the Test button for the first drop down selection.

If it's working it should produce a constant tone.

I am posting a screenshot with the error that came up when I tried the test.

---

### Post by PureRicanGringo on 2008-09-04
> **halitech said:**
> that means the system doesn't have a suitable module lodaed to make your sound card work. Still in the terminal, post the output of```
lspci
```

Here are the results:

> lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


Thanks again.

---

### Post by halitech on 2008-09-04
that came up because you don't have any sound card working in the system

from this thread (post 4) [http://ubuntuforums.org/showthread.php?t=662393](http://ubuntuforums.org/showthread.php?t=662393)

```
sudo apt-get install linux-backports-modules
```
```
depmod -a
```
```
modprobe snd-hda-intel
```

---

### Post by PureRicanGringo on 2008-09-04
> **halitech said:**
> that came up because you don't have any sound card working in the system

from this thread (post 4) [http://ubuntuforums.org/showthread.php?t=662393](http://ubuntuforums.org/showthread.php?t=662393)

```
sudo apt-get install linux-backports-modules
```
```
depmod -a
```
```
modprobe snd-hda-intel
```

I get to here with the process:

> bigdog@BigDog-Ubuntu-desktop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.24-21-rt/modules.dep.temp for writing: Permission denied


Where did I go wrong?

---

### Post by HunterA3 on 2008-09-04
Try performing the same instructions as superuser.

sudo <command>
(supply your root password and hit Enter)

It should then perform the command, unless the system is currently using it for what ever reason.

---

### Post by halitech on 2008-09-04
> **PureRicanGringo said:**
> I get to here with the process:



Where did I go wrong?

sorry, probably need to do both of those last 2 commands as sudo

---

### Post by PureRicanGringo on 2008-09-04
> **HunterA3 said:**
> Try performing the same instructions as superuser.

sudo <command>
(supply your root password and hit Enter)

It should then perform the command, unless the system is currently using it for what ever reason.


I feel like I am getting closer:


> bigdog@BigDog-Ubuntu-desktop:~$ sudo depmod -a
[sudo] password for bigdog: 
bigdog@BigDog-Ubuntu-desktop:~$ modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.
bigdog@BigDog-Ubuntu-desktop:~$ sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.


---

### Post by halitech on 2008-09-04
strange...

okay, some are saying that procedure works, others are saying they had to recompile alsa

[https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560)

maybe just go into Synaptic and remove alsa, reboot then readd it with work before trying the other steps in the link

hopefully it will help

---

### Post by PureRicanGringo on 2008-09-04
> **halitech said:**
> strange...

okay, some are saying that procedure works, others are saying they had to recompile alsa

[https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560)

maybe just go into Synaptic and remove alsa, reboot then readd it with work before trying the other steps in the link

hopefully it will help

I do not know much about the provenance of this computer. How likely is it that there actually is no sound card present?

---

### Post by halitech on 2008-09-04
if you have jacks on the back of the computer I would say you have a sound card. Something I just thought of though, if the sound is built into the motherboard (which I think it is) then I wonder if its been disabled in the BIOS

---

### Post by PureRicanGringo on 2008-09-04
> **halitech said:**
> if you have jacks on the back of the computer I would say you have a sound card. Something I just thought of though, if the sound is built into the motherboard (which I think it is) then I wonder if its been disabled in the BIOS

There are indeed jacks for speakers and microphones back there. I am going to attempt to remove alsa, reboot, and put it back to see if that works.

---

### Post by halitech on 2008-09-04
good luck and let us know how it goes

---

### Post by HunterA3 on 2008-09-04
Not sure how new your motherboard is, but if there isn't an option in BIOS to enable onboard sound, look for a two pin jumper on the board itself that disables the sound and move it to the other set of jumpers.

---

### Post by PureRicanGringo on 2008-10-10
Nothing I have tried has worked. This is pretty frustrating.

---

