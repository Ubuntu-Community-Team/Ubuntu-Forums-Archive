---
title: "how do i use scp to copy one file to another server??"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by gone1 on 2008-09-25
I am trying to copy a file call dump.sql from bccdb01p2 (213.219.22.70) /otp/backup directory to our other server bccdb02p2 (213.219.22.76) and I am getting the error message below, can you help?????

 

[root@bccdb01p2 /opt/backup]# scp dump.sql 213.219.22.76:/otp/BoxUK_replicate/backup/

ssh: connect to host 213.219.22.76 port 22: Connection refused

lost connection

---

### Post by Orange_and_Green on 2008-09-25
Hello gone1

I would try

```
scp dump.sql USERNAME@213.219.22.76:/otp/BoxUK_replicate/backup/
```

where USERNAME is a valid login. Can you log into the server at all? Like with

```
ssh USERNAME@213.219.22.76
``` ?

Good luck

---

### Post by Solicitous on 2008-09-25
Connection refused?  Sounds like SSH isn't running on the server you're trying to copy a file to.  I would verify that the SSH service is running.

Once thats going, if the user you're currently logged in as has a valid account on the server as well, the scp command you're using should work (you should be prompted for your password).

HIH

---

