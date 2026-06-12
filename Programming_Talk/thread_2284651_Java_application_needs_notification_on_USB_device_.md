---
title: "Java application needs notification on USB device connection/disconnection"
date: 2015-07-01
forum: Programming Talk
---

### Post by lyf on 2015-07-01
Hi Experts,

I am developing a JAVA application which requires notification on USB device arrival/removal.


How to achieve the same ?

Can I register any callback for the same ?

---

### Post by lisati on 2015-07-01
*Thread moved to **Programming Talk**.*

---

### Post by kostkon on 2015-07-01
> **lyf said:**
> Hi Experts,

I am developing a JAVA application which requires notification on USB device arrival/removal.


How to achieve the same ?

Can I register any callback for the same ?
If you only want  to check for disks then you could use the D-Bus interface of UDisks. You'll also also need to install the java bindings (libdbus-java package.)

If you want to check for USB devices in general, you'll need udev. udev does not provide a D-Bus Interface and there aren't any Java bindings available. Probably the only option is to use libudev and thus you'll need to have your Java app call some C code.

You'll be able to register callbacks in both cases.

There is also the option of creating a udev rule and doing some tricks with that, but it will require the extra step of installing the udev rule (copying the file to a system folder.)

Hope that helps.

---

### Post by lyf on 2015-07-02
Hi kostkon,


In Libudev, I tried the sample code but it seems like continously polling the device arrival and removal notification. It doesn't seems to be straight forward like udev rules file execution.


I tried with udev rules file addition. I am able to trigger an application or execute something on device arrival but is it possible to send the IPC to the JAVA application regarding the same ?

Regards,
Lyf

---

