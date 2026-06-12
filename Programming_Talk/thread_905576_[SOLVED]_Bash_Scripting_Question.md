---
title: "[SOLVED] Bash Scripting Question"
date: 2008-08-30
forum: Programming Talk
---

### Post by gmxgeek on 2008-08-30
I have been working with a few bash scripts lately, one using gvfs-mount to mount remote drives. Anyway..

My issue is that i can call 'gvfs-mount ServerName ShareName', and as long as it is a public share, or the password is in my keyring, i can mount it without any further confirmation.

But if it is a secured drive, then it asks for username, domain, and password. Is there a way that i can pass these to my script and have it into them at the appropriate time?


```

#!/bin/bash
Server = $1
Share = $2
SMB="smb://$Server/$Share/"
DIR="$HOME/.gvfs/$Share on $Server"
/usr/bin/gvfs-mount "$SMB"
sleep 5
/usr/bin/nautilus "$DIR"

```

---

### Post by tamoneya on 2008-08-30
im not familiar with gvfs-mount but I have the same issue with smbmount for samba drives.  What you can do is pass the -o parameter for "options".  Then do something like this:```
-o username=my_username,password=mypassword
```

Type man gvfs-mount and it should describe these options more in depth.

---

### Post by gmxgeek on 2008-08-30
Hmm doesn't look like it supports that option
```

$ gvfs-mount --help
Usage:
  gvfs-mount [OPTION...] - mount <location>

Help Options:
  -?, --help               Show help options

Application Options:
  -m, --mountable          Mount as mountable
  -u, --unmount            Unmount
  -s, --unmount-scheme     Unmount all mounts with the given scheme
  -l, --list               List
  -i, --list-info          List extra information

```

---

### Post by monkeyking on 2008-08-31
I've never used the tool, but I think you can use expect for stuff like this.
[http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)

It can automate commandline request.

good luck

---

### Post by gmxgeek on 2008-08-31
Thank you very much. It seems this is exactly what i needed. Although, it hangs on each command for a bit. It will prompt for username, hang for about 3 seconds, then input it and continue, hang on the password, etc. Is there a way to fix this?

---

### Post by unutbu on 2008-08-31
Can you post your expect script with any private parts excised?

---

### Post by slavik on 2008-08-31
you can change the timeout

---

### Post by gmxgeek on 2008-08-31
> **slavik said:**
> you can change the timeout

How might i change that

```

spawn gvfs-mount [lindex $argv 0]
expect "username:"
send "[lindex $argv 1]\r"
expect "domain:"
send "\r"
expect "password:"
send "[lindex $argv 2]\r"
expect eof

```


EDIT: I fixed the timeout, and it works great now. Thanks everyone!

---

