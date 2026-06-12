---
title: "don't have root privilege"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by alokme on 2008-10-11
i've recently installed ubuntu 7.04
there was no error while installation
but while working in ubuntu i'm not able to create or edit root account
i neither know how to enable or edit root account nor install any software

what should i do???

---

### Post by mejy on 2008-10-11
Ubuntu uses the 'sudo' authentication system rather than having a root account.  Normally, you would use "sudo xx" where xx is a command which requires root privileges.  Alternatively, you can use "sudo -s" which has a similar effect to "su".  Both methods require only your own password, rather than that of a separate root account.  There are ways to enable the root account, but it's unsupported, a potential security risk and there's nothing to be gained from doing so.

---

### Post by SunnyRabbiera on 2008-10-11
By default Ubuntu doesnt use the root account, to use administration tasks we use a command called sudo in a terminal to execute root commands.
sudo uses the password you use to log in, so no extra passwords are needed for administration tasks.
To install software there are tools on Ubuntu you can use, one is called add/remove located in your applications menu and then there is synaptic located under system> administration> synaptic package manager.
Those are the basics to get you started, but if there is a specific program you wish to install under ubuntu just ask.

---

### Post by shifty_powers on 2008-10-11
quite. in fact it is against the forum rules for any of us to show you how to enable the root account.

anyways, there is nothing you can do with the root account that can't be done with sudo...

---

### Post by alokme on 2008-10-11
ok...so there are no benefits of root account
but when i type "su" command and enter the password of my current account it says "authentication failure"
moreover...when i type "make install" for inbstallation...it says "permission denied"

so what to do now?

---

### Post by sisco311 on 2008-10-11
> **alokme said:**
> ok...so there are no benefits of root account
but when i type "su" command and enter the password of my current account it says "authentication failure"
moreover...when i type "make install" for inbstallation...it says "permission denied"

so what to do now?

use:
```
sudo -s
```to start a root shell
and:
```
sudo *command*
```to run a command as root.

Example:```
sudo make install
```

more info:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by sh_son on 2008-10-11
> **alokme said:**
> ok...so there are no benefits of root account
but when i type "su" command and enter the password of my current account it says "authentication failure"
moreover...when i type "make install" for inbstallation...it says "permission denied"

so what to do now?

In working in Linux OS, you definitely will need to use 'sudo' command, there is benefits; it's just matter of what you are trying to do. Try;

# sudo -s

then type your password, then you will get root access; though you couldn't get 'root' account, as someone said above, it's against forum rule;

Hope it helps;

---

### Post by roelpeeters on 2008-10-11
Have you tried 'sudo make install' and then enter your password? In order to use sudo you need to be part of the admin group.

---

### Post by bodhi.zazen on 2008-10-11
```
sudo -i
```

sudo -i is, IMO, preferable to sudo -s. The difference is with the environmental variables. -s uses your user variables, -i uses root's.

To translate that to english, open a terminal, and sudo -s and enter 

```
echo $HOME
```

Now exit the shell and sudo -i

again ```
echo $HOME
```

In general, when using a root shell, we want to use root's environmental variables.

---

### Post by alokme on 2008-10-11
thanx 2 all

---

### Post by Ryadt on 2008-10-11
Have a look here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

