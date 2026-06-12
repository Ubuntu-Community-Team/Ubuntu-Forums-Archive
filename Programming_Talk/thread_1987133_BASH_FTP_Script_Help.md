---
title: "BASH FTP Script Help"
date: 2012-05-26
forum: Programming Talk
---

### Post by hantechbl on 2012-05-26
When I run the Script I get this output: ```
Connected to localhost.localdomain.
220 ProFTPD 1.3.3a Server (Ubuntu) [::ffff:127.0.0.1]
Remote system type is UNIX.
Using binary mode to transfer files.
?Invalid command
?Invalid command
530 Please login with USER and PASS
530 Please login with USER and PASS
221 Goodbye.
tar: Removing leading `/' from member names
/home/
/home/file
/home/boss/
/home/boss/.profile
/home/boss/.bash_logout
/home/boss/.bashrc
/home/ftp/
/home/ftp/welcome.msg
Connected to localhost.localdomain.
220 ProFTPD 1.3.3a Server (Ubuntu) [::ffff:127.0.0.1]
Remote system type is UNIX.
Using binary mode to transfer files.
?Invalid command
?Invalid command
530 Please login with USER and PASS
local: /tmp/9-usmc1.tar.gz remote: /tmp/9-usmc1.tar.gz
530 Please login with USER and PASS
ftp: bind: Address already in use
221 Goodbye.

```

Concerned Code:
```
function ftphandle () {
local query="$1 $2"
ftp -inv $server <<ENDFTP
USER $user
PASS $password
cd $directory
$query
bye
ENDFTP
log INFO executed query $query
}
``` It's executed delete $file, and then put $file  Any ideas on how to fix the authentication issue?

---

### Post by codemaniac on 2012-05-26
Just to make sure in which part of your script you are supplying values of $user and $password ?

---

### Post by hantechbl on 2012-05-26
There's a section at the top of the file that contains this: ```
server="localhost"
user="boss"
password="password"
directory="/srv/backup"
```

---

### Post by codemaniac on 2012-05-26
try something like below
```
quote USER $USER
quote PASS $PASSWD
```

---

### Post by hantechbl on 2012-05-26
alright, now I've still got similar output:
```
220 ProFTPD 1.3.3a Server (Ubuntu) [::ffff:127.0.0.1]
Remote system type is UNIX.
Using binary mode to transfer files.
331 Password required for root
530 Login incorrect.
530 Please login with USER and PASS
local: /tmp/1-usmc1.tar.gz remote: /tmp/1-usmc1.tar.gz
530 Please login with USER and PASS
ftp: bind: Address already in use
221 Goodbye.

```

$query was: put /tmp/1-usmc1.tar.gz
It should have switched directories, but it appears it didn't.

---

### Post by codemaniac on 2012-05-26
Now that i can see your script is trying to log in to ftp server , but the authentication is failing .By any chance aren't you passing wrong userid or password .

One more thing i believe you cannot pass the absolute path to put ftp directive .You need to change directory to /tmp , then put the file .

---

