---
title: "Experiencing Screen Tearing when Plugging In or Adjusting Monitors in Any Way"
date: 2023-02-09
forum: New to Ubuntu
---

### Post by angomangooss on 2023-02-09
[U]Device: ASUS Vivobook 15
Graphics Card: Intel iRIS Xe Graphics
Version: Ubuntu 20.04[/U]

Monitors fail to function with this version of Ubuntu. 

[I]After making this tweak:

```apt install linux-oem-20.04 && sudo reboot 0```[/I]

I was able to successfully get Ubuntu 20.04 to recognize my second monitor through the HDMI port. However, [both screens experience huge tears]("https://i.stack.imgur.com/uA6sl.png") (The top monitor is the external HDMI monitor. The bottom monitor is the built-in display) upon making the slightest adjustment of the monitor position in the "Displays" setting.

Furthermore, when disconnecting the HDMI monitor and reconnecting it, both screen goes fully black and ceases to function except for a lone mouse forcing a reboot. I have no screenshot I can provide with this one.

** What could possibly be causing this issue?**

This situation is only resolved upon rebooting. However, if you adjust the monitors once more, or remove the HDMI, then it breaks again.

---

### Post by angomangooss on 2023-02-09
As of now, this solution worked for me:
[https://askubuntu.com/a/1237079/1053554](https://askubuntu.com/a/1237079/1053554)

---

