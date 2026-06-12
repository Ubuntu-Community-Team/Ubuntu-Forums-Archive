---
title: "Python String Question"
date: 2006-06-28
forum: Programming Talk
---

### Post by krypto_wizard on 2006-06-28
mac_string = '001485e55503'  (This is the mac address of a computer.)

I am using wake on LAN python script to start computer remote.It uses
format like this ....

s.sendto('\xff'*6 + '\x00\x014\x85\xe5\x55\x03'*16, ('192.168.1.255',
80))

where '\x00\x14\x85\xe5\x55\x03' is the MAC address to be used. \x is preceeding I think because of it being a hexadecimal number.

What I do is break the string into 6 parts like this,

str01=mac_string[0:2]
str02=mac_string[2:4]
str03=mac_string[4:6]
str04=mac_string[6:8]
str05=mac_string[8:10]
str06=mac_string[10:12]

and if I use it like this

s.sendto('\xff'*6 + '\xstr01\xstr02\xstr03\xstr04\xstr05\xstr06'*16,
('192.168.1.255', 80))
I get an error

I also tried like this
s.sendto('\xff'*6 + 'mac_string'*16, ('192.168.1.255', 80))

This also didnt work.

Since the MAC adddress are hexadecimal, how should I go about it here.

Please help, every help is appreciated. Thanks

---

### Post by thumper on 2006-06-28
```
>>> ''.join([chr(int(mac_string[x*2:x*2+2],16)) for x in range(6)])
'\x00\x14\x85\xe5U\x03'

```

---

### Post by krypto_wizard on 2006-06-28
Thanks thumper as always !!! I found another solution.
```

s.sendto('\xff'*6 + binascii.unhexlify(mac_string) *16, ('192.168.1.255', 80)) 

```

[QUOTE=thumper]```
>>> ''.join([chr(int(mac_string[x*2:x*2+2],16)) for x in range(6)])
'\x00\x14\x85\xe5U\x03'

```[/QUOTE]

---

### Post by thumper on 2006-06-29
Thanks, didn't know about that one, or its sister function hexlify.

---

