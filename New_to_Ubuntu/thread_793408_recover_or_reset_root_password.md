---
title: "recover or reset root password"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by patwhalen on 2008-05-13
The specific need is to turn off the execute bit for some text files on my ms windows directory (running wubi sharing ubunto 8.4 and ms vista). The file shows as being owned by root so I need to su to root to do that.

My login password doesn't work and I don't remember in the install putting in anything else. So is there a way to reset the root password?

Any help will be appreciated.

---

### Post by Monicker on 2008-05-13
Choos Recovery Mode from the boot menu, then select the option for a root shell.  From there you can change your password.

---

### Post by Inxsible on 2008-05-13
> **patwhalen said:**
> The specific need is to turn off the execute bit for some text files on my ms windows directory (running wubi sharing ubunto 8.4 and ms vista). The file shows as being owned by root so I need to su to root to do that.

My login password doesn't work and I don't remember in the install putting in anything else. So is there a way to reset the root password?

Any help will be appreciated.When you say your password doesn't work, what exactly do you mean? That it doesn't show you asterisks when you type it in?

if it actually doesn't work then you can go to recovery mode and type in ```
passwd
``` and reset the password.

---

### Post by Ender305 on 2008-05-13
as long as you are sudo-capable, you can go into System -> Administration -> Users and Groups, unlock, then select root, click properties, then change the password

---

### Post by aysiu on 2008-05-13
You don't need to *su*.

Ubuntu uses *sudo* to obtain root privileges.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

