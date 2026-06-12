---
title: "Network Login directly to GTK2 application"
date: 2010-11-11
forum: Programming Talk
---

### Post by bcz on 2010-11-11
I have a GTK application that I want users to be able to access via ssh login using an X client to a Linux application server.

I assumed I could edit bashrc to run the program and then logout, so the user connects to the networked box; immediately sees the application they want; and when they exit the application, they are disconnected.

I find this does not work.  I get a Ubuntu desktop displayed.  Then the user must load the application manually by clicking on some item.  When the program is terminated, the user has to logout from Ubuntu desktop.  These unnecessary steps are messy; windows users dont want to operate a Gnome desktop.

Is there a howto to do what I want to do  ( I like this sentance)

Is the answer, just use Ubuntu server rather than Ubuntu Desktop

Any thoughts appreciated

Rgds BillC

---

### Post by dwhitney67 on 2010-11-11
Regardless of the type of application, one can run it using the SSH command.  The gist is:
```

ssh -n user@host "command"

```

For example:
```

ssh -n joe@canoli "ls -l"

```

P.S.  You may also need to supply the -X option to SSH.

---

### Post by bcz on 2010-11-11
Thanks dW67.  Useful post as usual

ssh -n -X user@192.168.0.1 "cd /home/user/menu;/home/user/menu/prog"

brings up expected screen from another Ubuntu node and it loads child processes as expected

Any ideas on running from Windows node

---

### Post by dwhitney67 on 2010-11-11
> **bcz said:**
> Thanks dW67.  Useful post as usual

ssh -n -X user@192.168.0.1 "cd /home/user/menu;/home/user/menu/prog"

brings up expected screen from another Ubuntu node and it loads child processes as expected

Any ideas on running from Windows node

This should suffice:
```

ssh -n -X user@192.168.0.1 "./menu/prog"

```

As for Windows, one would need cygwin, I suppose... or an SSH client application (which typically is not free).

I do not use Windows, at home, or even at work.  I'm blessed.

---

