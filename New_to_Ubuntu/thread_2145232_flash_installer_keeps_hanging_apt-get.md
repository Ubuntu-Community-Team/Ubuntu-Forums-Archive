---
title: "flash installer keeps hanging apt-get"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by spaceshipguy on 2013-05-14
Apt-get in a terminal tells me --- you must manually run 'sudo dpkg --configure -a'
but I know if I do this it will try to download flash and hang (it's done this five times now)
((Actually I suspect it is downloading superslow and not showing a status bar, but I haven't time to wait for it to complete my laptop is melting and I need to solve heat issues.)
How do I stop it doing this?

I think its related to this bug
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/578625](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/578625)

I don't care about flash - I just want apt-get to stop trying

---

### Post by Kopkins on 2013-05-14
Uninstall flash. Then do that command.

sudo apt-get remove flashplugin-installer

---

### Post by spaceshipguy on 2013-05-14
> **Kopkins said:**
> Uninstall flash. Then do that command.
Cool

What command do I give? Is it an apt-get command in the terminal?

edit---

**apt-get --purge remove <package> worked!!! thanks**

---

### Post by Kopkins on 2013-05-14
in the future, for the same result, you can use apt-get purge <package>

It's the same and --purge remove.

Kopkins

---

