---
title: "HTC Desire no recognised in Eclipse?"
date: 2010-07-26
forum: Programming Talk
---

### Post by ojdon on 2010-07-26
Hi there, hopefully this is in the correct forum. Basically, I've just started out programming for the Android platform and I want to test my application on my phone which is a HTC Desire. I've read around and I've seen there are a few fixes to make sure the HTC Desire is recognised. But I'm still running into issues. 

Now, when running "adb devices" I get this result: 
```
List of devices attached 
HT05WPL07209	device

```

But when I go to the Run options in Eclipse it still doesn't recognise the phone: 
[IMG]http://img825.imageshack.us/img825/1653/screenshotandroiddevice.png[/IMG]
Does anyone know the problem? 

Thanks

---

### Post by ojdon on 2010-07-26
Urgent BUMP.

---

### Post by der_Lukas on 2011-01-04
Create/Edit file ```
/etc/udev/rules.d/51-android.rules
```
Add following line ```
SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```
change rights with ```
chmod a+r
```
of course, you need to run commands with sudo

(Re)start Eclipse
Should work with all HTC Phones, for others change idVendor

---

### Post by tapin13 on 2011-04-07
thanks a lot!!! \\:D/

---

