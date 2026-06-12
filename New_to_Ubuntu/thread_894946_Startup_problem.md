---
title: "Startup problem"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Turwaithien on 2008-08-19
When I start up the computer it does the normal Ubuntu orange bar thingie until about 3/4 of the way, then it goes to a command looking thing and goes rather quickly until it gets to *Starting System Log Daemon

It chills here for a bit (a long bit) then does something too fast for me to see and there are a bunch of lines that look like this:

NetworkManager: <debug> [12191813175.868468] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_224E').

It goes no further and does naught else. I've restarted it a couple of times, and did recovery mode once, but I don't know how recovery mode works, so I didn't do anything with it. This is the first time it's ever done this at me, meaning it's been working fine for a few months now (I'm surprised I haven't broken it...I have bad luck with electronics).

---

### Post by Turwaithien on 2008-08-19
Does this have something to do with my network? or my wireless card? Maybe?

---

### Post by Cheesehead on 2008-08-19
See if you can get us the bottom four or five entries in /var/syslog and var/dmesg.

Boot into recovery mode and just copy them by hand if you must. Try mounting a USB drive to get the whole files...but only if you already know how to mount a USB drive from the command line.

Have you recently changed any configs? updates? given a toddler root access and then left the room for a half hour?

---

### Post by Cheesehead on 2008-08-19
Worst case scenario: If it's not an easy fix (let us try first), spend a few minutes learning the mount command and mounting a usb drive, copy your /home/yourname directory onto the stick to salvage your data...and then reinstall.

---

