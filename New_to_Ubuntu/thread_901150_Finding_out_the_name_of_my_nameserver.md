---
title: "Finding out the name of my nameserver"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Yaspoon on 2008-08-26
Hey im newb to dns and bind and it says when configuring it that i need to know the name of my nameserve ie nameserver.mydomain.com how do i found out what my name server is called is it just the computer name? ie computer is called server so it would be server.mydomain.com
thanks for any help

---

### Post by iaculallad on 2008-08-26
> **Yaspoon said:**
> Hey im newb to dns and bind and it says when configuring it that i need to know the name of my nameserve ie nameserver.mydomain.com how do i found out what my name server is called is it just the computer name? ie computer is called server so it would be server.mydomain.com
thanks for any help

Issue the following commands on your terminal.

For your computer name:

```
cat /etc/hosts
```

For your name-servers"

```
cat /etc/resolv.conf
```

For the currently logged user:

```
whoami
```

---

