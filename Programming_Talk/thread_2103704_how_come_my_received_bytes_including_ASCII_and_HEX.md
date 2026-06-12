---
title: "how come my received bytes including ASCII and HEX ?"
date: 2013-01-11
forum: Programming Talk
---

### Post by chinye2020 on 2013-01-11
```
'''
Created on Jan 11, 2013

@author: root
'''
import socket,select

import sys
import datetime
import struct
import os

try:
    username = "root"
    password = "Apacheah64"
    db_name = "DB_GPS"
    table_name = "Tbl_GPS"
    host = ""
    port = 6903
    buf = 4096
    
except IndexError:
    
    sys.exit(1)

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.bind((host, port))
s2 = socket.socket(socket.AF_INET, socket.SOCK_RAW, socket.IPPROTO_UDP)
s2.bind((host, port))
print("Setting Done!")
data=[1024];
while 1:
    print("waiting!")
    while True:
        r, w, x = select.select([s, s2], [], [])
        for i in r:
            print(i, i.recvfrom(131072))
        
    '''
    data = s.recv(buf)
    print("\nReceived message %r" % data)
    if not data:
        print("Client has exited!")
        break
    else:
        
        print("\nReceived message %r" % data)
        print(len(data))
     '''   
# Close socket
mysql_c = None

s.close()
print("close")

```<socket.socket object, fd=5, family=2, type=3, proto=17> (b'E(\x00+\x03\xfb\x00\x004\x11{}\xcbRZ\xa9g\rz\x19&\xe8\x1a\xf7\x00\x17v\x9d\x0f\x00\x00\x00NR09G05164\x00', ('203.82.90.169', 0))

x00+\x03\xfb\x00\x004\x11{}\xcbRZ\xa9g\rz\x1  9&\xe8\x1a\xf7\x00\x17v\x9d\x0f\x00\x00\x00NR09G05164\x00 <--- this is the byte received

how come my received bytes including ASCII and HEX one? how to do i only wan all convert to HEX data?

---

### Post by ofnuts on 2013-01-11
Not a socket expert but part of what you receive is the whole datagram, not just the data. For instance, the part "\xcbRZ\xa9" is really 4 bytes with values (203,82,90,169), if that rings a bell :).

---

### Post by Tony Flury on 2013-01-11
> **chinye2020 said:**
> ```
'''
Created on Jan 11, 2013

@author: root
'''
import socket,select

import sys
import datetime
import struct
import os

try:
    username = "root"
    password = "Apacheah64"
    db_name = "DB_GPS"
    table_name = "Tbl_GPS"
    host = ""
    port = 6903
    buf = 4096
    
except IndexError:
    
    sys.exit(1)

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.bind((host, port))
s2 = socket.socket(socket.AF_INET, socket.SOCK_RAW, socket.IPPROTO_UDP)
s2.bind((host, port))
print("Setting Done!")
data=[1024];
while 1:
    print("waiting!")
    while True:
        r, w, x = select.select([s, s2], [], [])
        for i in r:
            print(i, i.recvfrom(131072))
        
    '''
    data = s.recv(buf)
    print("\nReceived message %r" % data)
    if not data:
        print("Client has exited!")
        break
    else:
        
        print("\nReceived message %r" % data)
        print(len(data))
     '''   
# Close socket
mysql_c = None

s.close()
print("close")

```<socket.socket object, fd=5, family=2, type=3, proto=17> (b'E(\x00+\x03\xfb\x00\x004\x11{}\xcbRZ\xa9g\rz\x19&\xe8\x1a\xf7\x00\x17v\x9d\x0f\x00\x00\x00NR09G05164\x00', ('203.82.90.169', 0))

x00+\x03\xfb\x00\x004\x11{}\xcbRZ\xa9g\rz\x1  9&\xe8\x1a\xf7\x00\x17v\x9d\x0f\x00\x00\x00NR09G05164\x00 <--- this is the byte received

how come my received bytes including ASCII and HEX one? how to do i only wan all convert to HEX data?

I think you are confused by what ASCII and HEX actually are.

HEX is just a way of representing a piece of data (i.e. displaying it in base 16 rather than our normal base 10). ASCII is another way of representing a piece of data, by displaying it as a printable character.

So if you think of a byte of data which has the value 97 - that could be represented as 97 (in decimal), \x61 (in hex) or "a" in ASCII. They are all the same piece of data, with three different representations.

So your code receives a datagram as a series of bytes (which seems to include the headers), some of those bytes may have a ASCII representation, and your code tries to print out the data the best it can so will print out hex numbers for those bytes which don't have printable ASCII character and ASCII characters for those that do.

That is the reason for instance that your output contains the segment \x00NR09G05164 - this clearly is not a valid HEX number - letters should only go up to F - so this is actually a combination of a series of bytes - many of which have printable ASCI representations - in fact \x00NR09G05164 is actually the following bytes : 

```

\x00 'N'  'R'  '0'  '9'  'G'  '0'  '5'  '1'  '6'  '4'
\x00 \x4E \x52 \x30 \x39 \x47 \x30 \x35 \x31 \x36 \x34

```

---

### Post by Zugzwang on 2013-01-11
> how come my received bytes including ASCII and HEX one? how to do i only wan all convert to HEX data?

They don't. The binary stream is just formatted this way by the print function. Internally, things look different. For example, try printing the length of the binary string. You will see that it is as short as you would expect.

---

