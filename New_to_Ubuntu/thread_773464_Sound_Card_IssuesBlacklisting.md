---
title: "Sound Card Issues/Blacklisting"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by MasterCylinder on 2008-04-28
My sound is kind of iffy. I can get it to test fine to the 'CAO106' driver, but thats all it will do. I cant listen to music, YouTube, no system sounds, or anything. I have restarted atleast severl times. I worked for about five minutes earlier today, but now it is no longer working.

I have been doing a little googling as to what my problem is. I think that Ubuntu is reading two drivers for my card, and using the wrong one 'ICH6'. And I am trying to blacklist it. I found the file where the blacklisted drivers live (/etc/modprobe.d/blacklist) and made a new entry on the bottom.

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# causes sound to malfunction
blacklist snd_ICH6



However when I go to save the file I get a "You do not have permission to save this file" message... help?

---

### Post by southernman on 2008-04-28
May or may not be related but, please look at the following thread. Try the fixes mentioned in it.

Can't hurt, right? ;)

---

