---
title: "Browsing from windows"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by rezaf on 2012-12-29
Hi, I'm using ubuntu within windows xp with virtual machine. please recommend to me a software for browsing and working with ubuntu files from within windows. I worked with winscp in the past but winscp don't work with ubuntu 12.04 because refuse the connection.
Thanks.

---

### Post by steeldriver on 2012-12-29
do you actually have an ssh server running on the Ubuntu 12.04?

```
$ service ssh status
ssh start/running, process 1098
```If not, install openssh-server and then try again with winscp

---

### Post by rezaf on 2012-12-29
Very Thanks. I installed openssh-server and my problem resolved.

---

### Post by rezaf on 2012-12-29
a new problem. when I connect with my username and pass, it login successfully but don't give permission to work in root. how can I resolve the problem?

---

### Post by steeldriver on 2012-12-29
You're welcome - glad it worked

EDIT: oops, just saw your new post - what exactly do you need to do as root? if you are in an ssh shell you can use 'sudo'. Or are you trying to upload directly into a system location using winscp?

---

### Post by rezaf on 2012-12-29
I want to copy some files to root/usr/src and also edit some system files. terminal of winscp give error. also I logged in with sudo su in terminal of ubuntu. I want to use winscp to escape of entering commands in terminal.

---

### Post by gnush on 2012-12-29
You could just eleave your privileges to root.

```
$ su root
```> **rezaf said:**
> I want to use winscp to escape of entering commands in terminal.

I have no idea what that means.

*Edit:*

Oh, you want to access your files through FTP instead of SSH? I guess you could just log in as root.

---

### Post by rezaf on 2012-12-30
the problem has been resolved. I changed the user and logged in successfully. Thanks Friends.

---

