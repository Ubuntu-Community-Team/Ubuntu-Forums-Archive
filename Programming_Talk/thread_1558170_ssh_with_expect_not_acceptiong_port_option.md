---
title: "ssh with expect not acceptiong port option"
date: 2010-08-21
forum: Programming Talk
---

### Post by xzased on 2010-08-21
I have a bash script with the following command:

```
VAR=$(expect -c "
spawn ssh $USER@$HOST -p 2020
expect \"password:\"
send \"$PASS\r\"
expect \"\\\\$\"
send \"uname -r\r\"
expect -re \"$USER.*\"
send \"logout\"
")
```

But the -p 2020 option is not working. It returns:

root@127.0.0.1's password: 2020

If I remove the -p option it works ok. How can I write this so it takes the port option? Thanks in advance.

---

### Post by pbrane on 2010-08-22
I found this link, may be some help...
[http://bash.cyberciti.biz/security/expect-ssh-login-script/]("http://bash.cyberciti.biz/security/expect-ssh-login-script/")

---

