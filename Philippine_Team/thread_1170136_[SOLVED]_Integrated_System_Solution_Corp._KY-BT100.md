---
title: "[SOLVED] Integrated System Solution Corp. KY-BT100 Bluetooth Adapter on ubuntu 9.04"
date: 2009-05-25
forum: Philippine Team
---

### Post by dodimar on 2009-05-25
```
Bus 004 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter

```

I have this bluetooth dongle, it's detected by Ubuntu 9.04 (running on live session)..

It was detected by the cellphone I am using (Samsung E730), however the only one service appears... "Headset"..

When I tried to transfer a file from the phone, it can't detect the bluetooth device (even if it was already paired, maybe only as a headset?)...

Should I make a full install first to make this work? (which I won't be able to do until the end of the week). I need to transfer those files asap (no, it's not a new scandal, they are photos of my nephew's graduation)..

---

### Post by loell on 2009-05-26
have you tried configuring the device with **bluez**?

perhaps there's an option where you can change it from headset mode to file mode?

[SIZE="1"]Disclaimer: wala akong bluetooth dongle :)[/SIZE]

edit--

try looking at this project too [blueman]("http://blueman-project.org/")

---

### Post by Script Warlock on 2009-05-26
try mo na ba ang hcitool scan? oo nga the bluez thing....sometimes kung di mag auto connect tong msi blue tooth ko sa command line ko tinira..

---

### Post by dodimar on 2009-05-26
> **loell said:**
> have you tried configuring the device with **bluez**?

perhaps there's an option where you can change it from headset mode to file mode?

[SIZE="1"]Disclaimer: wala akong bluetooth dongle :)[/SIZE]

edit--

try looking at this project too [blueman]("http://blueman-project.org/")

> **boyet said:**
> try mo na ba ang hcitool scan? oo nga the bluez thing....sometimes kung di mag auto connect tong msi blue tooth ko sa command line ko tinira..

Tried the bluez thing, still didn't work... was trying to install Ubuntu 9.04 on vmware, pero lagi may disc error, tried md5summer and merong isang file na di nag match yung hash.. redownloading the ISO..

will check out blueman project..

thanks...

---

### Post by dodimar on 2009-05-26
Solved by using the blueman project...

Thanks :)

...

now .. how do I mark this thread solved? (forgot how)

---

### Post by tagabukid on 2009-05-26
> **dodimar said:**
> Solved by using the blueman project...

Thanks :)

...

now .. how do I mark this thread solved? (forgot how)

that feature has been removed. i hope they bring it back, it was a useful feature..

---

### Post by dodimar on 2009-05-26
mods, mods, mods... please mark this [SOLVED]...

:)

---

### Post by loell on 2009-05-26
done. :)

---

### Post by dodimar on 2009-05-26
> **loell said:**
> done. :)

Thanks boss.. wondering why they removed the option for TS to mark the thread solved?... anyway... still have a bunch of pictures to transfer...

---

