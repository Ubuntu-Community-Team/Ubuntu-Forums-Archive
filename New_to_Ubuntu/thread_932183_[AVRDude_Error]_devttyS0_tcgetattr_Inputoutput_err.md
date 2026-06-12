---
title: "[AVRDude Error] /dev/ttyS0: tcgetattr: Input/output error"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by cackharot on 2008-09-28
hi guys,
i build a new avr programmer(ponyser) and connected to my serial port
when i run this 'avrdude -c ponyser -p m8 -V -U flash:w:led.hex' 
i get the following

type=SERBB
/dev/ttyS0: tcgetattr: Input/output error

avrdude done.  Thank you.

HELP ME!
the hardware is fine and i checked the electrical conn
also 'setserial -a /dev/ttyS0'  yields

/dev/ttyS0, Line 0, UART: unknown, Port: 0x03f8, IRQ: 4
        Baud_base: 115200, close_delay: 50, divisor: 0
        closing_wait: 3000
        Flags: spd_normal

Thanks

---

### Post by cackharot on 2008-09-28
soryy guys
i figured it out myself
i got the problem solved

demesg | grep ttyS0

[   16.340066] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.341020] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, unknown : , Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal

see unkown in the o/p of setserial and from dmesg i got uart type is 16550A

so use this command and everything goes alright

setserial /dev/ttyS0 uart 16550A

thanks guys

---

### Post by gap113 on 2011-06-17
> **cackharot said:**
> soryy guys
i figured it out myself
i got the problem solved
 
demesg | grep ttyS0
 
[ 16.340066] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 16.341020] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 
setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, unknown : , Port: 0x03f8, IRQ: 4
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal
 
see unkown in the o/p of setserial and from dmesg i got uart type is 16550A
 
so use this command and everything goes alright
 
setserial /dev/ttyS0 uart 16550A
 
thanks guys
 
Plz help me also....i m also getting same following error
**/dev/ttyS0: tcgetattr: input/output error**
i d tried ur method
**setserial /dev/ttyS0 uart 16550A**
but it is giving error as
**operation not permitted **
so what should i do now please guide in details
 
thanks

---

