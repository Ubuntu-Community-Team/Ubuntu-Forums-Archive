---
title: "Problems running ubuntu 12.10 and desperately need help!"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by graym on 2012-10-31
Hey guys,

I have been trying to get ubuntu 12.10  to work on my Lenovo Ideapad S110, but it keeps on having problems booting up. I have never used  linux before, so I don't really know what I'm doing.

When the computer boots up it always stops loading at a screen that says it is either starting or stopping a bunch of processes.

I think it might be a problem with my video card (intel integrated) and/or the driver because when I install/reinstall ubuntu, it says my graphics card is "unknown".

Any help would be greatly appreciated!

---

### Post by euphoric_anomaly on 2012-10-31
> **graym said:**
> Hey guys,

I have been trying to get ubuntu 12.10  to work on my Lenovo Ideapad S110, but it keeps on having problems booting up. I have never used  linux before, so I don't really know what I'm doing.

When the computer boots up it always stops loading at a screen that says it is either starting or stopping a bunch of processes.

I think it might be a problem with my video card (intel integrated) and/or the driver because when I install/reinstall ubuntu, it says my graphics card is "unknown".

Any help would be greatly appreciated!

For Intel Graphics cards install mesa-utils (if you can get it to boot)
sudo apt-get install mesa-utils

I have the onboard 945G.

---

### Post by graym on 2012-10-31
Thanks for the quick response! But at what screen would I input that command?

---

### Post by jroa on 2012-10-31
Can you boot the live disk?  If so, then you probably need to reinstall.  If not, then you might have a bad .iso or a bad burn.

---

### Post by graym on 2012-10-31
I installed ubuntu from a usb drive and used unetbootin to prep the .iso  so that it could boot from the usb drive.

---

### Post by jroa on 2012-10-31
You should be able to boot the computer from the same USB drive.  Just select the option to try it and it will run completely from the drive and RAM.

If you can't boot the drive, then you might have a bad download.  You can compare the checksum of the .iso to see if it is good.

---

### Post by graym on 2012-10-31
When I boot from the usb and select "try ubuntu" I am eventually brought to a black screen with a flashing command line in the top left corner, but I am unable to type anything and the only reason any text pops up is if I hit the power button, in which case it just says that all processes are being stopped and preparing to shut down.

I think I may have got a bad download, but I downloaded the .iso from the official ubuntu site.  Should I try picking it up somewhere else?

---

### Post by jroa on 2012-10-31
You can check to see if your .iso is good by downloading a checksum checker, such as [this one]("http://download.cnet.com/MD5-SHA-1-Checksum-Utility/3000-2092_4-10911445.html").  Browse to your .iso image and compare the version that you downloaded to [this]("https://help.ubuntu.com/community/UbuntuHashes").  If they don't match, then you need to download again.

---

### Post by graym on 2012-10-31
Thanks jroa. I'll be able to check that once I get to a working computer (just using my phone for the posts). I actually followed the advice of another post and was able to run ubuntu in text-only mode. I tried using apt-get to update my graphics driver, but I am not sure how I connect to the wi-fi at the hostel that I am staying at in this mode. Does anyone know how to connect to a wireless network in text-only mode (through specific commands)?

---

### Post by squakie on 2012-10-31
I think you're going to have to edit the boot line when you boot from the USB and include:

i915.modeset = 0  

or 

i915.modeset =1


It may also be a case of needing to specify acpi=no or apic=no on the same boot line.

---

### Post by graym on 2012-10-31
Where in the boot line would I input those edits?

---

### Post by graym on 2012-10-31
> **squakie said:**
> I think you're going to have to edit the boot line when you boot from the USB and include:

i915.modeset = 0  

or 

i916.modeset =1


It may also be a case of needing to specify acpi=no or apic=no on the same boot line.
Would I input those edits after:

quiet splash $vt_handoff

?

---

### Post by Mark Phelps on 2012-10-31
> **graym said:**
> Would I input those edits after:

quiet splash $vt_handoff

?

Doesn't really matter -- but I would insert those edits between "quiet" and "splash".

---

### Post by squakie on 2012-10-31
I should tell you there are no spaces in the i915.modeset=x lines - I put those in the post to make it a little easier to read and forgot to mention it.

Also - the acpi and/or apic = statements will have no spaces as well, and it may be "off" on those instead of zero.

Do as MarkPhelps said for placement (and btw - MarkPhelps may not admit it, but he is a real expert at ubuntu!).

Let us know if any of that works or not.

---

### Post by squakie on 2012-10-31
Well, I just went and double-checked at [this]("https://help.ubuntu.com/community/BootOptions") page and indeed, it would be noapic or acpi=off

---

### Post by karlstad on 2012-10-31
> **graym said:**
> Hey guys,

I have been trying to get ubuntu 12.10  to work on my Lenovo Ideapad S110, but it keeps on having problems booting up. I have never used  linux before, so I don't really know what I'm doing.

When the computer boots up it always stops loading at a screen that says it is either starting or stopping a bunch of processes.

I think it might be a problem with my video card (intel integrated) and/or the driver because when I install/reinstall ubuntu, it says my graphics card is "unknown".

Any help would be greatly appreciated!

Do you get access to a "login screen" if you press CTRL+ALT+F1?

---

### Post by graym on 2012-11-02
No, I don't reach a log in screen unless I enter text mode.

As for the other suggestions,  I will give them a shot tonight.  I just arrived in Vietnam. Thanks again for the help guys, it is immensely appreciated.

---

### Post by biletsky on 2012-12-27
> **graym said:**
> Hey guys,

I have been trying to get ubuntu 12.10  to work on my Lenovo Ideapad S110, but it keeps on having problems booting up. I have never used  linux before, so I don't really know what I'm doing.

When the computer boots up it always stops loading at a screen that says it is either starting or stopping a bunch of processes.

I think it might be a problem with my video card (intel integrated) and/or the driver because when I install/reinstall ubuntu, it says my graphics card is "unknown".

Any help would be greatly appreciated!

Have you solved the problem? 
I've experienced the same :(

---

