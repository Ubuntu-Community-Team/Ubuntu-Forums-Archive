---
title: "how to change user name"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Jim Lennington on 2008-10-23
The FAQ says I can't change my user name. I have to create a new account. When I try that I get the message that my email is already in use. How do I go about doing this?  Thanks in advance.

---

### Post by Catalyst2Death on 2008-10-23
Check here for information on adding/removing and editing user accounts.  I'm pretty sure that you can't change a username, but you can change a user's name:

```
$ sudo chfn -f "John Doe" johnny
```

[http://oreilly.com/catalog/debian/chapter/book/ch07_01.html](http://oreilly.com/catalog/debian/chapter/book/ch07_01.html)

---

### Post by handydan918 on 2008-10-23
> **Jim Lennington said:**
> The FAQ says I can't change my user name. I have to create a new account. When I try that I get the message that my email is already in use. How do I go about doing this?  Thanks in advance.

I would think that ```
usermod -l <new_username> 
```
would do it. 
See man usermod for more info.

Always question the expert who says, "Nah, Linux can't do that..."

---

### Post by perlluver on 2008-10-23
> **Catalyst2Death said:**
> Check here for information on adding/removing and editing user accounts.  I'm pretty sure that you can't change a username, but you can change a user's name:

```
$ sudo chfn -f "John Doe" johnny
```

[http://oreilly.com/catalog/debian/chapter/book/ch07_01.html](http://oreilly.com/catalog/debian/chapter/book/ch07_01.html)

I think he wants to change his Forums user name.

---

### Post by Jim Lennington on 2008-11-01
Catalyst2Death is right. I want to change my Ubuntu username.

When I simply try to create another account the system responds that the email address I entered is already registered. I was very naive to use my actual given name as a username.

---

### Post by Jim Lennington on 2008-11-01
My apologies Perluver.

---

### Post by Marshal0505 on 2008-11-01
have you tried simply changing the original email address in your profile?That should atleast make your email adress available again.

---

### Post by overdrank on 2008-11-01
Hi and Jim Lennington I am going to close this thread and please make a new thread in the Resolution Center and I believe the Admin can help you. 
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

Thanks :)

---

