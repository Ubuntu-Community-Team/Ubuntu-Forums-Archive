---
title: "User Input Python"
date: 2008-03-30
forum: Programming Talk
---

### Post by klanman8908 on 2008-03-30
Task:
Make a python program that locks the computer when a particular flash drive is removed.  Unlock the computer when the flash drive is reinserted.

Problem:
How does one block user input from mouse and keyboard globally?

Suggested Solutions:
1.```

import os

if usbdrive == true:
    os.system('rmmod [the correct modules to remove input]')
elif usbdrive == false:
    os.system('modprobe [the correct modules to remove input]')

```.(No clue which modules I need to remove I tired multiple modules to no avail.)
2. start and stop a screen saver (not preferred but could work)

Thanks in advance for any help.



Kyle

---

### Post by Jacks0n on 2008-04-01
Hm, ok. As far as I know, removing modules are for the kernel, not individual devices. So I *suppose* you could remove the module responsible for the usb stack (usbcore?), but you'd have to restart, no usb devices would work and it'd be very ugly.

Your best bet is probably making a loop looking for the folder '/media/nameofdrive' where it's mounted, and then execute 'gnome-screensaver-command -a' if it exists.

eg..

```

import os
import time

while True:
	# Mounted
	if os.path.exists('/media/nameofdevice'):
		os.system('gnome-screensaver-command -a')

		while True:
			# Mounted => Unmounted
			if not os.path.exists('/media/nameofdevice'):
				break
			else:

			time.sleep(1)

	time.sleep(1)

```

That won't stop the screen saver though. Google for dbus and the gnome screensaver for that.

- Jackson

---

### Post by klanman8908 on 2008-04-02
Thanks for the reply Jacks0n.  After talking with someone else I decided that rmmod a module was not the route to go.  The person recommended taking away input from other programs using pygame.  In short  I create a surface the size of the monitor and don't allow other programs to grab input.

```

import time
import pygame

pygame.init()
locked = True

while 1:
    time.sleep(1)
    try:
         file=open('/media/[devicename]', 'r')
         key = file.readline()
         if key[0:4] == [chosen key code]
             pygame.display.quit()
             locked = False
    except:
        if locked:
            pass
        else:
            pygame.display.set((2560,1024),pygame.FULLSCREEN)
            pygame.event.set_grab(0)
            locked = True


```

My seems to be more complex.  I plan on adapting it to use the os.path.exist instead of checking the file like you suggested I didn't do this in the first place because I wasn't aware the option existed.  As for the screen saver vs. pygame both lack the ability to disable dropping into a virtual terminal and executing commands that way.

---

### Post by nanotube on 2008-04-02
> **klanman8908 said:**
> Thanks for the reply Jacks0n.  After talking with someone else I decided that rmmod a module was not the route to go.  The person recommended taking away input from other programs using pygame.  In short  I create a surface the size of the monitor and don't allow other programs to grab input.

```

import time
import pygame

pygame.init()
locked = True

while 1:
    time.sleep(1)
    try:
         file=open('/media/[devicename]', 'r')
         key = file.readline()
         if key[0:4] == [chosen key code]
             pygame.display.quit()
             locked = False
    except:
        if locked:
            pass
        else:
            pygame.display.set((2560,1024),pygame.FULLSCREEN)
            pygame.event.set_grab(0)
            locked = True


```

My seems to be more complex.  I plan on adapting it to use the os.path.exist instead of checking the file like you suggested I didn't do this in the first place because I wasn't aware the option existed.  As for the screen saver vs. pygame both lack the ability to disable dropping into a virtual terminal and executing commands that way.

well, if a person has physical access and can drop into a vty, and knows the username/password to log in... then you are already playing a losing game - he can just reboot the box into single-user mode!

so maybe it will help if you tell us exactly what problem you are trying to solve with this. :)

also, fyi, in my output of modprobe -l, i found the following that may be relevant:
```

lib/modules/2.6.20-16-generic/kernel/drivers/input/keyboard/xtkbd.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/keyboard/sunkbd.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/keyboard/stowaway.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/keyboard/newtonkbd.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/keyboard/lkkbd.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/pc110pad.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/inport.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/sermouse.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/psmouse.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/logibm.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/vsxxxaa.ko

```
so i'm betting removing the kbd and mouse modules (possibly only a selection thereof) would disable kbd and mouse input.

---

### Post by klanman8908 on 2008-04-03
I would quote this but I don't have a mouse currently. I think I will have to reboot.  Removing all the modules worked but 3 did not reinsert right: logibm, vsxxxaa, and pc110pad.  I realize I'm fighting a loosing battle and have decided that what I have now is as secure as a screen saver and will suffice.

---

