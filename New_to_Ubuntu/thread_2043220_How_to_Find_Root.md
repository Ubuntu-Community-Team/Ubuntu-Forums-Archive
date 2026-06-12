---
title: "How to Find Root"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by rraj.be on 2012-08-16
Hi All,

How can we find if we are being in root user mode?

What are the possible ways to determine this?
Like

1) find -name su

Please let me know.

Thanks in advance.

---

### Post by smartboyhw on 2012-08-16
We don't recommend you to use root, since sometimes if you did anything in root you'll end up damaging your system.

---

### Post by nothingspecial on 2012-08-16
> **smartboyhw said:**
> sudo -passwd root.
 
However, we don't recommend you to use root, since sometimes if you did anything in root you'll end up damaging your system.

In ubuntu the root account is disabled. sudo is used instead. Read this

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> When giving advice on the Ubuntu Forms and IRC, please take the time to teach "the basics" such as ownership, permissions, and how to use sudo / gksu / kdesudo in such a way that new users do not break systems. 

---

### Post by rraj.be on 2012-08-16
Hi, Thanks you all...

But my question is

**"How can we find if we are being in root user mode?"**

---

### Post by Elfy on 2012-08-16
If you're in a terminal
hob@sidh:~$ 

with root

root@sidh:~#

---

### Post by albandy on 2012-08-16
type whoami

For example:
if I type whoami, it says:
albandy
but if I type sudo whoami, it says:
root

---

### Post by rraj.be on 2012-08-16
Yes. All of this can be done, by visually checking. 
That is by a human.
How can we automate it or tell the machine via a program or script?
Or I should inform the user, if they are root or a normal user, by checking something in the current user privileges.

Thanks.

---

### Post by smartboyhw on 2012-08-16
> **rraj.be said:**
> Yes. All of this can be done, by visually checking. 
That is by a human.
How can we automate it or tell the machine via a program or script?
Or I should inform the user, if they are root or a normal user, by checking something in the current user privileges.
 
Thanks.
 I think the last option is the best.

---

### Post by rraj.be on 2012-08-16
One more thing i have found is 

```
id
```

This will give the uid of current user like

```

root@rraj-ubuntu:/home/rraj# id
uid=0(root) gid=0(root) groups=0(root)
root@rraj-ubuntu:/home/rraj# 

```

---

### Post by albandy on 2012-08-16
> **rraj.be said:**
> Yes. All of this can be done, by visually checking. 
That is by a human.
How can we automate it or tell the machine via a program or script?
Or I should inform the user, if they are root or a normal user, by checking something in the current user privileges.

Thanks.

Script example to ensure you're running under root.
```

#! /bin/bash

if [ "$(whoami)" != "root" ]
then
echo "you must be root"
exit 1
fi

#commands to run under root
echo "OK running under root"
#type the commands to run under root.

```

---

### Post by ajgreeny on 2012-08-16
You could also edit the /etc/sudoers file (very carefully, using **sudo visudo** command) to ensure that every command in a terminal that needs root privileges asks for the password.  Normally there is a timeout on sudo of 15 mins (I think it's 15) but you can set a timeout of zero.  That would mean that it does not matter if the last command was with root privileges, as no further commands will be allowed without the password again.

See [http://ubuntuforums.org/showthread.php?t=763142](http://ubuntuforums.org/showthread.php?t=763142) or do a search for lots more info about editing /etc/sudoers file, but as I said, be very careful; get it wrong and you may lock yourself out of the system completely.

---

