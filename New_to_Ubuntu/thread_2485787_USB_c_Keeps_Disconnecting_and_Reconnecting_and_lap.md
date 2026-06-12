---
title: "USB c Keeps Disconnecting and Reconnecting and laptop camera not working on Acer swif"
date: 2023-04-09
forum: New to Ubuntu
---

### Post by alopezcarvallo on 2023-04-09
I just install Ubuntu 22.04.2 LTS on my Acer swift 3 SF314-71 and I  am having some troubles with the USB c ports (both of them), integrated  camera and fingerprint scanner recognition.
 When the USB c port is connected to power source the laptop sometime  do not recognize it. Additionally, when using pen drive it keeps  disconnecting and reconnecting.


 The camera is not even recognized.


 I have noticed the following boot-errors:


 kernel: int3472-discrete INT3472:01: error -EINVAL: Failed to map  regulator to sensor kernel: int3472-discrete: probe of INT3472:01 failed with error -22 systemd[1]: Condition check resulted in Process error reports when  automatic reporting is enabled (file watch) being skipped. systemd[1]: Condition check resulted in Process error reports when  automatic reporting is enabled (timer based) being skipped. canonical-livepatch.canonical-livepatchd[855]: Task "refresh" returned  an error: livepatch check failed: POST request to  "https://livepatch.canonical.com/v1/client/1901567b1d0e4edeab0f513d099f8371/updates"  failed, retrying in 30s. gnome-session[1329]: gnome-session-binary[1329]: GLib-GIO-CRITICAL:  g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed gnome-session[1329]: gnome-session-binary[1329]: GLib-GIO-CRITICAL:  g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed gnome-session-binary[1329]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion  'error == NULL || *error == NULL' failed gnome-session-binary[1329]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion  'error == NULL || *error == NULL' failed udevmon.go:149: udev event error: Unable to parse uevent, err: cannot  parse libudev event: invalid env data udevmon.go:149: udev event error: Unable to parse uevent, err: cannot  parse libudev event: invalid env data udevmon.go:149: udev event error: Unable to parse uevent, err: cannot  parse libudev event: invalid env data


 I would be really happy to hear some suggestion to fix it.


 Thank you in advance.

---

