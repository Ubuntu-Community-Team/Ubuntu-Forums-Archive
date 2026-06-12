---
title: "SCP with password Script"
date: 2011-03-15
forum: Programming Talk
---

### Post by Koffie24 on 2011-03-15
I'm trying to join the following two scripts to make a script to copy my Backups from local machine to another machine.

Can anyone help?

This one does the actual copying
```

#!/bin/bash
FILE_TO_MOVE=/home/user/Backup1/Backup_File
IP=xxx.xxx.xxx.xxx
USERNAME=username
LOCATION_TO_MOVE_TO=/home/user/Backups

scp $FILE_TO_MOVE $USERNAME@$IP:$LOCATION_TO_MOVE_TO

```

This one logs in
```

#!/usr/bin/env expect

set username username
set pass password
set host xxx.xxx.xxx.xxx

spawn ssh username@${host}

expect "Password:"
send "${pass}\r"

expect eof 

```

---

### Post by conundrumx on 2011-03-15
It would be much better to use public key authentication for this then to store the password in a plain text file.

---

### Post by Koffie24 on 2011-03-15
The thing is I want it to be completely automated, no input required.

Also this is completely for internal use, so ussing a jippo is completely cool with me.

---

### Post by talonmies on 2011-03-15
> **Koffie24 said:**
> The thing is I want it to be completely automated, no input required.

which is why you need to use public keys. Ssh logins with public keys can be completely automated with no input required, and without any of the potential risks of having to stored anything in clear text.

---

### Post by Koffie24 on 2011-03-16
So how do I automate it using public keys?

---

### Post by talonmies on 2011-03-16
There are a million tutorials floating around and the ssh documentation is also pretty clear, but [http://linuxproblem.org/art_9.html](http://linuxproblem.org/art_9.html)  was near the top of what google returned.

---

### Post by Koffie24 on 2011-03-16
Thanks guy! :D

---

