---
title: "Dual monitor problem in 11.10"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by geomcd1949 on 2011-10-13
Updated to Ubuntu 11.10
Motherboard: ASUS M2N68-AM Plus
Video card: GeForce 8400 GS 1GB
Driver: NVIDIA accelerated graphics driver (version current) [Recommended]
Additional Drivers file indicates "This driver is activated and currently in use."

Works fine with one monitor connected by VGA cable.

Hooked up a second monitor with a DVI cable and re-booted.

Second monitor got a screen, but the first monitor was blank.

Unhooked the second monitor and rebooted.

First monitor got a screen, and on it is a box one-third the size of the screen saying "Could not apply the stored configuration for monitors," then listing a many configurations.

I cannot make this box disappear - I clicked everywhere on it and off it, but it just stays there.

The screen that comes up when I click "Displays" shows only one monitor. The box to "Detect Displays" is active (clickable; not grayed out), but when I click it, it does not display/detect/show the other monitor. This happens when either monitor has a screen and the other monitor is hooked up but blank. 

Also, in both instances, I cannot check the box "Mirror displays."

Help is greatly appreciated!

~George

---

### Post by wolfen69 on 2011-10-13
You need to open nvidia settings with:
```
gksu nvidia-settings
```
then configure the monitors. Hit apply, then save to X.

---

### Post by geomcd1949 on 2011-10-13
Wolfen69,

Thanks for your kind reply. It solved both problems.

Sorry if you thought my post was a complaint - it wasn't. Just a request for advice from more experienced users.

~George

---

### Post by kelliott0965 on 2011-10-14
Hi Wolfen,

I'm also having a similar problem...everything was working fine until I upgraded to 11.10 tonight. I'm using a nvidia GE Force 9600GT card with dual monitors. I'm only getting video on one monitor...the other is not recognized by the system.

So, I opened up the nvidia xserver settings program you noted above. Under xserver display information, I get the following message: 

Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

Also, I checked System Settings / Displays to see what it had listed and it just said "Unknown" and showed one single monitor icon.

Do you have any idea what could be wrong?

Thank you for any help you can provide.

Cordially,

-Keith

---

### Post by carranty on 2011-10-14
> **kelliott0965 said:**
> Hi Wolfen,

I'm also having a similar problem...everything was working fine until I upgraded to 11.10 tonight. I'm using a nvidia GE Force 9600GT card with dual monitors. I'm only getting video on one monitor...the other is not recognized by the system.

So, I opened up the nvidia xserver settings program you noted above. Under xserver display information, I get the following message: 

Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

Also, I checked System Settings / Displays to see what it had listed and it just said "Unknown" and showed one single monitor icon.

Do you have any idea what could be wrong?

Thank you for any help you can provide.

Cordially,

-Keith


This exact same thing is happening to me.  According to the output of *lspci *I have an nVidia Corporation G72 [GeForce 7500 LE] (rev a1).  Whichever monitor I have hooked up to the VGA connection works, but DVI seems a no go.

---

### Post by bcollier on 2011-10-14
I had this problem and had to update the Nvidia drivers for Gnome 3.  Here is the guide:  [http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html)  they have a very simple PPA you can use.  The latest for me on a 64 bit system is this driver:  [http://www.nvidia.com/object/linux-display-amd64-285.05.09-driver.html](http://www.nvidia.com/object/linux-display-amd64-285.05.09-driver.html)

---

