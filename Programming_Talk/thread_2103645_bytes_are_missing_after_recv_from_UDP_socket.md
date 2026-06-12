---
title: "bytes are missing after recv from UDP socket"
date: 2013-01-10
forum: Programming Talk
---

### Post by chinye2020 on 2013-01-10
```
import socket
import sys
import datetime
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

while 1:
    data = s.recv(buf)
    if not data:
        print("Client has exited!")
        break
    else:
        print("\nReceived message '", data,"'")
        
# Close socket
s.close()
```the bytes i m received should be 43 bytes, but what i received from client is
Received message ' b'\x0f\x00\x00\x00NR09G05164\x00' ' ?
only 15 bytes. why?

---

### Post by ju2wheels on 2013-01-22
Are you running this in a vm thats using NAT by any chance? I had a similar problem using ftplib the other day where the socket would just hang when receiving data and wouldnt get all the data because of NAT on vbox affecting it.

---

