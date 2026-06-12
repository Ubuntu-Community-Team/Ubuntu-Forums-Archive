---
title: "have little trouble with Ubuntu Software Center"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by dhdarka on 2012-10-02
I made a change to my root. Like make a root passwd. But USC keep using my user pass word. I can't figure out how to get USC to used my root password over my users? or I'm just going have to make a new passwd root again?

Using Ubuntu 12.04

---

### Post by sandyd on 2012-10-02
Ubuntu does not (normally) have the root password enabled by default (password is scrambled).

Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info.

Also, the Ubuntu Software Center accepts the password of your currently running user.

I.E. When using USC, and you are logging in with a user named 'mike', you need mike's password. Likewise, if you want to login with root, you must be running USC with root perms, but I would **NOT** reccomend it, as it can create security issues and possibly nuke your .IceAuthority.


Of course, you can change to root in the terminal with
```

su
```
but it is prefered to use sudo.
Thanks!

---

### Post by dhdarka on 2012-10-02
So something like this:
```
su -c 'software-center'
```

---

### Post by newb85 on 2012-10-02
I'm confused.  Why do you want to run Software Center as root?

---

### Post by sandyd on 2012-10-02
> **dhdarka said:**
> So something like this:
```
su -c 'software-center'
```

as said - you do not want to run software center as root. That is still running software center as root, and can cause quite a lot of security problems

---

