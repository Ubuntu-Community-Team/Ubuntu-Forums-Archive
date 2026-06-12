---
title: "PySerial Not writing to sensor."
date: 2017-05-30
forum: Programming Talk
---

### Post by eraserpencil on 2017-05-30
The sensor I'm using comes only with Windows software, but I'm writing(learning to write) a driver for the sensor to work with Raspberry Pi etc.

I have am using Python 3 and PySerial 3.0.1. I am new to the forum and hence do pardon my formatting.

I have the following code

```
port = serial.Serial("/dev/ttyUSB0", baudrate=9600, timeout=20, bytesize=8, rtscts =1,dsrdtr=1, write_timeout = 10)

port.send_break()
while (1):
    sys_reply = port.read(1)
    sys_reply_str = sys_reply.decode('cp437')
    print (sys_reply_str);
    if sys_reply_str == '>':
        break;


port.flushInput()
ip = "g\r"
ip_en = ip.encode('CP437')
port.write(ip_en)
while (1):
    syscheck = port.read(1100)
    syscheck_str = syscheck.decode('cp437')
    print (syscheck_str);
    if sys_reply_str == '>':
        break;

```
This code gives me two issues:
1) output is printed as such:

```
V
e
r
s
i
o
n
```


Despite having no \r nor \n while testing with GtkTerm.

2) The command input "g" should trigger a "Bad Command!" reply from the sensor, but I receive nothing. Similarly, when having a correct input, I still receive no reply from the sensor. Because I am able to receive a reply from the sensor, I am led to believe that I am actually not writing anything to the sensor. I have tested it with port.writable(), and it came back True. I have set the port to 777 permission access.

I am unsure how I can troubleshoot this error and am hoping for guidance. Thank you very much in advance for the interest in assisting me.

---

### Post by norobro on 2017-05-30
1) By default print() outputs a new line. You can change that with print(syscheck_str, end='')  [https://docs.python.org/3/library/functions.html#print](https://docs.python.org/3/library/functions.html#print)


2) Don't know whether this will help or not, but for my device on /dev/ttyS0 I have to have a delay between a read and a write or I get no response. 

Try:```
import time
...
...
port.flushInput()
ip = "g\r"
ip_en = ip.encode('CP437')
time.sleep(0.2)
port.write(ip_en)
while (1):
syscheck = port.read(1100)
...

```

---

### Post by lisati on 2017-05-30
@eraserpencil: Please use [noparse]```
 and 
```[/noparse] to enclose program listings and terminal output. It helps preserve the formatting, which can make a difference in interpreting what we're reading.

---

