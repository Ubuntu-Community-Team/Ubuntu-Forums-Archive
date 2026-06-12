---
title: "How to work as superroot on ubuntu"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by edsh on 2012-08-11
Hi !
I am begineeer on ubuntu...
I want to run on ubuntu terminal as a superroot
when my command propt start it shows : ```
pc1@ubuntu:~$
```
I want to appear : ```
pc1@ubuntu:~#
```
Please hepl me...
regards edsh

---

### Post by hakermania on 2012-08-11
Hi edsh!
There is no such thing as superroot, it is either called 'super user' or 'root'.

Please give us some more information on what exactly you want. You want to open your terminal and immediately to have root permissions?

Or you simple want to become root? If this is the case, then give:
```

sudo su

```
type your password and hit [Enter] and you will become root :)

---

### Post by ads52 on 2012-08-11
Some great background reading in these 2 pages:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

If you are not already aware super user access should be used wisely :).

---

### Post by Kalanac on 2012-08-11
Working in root is unwise, you'll hear this many times all over the linux support forums.  It's much better to use sudo.

---

### Post by edsh on 2012-08-11
thank hacermainia...that all that i want

---

### Post by Cheesemill on 2012-08-11
> **hakermania said:**
> 
Or you simple want to become root? If this is the case, then give:
```

sudo su

```type your password and hit [Enter] and you will become root :)

You shouldn't use 'sudo su', it doesn't set all of the environment variables properly.
To get a root shell the preferred method is to do:
```
sudo -i
```

---

