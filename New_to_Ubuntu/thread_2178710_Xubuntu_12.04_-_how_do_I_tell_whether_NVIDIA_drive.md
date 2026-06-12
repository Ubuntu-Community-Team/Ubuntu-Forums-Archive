---
title: "Xubuntu 12.04 - how do I tell whether NVIDIA driver is running?"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by Remten on 2013-10-04
I have an Asus N550JV laptop, which has an integrated Intel GPU along with an NVIDIA GT750M GPU. The GT750M is advertised as being compatible with NVIDIA's Optimus technology that switches between GPU's depending on the specific video demands.
I've tried to install NVIDIA's 319 driver downloaded from the NVIDIA website.
When I run Additional Drivers, it finds NVIDIA_319, but displays a message that says, "This driver is activated but not currently in use."

[COLOR=#0000ff]My question is how can I tell whether the NVIDIA driver is actually currently accessible to the system and whether at a given moment it is running?[/COLOR]

I would prefer to just use the NVIDIA driver all the time (I mainly use the laptop while plugged into an AC electrical source, so I'm not worried about battery drain and don't need to use the integrated Intel GPU on that account).

**Background info:**
(not sure what is relevant, so maybe I am listing too much)

I am running Xubuntu 12.04 LTS 64-bit - with linux 3.2.0-54. (It's a dual-boot setup with Win 7, if that's relevant.)

I looked in the bios to see whether there was an option to choose which GPU to use, but there wasn't (it's a pretty bare-bones bios menus setup).

When I initially intalled Xubuntu, I noticed that with every few boots, there would be a graphics glitch in which the screen would flicker and shiver and blank-out so much that it was impossible to read what was on the screen. And even on the boots in which there were no immediate graphics anomalies, whenever I would go into the Settings Manager and try to open the Screensaver settings module, the graphics anomalies would be immediately triggered. (I also noticed that whenever I would try to boot the computer to a live CD running other linux distros, such as to run Terabyte Image for Linux or Parted Magic, I would get the same graphics anomalies every few boots.)

So I did the following:

following info from dedoimedo.com for installing Nvidia drivers with Ubuntu 12.10:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install build-essential linux-source linux-headers
sudo apt-get install linux-headers-`uname -r `
sudo apt-get install nvidia-current

but when I tried to confirm that an nvidia driver had been installed, I got 'not found' messages:

sudo /sbin/lsmod ! grep nvidia      # (I'm typing this on a different computer, that doesn't have a character for the vertical bar, so using ! here instead to represent what I actually typed)
sudo depmod -a   #this and the previous line produced no output
sudo modprobe nvidia_current
#the above line produced   "FATAL: module nvidia_current not found"

At this point, I started trying to follow suggestions from bogan in post #19 of this thread:
[http://ubuntuforums.org/showthread.php?t=2075318&page=2&p=12315130#post12315130](http://ubuntuforums.org/showthread.php?t=2075318&page=2&p=12315130#post12315130)

I confirmed that I had in /etc/modeprobe.d blacklists, including in /etc/modeprobe.d/nvidia_graphics_drivers.conf

Then I did:

sudo nvidia-installer --uninstall
#this produced "nvidia-installer: command not found"

sudo apt-get remove --purge nvidia*
sudo service lightdm stop
cd /home/myuserame/Downloads  #I had previously downloaded the Nvidia driver to this folder
sudo chmod a+x NVIDIA-Linux-x86_64-319.60.run
sudo sh NVIDIA-Linux-x86_64-319.60.run
#the NVIDIA installer ran, and I chose accept for the question about installing 32bit compatibility OpenGL libraries
sudo reboot

I think at this point I still kept getting a message about no proprietary drivers being installed when I would run Additional Drivers as a check, so I did 
sudo software-properties-gtk

On the next run I was able to select an Nvidia binary Xorg driver (there were two listed that looked the same, I chose one of them)
After rebooting, I saw Nvidia_319 as an additional drivers option, and I selected it and clicked Activate (or something like that). I rebooted again.

Now, I haven't seen anymore of the graphics anomalies on random reboots OR when I try to open the Screensaver setting module. (I was finally able to adjust the screensaver settings.)

However, when I run Additional Drivers, there is a message at the top that says No proprietary drivers are in use on this system.
Below that there are two drivers listed:
Nvidia_319 and
NVIDIA binary Xorg driver, kernel module and VDPAU library

The Nvidia_319 has a green (highlighted) mark beside it, and the message at the bottom reads, "This driver is activated but is not currently in use."
When I place the cursor over the greyed-out orb next to the NVIDIA binary Xorg line, the message at the bottom reads, "This driver is not activated."

---

### Post by Remten on 2013-10-04
lspci ! grep VGA     gives me

00:02.0  VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)

but

lspci ! grep 3D  gives me
01:00.0  3D Controller: NVIDIA Corporation GK107M [GeForce GT 750M]  (rev a1)

---

### Post by The Cog on 2013-10-04
**lspci -v**
will show details on the video card, including a line that says "Driver in use: ..."

---

### Post by Remten on 2013-10-04
> **The Cog said:**
> **lspci -v**
will show details on the video card, including a line that says "Driver in use: ..."

thanks for replying so quickly

here's what that shows:


00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 11cd
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features

...

01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 11cd
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    [COLOR=#0000ff]Kernel driver in use: nvidia[/COLOR]
    Kernel modules: nvidia_319, nvidia, nouveau, nvidiafb

Since there is no "kernel driver in use" line for the VGA/Intel GPU but there is one for the GT 750M, does that mean that the NVIDIA driver is the only video driver currently running?
Or does the "Kernel driver in use: nvidia" only apply for processes specifically requiring a 3D controller?

---

### Post by Bashing-om on 2013-10-04
Remten; Hi !

I have not kept up to date but;
NVIDIA GT750M GPU-> Optimus = BumbleBee
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

To manage switchable graphics.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

