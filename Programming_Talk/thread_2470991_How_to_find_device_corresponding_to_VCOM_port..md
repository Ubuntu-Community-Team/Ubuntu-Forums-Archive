---
title: "How to find device corresponding to VCOM port."
date: 2022-01-19
forum: Programming Talk
---

### Post by m-elodie on 2022-01-19
Hello!

Not too sure whether this is the right place to post this question, so if you are a moderator and
think it would be better somewhere else, don't hesitate to move this. And please drop me a line
by mail to tell me the new location.

I have made a hardware based on an STM32 chip. It features a VCOM port, and I would like to
connect to it with Ubuntu.

If I run lsusb, I get this line (among others):
Bus 001 device 032: ID 0483:5740 STMicroelectronic virtual COM port

Which seems to indicate that the hardware is recognized.

Usually when writing something to a port, I have to open it (open(/dev/ttysxx with possibly other
parameters).

How should I proceed with this one?
- Is there a device automatically associated with the device above?
- If not, can I associate a device myself
   -> If yes, how can I associate that device with, say, ttySx?
- Is there another way to open a port with the above VCOM?

Thanks for any hint, code snippet or other pointer.

Elodie

---

