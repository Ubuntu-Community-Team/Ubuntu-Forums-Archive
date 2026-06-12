---
title: "Setting sysfs values using libudev (libudev.h)"
date: 2012-12-17
forum: Programming Talk
---

### Post by mahdiolfat on 2012-12-17
Hi,

I have a few sensor drivers (accelerometer, temperature, RTC) that expose their functionality through sysfs.

I've been using libudev (libudev.h) in my C program to access the sysfs attributes.
In particular, the "[udev_device_get_sysattr_list_value]("http://www.freedesktop.org/software/systemd/libudev/libudev-udev-device.html#udev-device-get-sysattr-value")" gets me the attributes I need.

However, I don't see a way possible for *setting *values in sysfs from libudev.

For example, the RTC has a sysfs interface. I am able to read all the RTC data exposed by the driver (with libudev that is), however, I don't see any way with libudev to set the time. 

Is there a way to set sysfs attribute values through libudev?

Regards,
Mahdi

(btw, very little documentation on libudev :sad:. What's up with that??)

---

