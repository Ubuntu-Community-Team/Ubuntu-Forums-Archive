---
title: "Why does xfwm produce video tearing?"
date: 2016-10-10
forum: Programming Talk
---

### Post by Pablo_San_Martn on 2016-10-10
I'd like to start this post saying I'm not a programmer, but regard myself as a fairly competent Linux user at this point.

I migrated from Unity and LXDE to Xfce this year (on two different laptops) and I love it, especially all the new features available since 16.04!

I've read a couple of articles and threads discussing how to "fix" the video tearing created by the native Xfce compositor. So far the only working solution seems to be to turn it off and install Compton, losing thereby many aspects of its integration with the desktop environment as a whole.

If possible, I would like to understand in simple terms why xfwm produces video tearing. Xfce is a pretty solid DE overall, but this seems to be an issue that has been going on for some years. Maybe programmers themselves do not understand why it happens? Or they can't fix it keeping with the lightweight requirements of Xfce?

---

### Post by T.J. on 2016-10-13
The cause for the tearing effect is because of two reasons.  Some commercial drivers, such as Nvidia's do not set vsync by default.  The second reason is that XFCE does not use OpenGL vsync by default; rather it uses XRender - which is more compatible with older cards.  Your best option if you chose not to use an OpenGL compositor like Compton is to enable vsync in your video driver.  In the case of Nvidia, you will have to enable full composition pipelining in order to get it to work.

If it helps, full OpenGL vsync is a planned feature for the next release of XFCE.  Drop me a post if you need specifics.

---

### Post by vasa1 on 2016-10-13
> **T.J. said:**
> ... Drop me a post if you need specifics.

:confused:

Or just continue right in this thread?

---

### Post by Pablo_San_Martn on 2016-10-14
Thank you very much for your answer, T.J.! 

So xfwm still uses XRender then. I currently have an Intel integrated graphics card and an AMD, but am planning to buy a laptop with an Nvdia card soon. Is vsync the option named "Synchronize drawing to the vertical blank" in Window Manager Tweaks?

And it's great to know that Xfce 4.14 will migrate to OpenGL :D

---

### Post by T.J. on 2016-10-15
> **Pablo_San_Martn said:**
> Thank you very much for your answer, T.J.! 

So xfwm still uses XRender then. I currently have an Intel integrated graphics card and an AMD, but am planning to buy a laptop with an Nvdia card soon. Is vsync the option named "Synchronize drawing to the vertical blank" in Window Manager Tweaks?

And it's great to know that Xfce 4.14 will migrate to OpenGL :D

You're very welcome. 

Yes, you should be able to get a basic vsync by "Synchronize drawing to the vertical blank".  It will still be XRender and not actually OpenGL but it should provide reasonable results.  Depending on the quality of your primary driver, you may experience some issues with tearing when streaming video. I'd be happy to help you configure Compton to overcome these issues and give you full OpenGL vsync.  In order to do that I would need to know what video card X11 is actually using or if it is using both.

The feature is planned for XFCE 4.14, but there are no promises that I am aware of that it will actually arrive.

---

### Post by Pablo_San_Martn on 2016-10-18
> **T.J. said:**
>  In order to do that I would need to know what video card X11 is actually using or if it is using both. 

I have two laptops actually, a Toshiba with AMD and a Dell with Intel. 

Does Compton support transparency while resizing and moving windows? And inactive dim? For me the main drawback is the loss of the window thumbnails when switching with Alt+Tab. Is there any way around that?

Thanks again.

---

### Post by T.J. on 2016-10-18
> **Pablo_San_Martn said:**
> I have two laptops actually, a Toshiba with AMD and a Dell with Intel. 

Does Compton support transparency while resizing and moving windows? And inactive dim? For me the main drawback is the loss of the window thumbnails when switching with Alt+Tab. Is there any way around that?

Thanks again.

I believe some of those options are possible if you create and edit  a personal .compton.conf file in your home directory.  As to thumbnails, I am not sure.   I find most of the eyecandy less than useful.  I have a personal config file: 

```
# Shadow
shadow = true;
no-dnd-shadow = true;
no-dock-shadow = true;
clear-shadow = true;
shadow-radius = 7;
shadow-offset-x = -7;
shadow-offset-y = -7;
# shadow-opacity = 0.7;
# shadow-red = 0.0;
# shadow-green = 0.0;
# shadow-blue = 0.0;
shadow-exclude = [
    "name = 'Notification'",
    "class_g = 'Conky'",
    "class_g ?= 'Notify-osd'",
    "class_g = 'Cairo-clock'",
    "_GTK_FRAME_EXTENTS@:c"
];
# shadow-exclude = "n:e:Notification";
# shadow-exclude-reg = "x10+0+0";
# xinerama-shadow-crop = true;

# Opacity
menu-opacity = 1;
inactive-opacity = 1;
# active-opacity = 1;
frame-opacity = 1;
inactive-opacity-override = false;
alpha-step = 0.06;
# inactive-dim = 0.2;
# inactive-dim-fixed = true;
# blur-background = true;
# blur-background-frame = true;
blur-kern = "3x3box"
# blur-kern = "5,5,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"
# blur-background-fixed = true;
blur-background-exclude = [
    "window_type = 'dock'",
    "window_type = 'desktop'",
    "_GTK_FRAME_EXTENTS@:c"
];
# opacity-rule = [ "80:class_g = 'URxvt'" ];

# Fading
fading = false;
# fade-delta = 30;
fade-in-step = 0.03;
fade-out-step = 0.03;
# no-fading-openclose = true;
# no-fading-destroyed-argb = true;
fade-exclude = [ ];

# Other
backend = "glx"
mark-wmwin-focused = true;
mark-ovredir-focused = true;
# use-ewmh-active-win = true;
detect-rounded-corners = true;
detect-client-opacity = true;
refresh-rate = 0;
vsync = "none";
dbe = false;
paint-on-overlay = true;
# sw-opti = true;
# unredir-if-possible = true;
# unredir-if-possible-delay = 5000;
# unredir-if-possible-exclude = [ ];
focus-exclude = [ "class_g = 'Cairo-clock'" ];
detect-transient = true;
detect-client-leader = true;
invert-color-include = [ ];
# resize-damage = 1;

# GLX backend
# glx-no-stencil = true;
glx-copy-from-front = false;
# glx-use-copysubbuffermesa = true;
# glx-no-rebind-pixmap = true;
glx-swap-method = "undefined";
# glx-use-gpushader4 = true;
# xrender-sync = true;
# xrender-sync-fence = true;

# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = true; opacity = 0.75; focus = true; };
};


```

I use compton in KDE in place of KWin's compositor - as KWin's has proven less than reliable. The only response from the KDE devs is it is the driver stack's fault.  Funny, considering compton does not seem to have that problem and works almost equally well regardless of the driver.  Personally, I think KDE needs to rethink Plasma and their compositor.

---

### Post by Pablo_San_Martn on 2016-10-19
I'll try it! 

Is there any configuration difference I should be aware of for AMD and Intel?

Thank you once again!

---

### Post by T.J. on 2016-10-19
> **Pablo_San_Martn said:**
> I'll try it! 

Is there any configuration difference I should be aware of for AMD and Intel?

Thank you once again!

The settings I gave you should work flawlessly with XFCE using the open Radeon driver for AMD.  Remember to disable XFCE's compositor first or it will not work at all.  You will need to disable XFCE's compositor, add compton to your startup, put the config file in your home folder, and then log out and back in before things will work correctly.

Depending on the level of actual OpenGL support in the driver you decide to use, you may have issues with the "glx" setting.  You will have to perform some trial and error, if it does not work out of the box.  I'll help if I can.  In my opinion, stick with the open drivers  or the proprietary Nvidia drivers - which are your best choices for stable OpenGL behaviour.    

I say this because Intel tries, but their own driver support tends to be hit or miss - it's a toss up. AMD's own support is just plain awful - unless you own the new GCN cards.  The older FGLRX driver is full of bugs - such as cursor and font corruption.  The open drivers are way better, even if they isn't as fast as the closed ones.  The only exception to that seems to be Nvidia.  The people who work on the open drivers for Nvidia work really hard, but Nvidia simply makes a better driver right now.  Nvidia has put a lot of time and money into supporting Linux and their closed drivers are very good.

In fact, if you are interested in gaming on Linux, virtual passthrough or using Wine - I recommend Nvidia over any other, period.  That is not to say you can't make the others work.  Nvidia is just the "gold standard" right now.

---

### Post by Pablo_San_Martn on 2016-11-16
Hi again, T.J. 

I have been using Compton for some weeks now, and have found it's a great lightweight compositor.

 The only thing I don't like is the fact that windows seem to lag a bit behind the cursor when I move them. Is this a compositing feature that can be turned off, or is it just the result of the demands on the system? This laptop is a bit old now, but not ancient (Intel i5-520m; integrated graphics; 6GB of RAM), so it shouldn't be struggling so much with this.

---

### Post by T.J. on 2016-11-16
> **Pablo_San_Martn said:**
> Hi again, T.J. 

I have been using Compton for some weeks now, and have found it's a great lightweight compositor.

 The only thing I don't like is the fact that windows seem to lag a bit behind the cursor when I move them. Is this a compositing feature that can be turned off, or is it just the result of the demands on the system? This laptop is a bit old now, but not ancient (Intel i5-520m; integrated graphics; 6GB of RAM), so it shouldn't be struggling so much with this.

Of this, I cannot speak of without knowing the load on your processor and the quality of your video driver.  I can suggest that you test enabling/disabling the various features - such as shadows and see what balance you can strike with your hardware.  I'd think that you would have no problems - but I cannot guess if your RAM is being captured and shared with your video.  Integrated video cards are generally sub-optimal. Your performance is always going to be less than those with discrete hardware.  My settings that I shared might be a bit much - all of my hardware is discrete, with onboard DDR5 and a large number of processors.

 I'd see if you can find an updated driver first, it is probably the main source of your performance problems.  Not all drivers are completely up to spec with OpenGL, you may need to switch the backend to XRender or basic OpenGL (compton has more than one setting) if it gets too bad.  Either way, you will need to run tests.  Sometimes disabling certain refresh/paints  might help.

It is also highly possible that you may be able to force vsync in your video driver and remove the need for compton altogether.  I do not know enough about your hardware to answer that.  You'd have to post more information such as an output of "lspci -vnn".

---

### Post by Pablo_San_Martn on 2016-11-22
Hi T. J.
Thank you once again. I just saw your reply today as I didn't realise it was on the second page of this thread already!
Hers is my output:
> 00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 7110 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Dell 5 Series/3400 Series Chipset HECI Controller [1028:040a]
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at f69a0000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:16.3 Serial controller [0700]: Intel Corporation 5 Series/3400 Series Chipset KT Controller [8086:3b67] (rev 06) (prog-if 02 [16550])
    Subsystem: Dell 5 Series/3400 Series Chipset KT Controller [1028:040a]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
    I/O ports at 7100 [size=8]
    Memory at f6980000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
    DeviceName:  Onboard LAN
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at f6900000 (32-bit, non-prefetchable) [size=128K]
    Memory at f6970000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 7020 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f6960000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f6950000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: f5500000-f68fffff
    Prefetchable memory behind bridge: 00000000f6a00000-00000000f6bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f4100000-f54fffff
    Prefetchable memory behind bridge: 00000000f6c00000-00000000f6dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00003fff
    Memory behind bridge: f0400000-f2cfffff
    Prefetchable memory behind bridge: 00000000f6e00000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Bus: primary=00, secondary=05, subordinate=0a, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f2d00000-f40fffff
    Prefetchable memory behind bridge: 00000000f7000000-00000000f71fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, medium devsel, latency 0, IRQ 17
    Memory at f6940000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation QM57 Chipset LPC Interface Controller [8086:3b07] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b2e] (rev 05) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell 5 Series/3400 Series Chipset 4 port SATA IDE Controller [1028:040a]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at 70f0 [size=8]
    I/O ports at 70e0 [size=4]
    I/O ports at 70d0 [size=8]
    I/O ports at 70c0 [size=4]
    I/O ports at 70b0 [size=16]
    I/O ports at 70a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: medium devsel, IRQ 10
    Memory at f6930000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 7000 [size=32]
    Kernel modules: i2c_i801

00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b2d] (rev 05) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell 5 Series/3400 Series Chipset 2 port SATA IDE Controller [1028:040a]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at 7090 [size=8]
    I/O ports at 7080 [size=4]
    I/O ports at 7070 [size=8]
    I/O ports at 7060 [size=4]
    I/O ports at 7050 [size=16]
    I/O ports at 7040 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f6920000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

03:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 03) (prog-if 01)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f2c40000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

03:00.4 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller [1180:e832] (rev 03) (prog-if 10 [OHCI])
    Subsystem: Dell Latitude E6410 [1028:040a]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f2c00000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci

3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:8086]
    Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:8086]
    Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Intel Corporation Core Processor QPI Link 0 [8086:8086]
    Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:8086]
    Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:8086]
    Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:8086]
    Flags: bus master, fast devsel, latency 0



---

