---
title: "Frozen at log in"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Niemand000 on 2012-05-03
So, I changed my Toshiba laptop to Ubuntu 12.04 and it worked great. But after I restarted it after downloading all of the recent updates, it freezes up after I type in my password at login.

---

### Post by dgharmon on 2012-05-03
> **Niemand000 said:**
> So, I changed my Toshiba laptop to Ubuntu 12.04 and it worked great. But after I restarted it after downloading all of the recent updates, it freezes up after I type in my password at login.

err.. see if /tmp is writeable by user, <ctrl><alt<F1> gets you to a login prompt. Then chown root:users /tmp, chmod g+rwx /tmp ...

---

### Post by joetait on 2012-05-03
Can you log in on a different desktop?

It might be worth trying ctrl+alt+F1. This will take you to a login screen (not visual). From there you will need to type in your username and password to log in. Then try running 
```

sudo apt-get update && sudo apt-get upgrade

```
just in case any new updates will affect stuff.

To get back to the standard login screen just hit ctrl+alt+F7

---

### Post by Niemand000 on 2012-05-03
I'm stuck at the login prompt.  Clt+alt+F1 isn't working hmmmmm

---

### Post by joetait on 2012-05-04
> **Niemand000 said:**
> I'm stuck at the login prompt.  Clt+alt+F1 isn't working hmmmmm
If you use a live cd you can access the files that dgharmon mentioned and edit them.
Alternatively if you dual boot you will probably be able to access them from your other OS.

Either way, you will just have to mount the partition that has Ubuntu on it, then it will all be normal, except you will have to prefix any file paths with /mnt/...

---

### Post by Niemand000 on 2012-05-05
Alright, update: the computer is currently running ubuntu 10.04.  I tried installing 11.10 but I encountered the same issues I was having with 12.04. 
Now that I'm trying to clean install 12.04 I encounter a lot of reoccuring issues:
1. It's prone to freezing up BEFORE you get to that "Try Ubuntu" "Install Ubuntu". The entire computer freezes, as in, you can't even eject the disc.
2. When I do actually get the chance click Install Ubuntu, I freeze as soon as I try to access the internet.
 
What is the deal here? I'm starting to wonder if it's a hardware issue?

---

### Post by *^kyfds( on 2012-05-05
it might possibly be a hardware issue, but i can't quite say yet.

have you run a hash check on the ISO file you downloaded?

---

### Post by Niemand000 on 2012-05-05
> **Thehumorouscheese said:**
> it might possibly be a hardware issue, but i can't quite say yet.
 
have you run a hash check on the ISO file you downloaded?
 
How do I do that?

---

### Post by joetait on 2012-05-06
I could describe it, but the instructions here are probably a lot better than anything I would do: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

---

