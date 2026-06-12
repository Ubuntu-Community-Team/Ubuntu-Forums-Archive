---
title: "python, ssh"
date: 2011-05-10
forum: Programming Talk
---

### Post by sprouty on 2011-05-10
Hi,

I'm wondering if someone is able to offer some advice. I've created a simple python program using paramiko so take a screenshot and transfer it to a server using ssh. I know it bad practice to hard code user name and password into a application, but i wanted it to happen without any user interaction just run a script. So i'm wondering if anyone has any advice to obsure the combination or a different method to use/

Many Thanks,

Sprouty

---

### Post by StephenF on 2011-05-10
The ~/.netrc config file is a place where users can store their ftp logins and passwords. An ftp client can then be directed to use the netrc file instead of prompting the user. Python even has a module for parsing this file.

[http://docs.python.org/library/netrc.html](http://docs.python.org/library/netrc.html)

A netrc entry looks like this:

```

machine ftp.example.com
        login joe
        password 12345

```

curl, can be made to use netrc with the --netrc switch.


Another thing you could try is passwordless ssh. 

[http://blogs.translucentcode.org/mick/archives/000230.html](http://blogs.translucentcode.org/mick/archives/000230.html)

---

