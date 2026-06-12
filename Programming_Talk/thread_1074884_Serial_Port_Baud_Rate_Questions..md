---
title: "Serial Port Baud Rate Questions."
date: 2009-02-19
forum: Programming Talk
---

### Post by leachja on 2009-02-19
I've been doing quite a bit of research into how to modify the baud rate of serial ports in linux. 

stty works well for me, but I am only able to use it to set the ports to the standard baud rates. 

I believe I know a way to use setserial (115200 divisor 32) to get the non-standard rates that I need, but I am using a usb to serial port and setserial will not function with these devices (when you use ttyUSB** it fails). 

If anyone has any ideas I would be very appreciative.

Thanks,
Jared

---

