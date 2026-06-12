---
title: "How to catch the &quot;usb mass storage inserted&quot; signal?"
date: 2006-10-23
forum: Programming Talk
---

### Post by ckh on 2006-10-23
Hello everybody,

I have lots of SD-cards and need to
  1. create 2 partition to an inserted SD-card
  2. copy some files in to these 2 partitions

so I plan to wrote a program to:
  1. disable the auto-mount mechanism in ubuntu
  2. partition the SD-card when I insert an SD-card (call parted)
  3. mount these 2 partitions
  3. copy some files to it (call cp)
  4. umount SD-card
  5. promt message to insert the next card  (loop 3-5)
  6. restore the auto-mount mechanism before exit program
  

but I don't know how to 
  1. disable auto-mount mechanism
  2. catch the "SD-card inserted" signal
     (the timing ubuntu will mount sd-card, and open a nautilus window)
     (I need to replace it with my program)
     
anybody can help me?:confused: 
thank you in advanced for any helpful infomation!!:D 


-ckh

---

### Post by Ragazzo on 2006-10-24
I found this in [udev's FAQ]("http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev-FAQ"):

"Q: Can I use udev to automount a USB device when I connect it?
A: Technically, yes, but udev is not intended for this. All major distributions
   use HAL ([http://freedesktop.org/wiki/Software_2fhal](http://freedesktop.org/wiki/Software_2fhal)) for this, which also
   watches devices with removable media and integrates into the desktop software."

I was first going to suggest udev but it seems you should look into HAL (I don't know anything about it).

Edit: Here's a Python program that catches these signals ([source]("http://dbus.freedesktop.org/doc/dbus-tutorial.html")):

```

#!/usr/bin/env python

import gobject 
import dbus
if getattr(dbus, 'version', (0,0,0)) >= (0,41,0):
    import dbus.glib

def device_added_callback(udi):
    print 'Device with udi %s was added' % (udi)

def device_removed_callback(udi):
    print 'Device with udi %s was added' % (udi)

def device_capability_callback(udi, capability):
    print 'Device with udi %s added capability %s' % (udi, capability)

bus = dbus.SystemBus()
hal_manager_obj = bus.get_object('org.freedesktop.Hal', 
                                 '/org/freedesktop/Hal/Manager')
hal_manager = dbus.Interface(hal_manager_obj,
                             'org.freedesktop.Hal.Manager')

hal_manager.connect_to_signal('DeviceAdded', device_added_callback)
hal_manager.connect_to_signal('DeviceRemoved', device_removed_callback)
hal_manager.connect_to_signal('NewCapability', device_capability_callback)

mainloop = gobject.MainLoop()
mainloop.run()

```

---

### Post by ckh on 2006-10-24
Hello Ragazzo:
Thanks for your great infomation,
I just tried the script, it works!
and I will start to study into it.

Thank you very much!!

-ckh

---

