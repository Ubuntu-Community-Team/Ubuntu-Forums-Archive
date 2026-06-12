---
title: "system administration"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by elleppahc on 2008-10-29
Can someone help?
I have a desktop message saying not in the sudoers file.  This incident will be reported.

I have tried system/users and groups
can open this but cannot unlock to go further.
DO I need to do some repairs to continue??

---

### Post by Amarsingh0793 on 2008-10-29
> **elleppahc said:**
> Can someone help?
I have a desktop message saying not in the sudoers file.  This incident will be reported.

I have tried system/users and groups
can open this but cannot unlock to go further.
DO I need to do some repairs to continue??

I'm not on my Ubuntu partition right now, so I'm not sure if this is accurate. Follow the steps:

1) Open a terminal (Accessories > Terminal)
2) Log in as root (in the terminal!!!) and type:
          ```
usermod -a -G admin (yourusername)
```
                     (Without the brackets)
3) Restart your computer.
4) Log in and check if you can do any administrative tasks. 

Like I said, I'm not on Ubuntu right now, so I'm not sure if this code is correct or not, so please confirm this code before you put it into the terminal! 

Good Luck and I hope this helps :)

---

### Post by bodhi.zazen on 2008-10-29
Amarsingh0793's advice is accurate, but you will not be able to directly follow as you do not have sudo access.

what you will need to do is boot to recovery mode -> select the command line option.

You will get a command line interface, enter the command :

```
usermod -a -G admin (yourusername)
```

:twisted:

---

