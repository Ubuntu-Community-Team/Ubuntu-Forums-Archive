---
title: "Toggling pins on the serial/parallel port"
date: 2010-07-05
forum: Programming Talk
---

### Post by ownaginatious on 2010-07-05
Hello everyone,

I recently made a small piece of hardware as a project (5 x 11 LED screen with a whole bunch of shift registers).

The only thing I need to do now is somehow interface the computer to it. I have a clock pin, a 'send' pin, and the data pin. I'm guessing using USB is probably way beyond me, so I was thinking of using the parallel port or serial port instead. The only problem is, I have no idea how to control either using C++ or C. Everything I look up online is related to APIs and Windows, and obviously I don't really care about that since I'm not trying to make a true interface between two computers - and since I'm on linux.

I remember years ago using a programming language related to Pascal in Windows called 'Turing', in which I could do:

```
parallelput(number)
```

Where number was some 8-bit number, and the function would simply drop it onto the parallel port.

Is there something that simple for C/C++ in linux?

Thanks!

---

### Post by gordintoronto on 2010-07-06
People who write terminal emulator programs need to be able to control the pins on the serial port, so there is surely a way to, for example, turn on RTS.

---

### Post by ownaginatious on 2010-07-06
> **gordintoronto said:**
> People who write terminal emulator programs need to be able to control the pins on the serial port, so there is surely a way to, for example, turn on RTS.

Awesome to know it's possible :D. Could you possibly explain a bit more what RTS is? I tried to look it up, but there are way too many things that fall under than acronym.

---

### Post by CannibalZerg on 2010-07-06
> **ownaginatious said:**
> 
Is there something that simple for C/C++ in linux?


[http://blog.kirves.pri.ee/2009/03/lpt-programming-example-in-c-for-ubuntu-linux/](http://blog.kirves.pri.ee/2009/03/lpt-programming-example-in-c-for-ubuntu-linux/)

---

### Post by xb12x on 2010-07-06
On Linux (or Windows or MacOS, etc) the O.S. is 'protected': you cannot write directly to the hardware. 
For the serial-port you'll need to call the serial driver. 
The serial driver provides system calls, called i-o-controls (Ioctl's). 
Your application will make an Ioctl call to the driver and the driver will then access the hardware.

See the prototype file sys/ioctl.h to see the commands provided by the serial driver. 

Here's an example in 'C' which opens the serial port and gets the status of its DTR pin.

```

#include <termios.h>
#include <fcntl.h>
#include <errno.h>
#include <sys/ioctl.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h> 


main()
{
  int fd, status;

   fd = open("/dev/ttyS0", O_RDONLY);
   if (ioctl(fd, TIOCMGET, &status) == -1)
      printf("TIOCMGET failed: %s\n",
             strerror(errno));
   else {
      if (status & TIOCM_DTR)
         puts("TIOCM_DTR is not set");
      else
         puts("TIOCM_DTR is set");
   }
   close(fd);
}

```

---

### Post by gordintoronto on 2010-07-07
> **ownaginatious said:**
> Awesome to know it's possible :D. Could you possibly explain a bit more what RTS is? I tried to look it up, but there are way too many things that fall under than acronym.

If you look up RS232 you can find a description of the various pins. Here's an example: [http://www.lammertbies.nl/comm/cable/RS-232.html](http://www.lammertbies.nl/comm/cable/RS-232.html) 

On a 9-pin serial port, the computer only outputs on three of the wires: request to send, data terminal ready and transmit data.

---

