---
title: "set gedit as default root crontab editor"
date: 2018-07-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2018-07-20
can this be done and if so how./tks

---

### Post by mIk3_08 on 2018-07-20
> **rburkartjo said:**
> can this be done and if so how./tks


What you mean rburkartjo?

[HTML]

Code;
```
 message 
```
>  message 


[/HTML]

---

### Post by Frogs Hair on 2018-07-20
> **rburkartjo said:**
> can this be done and if so how./tks

This may give some direction.


[https://askubuntu.com/questions/55022/changing-default-crontab-editor](https://askubuntu.com/questions/55022/changing-default-crontab-editor)

---

### Post by steeldriver on 2018-07-20
Well, it depends ...

If you're running 

```

crontab -e

```

**from a root shell**, then it will respect any `VISUAL=` and `EDITOR=` environment variables that you have defined for root.

OTOH, if you are editing root's crontab via

```

sudo crontab -e

```

then IIRC the default sudoers configuration does not "keep" these variables. You could change that by modifying env_keep however you probably shouldn't, for the reasons outlined below:

[Why should users never use normal sudo to start graphical applications?]("https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications")

Hope this helps

---

### Post by rburkartjo on 2018-07-20
tks frog and steel. you answered my question

---

