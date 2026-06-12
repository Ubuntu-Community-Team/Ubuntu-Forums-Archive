---
title: "Turn Bluetooth off by default AC 7260 wifi + bluetooth card - 14.04"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by OpenFerret on 2014-06-02
Hi all,

Does anyone know how to make Ubuntu 14.04 start with the Bluetooth powered off?

I've tried editing the main.conf file at:

/etc/bluetooth/main.conf

But nothing seems to work, it always defaults to on.

---

### Post by slickymaster on 2014-06-02
There's actually a already reported bug on LP about this issue: [Bug #1296554]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1296554"), surprisingly marked with a _Fix Released_ status but no indications whatsoever in what package.

There's something you could try though, add the line```
rfkill block bluetooth
```above the line```
exit 0
```to your **/etc/rc.local** file.

---

### Post by OpenFerret on 2014-06-02
The only issue is with this is that it will block bluetooth entirely won't it?  I just wish for Ubuntu to start with it off, as opposed to stop it completely.

---

### Post by slickymaster on 2014-06-02
This will keep bluetooth turned off when you boot/login but you can still turn it on at will with the bluetooth applet in the panel.

---

### Post by OpenFerret on 2014-06-02
> **slickymaster said:**
> This will keep bluetooth turned off when you boot/login but you can still turn it on at will with the bluetooth applet in the panel.

My apologies, you're right.  It is on for like a second or so when logging in... But it does default to off.  Good temporary fix until the bug is actually solved.

Many thanks!!!

---

### Post by slickymaster on 2014-06-03
You're welcome. Happy *buntuing.

---

