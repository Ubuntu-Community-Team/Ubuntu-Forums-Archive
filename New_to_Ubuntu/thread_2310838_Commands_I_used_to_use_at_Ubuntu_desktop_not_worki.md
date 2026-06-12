---
title: "Commands I used to use at Ubuntu desktop not working at server"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by Mahamad on 2016-01-22
Hello

I used to use commands for installing mysql and php at Ubuntu Desktop, today I tried to work on a remote server (VPS) but these commands not working.

For example apt-get install mysql-server mysql-client
I get that:
Reading package lists... Done
Building dependency tree... Done
E: Unable to locate package mysql-server
E: Unable to locate package mysql-client

Note: I am trying to learn PHP and the tutorials based on working at Ubuntu Desktop, do you think I should stuck with desktop too, or there are no difference ?

---

### Post by steeldriver on 2016-01-22
Hello and welcome to the forums

Can you tell us what version of Ubuntu is running on the VPS?

```

cat /etc/lsb-release

```

---

### Post by Mahamad on 2016-01-22
Version 14.04

---

### Post by steeldriver on 2016-01-22
What happens if you run

```

sudo apt-get update

```

In particular, is apt able to connect to the repositories?

---

### Post by Mahamad on 2016-01-23
Yes, when I ran update, everything seems fine, it seems the packages wasn't included by default.

---

