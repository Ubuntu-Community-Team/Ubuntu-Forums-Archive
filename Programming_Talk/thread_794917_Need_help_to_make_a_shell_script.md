---
title: "Need help to make a shell script"
date: 2008-05-15
forum: Programming Talk
---

### Post by Verminox on 2008-05-15
I'm using Ubuntu 8.04, and my ISP has rather limited support for Linux. They have supplied me with two binary files, one is a daemon that must be started and then the other one for login/logout/info.

What I want to do is make a script that will automatically handle these tasks at startup.

This is what I generally have to do manually everyday:
```
$ sifyd
$ sifyconnect --login
Username: <username>
Password: <password>
You are now connected to Sify...
```

I don't have any experience with shell scripts so I want to know how I can supply those <username> and <password> values, which I generally have to enter manually everytime.

---

### Post by dtmilano on 2008-05-15
Using python and python-pexpect:

> 
#! /usr/bin/env python

import sys
import pexpect

child = pexpect.spawn("sifyconnect --login")
child.expect("Username:")
child.sendline("user")
child.expect("Password:")
child.sendline("mypass")
child.expect("You are now connected to Sify...")


---

### Post by Verminox on 2008-05-15
Thanks for the quick reply, but when I execute it, it tells me that the 'pexpect' module cannot be imported.

---

### Post by ghostdog74 on 2008-05-15
> **Verminox said:**
> 
This is what I generally have to do manually everyday:
```
$ sifyd
$ sifyconnect --login
Username: <username>
Password: <password>
You are now connected to Sify...
```
check on the manual for sifyconnect. might tell you how to login using automation. Otherwise, you can try here document
an example only
```

$ sifyconnect --login << EOF
username
password
EOF

```

---

### Post by dtmilano on 2008-05-15
Install python-pexpect.

---

### Post by Verminox on 2008-05-16
Thanks, pexpect did the trick. I read the docs and made my own modifications using timeouts to handle cases when a connection could not be made.

---

