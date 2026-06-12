---
title: "Python, USB detect notification"
date: 2011-02-26
forum: Programming Talk
---

### Post by xpow on 2011-02-26
Hi,

would somebody tell me how to have a notification if a usb inserted using Python?

Thanks

---

### Post by hakermania on 2011-02-26
I don't know python (yet) but I suppose you'll do a check in /media/ and when a USB is logged in then print your notification?
What is the answer? How to detect the USB or how to print a notification with python? or both?

---

### Post by kostkon on 2011-02-26
HAL (HAL through DBUS would have been an easy thing to do) is now deprecated (although, you may want to follow this road if you want to support versions of Ubuntu older than 10.04 [as unnecessary as it may seem]), so you'll have to use udev. Since pyudev is only [in the 11.04 repos]("http://packages.ubuntu.com/natty/python-pyudev"), you'll use the [gudev python bindings]("http://packages.ubuntu.com/search?keywords=udev+python&searchon=names&suite=natty&section=all").

Your code can be as simple as:
```
#!/usr/bin/env python

import glib
import gudev
import pynotify
import sys


def callback(client, action, device, user_data):
    device_vendor = device.get_property("ID_VENDOR_ENC")
    device_model = device.get_property("ID_MODEL_ENC")
    if action == "add":
        n = pynotify.Notification("USB Device Added", "%s %s is now connected "
                                  "to your system" % (device_vendor,
                                  device_model))
        n.show()
    elif action == "remove":
        n = pynotify.Notification("USB Device Removed", "%s %s has been "
                                  "disconnected from your system" %
                                  (device_vendor, device_model))
        n.show()


if not pynotify.init("USB Device Notifier"):
    sys.exit("Couldn't connect to the notification daemon!")

client = gudev.Client(["usb/usb_device"])
client.connect("uevent", callback, None)

loop = glib.MainLoop()
loop.run()

```

The documentation for the c version of the lib (:sad:) is [here]("http://www.kernel.org/pub/linux/utils/kernel/hotplug/gudev/").
Info about notify-osd [here]("http://wiki.ubuntu.com/NotificationDevelopmentGuidelines").

Hope that helps.

---

### Post by xpow on 2011-02-26
Thanks kostkon for the info, i really appreciate it  I ultimately wants this piece of script to run all the time to detect certain device when inserted, for example: arduino, and when it detects it, another script will run to do operations on the arduino like flashing latest firmware, etc ...  My question is that is it safe to have this script run all the time? Do you think this kind of script will be resourceful hog in the long run?  Thanks

---

### Post by lavinog on 2011-02-28
> **xpow said:**
>   My question is that is it safe to have this script run all the time?
You set the permissions so that the script is read only.
If the script is going to do something specific like flash firmware, make sure that it checks for specific file formats, and does not accept just any file.

> Do you think this kind of script will be resourceful hog in the long run?  Thanks

You can do a check once a second, and use little to no resources.

---

### Post by kostkon on 2011-03-02
> **xpow said:**
> My question is that is it safe to have this script run all the time? Do you think this kind of script will be resourceful hog in the long run?  Thanks
I don't believe so; it will idle 99% of the time, waiting for usb device events to happen (which aren't frequent anyway).

---

