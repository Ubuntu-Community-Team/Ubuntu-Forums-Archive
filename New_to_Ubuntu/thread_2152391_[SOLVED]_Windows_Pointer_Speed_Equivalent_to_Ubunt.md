---
title: "[SOLVED] Windows Pointer Speed Equivalent to Ubuntu?"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by altirisx on 2013-06-07
I have a Logitech G9X mouse (the mouse has a DPI of 56000). The problem is on Windows my mouse setting is set to something I really like and then on any linux distro the mouse is a lot faster., too fast. I do have Logitech SetPoint installed as well as edited the settings in Windows, is the speed of the mouse on linux the actual speed of the mouse and on Windows its slower or is it linux that speeds it up?


On Windows, I have the pointer settings to 6, I have disabled Enhance pointer precision. What would be the equivalent to this on Ubuntu?

Below is a sample image from a website, the pointer speed is the same on my PC except enhance pointer precision is disabled.
[IMG]http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/900/c03499689.jpg[/IMG]

---

### Post by papibe on 2013-06-07
Hi altirisx.

Open 'System Settings' and go to 'Mouse and Touchpad'.

Regards.

---

### Post by altirisx on 2013-06-07
Ive tried that and it does little to nothing. I figured out on my own actually what the problem is, I have mouse accel. disabled on Windows and when I enabled it I experienced the crazy fast cursor speed that I get on linux. I found a command to disable it, as well as a guide actually. [http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

In the guide it says to use the mouse name from the xinputlist, however if you get an error use the ID name instead.

---

