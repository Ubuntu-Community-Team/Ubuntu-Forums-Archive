---
title: "how to login as root?"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by kapi on 2012-11-28
Morning all,

A while back I managed to login as root using a command (not sudo) but can't remember what it was. I used the root command to view mysql files that were restricted.

Can anyone remember the correct proceedure please

Thanks

---

### Post by coffeecat on 2012-11-28
All you need to know is here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you were thinking of wanting to log in as root to a graphical environment, then this is not supported here:

[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=1486138")

---

### Post by sudodus on 2012-11-28
> **kapi said:**
> Morning all,

A while back I managed to login as root using a command (not sudo) but can't remember what it was. I used the root command to view mysql files that were restricted.

Can anyone remember the correct proceedure please

Thanks
You are encouraged to use sudo and use temporary root privileges for security. It is possible to stay 'in sudo' that is as root, if you really need to, but it is not recommended. Read
```
man sudo
```
particularly about [FONT="Courier New"]sudo -i[/FONT] and [FONT="Courier New"]sudo -s[/FONT]

---

### Post by sffvba[e0rt on 2012-11-28
All you are likely to need to know about root and sudo in Ubuntu - [RootSudo]("https://help.ubuntu.com/community/RootSudo").


404

*edit: double ninja'ed*

---

### Post by lestertorres on 2012-11-28
I am not sure if this might help but doing...
*sudo su*
in a terminal will make you root and you do not have to put in your password any longer for the rest of the session.

---

### Post by snowpine on 2012-11-28
Try

```
sudo -i
```

---

### Post by steeldriver on 2012-11-28
> **kapi said:**
> Morning all,

A while back I managed to login as root using a command (not sudo) but can't remember what it was.[B] I used the root command to view mysql files that were restricted.
[/B]
Can anyone remember the correct proceedure please

Thanks

possibly you are getting confused between logging in to the system as  root, and logging in to mysql as root? mysql maintains its own  user/password database and (optionally) sets a 'root' password when you  install it

---

### Post by mastablasta on 2012-11-28
for mysql use phpmyadmin. you can login as root there. you can also reset root password if needed.

---

### Post by kapi on 2012-11-30
Hi, thanks for the replies.

I remember using a input a while back that enables me to have total access within the cli while the window was opened. I only used it temporarily. I just cant remember the input.

It's real use was for accessing some backup files I had transferred from a damaged hard disk and that with the use of the normal sudo was informed that I didn't have access- that's when I used the command.

Thanks for all your help

---

### Post by shaktiman1234 on 2012-11-30
Even if you have tried something else it will be better if you stick with sudo otherwise i have known number of cases where wring privileges ruined whole systems.

---

### Post by Wim Sturkenboom on 2012-11-30
> 
I remember using a input a while back that enables me to have total access within the cli while the window was opened

It as already mentioned, but to refresh your memory ;)
```

sudo -i

```
Or alternatively
```

sudo su -

```

---

