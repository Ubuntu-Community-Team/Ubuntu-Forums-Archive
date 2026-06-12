---
title: "Screen Flickering"
date: 2017-04-24
forum: New to Ubuntu
---

### Post by anon24 on 2017-04-24
I have used Ubuntu for a while now. I have never experienced this until now. I reinstalled Ubuntu and I experience flickering. Sometimes it's worse than others. However, when I'm running WIndows, I don't experience this problem. I have an MSI GS70 2QE. Any help would be greatly appreciated.

edit: I might add that it stopped flickering for now. I'm not sure what's going on.

---

### Post by ajgreeny on 2017-04-24
What graphics card and driver do you have?
Let's see the output of **lspci -k** in terminal.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by anon24 on 2017-04-24
I have an NVIDIA GM204M [GeForce GTX 970M] and I'm using the current Nouveau driver.
```
superuser@computer:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
    Kernel modules: ie31200_edac
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Micro-Star International Co., Ltd. [MSI] 4th Gen Core Processor Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family USB xHCI
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family MEI Controller
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family USB EHCI
    Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset High Definition Audio Controller
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family USB EHCI
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] HM87 Express LPC Controller
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family SMBus Controller
    Kernel modules: i2c_i801
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] GM204M [GeForce GTX 970M]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5249 PCI Express Card Reader (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTS5249 PCI Express Card Reader
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
04:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E220x Gigabit Ethernet Controller
    Kernel driver in use: alx
    Kernel modules: alx
05:00.0 Network controller: Intel Corporation Wireless 7265 (rev 3b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
```

---

### Post by QIII on 2017-04-24
Could you describe what you mean by "flickering"?  Occasional black?  Occasional white?  Washout?  Dimming?

---

### Post by anon24 on 2017-04-24
No black screen, no white screen. It's like a quick dimming in and out. It's more noticeable in darker colors.

---

### Post by QIII on 2017-04-24
Is it occasional or steady and fairly fast?

---

### Post by anon24 on 2017-04-24
It's not all of the time... it will go away sometimes. I tried to jostle the screen around to see if it was a mechanical issue and didn't find that to be the case. It seems to happen randomly.

---

### Post by yetimon_64 on 2017-04-24
> **anon24 said:**
> I have an NVIDIA GM204M [GeForce GTX 970M] and I'm using the current Nouveau driver...
I am on hardware here with an NVIDIA GM107M  [GeForce GTX 850M] controller and an intel onboard (i915) VGA set up.
I have always found the Nouveau driver unusable, with screen distortion and occasionally flickering etc, on this particular hardware setup. I got rid of the problem by installing the nvidia recommended driver in the "Additional Drivers" utility.

My suggestion would be to open dash and search for "Additional Drivers" and check if your installation has any proprietary drivers available for your hardware. You only need to tick the "recommended driver" there (if one is available) and it will download and install it for you. You may need to restart the installation for the new driver to take effect. It certainly fixed some strange effects here, hope it helps you. Regards, yeti.

---

### Post by anon24 on 2017-04-24
I'm going to give that a try, though, when using Ubuntu before... I had tearing issues with the proprietary driver and Nouveau was more stable. we'll see what happens.

---

### Post by yetimon_64 on 2017-04-24
> **anon24 said:**
> I'm going to give that a try, though, when using Ubuntu before... I had tearing issues with the proprietary driver and Nouveau was more stable. we'll see what happens.

I also used to see the screen tearing on older ubuntu systems with the nvidia drivers and had to adjust "sync to vblank" settings, in compiz and the proprietary driver, in the past to lessen the problem. Nowadays it seems both compiz and the nvidia drivers set it up by default much better, definitely worth re-trying nowadays for you in my opinion. 
Good luck, yeti.

---

### Post by anon24 on 2017-04-24
I mean, it was like a month or so ago that I was having these issues. Unfortunately, the proprietary driver didn't fix the issue. :(

edit: issue is about the same. It was flickering when starting up and has now stopped for the time being, though I expect it to start again kind of like before.

Also, I see the tearing that I was speaking of before. It is an Optimus laptop.

edit: I want to say, thanks for everyone's input so far! I really appreciate your willingness to help. I hope to figure out what is causing this issue, as it's pretty annoying. I just installed bumblebee, I haven't tested it out to see if I get tearing still, but it is certainly helping my battery life to use the intel graphics for general use.

---

### Post by anon24 on 2017-04-25
I literally just got this laptop back in the mail from MSI. I have until May 7th until my warranty is up. This is kind of a dire situation. I need to know if it's possible that this is a software issue because if it's a hardware issue. I have to send it off again right away.

Another way symptom is occasionally seeing ghosts of windows that I minimize on the desktop. It doesn't last forever, it goes away just like the flickering. Again, I would think that if it were a hardware issue that it would be affected by opening and closing the lid of the laptop. This doesn't affect it at all, as I tried doing that during flickering and also when it isn't flickering to see if there was any change.

---

### Post by anon24 on 2017-04-26
I've noticed something new. When I'm either typing or moving the mouse, the weird dimming / flickering stops. I'm not sure what that means. I tried to use a screen recorder to see if it would capture this to no avail.

I also noticed that the flickering stop when listening to the music or watch videos.

edit: I take that back, it doesn't stop with music playing. However, the mouse movements and typing definitely do stop the flickering.

---

### Post by anon24 on 2017-04-28
Update, I sent my computer back to MSI to check if this is caused by the graphics card or the LCD. We will see if they figure it out. It seems to me that it has to be one of those things because this issue occurred under both open and closed source drivers. Also, I noticed it in the BIOS screen just before sending it out.

---

### Post by anon24 on 2017-12-28
It's been a long time. I did send my computer back to check this. They replaced the graphics card at no charge. Ubuntu still has this blinking issue. Any ideas on what might be causing this?

---

### Post by cressrt2 on 2017-12-29
You don't say what version you are running, I am on Ubuntu 17.10 and had flickering, I changed from using Wayland to XOrg and this seemed to solve it.

---

### Post by Geoffrey_Arndt on 2017-12-30
Does this seem related to the Browser you're using?  If so,  I see this sometimes for certain web pages on Chrome or Chromium.    I haven't seen it yet to view the same web pages in Firefox.

---

