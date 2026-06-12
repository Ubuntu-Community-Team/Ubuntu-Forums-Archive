---
title: "Python. How to send binary data trough serial port?"
date: 2008-06-14
forum: Programming Talk
---

### Post by rlameiro on 2008-06-14
I'm helping a friend of me in a project with microcontroller (atmel). I need to send bytes trough the serial port. I have found the pyserial, and USPP libs for python. I have tested some programs, but I cant send raw binary numbers, or bytes. I can send ascii, but no binary. any one have some idea how to do this?
thanks

---

### Post by mindwarp on 2008-07-03
> **rlameiro said:**
> I'm helping a friend of me in a project with microcontroller (atmel). I need to send bytes trough the serial port. I have found the pyserial, and USPP libs for python. I have tested some programs, but I cant send raw binary numbers, or bytes. I can send ascii, but no binary. any one have some idea how to do this?
thanks

```
tty=SerialPort("/dev/ttyUSB0", 1000, 9600)
output = ''
output = '' + chr(0x08) + chr(0x11) 

tty.send(output)
```

That should work

---

### Post by encompass on 2009-10-20
I tried it with the following result:
```

ser.send(output)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Serial' object has no attribute 'send'

```
I have imported serial.
```
import serial
```
And the object seems to be working as I can write other data and see it travel in the line.
Best Regards.

---

### Post by Zugzwang on 2009-10-20
> **encompass said:**
> I tried it with the following result:
```

ser.send(output)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Serial' object has no attribute 'send'

```
I have imported serial.


Looks like "send" has been renamed(?) to "write"

---

### Post by encompass on 2009-10-20
Cool, that is what I was using before.  I actually ran accross a conversion system as well.
[It's in these python Docs.]("http://docs.python.org/library/struct.html")
Let's see what the difference is.

---

### Post by jpkotta on 2009-10-21
struct is great for some things.  If you just need to write some bytes, it's not difficult to convert numbers to a string of arbitrary bytes.
```

l = [0x30, 0x31, 0x32]
s1 = "".join([chr(x) for x in l])
s2 = "\x30\x31\x32"
s3 = "123"
s1 == s2 == s3 # True

```

---

