---
title: "run sqlplus on ubuntu 32 bit"
date: 2014-11-10
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-10
Hi all, 
 
Trying to run sql plus and got error: 
 
$ bash /home/user1/Downloads/instantclient_12_1/sqlplus 
/home/user1/Downloads/instantclient_12_1/sqlplus: /home/user1/Downloads/instantclient_12_1/sqlplus: can not execute binary file
 
Thied this:
chmod 777 sqlplus
 
But it didn't help. 
 
Ubuntu 14.04.1 LTS 
Desktop: Lubuntu 
 
Any help?

---

### Post by The Cog on 2014-11-10
What kind of file is it? Try this command (that tries to identify the file type) and post the result:
```
file /home/user1/Downloads/instantclient_12_1/sqlplus
```

---

### Post by marchello_lippi2 on 2014-11-10
$ file sqlplus 
sqlplus: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped

Now I guess that it is wrong platform, I should use 32-bit... But where can I get it?

---

### Post by marchello_lippi2 on 2014-11-10
Tried instantclient_11_2 version.
 
user@pc:~/Downloads/instantclient_11_2$ ./sqlplus 
./sqlplus: error while loading shared libraries: libsqlplus.so: cannot open shared object file: No such file or directory

---

### Post by The Cog on 2014-11-11
Libsqlplus.so is a Shared Object file - equivalent of a windows DLL. It is not part of the normal Ubuntu repositories, so I don't know where you would get it from. I would have expected the sqlplus installer to install it.

---

