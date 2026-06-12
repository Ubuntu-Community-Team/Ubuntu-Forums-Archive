---
title: "screen resolution changed and stuck after updates"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by eckzwolfe on 2011-12-26
ok i just did a fresh install of ubuntu 11.10 and after the updates and a reboot my screen resolution changed to 640x480 and i cannot change it to any other setting. i am very new to ubuntu and need help please.

---

### Post by orange2k on 2011-12-26
What kind of graphic card are you using?
This is important because after you download the propriatary drivers for your card you will be able to change the resolution...

---

### Post by emmomalick on 2011-12-26
> **eckzwolfe said:**
> ok i just did a fresh install of ubuntu 11.10 and after the updates and a reboot my screen resolution changed to 640x480 and i cannot change it to any other setting. i am very new to ubuntu and need help please.
Search in Dash for ADDITIONAL DRIVERS and install the Current Recommended drivers for your Graphic Card 2d and 3d acceleration and then change the resolution to whatever you want.

---

### Post by eckzwolfe on 2011-12-26
> **orange2k said:**
> What kind of graphic card are you using?
This is important because after you download the propriatary drivers for your card you will be able to change the resolution...
 
nVidia Corporation G71 [Quadro FX 1500] (rev a1)? i dont really know 

@[emmomalick]("http://ubuntuforums.org/member.php?u=1256104"): one of my updates was the nvidia accelerated graphics driver version 173

---

### Post by orange2k on 2011-12-26
> **eckzwolfe said:**
> nVidia Corporation G71 [Quadro FX 1500] (rev a1)? i dont really know 

one of my updates was the nvidia accelerated graphics driver version 173

Then in dash search for nvidia, and nvidia x server setting should pop up, and there you can change your resolution...

after that run in terminal: sudo nvidia-xconfig

then run nvidia x server settings again, and click on "save to x configuration file" to make this change permanent...

---

### Post by eckzwolfe on 2011-12-26
> **orange2k said:**
> Then in dash search for nvidia, and nvidia x server setting should pop up, and there you can change your resolution...

after that run in terminal: sudo nvidia-xconfig

then run nvidia x server settings again, and click on "save to x configuration file" to make this change permanent...

i found that app but now this is in the display config tab "unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0."

---

### Post by orange2k on 2011-12-26
> **eckzwolfe said:**
> i found that app but now this is in the display config tab "unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0."

:confused: I don't know what that means...

Have you tried running "sudo nvidia-xconfig"?

---

### Post by eckzwolfe on 2011-12-26
> **orange2k said:**
> :confused: I don't know what that means...

Have you tried running "sudo nvidia-xconfig"?

 i got this output from running "sudo nvidia-xconfig"

#```
"/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

---

### Post by orange2k on 2011-12-26
I don't know about the missing driver line but try now to launch nvidia x-server settings to check if now you can change the resolution...

Beyond that I'm clueless...:(

---

### Post by eckzwolfe on 2011-12-26
> **orange2k said:**
> I don't know about the missing driver line but try now to launch nvidia x-server settings to check if now you can change the resolution...

Beyond that I'm clueless...:(

no go mate. i dont think i did anything wrong but it still says "Unable to load X Server Display Configuration page"
thanx bunch anyway!

---

### Post by eckzwolfe on 2011-12-26
fixed it by going back to the drivers tab in all settings and installing a different accelerated graphics driver (version 96)
although my nvidia x server settings still wont load my display config, my resolution has been corrected after the reboot

---

