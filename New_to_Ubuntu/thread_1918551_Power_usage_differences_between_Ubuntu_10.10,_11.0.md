---
title: "Power usage differences between Ubuntu 10.10, 11.04, 11.10"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by ghostdunks on 2012-02-01
Been reading the power usage diff articles on Phoronix with quite a bit of interest.  I'm interested in setting up a low-power NAS using Ubuntu as OS, so have been playing with different distros, and measuring power usage.  I'm a complete newbie to Linux so I may be asking a really simple question, apologies if I am.

Test setup-
Motherboard: Intel DH67GD
CPU: Intel Pentium 620(Sandy Bridge), integrated graphics
Power Supply: Seasonic S12II-330Bronze 330 watts 80plus power supply
RAM: 2 sticks of 2gb Kingston RAM
Case: Fractal Design Define R3 case, 3 120mm fans running, and stock CPU cooler

OS media for Live(persistent): Sandisk 4gb USB flashdrive
OS media for full Linux install: Sandisk 8gb USB flashdrive

I tested with the following Ubuntu distros:
Ubuntu 10.10 Desktop 64bit
Ubuntu 11.04 Desktop 64bit
Ubuntu 11.10 Desktop 64bit

I used Unetbootin to create a Persistent Pendrive Linux install on the 4gb flashdrive.  I then installed openssh so I could ssh into the box.  I'll then use the same flashdrive to install a full install of linux onto the 8gb flashdrive, and install ssh on that as well.

To test the power consumption, I'll boot the flashdrives in the following scenarios, give it time to start everything up(10 mins), then measure the power draw using a power meter, would also SSH into box to make sure it was booted:
a) everything connected(integrated graphics enabled,monitor, keyboard/mouse)
b) same as (a) but disconnect the DVI cable to monitor
c) same as (b) but disable onboard integrated graphics in BIOS

Notes on test
- 10.10 figures are given just for reference.  couldn't really do anything with this, as the ethernet card on my board(relatively new) wasn't recognised, so couldn't connect to internet, etc...so didn't bother installing full install.
- with all versions, never managed to boot the Live install without graphics enabled
- with 11.10 version, I had an extra test option, something I was working on before I started measuring the power usage. Has xrdp installed, samba, using gnome shell instead of unity
- nothing special was done to try and decrease power usage, eg. pcie_aspm=force, custom kernels, etc


[IMG]http://i.imgur.com/TL6ik.png[/IMG]

Results:
- Doesn't seem to be a huge difference in the power usage figures for what I have for 10.10 and 11.04.  Seems to be a big jump in power usage when going to 11.10 from 11.04, approx approx 15%.
- when there's no monitor connected, both 11.04 and 11.10 seem to detect the condition, but 11.04 drops about 4w in power, while 11.10 drops less than 2W.
- Once i disable the onboard integrated graphics, power usage on 11.10 drops significantly.  I would say that it might even be similar to what I think the 10.10 distro would do, if I could have got it installed and setup.

I'm suspecting that something's gone weird with the display driver or something related in 11.10.  Is there any way to drop back to the display driver used in 11.04 while still running 11.10?

---

### Post by sanderd17 on 2012-02-01
I believe that was to problem with the recent kernels (although I believe it's fixed in the most recent ones). PCI cards drew too much power. So disabling the graphics card gained a you lot of power.

You should try the power usage in 11.10 with the pcie_aspm=force option. It might be better. This option wouldn't have an effect on older kernels.

Forgive me, but I don't know exactly when the issue came up, and when they fixed (parts of) it. So I can't say for what kernel versions what you would do.

---

### Post by ghostdunks on 2012-02-01
> **sanderd17 said:**
> I believe that was to problem with the recent kernels (although I believe it's fixed in the most recent ones). PCI cards drew too much power. So disabling the graphics card gained a you lot of power.

You should try the power usage in 11.10 with the pcie_aspm=force option. It might be better. This option wouldn't have an effect on older kernels.


Ya, the PCI thing doesn't really affect my case I don't think.  I don't have a separate PCI graphics card, its just the integrated graphics on the CPU that I was toggling on and off.  I actually did a couple more tests with my xrdp custom install(since that was the most power friendly 11.10 setup I had).  Tried the pcie_aspm=force option and retested on 11.10, but power usage was no different at all.

I then tried that with a few other graphics tweaks("pcie_aspm=force*i915.i915_enable_rc6=1*i915.i915_enable_fbc=1i915.lvds_downclock=1") and I immediately saw the power usage drop from 33.2 down to 25.9 with everything connected.  Then I tested with monitor disconnected and for some weird reason, the power usage went up(??) to 26.5.... That part made no sense.

Going to see what effect those same tweaks have on the 11.04 install as well.

---

