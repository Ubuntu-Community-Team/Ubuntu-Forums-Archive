---
title: "why sudo requires my password even if configured as NOPASSWD"
date: 2016-06-14
forum: New to Ubuntu
---

### Post by meta2 on 2016-06-14
I configured sudoers like this never to require my password.

```
ubuntu  ALL=(ALL:ALL) NOPASSWD:ALL
```

I'm wondering why sudo requires my password when doing "sudo -v".
For example, "sudo ls /root" or "sudo -s" can gain root privilege without typing my password.
However, in case of "sudo -v" requires password, why? Other Linux distro never require password
such case.

No password required in this case. That's what I expect.
```
ubuntu@localhost $ sudo ls -lha /root; sudo -k; sudo ls -lha /root;
total 24K
drwx------  4 root root 4.0K Jun 14 07:15 .
drwxr-xr-x 23 root root 4.0K Jun 14 07:35 ..
-rw-r--r--  1 root root 3.1K Oct 22  2015 .bashrc
drwxr-xr-x  2 root root 4.0K Jun 14 07:15 .nano
-rw-r--r--  1 root root  148 Aug 17  2015 .profile
drwx------  2 root root 4.0K May 20 07:09 .ssh
total 24K
drwx------  4 root root 4.0K Jun 14 07:15 .
drwxr-xr-x 23 root root 4.0K Jun 14 07:35 ..
-rw-r--r--  1 root root 3.1K Oct 22  2015 .bashrc
drwxr-xr-x  2 root root 4.0K Jun 14 07:15 .nano
-rw-r--r--  1 root root  148 Aug 17  2015 .profile
drwx------  2 root root 4.0K May 20 07:09 .ssh

```

Oddly, password required twice. In this case, password shouldn't be required.
```

ubuntu@localhost $ sudo -v; sudo -k; sudo -v
[sudo] password for ubuntu:
[sudo] password for ubuntu:

```

Debian's behaviour is what I expected.
```

debian@localhost $ sudo -v; sudo -k; sudo -v
debian@localhost $

```

Thanks,

---

### Post by meta2 on 2016-06-14
I'm using 16.04 LTS.

---

### Post by leunam12 on 2016-06-17
Put "ubuntu  ALL=(ALL:ALL) NOPASSWD:ALL"  at the end of the sudoers file. My nopasswd commands don't work either unless it's at the end of the sudoers file.

---

### Post by thegner2 on 2016-07-26
@meta2: this issue has been bugging me for a couple of weeks also... hopefully this reply is not too late to help you.

This is a relatively new issue specific to the behavior of `sudo -v` with regard to a recent change in behavior in the sudo command itself, as referenced by: [https://www.sudo.ws/stable.html#1.8.17](https://www.sudo.ws/stable.html#1.8.17). My guess is that it's working for you in debian due to an older version of sudo.

I am posting this answer with the hopes that it may help you or any future searcher from continuing to see "put your nopasswd line at the end or your sudoers file", when some of us already know that rule and it isn't working when specifically invoking `sudo -v`.

The change in behavior can be over-ridden with a new "Defaults" line in your sudoers file:

```
Defaults verifypw = any
```

The `verifypw` option can be set to many different options (found in the sudoers man page). The default is `all` which requires all matching sudoer lines to contain NOPASSWD in order to avoid the password prompt with `sudo -v`. Setting it to `any` allows any **one** matching line to bypass the prompt when invoking `sudo -v`.

Hope this helps!

Travis

---

