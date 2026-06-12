---
title: "[SOLVED] Problems changing password"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by mczonie on 2008-08-02
I'm trying to change the password for one of my accounts by going to system > administration > users and groups, but it isn't working. After I change the password, when I try to log in to the new account, the new password won't work. 

Also, I've noticed that in the login screen, there are three little dots in the username field for the first second or two when they show it.

Any idea what's going on here.

TIA

---

### Post by Xerp on 2008-08-02
In terminal, try:

```
sudo passwd username
```

---

### Post by mczonie on 2008-08-02
> **Xerp said:**
> In terminal, try:

```
sudo passwd username
```

OK, that worked, thanks.

Any idea why the other method isn't working and what I can do to fix it?

---

### Post by sisco311 on 2008-08-02
> **mczonie said:**
> OK, that worked, thanks.

Any idea why the other method isn't working and what I can do to fix it?

Did you click the *Unlock *button?

---

### Post by armbendera1a on 2008-08-02
before u enter your password highlight the area where u see the dots even if u can not see the dots and delete it.Then enter it.

---

### Post by mczonie on 2008-08-02
> **armbendera1a said:**
> before u enter your password highlight the area where u see the dots even if u can not see the dots and delete it.Then enter it.

The dots go away after a second or two.

---

### Post by mczonie on 2008-08-02
> **sisco311 said:**
> Did you click the *Unlock *button?

I don't have to to get the "properties" button to work.

---

