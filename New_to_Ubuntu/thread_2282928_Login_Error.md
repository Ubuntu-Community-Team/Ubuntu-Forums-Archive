---
title: "Login Error"
date: 2015-06-17
forum: New to Ubuntu
---

### Post by geoff20 on 2015-06-17
Hi,
When trying to login as root through the GUI I'm getting this message
Error found when loading
/root/.profile
stdin:is not a tty
You need to fix as soon as possible.
Ubuntu loads but with limited access, ie no root access.
Have recently upgraded from 14.10 to 15.04 and previously I had no problem with accessing the root login.

---

### Post by QIII on 2015-06-17
Hello!

We do not allow discussions regarding logging in to a GUI as root.

Please refer to [this]("http://ubuntuforums.org/showthread.php?t=1486138") thread and note the first text in red.

Closed.

---

### Post by cariboo on 2015-06-18
Before closing the thread, I'm not sure why you think you need to log in a s root, as that is the windows way of doing this. The Ubuntu way is to log in as a regular user, and use sudo from administration purposes. If you really have to use root for something, you can create a root account, then log in as a regular user, then when you need to do an administrative task, just issue the following command:

```
su root
```

and run whatever commands you need to run.

For more info see [here]("https://help.ubuntu.com/community/RootSudo")

**Note:** When I first started using a Linux distribution, I ran as root always. I spent more time fixing mistakes because I forgot I was running root, then I actually did anything with my newly installed distro. :)

---

### Post by coffeecat on 2015-06-18
@geoff20, I don't normally comment on threads that have been closed by other members of forum staff, but I'm going to comment on this:

[quote= geoff20]You need to fix as soon as possible.[/quote]

You are mistaken if you think that this forum community of volunteers is in any way responsible for developing Ubuntu, or that, even if they were, they would want to compromise the security of Ubuntu by enabling login to a graphical desktop environment.

---

