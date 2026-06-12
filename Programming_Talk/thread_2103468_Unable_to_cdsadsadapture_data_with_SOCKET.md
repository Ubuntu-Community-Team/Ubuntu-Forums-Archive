---
title: "Unable to cdsadsadapture data with SOCKET"
date: 2013-01-10
forum: Programming Talk
---

### Post by chinye2020 on 2013-01-10
```
import socket
import mysql.connector
import sys
import datetime

try:
    username = "root"
    password = "123456"
    db_name = "DB_GPS"
    table_name = "Tbl_GPS"
    host = ""
    port = 6903
    
except IndexError:
    
    sys.exit(1)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((host, port))
s.listen(1)

c, addr = s.accept()

while 1:
    data = c.recv(1024)
    if not data: break
c.close()

mysql_c = None

try:
    f = open('/GPS_Log/Log', 'a')
    f.write(datetime.datetime.now() + ' '+ data)
    f.close()
    mysql_c = mysql.connector.connect('127.0.0.1', username, password, db_name)
    mysql_c.query('insert into '+table_name+' values '+data)

except mysql.connector.Error as e:

    sys.exit(1)

finally:
    if mysql_c:
        mysql_c.close()
```

> 
Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    2   112 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:80
    1    60 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8080
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8080
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3306
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:3306
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6901
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:6901
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6902
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:6902
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6903
   10   430 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:6903
    1    52 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5900
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5900
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5902
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5902



6903 are having incoming data, but my script unable to read and save it to LOG file? why?what's wrong?

---

### Post by chinye2020 on 2013-01-10
Please Help, Urgent !

---

### Post by chinye2020 on 2013-01-10
Problem Solved, because it is UDP not TCP/IP !

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



```

---

