---
title: "keyboard control library, or program?"
date: 2012-02-06
forum: Programming Talk
---

### Post by conradin on 2012-02-06
Hi all,
Ive been working with the keyboard lately, and have wondered: 
If I can control the LEDs on the keyboard, I would have a wonderfully available device to get data from and drive outputs (Ill handle the electric part of this) So I'm wondering, if there a program in Linux I can build a struct around in C that will allow me to listen for key presses, and freely control the keyboard lights?

---

### Post by MG&amp;TL on 2012-02-06
I don't know if [this]("http://www.linuxtopia.org/online_books/Linux_Kernel_Module_Programming_Guide/x1174.html") helps much?

---

### Post by conradin on 2012-02-07
It looks like it would be helpful, but there are a couple files missing?
my system doesn't recognize 
#include <linux/module.h>
#include <linux/config.h>
#include <linux/init.h>
and none of this:
  /usr/src/linux/drivers/char/vt_ioctl.c, function vt_ioctl().
  /usr/src/linux/drivers/char/keyboard.c, function setledstate().
They might be nice, but I dont know where they are. 
What is nice about this article is it tells me ioctl is the way to go.

---

### Post by MG&amp;TL on 2012-02-07
Unless I'm mistaken, you probably need the linux source to include those headers...I'm looking it up, but it was quite difficult last time I tried...

If that seems bit big an effort just to blink some LEDs, you could see if [ledd]("http://manpages.ubuntu.com/manpages/hardy/man8/ledd.8.html") has an API, otherwise you'll have to include <stdlib.h> and use system().

---

### Post by conradin on 2012-02-08
LEDD, ledcontrol, xset, and others have all looked cool but have not been things I can figure out how to make work. I would think the lights are an address, and that I should be able to flip some bits and make the think light or turn off. but I cant seem to figure this out!:confused::confused:

---

### Post by juancarlospaco on 2012-02-08
```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
import fcntl
import os
import time

# here is what are you looking for my young padawan...
KDSETLED = 0x4B32
SCR_LED  = 0x01
NUM_LED  = 0x02
CAP_LED  = 0x04

console_fd = os.open('/dev/console', os.O_NOCTTY)

all_on = SCR_LED | NUM_LED | CAP_LED
all_off = 0

while 1:
    fcntl.ioctl(console_fd, KDSETLED, all_on)
    time.sleep(0.1) 
    fcntl.ioctl(console_fd, KDSETLED, all_off)
    time.sleep(0.1) # Here changes the Timming, or something more complex

```

---

### Post by conradin on 2012-02-08
ZOMG! Something did something!! 
I have so many questions about the force! How do I control it?
(I'm new to python this week)

---

### Post by juancarlospaco on 2012-02-09
To control the Force you learn must:

```

import fcntl;help(fcntl)

```

---

