---
title: "Screen auto-rotation is not working for me, and could really do with some help."
date: 2022-10-16
forum: New to Ubuntu
---

### Post by peps123 on 2022-10-16
Hi, new to Ubuntu and just installed it on a Lenovo N23 with a touch screen.


The auto-rotation worked fine on the live media USB and had an option to lock and unlock but, after the full installation, I'm getting no rotation and nothing in the menu.


Seems I can lock and unlock rotation with a Superkey+O but that just shows if it locked on not, doesn't rotate despite being unlooked.


Could really do with some help.


Hardware: Lenovo N23 WinBook


OS: Ubuntu 22.04

Checked the following:

iio-sensor-proxy is installed.

If I run systemctl status iio-sensor-proxy I get:

```
iio-sensor-proxy.service - IIO Sensor Proxy service
     Loaded: loaded (/lib/systemd/system/iio-sensor-proxy.service; static)
     Active: active (running) since Mon 2022-10-17 00:02:26 BST; 11min ago
   Main PID: 682 (iio-sensor-prox)
      Tasks: 3 (limit: 4451)
     Memory: 1.2M
        CPU: 473ms
     CGroup: /system.slice/iio-sensor-proxy.service
             &#9492;&#9472;682 /usr/libexec/iio-sensor-proxy


Oct 17 00:02:25 pigeon-Lenovo-N23 systemd[1]: Starting IIO Sensor Proxy service>
Oct 17 00:02:26 pigeon-Lenovo-N23 systemd[1]: Started IIO Sensor Proxy service.
lines 1-12/12 (END)

```

And when I run monitor-sensor in a terminal and rotate the laptop I get the expected behaviour:

```
$ monitor-sensor
    Waiting for iio-sensor-proxy to appear
+++ iio-sensor-proxy appeared
=== Has accelerometer (orientation: normal)
=== No ambient light sensor
=== No proximity sensor

Accelerometer orientation changed: right-up
    Accelerometer orientation changed: bottom-up
    Accelerometer orientation changed: left-up
    Accelerometer orientation changed: normal


``` 

But the screen doesn't auto rotate....know it can do it as it worked fine on the live USB. I just need some help from someone who know a lot more then me!

---

### Post by MAFoElffen on 2022-10-18
What is the output of:
```

gsettings list-key org.gnome.settings-daemon.plugins.orientation active

```

---

