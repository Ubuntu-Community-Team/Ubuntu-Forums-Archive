---
title: "Detecting sudo setup"
date: 2007-12-28
forum: Programming Talk
---

### Post by joshn_highjinx on 2007-12-28
I'm writing a web application that displays a setup page when first run. By default, it prompts the user for the root password, to ensure that not just anybody can change configuration. This obviously doesn't work for Ubuntu, since the root account is disabled.

What I would like to do is, in the case of a disabled root account, check which users are granted root access via sudo, and allow them to enter their username and password.

I can detect whether the root account is disabled easily enough, but I don't know how to detect sudo privileges. Can anybody help me?

Thanks in advance for any help you can give.

---

### Post by altonbr on 2007-12-28
```
$ sudo cat /etc/sudoers
```

The only problem with this is that the web server needs sudo privileges. Not safe!

Try looking at
```
$ man sudoers
```

The only problem with using sudoers is if this program is to be install on any Apache2/PHP5 install, that command will only work on Debian-based distros.

---

### Post by joshn_highjinx on 2007-12-28
The thing that I don't like about trying to parse the file out myself is that it's somewhat complicated, and I'm afraid of parsing bugs that would lead to a security vulnerability. I wasn't able to find a Python module to do the parsing either.

I thought about just trying to run sudo with the specified username/password, but if they are wrong, sudo will log to syslog, which doesn't seem ideal.

Ideas?

---

