---
title: "Logik MP3/MP4 player not recognised"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by bokgeneraal on 2011-09-27
Hi  I have a Logic MP3/MP4/AVI touchscreen  player that is not  recognised in ubuntu. Under Windows it is recognised and works as a  normal usb flash drive. Under Ubuntu never appears in the mount folder.  Any suggestions are welcome.:wink:

---

### Post by bokgeneraal on 2011-09-29
bump

---

### Post by technosysind on 2011-09-29
I think Linux compatibility might be a problem.

---

### Post by Dale61 on 2011-09-30
> **technosysind said:**
> I think Linux compatibility might be a problem.

Ya think?

---

### Post by mikechant on 2011-09-30
Does the player have any 'transfer mode' settings you can try changing?

Can you post the output from the 'lsusb' command with the device plugged in?

---

### Post by bokgeneraal on 2011-10-11
Here is the output with the device not connected:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 090c:3371 Feiya Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Here is the output with the device connected :
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 090c:3371 Feiya Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

seems identical .

---

### Post by mikechant on 2011-10-14
Do you have the model number?

Can you try it with a different release/version of Linux (e.g. running from live CD or live USB)?

---

