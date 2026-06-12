---
title: "Bluetooth drivers broken un Ubuntu 11.10"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by Anakunda on 2012-03-22
Greetings, something wrong happened to bluetooth drivers. The BT icon won't appear anymore in system tray despite that BT dongle is connected, moreover at shutdown time I see approximately this message in text console:

FATAL: Error inserting bluetooth (/lib/modules/3.0.0-16-generic/bluetooth.ko): Unknown symbol in module, or unknown package....

Is there a way to reinstall the bluetooth drivers from scratch?

---

### Post by Anakunda on 2012-03-28
BUMP

I did reinstall everything related to bluetooth in Synaptic but the problem persists.

---

### Post by cortman on 2012-03-28
I'm just curious and not real knowledgeable, but what is the output of

```
cat /lib/modules/3.0.0-16-generic/bluetooth.ko
```

---

### Post by Anakunda on 2012-03-28
My guess of logoff screen, after reinstalling all bluetooth components via Synaptic there's exactly this:

. . nodprobe: FATAL: Could not load /lib/modules/3.0.0-16-generic/modules.dep: No such file or directory
 * Stopping VirtualBox kernel modules
 * Stopping bluetooth on manager uicd
 * Asking all remaining processes to terminate...

I still don't have access to bluetooth subsystem


moreover the bootup screen prints this  text: Bluetooth: Can't change chain in loading configuration err

I uninstalled VirtualBox to see if that's not preventing BlueTooth to operate but it's same

---

