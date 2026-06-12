---
title: "Serial Port transmission not working"
date: 2009-07-31
forum: Programming Talk
---

### Post by hthakar on 2009-07-31
I am trying serial communication on Ubuntu 9.04 using C/C++. 

I have installed GtkTerm & minicom after unsuccessfully trying various C codes. Both these applications do not transmit the data.There is no write error as such but the data is not transmitted immediately on the bus. 
Seems that the write operation only updates the transmit buffer and doesn't transmit the data on serial bus.

This occurs while using a null modem (loop-back) as well as connecting to another PC.

The transmission occurs only after receiving some data from the other terminal.
can someone help us on this?

regards,
Harsh

---

### Post by jpkotta on 2009-08-01
For your C code, try tcdrain().  See also the termios(3) man page.
[QUOTE="man termios"]
#include <termios.h>
#include <unistd.h>
int tcdrain(int fd);

       tcdrain()  waits  until all output written to the object referred to by
       fd has been transmitted.

[/QUOTE]

I have never had such a problem with minicom.  You may want to try screen in tty mode or kermit.

---

### Post by hthakar on 2009-08-02
Hey..Thanks for the answer.
I tried per your suggestions, but didn't work.
Same results with Kermit as well, there is no transmission unless some byte is received.:(
Any idea?
regards,

---

### Post by jpkotta on 2009-08-02
Does it work perfectly after receiving one piece of data?  Or does it only transmit a limited number of bytes after receiving one?

How do you know that it isn't transmitting?  Are you looking at the TX pin with an oscope or voltage meter or something like that?

You could try simply dumping data into the device file, but this isn't much different than writing to it from a C program.
```
echo hello > /dev/ttyS0
```

Sometimes you need to enable a serial port in the BIOS, but that's probably not the problem because you say it works sometimes.

That's about all I can think of.

---

### Post by hthakar on 2009-08-03
After receiving some byte, The string that was typed previously is transmitted. For instance if I type ABCD followed by ENTER key, then the string "ABCD" is transmitted once I receive a byte.
I also verified this with oscilloscope. 

The behavior is always like that. The data written to the port is always held in the Tx buffer and actual transmission is triggered by some reception!

---

### Post by hthakar on 2009-08-06
ok! I tried to use the same program with another PC having an embedded RS232 port and everything works fine. 

If I use the RS232 connected through a PCI slot then the problem occurs. 

Any idea??

---

### Post by jpkotta on 2009-08-06
Probably a bug in the driver.  Maybe try a USB to serial converter.  They're very cheap and I've had good luck with them.

---

