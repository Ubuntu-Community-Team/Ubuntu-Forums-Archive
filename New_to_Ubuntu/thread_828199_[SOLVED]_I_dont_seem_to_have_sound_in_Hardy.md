---
title: "[SOLVED] I dont seem to have sound in Hardy"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-06-13
Hey all,pon trying to get better sound quality I seem to have run into a problem..I removed Pulseaudio then reinstalled it but get this error: No Volume control gstreamer plugins and/or devices found..I have an hp pavillion 7920 with an intel cellron processor with 384 mb ram and 00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:09.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller card..Can anyone help??

---

### Post by sports fan Matt on 2008-06-13
upon restarting the pc this message pops up: The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

---

### Post by cariboo on 2008-06-13
Go into System-->Preferences-->Sound and check your settings there

Jim

---

### Post by stchman on 2008-06-13
> **sox fan Matt said:**
> Hey all,pon trying to get better sound quality I seem to have run into a problem..I removed Pulseaudio then reinstalled it but get this error: No Volume control gstreamer plugins and/or devices found..I have an hp pavillion 7920 with an intel cellron processor with 384 mb ram and 00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:09.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller card..Can anyone help??

I prefer ALSA to Puleaudio.  Go to 

System--->Preferences--->Sound and select ALSA for your options over Automatic.

---

### Post by sports fan Matt on 2008-06-13
Everything is set to alsa, however i still get that same message i described in my second post..I will check symnaptic and see if I have everything for ALSA

---

### Post by kansasnoob on 2008-06-13
While you're in synaptic search for gstreamer. I install ALL gstreamer (good, bad and ugly). Everything beginning with gstreamer gets installed and I've never blown anything up ............ yet!

---

### Post by sports fan Matt on 2008-06-13
Ive installed all the gstreamer tools and will reboot

---

### Post by sports fan Matt on 2008-06-13
the same message from my 2nd post still appears even from a sudo-apt-get update, ticking all the gstreamer items ..I cant open up my volume control (that message from my 2nd post pops up)

---

### Post by kansasnoob on 2008-06-13
Check this thread:

[http://ubuntuforums.org/showthread.php?t=811180](http://ubuntuforums.org/showthread.php?t=811180)

There I'd listed what my Hardy has installed, partly by default, partly by choice.

---

### Post by kansasnoob on 2008-06-13
I should have mentioned this part in particular:

"So somehow my gstreamer properties were changed, or no long valid.

I opened up gstreamer-properties in the terminal, and messed with the settings: changed autodetect to alsa and now it works. Thanks for all your help guys"

---

### Post by sports fan Matt on 2008-06-13
im trying to reinstall all the linux kernels 2.6. something 19..to try and establish sound back

---

### Post by sports fan Matt on 2008-06-13
the suggestion i had solved nothing

---

### Post by sports fan Matt on 2008-06-13
Everything set to alsa in the gstreamer properties as per kansas noob as well

---

### Post by sports fan Matt on 2008-06-13
Im trying to figure out what i hosed to not be able to open my volume control..its frustrating cause im out of ideas..

---

### Post by kansasnoob on 2008-06-13
I may have already asked you this, but for fear of repeating myself, have you just tried clicking "reload" in synaptic and seeing if you have any "broken" packages?

Maybe run the command: sudo apt-get -f install

Just to try and resolve any unmet dependencies.

Otherwise I'm out of ideas.

Sorry:confused:

---

### Post by sports fan Matt on 2008-06-13
No broken packages..maybe in a new kernel release it will be fixed

---

### Post by sports fan Matt on 2008-06-14
I had to reboot into the old 18 kernel to regain sound...

---

