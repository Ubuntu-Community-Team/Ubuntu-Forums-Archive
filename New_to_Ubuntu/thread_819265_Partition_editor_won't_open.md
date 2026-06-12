---
title: "Partition editor won't open"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by logx on 2008-06-05
Hello everybody,

For the past week I tried several times to open the Partition editor app and it doesn't!

I get the "Starting Administrative task" and "Starting Partition editor" windows but then they go away and nothing happens.

I checked in "Users and groups" and my user has access to "Administer the system".

I don't know what to do. It use to be able to do it before, and I didn't change anything in the config (except the updates).

Any help will be welcome.

Rgds,

---

### Post by beanhead on 2008-06-05
Not sure why it stopped working. Have you tried to get another partition editor ? Like Qt parted? G-parted I think is the default but you might want to down load it again. Hope it helps , Ron

---

### Post by sisco311 on 2008-06-05
Try to run it from the terminal and post the error message:
```
gksu gparted
```

---

### Post by logx on 2008-06-05
With "gksu gparted" it actually opens!

I loged first as root.

What can be the problem?

---

### Post by sisco311 on 2008-06-05
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
> @RootSudo
[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/attention.png[/IMG] **Enabling the root account is rarely necessary.**
Anything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent root login, use sudo -i. **Logging in to X as root may cause very serious trouble.** If you believe you need a root account to perform a certain action, please consult the official support channels first, to make sure there is not a better alternative.

---

