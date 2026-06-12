---
title: "Sending command to USB device"
date: 2011-11-07
forum: Programming Talk
---

### Post by mtangoo on 2011-11-07
Hi I need to send AT Command to Linux device (Modem/Phone) connected via USB. Is there a way? I'm reading about libudev right now. Is it good solution?
Thanks!

---

### Post by haqking on 2011-11-07
> **mtangoo said:**
> Hi I need to send AT Command to Linux device (Modem/Phone) connected via USB. Is there a way? I'm reading about libudev right now. Is it good solution?
Thanks!

[s]minicom

[https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)

where your device is likely to be ttyusbx or similar[/s]

Edit: My bad just realised this isnt what you were after

---

### Post by mtangoo on 2011-11-07
> **haqking said:**
> [s]minicom

[https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)

where your device is likely to be ttyusbx or similar[/s]

Edit: My bad just realised this isnt what you were after

No problem! Do you have any idea how I can go about? I just asked also on SO

---

### Post by ofnuts on 2011-11-07
> **mtangoo said:**
> Hi I need to send AT Command to Linux device (Modem/Phone) connected via USB. Is there a way? I'm reading about libudev right now. Is it good solution?
Thanks!

See [http://tldp.org/HOWTO/Serial-HOWTO-10.html](http://tldp.org/HOWTO/Serial-HOWTO-10.html)
If configured properly you only need to write the bytes (or even just copy a file or issue "echo {bytes} > /dev/ttySx") to the right device.

---

### Post by matt_symes on 2011-11-07
Hi

> **mtangoo said:**
> Hi I need to send AT Command to Linux device (Modem/Phone) connected via USB. Is there a way? I'm reading about libudev right now. Is it good solution?
Thanks!

I'm pretty sure that libudev is only used to discover device nodes; it enumerates sysfs. I don't think it can be used to send and receive commands to the device but it will give you the node (i believe). Can't you write to that ?

You are writing this in C ?

Kind regards

---

### Post by mtangoo on 2011-11-07
> **matt_symes said:**
> Hi
Hello!

> **matt_symes said:**
> I'm pretty sure that libudev is only used to discover device nodes; it enumerates sysfs. I don't think it can be used to send and receive commands to the device but it will give you the node (i believe). 
After reading and reading you are right!

> **matt_symes said:**
> Can't you write to that ?
I'm very new to this arena!

> **matt_symes said:**
> You are writing this in C ?

Kind regardsYes, C or C++
Thanks for comment!

---

### Post by matt_symes on 2011-11-08
Hi

Try writing to it as you would any device node.

Best of luck. It sounds like an interesting project.

Kind Regards

---

### Post by mtangoo on 2011-11-08
> **matt_symes said:**
> Hi

Try writing to it as you would any device node.

Do you mean using ifstream/ofstream or what?
Should I treat it as file?
> **matt_symes said:**
> Best of luck. It sounds like an interesting project.

Kind Regards
Quiet interesting

---

### Post by matt_symes on 2011-11-08
Hi

> Should I treat it as file?Yes. Just treat it like a normal file. Be aware of permissions on the node.

> Do you mean using ifstream/ofstream or what?

I have never tried it in C++. Can't see it being different though as you are still writing to a file.

In C you fopen, fread, fputs, fwrite, fclose.

Have a look at this C example. It may give you some ideas. I don't know how sophisticated your program needs to be.

[http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html](http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html)

Kind regards

---

### Post by mtangoo on 2011-11-08
> **matt_symes said:**
> Hi

Yes. Just treat it like a normal file. Be aware of permissions on the node.



I have never tried it in C++. Can't see it being different though as you are still writing to a file.

In C you fopen, fread, fputs, fwrite, fclose.

Have a look at this C example. It may give you some ideas. I don't know how sophisticated your program needs to be.

[http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html](http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html)

Kind regards
I appreciate your help and link!

---

### Post by takobaba on 2013-05-05
> **mtangoo said:**
> Hi I need to send AT Command to Linux device (Modem/Phone) connected via USB. Is there a way? I'm reading about libudev right now. Is it good solution?
Thanks!



hi 
recently i was searching for this and i got the solution with pyserial which is really simple to use as i found.

here is my little script for you if you wanna take a look

```

#!/usr/bin/env python

import serial
import time

tarik = " "
ser = serial.Serial("/dev/ttyUSB0",115200, 8, 'N', 1, timeout=None)

```

this is a code that opens connection to device 

/dev/ttyUSB0
with baud rate of 115200
data bits of 8
parity of none
stop bit of 1
timeout set to None

cheers

---

