---
title: "Reguires super user privilege. Isn't that the same as sudo?"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by mikodo on 2012-02-11
Hi,

```
sudo dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge

```gives me:

```
dpkg: requested operation requires superuser privilege
```What am I doing wrong?

Thanks.

---

### Post by lisati on 2012-02-11
When you're using [piping]("http://www.tuxfiles.org/linuxhelp/iodirection.html") the admin privileges don't always carry across from one command in the chain to the next.

One way round this is described here: [https://help.ubuntu.com/community/RootSudo#Downsides_of_using_sudo](https://help.ubuntu.com/community/RootSudo#Downsides_of_using_sudo)

---

### Post by mikodo on 2012-02-11
Thank you lisati.

```
sudo -i
```and the command, did:

```
Purging configuration files for ca-certificates-java, etc.
```That is what I wanted.

---

