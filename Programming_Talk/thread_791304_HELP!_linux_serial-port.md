---
title: "HELP! linux serial-port?"
date: 2008-05-12
forum: Programming Talk
---

### Post by taehC on 2008-05-12
hello i just posted about avr-gcc
now i have another error which i didn't notice at first  
it says there is no such thing as com1(which i thought was the serial, but i guess that only windows) what is the serial port for linux called?

---

### Post by LaRoza on 2008-05-12
> **taehC said:**
> hello i just posted about avr-gcc
now i have another error which i didn't notice at first  
it says there is no such thing as com1(which i thought was the serial, but i guess that only windows) what is the serial port for linux called?

In /dev:
```

ttyS0-ttyS3 

```

---

### Post by taehC on 2008-05-12
i am not sure exactly  how to use what you just gave me...
sry im a noob
there is a file called Makefile
inside the file there is a line of txt that says 
```
AVRDUDE_PORT = com1
```
what exactly do i change com1 to?
please help!

---

### Post by WW on 2008-05-12
Change com1 to /dev/ttyS0.

---

