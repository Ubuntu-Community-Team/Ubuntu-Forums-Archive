---
title: "adding 1366x768 screen resolution to amd machine"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by Hairygrump on 2012-08-01
Hello. I just installed Ubuntu 12.04 onto a Gateway Lt3108h net book with an ATI/Radeon chipset. I have installed FGLRX so that the screen is stable but I need to add a resolution of 1366x768.  I have been searching for the correct set of commands to do this in Terminal but I'm not having any luck. I am a very basic user so something simple would help immensely. Any help would be appreciated here.

I have already downloaded and installed 
ATI binary x.org driver
Jockey kde
Jockey gtk

Thanks

---

### Post by Ubun2to on 2012-08-01
From what I have seen, 1366x768 isn't a very common screen resolution, usually reserved for laptops (like my System76 Lemur Ultra). Is this for a desktop or a laptop? If it's for a desktop, you might as well replace the monitor with a more common size (or, use a higher screen resolution).

---

### Post by Grenage on 2012-08-01
> **Hairygrump said:**
> Hello. I just installed Ubuntu 12.04 onto a Gateway Lt3108h net book with an ATI/Radeon chipset. I have installed FGLRX so that the screen is stable but I need to add a resolution of 1366x768.

I normally avoid downloading and installing the drivers manually, as they won't be automatically included when a new kernel comes along (I could be wrong here, but I'll be undoubtedly corrected if so).

Regardless, you can either set the resolution using [xrandr]("https://wiki.ubuntu.com/X/Config/Resolution/"), or [xorg.conf]("http://www.grenage.com/xorg.html").  I prefer the latter, the majority probably prefer the former.

---

### Post by Hairygrump on 2012-08-02
Thanks, used xorg.conf and it seems to have worked. Hopefully it stays that way. When I entered the mode lines into the terminal it said that it didn't understand subsection or section commands. Does this mean I screwed something up or is it normal?

---

### Post by Hairygrump on 2012-08-02
ARRRG!!!! Ran an update, restarted the computer and it reverted back to the original resolution 0f 1280x800. The 1366x768 resolution dosen't even show up in the display menu. What the hell happened? Do I need to do something to make this a permanent setting?

---

### Post by QIII on 2012-08-02
if you ran an update and it updated the kernel, then this is not unexpected if you manually installed the driver after downloading it from AMD's website..

Installing the driver from the repo ensures that it is compiled into the new kernel during normal updates.  When manually installed, a reinstall is required after a kernel update.

---

### Post by Hairygrump on 2012-08-02
ok, now I'm way in over my head. Not sure what updated, just followed the prompts the computer gave me. I have made so many changes that I have no idea which driver is doing what. I reran the original moniter reconfiguration and its not doing anything now. Can someone walk me through this step by step in plain simple english. It shouldn't be this hard to get a simple screen res. Right????? I hope

---

### Post by Grenage on 2012-08-02
I assume that under 'Additional Drivers', you'll get a list of several ATI/AMD drivers, if you activate one from there, I believe it should include it in future kernel updates.

---

