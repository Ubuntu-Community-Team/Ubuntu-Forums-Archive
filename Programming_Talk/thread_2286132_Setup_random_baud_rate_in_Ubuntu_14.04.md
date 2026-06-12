---
title: "Setup random baud rate in Ubuntu 14.04"
date: 2015-07-10
forum: Programming Talk
---

### Post by fsantosa on 2015-07-10
Hi all,

I am a newbie in developing software in Ubuntu. My task now is to create an application that platforms-independent (has to be run in Ubuntu, Mac Os X, and Windows).
I use c++ with dependencies to the standard libraries and boost 1.58.0.

The application has usb and uart communication to the target device. I chose HIDAPI library, and it run without any problem in all platforms.
For the serial communication (UART), Ubuntu implementation still face problem to run unusual baud rate. The unusual baud rate that I mean here is an integer such as 9601, 19201.
The addition of '1' is required to run some initialization on the target devices.

-        In windows: I used asio library as normal way, put the custom baud rate, and it works fine.
-        In Mac: I have to setup something different, use function: ioctl (fd_, _IOW('T', 2, speed_t), &initBaudRate, 1); //initBaudRate is 9601,19201,and so on
-        In Ubuntu I found some references from the internet, but unfortunately still bring no luck

Ubuntu trials:
o   first trial:
using the same as Mac implementation and the result is failed
 
o   second trial:
 
[TABLE="width: 825"]
[TR]
[TD]1
2
3
4
5
6[/TD]
[TD]struct serial_struct serialsettings;
ioctl(fd, TIOCGSERIAL, &serialsettings);
serialsettings.flags &= ~ASYNC_SPD_MASK;
serialsettings.flags |= ASYNC_SPD_CUST;
serialsettings.custom_divisor = 96;
ioctl(fd, TIOCSSERIAL, &serialsettings);[/TD]
[/TR]
[/TABLE]
 
Unfortunately this method using divisor with integer parameters, so I could not get 9601 in anyways.
 
o   third trial:
 
[TABLE="width: 825"]
[TR]
[TD]1
2
3
4
5
6
7
8
9
10[/TD]
[TD]#include <asm/termios.h>
 
struct termios2 tio;
ioctl(fd, TCGETS2, &tio);
tio.c_cflag &= ~CBAUD;
tio.c_cflag |= BOTHER;
tio.c_ispeed = 31250;
tio.c_ospeed = 31250;
/* do other miscellaneous setup options with the flags here */
ioctl(fd, TCSETS2, &tio);[/TD]
[/TR]
[/TABLE]
 
Source: [http://www.downtowndougbrown.com/2013/11/linux-custom-serial-baud-rates/](http://www.downtowndougbrown.com/2013/11/linux-custom-serial-baud-rates/)
 
Have a big hope on this one, but still failed to get the exact baudrate.

I don't ask the exact solution for this, but if you could link me to a better source that explains how the register of serial port set in Linux,
I really appreciate it! :)

Best regards,
Fatma

---

### Post by howefield on 2015-07-10
Thread moved to the "*Programming Talk*" forum for better chance of support.

---

### Post by fsantosa on 2015-07-10
Thanks for considering this, howfield![COLOR=#000000] [/COLOR]

---

### Post by ofnuts on 2015-07-11
Tried this? [http://stackoverflow.com/questions/12646324/how-to-set-a-custom-baud-rate-on-linux](http://stackoverflow.com/questions/12646324/how-to-set-a-custom-baud-rate-on-linux)

---

### Post by fsantosa on 2015-07-13
Hi ofnuts,

thanks for your suggestion! already tried this one too. but still no good result comes from this..

---

