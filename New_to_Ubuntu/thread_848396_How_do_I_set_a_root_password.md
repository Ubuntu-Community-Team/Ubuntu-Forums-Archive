---
title: "How do I set a root password?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by bbeckers on 2008-07-03
I have just installed Ubuntu Server Edition 8.04 LTS.
During the install process, I was asked to setup a user account and give it a password, (which I did), but I was never asked to setup a root password.

Did I miss something? 
What do I need to do to set a password for root?

---

### Post by shad0w_walker on 2008-07-03
Ubuntu leaves root disabled by default for security reasons, if you want to set a root password just run:

```
sudo passwd
```

From a console (Applications > Accessories > Terminal)

---

### Post by louieb on 2008-07-03
You didn't miss anything. Ubuntu doesn't set a root password by default. 
Makes it more secure. Hacker has to guess userid and password.
more on this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
But if you must have a root password, heres a hint **man passwd **

---

### Post by fatality_uk on 2008-07-03
What are you wanting to do that you need a root password? If you want to perform an action in the terminal tha requires you to have root privilages, then you could type the following

> sudo *root_action*

sudo give you temporary access as root and root_action is the comman you need to perform.

---

### Post by bbeckers on 2008-07-03
Thank you for your assistance.

This is my first experience with Linux, and my unix is a little rusty... I used to be a System Administrator in charge of multiple System V unix systems, but haven't touched one or even logged into a unix system since 1994...

Learning all over again...

---

