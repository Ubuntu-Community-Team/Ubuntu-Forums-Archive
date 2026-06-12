---
title: "HDMI output problem to Samsung TV"
date: 2020-02-08
forum: New to Ubuntu
---

### Post by woses21 on 2020-02-08
Hello everyone,

I made the switch from Windows 7 to Ubuntu 18.04 on an old media pc connected via HDMI to a Samsung TV. The TV did not work in the beginning until I connected a monitor to a DVI port and configured the TV display with proper resolution and refresh rate. Now everything runs smoothly with both the TV and monitor connected. When disconnecting the DVI monitor, the TV drops connection and the TV displays a "Mode Not Supported" error, as if the resolution and refresh rate changed again. I have no idea what is causing this and I don't know how to proceed.

Any ideas?

---

### Post by Autodave on 2020-02-08
Until someone higher on the pay scale comes along, try this:  Power down and only have the monitor connected.  Power up and back off again. Disconnect monitor and hook up TV.  Power up.  See if that works.  I have one such setup here that only works that way.  You may have to reboot once or twice.

---

### Post by grahammechanical on 2020-02-10
Digital TVs and monitors should have a chip containing information about the display. It is called EDID or Extended Display Identification Data. Some TVs do not present clear information to the operating system and the OS cannot set the display software to the correct screen resolution.

This wiki page might help.

[https://wiki.ubuntu.com/X/Config/HDMI](https://wiki.ubuntu.com/X/Config/HDMI)

Also, you have DVI output from the motherboard video card. Do you have DVI input on the TV? You could use that.

Regards

---

