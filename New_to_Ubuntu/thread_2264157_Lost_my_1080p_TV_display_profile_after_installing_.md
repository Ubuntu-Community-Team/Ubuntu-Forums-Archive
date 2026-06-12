---
title: "Lost my 1080p TV display profile after installing printer.*SOLVED*"
date: 2015-02-05
forum: New to Ubuntu
---

### Post by kingdominsight on 2015-02-05
Ok so my 60" 1080p LG tv was looking beautiful at full resolution. However after adding my Canon MP495 printer drivers through the terminal, which is working great, but when i restated, my TV profile was corrupted, Ubuntu no longer recognizes my TV even though it is a selectable option in the color profile. I now have 1024 x 768 max resolution. 
What did i screw up????

Update: i cannot remove the printer color profile, the button is grayed out.
I found the LG color profile, but i cannot make it the default, nor can i calibrate it.

Update: ok apparently the open source radeon drivers were corrupted after the printer install. I get an error that pops up but too quickly to read fully

Update: purged all video drivers and resinstalld xorg, no effect.


Update: These seem to be the relivent errors, while there are more boot errors, these seem to be the latest.

[   25.356975] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   26.349166] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   26.625573] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   27.157261] init: plymouth-upstart-bridge main process ended, respawning
[   27.198676] init: plymouth-upstart-bridge main process ended, respawning
[   31.819373] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   32.615857] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   34.933328] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   35.186495] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   35.349875] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   36.857412] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
[   47.558750] ath5k: ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x00000000
[   50.719667] type=1400 audit(1423179514.134:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2162 comm="apparmor_parser"
[   50.719675] type=1400 audit(1423179514.134:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2162 comm="apparmor_parser"
[   50.720074] type=1400 audit(1423179514.134:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2162 comm="apparmor_parser"
[   59.562429] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID

I have tried wiping all xorg fglrx drivers no avail.
I have tried to purge anty ati drivers but none found

Update: Just noticed something. my bios logo no loger displays when i start the machine.  From this i can only deduce that what ever code i ran when installing the printer software  has somehow affected the bios on the motherboard, or possibly the graphics card.  I will try using the onboard video and see what happens.


UPDATE: RESOLVED   Removing the case cover and manually resetting the BIOS seems to have worked. Apparently the drivers and or code i entered disabled the PCI-E slot and turned on the onboard Video. Clearing the BIOS manually allowed me to get back into the BIOS settings and turn back off the onboard video.

---

### Post by sandyd on 2015-02-05
Hi, a printer driver installation should not affect the graphics card, or the BIOS.

Just a suspicion- Does your display work if you press ESC during boot (if you have a hidden grub menu), go to 'Advanced Options for Ubuntu' and choose an earlier kernel to boot from?

---

### Post by kingdominsight on 2015-02-05
yep it screwed the graphics card bios, no signal all the way untill the ubuntu loading icon. Wont even display BIOS splash screen, yep tweeked my GPU wonderful. And now i cant even log in as administrator in ubuntu, the screen just blinks. Tried a clean install from CD same issue. Thanks Ubuntu. :/  guess a new graphics card will have to be invested in.

---

### Post by kingdominsight on 2015-02-06
Resolved

---

### Post by Bucky Ball on 2015-02-06
> **kingdominsight said:**
> Resolved

Good news. Please mark the thread as solved by following the second link in my signature. Good luck. ;)

---

