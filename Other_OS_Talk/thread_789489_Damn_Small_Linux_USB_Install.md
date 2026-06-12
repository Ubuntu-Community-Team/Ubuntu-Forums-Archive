---
title: "Damn Small Linux USB Install"
date: 2008-05-10
forum: Other OS Talk
---

### Post by weissnich on 2008-05-10
Hi,

I have a 128mb pendrive that I really don't need anymore so I tried to play with DSL Linux a bit.
I have copied the DSL-embedded version to my pendrive and everything works fine except that I cannot restore the settings I made, for example changing the keyboard to German, setting passwords for root and user, changing bookmarks in firefox.
I tried to backup in sda1 via the panel, but it crashes, and when I select backup on reboot or shutdown, next time I boot again the settings are gone.
Anyone here can help me, DSL forum doesn't let me register.

---

### Post by kerry_s on 2008-05-10
what dsl version?
are you sure the dev is sda1?
what do you mean it won't let you register on the forums?

---

### Post by weissnich on 2008-05-10
I have been registered in the forums on DamnSmallLinux but can't verify my account somehow, won't work, so I post my questions here ;).
DSL version is the most recent version 4.3.

---

### Post by kerry_s on 2008-05-10
i'm assuming you did the frugal install?

how did you partion the flash drive?

---

### Post by weissnich on 2008-05-10
I have to boot with floppy disc because my Bios doesn't allow usb boot.
I just downloaded the floppy image and copied it and then downloaded the embeddedDSL version and copied it to the pendrive with no partitioning.
DSL loads everything, works fine, only problem is I cannot restore settings.

---

### Post by kerry_s on 2008-05-10
that's that 1 that runs inside of windows?
i've never used that 1. :(
not sure what to tell you.

---

### Post by jvin248 on 2008-05-22
I think you manually copied the files over and there is a break in the file structure...

Make sure you've use the "USB-HDD pendrive install" that's on the DSL menu (start/apps/..).  That should install to the USB stick after a few quick questions.  Then when you exit DSL make sure you're selecting "backup" to save your settings.  

Not sure with 4.3, but older versions of DSL if you didn't do a nice shutdown inside DSL, like pulled the power cord, then when rebooting DSL would forget all previous settings.

---

