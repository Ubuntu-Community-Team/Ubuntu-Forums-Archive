---
title: "Python - how to send bytes to serial port?"
date: 2012-01-25
forum: Programming Talk
---

### Post by Miha1l on 2012-01-25
hello, i trying to send bytes over serial port, but there is some problems,

```
ser.write("\x06\x10\x46\x46")
```
works fine, but when i try to do it in function, there is no bytes are sended, only ascii codes

```

#!/opt/bin/python

import serial, string

def write_port(data):
#usage write_port("06 10 46 46")
	dataB = ""
	data = data.split(' ')
	for i in range(len(data)):
		data[i] = r"\x" + data[i] # raw add "\x" so line is \x06\x10\x46\x46

	dataB = "".join(data)
	ser.write( dataB )

print "Python 2.7\n\n"

ser = serial.Serial('/dev/usb/tts/2', 115200, timeout=1)

print "write bytes.."
write_port("06 10 46 46")

```

my function convert "06 10 46 46" to "\x06\x10\x46\x46", so i expect it should works like
ser.write("\x06\x10\x46\x46"), but it does not - it send like a string without transform "\x" symbols :(

---

### Post by Zugzwang on 2012-01-25
The point is that the translation of these "\x..." sequences is done when reading the .py script. To do so during runtime, you need to use some function like "bin(int(X,16))" for X="4e" or something like that.

---

### Post by Miha1l on 2012-01-25
thanks it was chr() function, so we should transform String list to Integer list and convert chr(int,16)

here is works code:

```
def write_port(data):
# write_port("06 10 46 46")
	dataB = []
	data = data.split(' ')
	for i in range(len(data)):
		dataB.insert(i,int(data[i],16))
	ser.write( "".join(chr(i) for i in dataB) )
```

---

### Post by epicoder on 2012-01-25
If you are using Python 3, this function could be better implemented with a star argument. That would make it easier to, for instance, mathematically compute ascii codes to write and then pass them in.

```
def write_port(*data):  # write_port(6, 10, 46, 46)
    dataB = []
    for i in range(len(data)):
        dataB.insert(i,int(data[i],16))
    ser.write( "".join(chr(i) for i in dataB) )

```This will take all arguments and compile them into a tuple.

```
write_port(3)
data=(3,)

write_port(23, 54)
data=(23, 54)
```

---

### Post by nvteighen on 2012-01-26
> **sh228 said:**
> If you are using Python 3, this function could be better implemented with a star argument. That would make it easier to, for instance, mathematically compute ascii codes to write and then pass them in.


That also works in Python 2.7... and I think I've even used that in 2.5, but not sure.

---

### Post by yanes on 2012-03-21
Hi,
I need to send some bytes via serial port USB , on ubuntu 11.10 and
from  the example made above

ser = serial.Serial('**/dev/usb/tts/2**', 115200, timeout=1)

the file :*** '/dev/usb/tts/2 '*** relative to serial port doesn't exists .
Please, which file have I to use ?
in my dev directory there is no dir named 'usb' and in the same dir I found
"ttys0 , .... to ttys28 " & "usbmon0 , ... to usbmon7 " 
I tried '/dev/usbmon0' and get the error :**[COLOR=Navy]Could not configure port: (25, 'Inappropriate ioctl for device') [/COLOR]**(this requires su privileges )
I tried also '/dev/ttyS0'  and get the error : **[COLOR=Navy]Could not configure port: (5, 'Input/output error')[/COLOR]**

which one is the correct file relative to usb port ?
thanks in advance ):P

---

### Post by Zugzwang on 2012-03-21
> **yanes said:**
> which one is the correct file relative to usb port ?


Run "dmesg" from the terminal. This will show you the kernel log. Somewhere there is a message by the driver for you USB-to-Serial adapter. The message will contain the information where the device was hooked into the file system.

---

