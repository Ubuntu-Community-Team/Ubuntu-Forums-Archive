---
title: "Bash Script for FTP login"
date: 2007-02-13
forum: Programming Talk
---

### Post by phossal on 2007-02-13
I would like a simple script to automate logging in to my FTP server, which requires authentication in clear text. I know, of course, how to launch a script that asks to open the ftp connection, but I don't know bash well enough to get it to supply the username and password. Of course, I can implement this in other languages, but I don't *want* to. 

Can anyone give me a lesson?

---

### Post by Tomosaur on 2007-02-13
Does your ftp program support supplying the user and pass directly from the command line? If so, just use that. If you're unsure, just check out the man page and see what obscure nuggets of information are there.

---

### Post by phossal on 2007-02-13
Maybe I wasn't clear. Currently, I can open a terminal and type "ftp". That opens ftp in my terminal. Then I use *open destination*. That establishes a connection to my ftp server, which prompts me for my username. I just want a script that will do this for me, so I don't have to keep doing it manually. I don't to keep manually typing the same set of commands each time I need to connect.

---

### Post by yaaarrrgg on 2007-02-13
You might check out scp .... it's more secure than ftp and will probably do more what you want.

You can set up a cert so that you do not have to login to transfer files.  

Also, I have shell aliases set up, so that moving files around looks like this:

```

#copies file  somefile.txt  to a server set in variable $server1

scp somefile.txt $server1:

```

---

### Post by ghostdog74 on 2007-02-13
> **phossal said:**
> Maybe I wasn't clear. Currently, I can open a terminal and type "ftp". That opens ftp in my terminal. Then I use *open destination*. That establishes a connection to my ftp server, which prompts me for my username. I just want a script that will do this for me, so I don't have to keep doing it manually. I don't to keep manually typing the same set of commands each time I need to connect.

basic way of doing this
```

ftp -n -i <<_EOF_
open hostname
user username password
bin
cd "$DEST_DIR"
lcd "$SRC_DIR"
mget *
quit
_EOF_ 

```

---

### Post by supirman on 2007-02-13
use sftp.  Then you can set up your keys to allow passwordless login via ssh and sftp.  To log into your sftp session, it's as simple as
```
sftp user@host
```
with no passwords.

---

### Post by SuperMike on 2007-02-13
Do it with 'Expect' and hook it through 'Bash'.

---

### Post by supirman on 2007-02-14
Here you go:
```
sudo apt-get install expect
```

Then take this code:
```

#!/usr/bin/env expect

set username yourUsername
set pass yourPasswd
set host theHost

spawn ftp ${username}@${host}
expect "Password:"
send "${pass}\r"
expect "ftp> "
interact

```

and put it into a file, say autoftp, then
```

chmod +x autoftp

```

That should do what you want.

---

