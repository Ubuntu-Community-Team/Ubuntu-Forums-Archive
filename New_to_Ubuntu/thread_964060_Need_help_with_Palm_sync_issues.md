---
title: "Need help with Palm sync issues"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-10-30
I have resurrected my old Palm m130 but I'm getting a lot of error messages and the palm doesn't sync. I tried several tutorials but nothing seems to work. It's very frustrating.

errors:

gpilotd

```
(gpilotd:7094): gpilotd-WARNING **: Unable to bind to PDA
```

jpilot

```
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
****************************************
 Syncing on device /dev/ttyUSB0
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB0 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
****************************************
 Syncing on device /dev/ttyUSB1
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
```

visor

```
visor: probe of 4-1:1.0 failed with error -5
```

Does someone knows if this is fixable or should I just give up?

---

### Post by plain_jim on 2008-11-03
My upgrade from Hardy was a disaster, and I had to install from the downloaded CD, so I lost a number of my settings (my /home/<name> directory is in a separate partition, so a lot of stuff was saved), including the Palm sync with jpilot.  What worked for me to get the Palm ticking again was the stuff on this page:

[http://kaybyrd.com/?p=56](http://kaybyrd.com/?p=56)

I did the stuff under the "JPilot" and "Automatic Modprobe Visor" settings, and it's working nicely.  (FWIW, when I was using Hardy, after I did this stuff, I could also use the "PalmOS Devices" tool in "System/Preferences", but my experience with Evolution was less than ideal - creating duplicates, mostly, but other stuff, too - so I'm sticking with jpilot.)

---

### Post by lovinglinux on 2008-11-06
> **plain_jim said:**
> My upgrade from Hardy was a disaster, and I had to install from the downloaded CD, so I lost a number of my settings (my /home/<name> directory is in a separate partition, so a lot of stuff was saved), including the Palm sync with jpilot.  What worked for me to get the Palm ticking again was the stuff on this page:

[http://kaybyrd.com/?p=56](http://kaybyrd.com/?p=56)

I did the stuff under the "JPilot" and "Automatic Modprobe Visor" settings, and it's working nicely.  (FWIW, when I was using Hardy, after I did this stuff, I could also use the "PalmOS Devices" tool in "System/Preferences", but my experience with Evolution was less than ideal - creating duplicates, mostly, but other stuff, too - so I'm sticking with jpilot.)

Thank you, but now I remembered why I wasn't using the palm anymore. It went crazy, blinking all the time. So I guess it doesn't worth the trouble.

---

