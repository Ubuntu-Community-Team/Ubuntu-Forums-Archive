---
title: "ftp transfer via script"
date: 2013-05-30
forum: Programming Talk
---

### Post by Hekabe on 2013-05-30
I'm writing a bash script to automatically update a local directory from a remote directory on an FTP server. I'm using the following code to get an automatic login, but I've run into trouble.
```
ftp -p -i -v ftp.myhostname.org <<EOF
username
password
EOF

```
It recieves the username input, but then it prompts for the password. Any ideas?

---

### Post by steeldriver on 2013-05-30
[http://en.wikipedia.org/wiki/Expect#Examples](http://en.wikipedia.org/wiki/Expect#Examples)

---

### Post by Hekabe on 2013-05-31
Alright, that's working. Thanks. One other question. Is there a way to do a recursive "newer" get in FTP using the ftp command?

---

### Post by ofnuts on 2013-06-02
> **steeldriver said:**
> [http://en.wikipedia.org/wiki/Expect#Examples](http://en.wikipedia.org/wiki/Expect#Examples)

Of "ftp -n" followed by a "user" command. Or you keep the login info in a .netrc file (see "man 5 netrc").

For your other problem, check the ftp command "newer", which is an intelligent "get". Otherwise there are FTP support libraries for many languages (Python, Java...)

---

