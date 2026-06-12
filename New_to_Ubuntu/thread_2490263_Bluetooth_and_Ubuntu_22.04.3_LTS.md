---
title: "Bluetooth and Ubuntu 22.04.3 LTS"
date: 2023-08-28
forum: New to Ubuntu
---

### Post by PurpleF on 2023-08-28
I recently bought a ConnectClip which, via Bluetooth connects my hearing aids direct to my computer music.   I successfully paired the ConnectClip with my hearing aids, but when I tried to pair it with my computer via Bluetooth Manager, ConnectClip showed briefly on the Manager then disappeared.  It didn't show on Devices in the Manager.  I later discovered that Ubuntu 20.04.3 LTS has problems with Bluetooth and, not understanding 97% of what's being suggested on the forum, could someone explain it in simple terms please?
PurpleF

---

### Post by jsdata on 2023-08-28
[COLOR=#111111][FONT=&quot]Hi @[/FONT][/COLOR]PurpleF,[COLOR=#111111][FONT=&quot]
[/FONT][/COLOR]I have a 22.04 LTS too, I guess, that we have an issue with missing manufactures drivers for the attached devices. I have the same issue with my mouse.[COLOR=#111111][FONT=&quot]

[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-08-28
If you do
```

bluetoothctl scan on

```
Does it discover any devices that way? Press keys <Cntrl><C> to cancel the scan...

---

