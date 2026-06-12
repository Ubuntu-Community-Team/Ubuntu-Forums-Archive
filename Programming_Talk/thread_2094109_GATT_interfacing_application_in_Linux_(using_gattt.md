---
title: "GATT interfacing application in Linux? (using gatttool)"
date: 2012-12-12
forum: Programming Talk
---

### Post by Kdar on 2012-12-12
I am using CC2540 Bluetooth Low-Energy development board. And today I was trying to connect to it using hcitool and gatttool.
I used following commands to scan and connect with hcitool:
```
$ sudo hcitool lescan
[sudo]LE Scan ...
78:C5:E5:6C:8A:01 (unknown)
78:C5:E5:6C:8A:01 OBP425-8A01
$ sudhcitool lecc 78:C5:E5:6C:8A:01
Connection handle 64
```
and later, I tried to connect with gatttool to read different UUIDs that I have inside application code of CC2540:
```
$ sudo gatttool -i hci0 -b 78:C5:E5:6C:8A:01 -m 48 --interactive
[   ][78:C5:E5:6C:8A:01][LE]> connect
[CON][78:C5:E5:6C:8A:01][LE]> char-read-uuid ffe1
[CON][78:C5:E5:6C:8A:01][LE]> 
handle: 0x0037   value: 1d 
[CON][78:C5:E5:6C:8A:01][LE]> 
```

But.... Can I write a little problem or maybe just a script to read some particular (1-3) uuid(s) every second?

---

