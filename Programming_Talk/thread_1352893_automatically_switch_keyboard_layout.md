---
title: "automatically switch keyboard layout"
date: 2009-12-12
forum: Programming Talk
---

### Post by prince.buster on 2009-12-12
Hey all -

I recently decided to learn to touch type Dvorak. Problem is, my housemates use the laptop all the time, and switching between the layouts would have been hella confusing.

So I bought an apple aluminium external keyboard and spent the afternoon writing a script to automatically switch between Dvorak and USA layouts whenever the keyboard is plugged in or removed.

It's my first attempt as such a thing, so I thought I would see if anyone here can offer any advice / improvements or better solutions.

In particular, is it possible to have two different layouts active simultaneously? one for each keyboard.

Here's the script. It's in Python using HAL and DBus. I added it to my session and it works a charm. Plug in the keyboard and BAM suddenly everything's turned Dvorak. Lovely.

EDIT: not so lovely - adding it to the session seems a bit problematic. How to I get the script to run reliably every time the computer is restarted / put to sleep?
I can get it to stick by starting it with alt-F2 and checking 'save my session', but then, although the script is running, the xmodmap commands have no effect.
Any ideas? I'm heaps out of my depth. Do I have to code a full-on daemon to do this correctly?

```
#!/usr/bin/env python 

# keyboard.py
# automatically changes the keyboard layout when an
# external keyboard with a specific UDI is inserted

keyboard_udi = '/org/freedesktop/Hal/devices/usb_device_5ac_220_noserial'
inserted = False

import dbus
from dbus.mainloop.glib import DBusGMainLoop
import gobject
import os

def added(device_udi):
  if device_udi == keyboard_udi:
    inserted = True
    print "Keyboard in!"
    os.system("setxkbmap dvorak")

def removed(device_udi):
  if device_udi == keyboard_udi:
    inserted = False
    print "Keyboard out!"
    os.system("setxkbmap us")

DBusGMainLoop(set_as_default=True)
dbus_system_bus = dbus.SystemBus()

hal_object = dbus_system_bus.get_object('org.freedesktop.Hal','/org/freedesktop/Hal/Manager')
hal_interface = dbus.Interface(hal_object, 'org.freedesktop.Hal.Manager')

if hal_interface.DeviceExists(keyboard_udi):
  inserted = True
  print "Keyboard is already in"
  os.system("setxkbmap dvorak")
else:
  os.system("setxkbmap us")
    
hal_interface.connect_to_signal('DeviceAdded', lambda *args: added(*args))
hal_interface.connect_to_signal('DeviceRemoved', lambda *args: removed(*args))

loop = gobject.MainLoop()
loop.run()
# end script
```

---

### Post by prince.buster on 2009-12-13
somebody else done the same thing [here]("http://ubuntuforums.org/showthread.php?t=350464")

---

