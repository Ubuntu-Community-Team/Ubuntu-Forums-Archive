---
title: "Double whammy problem: ATI/AMD fglrx and no sound"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by Agent Foxtrot on 2012-01-21
Hi, everyone.

I rebuilt a youngish-but-problematic computer (HP Pavilion d4000) with some new parts and decided to use Ubuntu as the OS, which I installed from a boot disk last night onto a virgin HDD.  The computer is connected to a Samsung 42" LCD TV.

The first issue is sound, or lack of it.  I originally had a DVI-to-HDMI cable going from the computer to the TV and a simple audio cable going from the sound card to the TV's audio input port.  No sound.  After a bit of research, I found that DVI doesn't transmit sound, but HDMI does, so I switched to a plain HDMI cable.  No sound.  I then read that while HDMI can send dual-channel video and audio, there are no standards established and not all TV's split the channels.  It would be odd that my TV doesn't, as it receives audio via HDMI just fine from my PS3 and Xbox 360.

This leads to the second issue.  Further research prompted me to try installing the proprietary ATI/AMD fglrx drivers.  I opened the Additional Drivers window and attempted to activate the driver with post-release updates, but I keep getting an error message stating, "Sorry, installation of this driver failed." and points me to /var/log/jockey.log.  I opened the log in vi, and from what I can understand (which isn't much), I'm missing a module nvidia_127, whatever that is.

So I tried to activate the section option, fglrx without the post-release updates.  Doing so causes the system to hang at the Ubuntu startup screen.  I was forced to deactivate that driver.

So do any of these problems sound familiar to anyone?  If it helps, the graphics card is a Radeon HD 3450.  Any help would be greatly appreciated.

Thanks!  

PS - Are there any other drivers/programs you would recommend I install?

---

### Post by 2F4U on 2012-01-21
I had the error message after installing the fglrx driver (post-release) too, but after a restart of the machine, everything was ok and the driver was loaded. Did you restart after installing the driver? If not, try that and after the restart verify that the driver is loaded by 

sudo lsmod | grep fglrx

---

### Post by Agent Foxtrot on 2012-01-21
> **2F4U said:**
> I had the error message after installing the fglrx driver (post-release) too, but after a restart of the machine, everything was ok and the driver was loaded. Did you restart after installing the driver? If not, try that and after the restart verify that the driver is loaded by 

sudo lsmod | grep fglrxThanks for responding.  The driver wouldn't even install in the first place... that's the problem.

---

### Post by 2F4U on 2012-01-21
Are you sure that the message was that you are missing the module nvidia_127? This seems to be a nVidia module, but your graphics card is ATI/AMD. Is that a dual-graphics laptop?

---

### Post by Agent Foxtrot on 2012-01-21
> **2F4U said:**
> Are you sure that the message was that you are missing the module nvidia_127? This seems to be a nVidia module, but your graphics card is ATI/AMD. Is that a dual-graphics laptop?I'm not sure of anything at this point. :)  I'm just stating what I read in jockey.log... that seems to be where things got hung up.  Would it help if I posted the logfile?

---

