---
title: "Why not to have a root password?"
date: 2008-01-01
forum: Recurring Discussions
---

### Post by Fixman on 2008-01-01
I mean, probably you will never use it, only if you lose your original password, where the only problem would be forgetting also the root password. But, isn't **very** exploitable an Ubuntu without a root password? I mean, somebody could just su and access your root account! Wouldn't be easier if somebody had a very easy to remember root password, and have lots more of security?

---

### Post by jken146 on 2008-01-01
There is more security if there is *no* root password, like the default setup in Ubuntu.  It isn't that there is no password -- the root account is locked, so no one can log in as root (not with su or any other way).  See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).

---

### Post by blithen on 2008-01-01
This really isn't the place for this..

---

### Post by HermanAB on 2008-01-01
Ubuntu uses Sudo to provide fine grained permission control.  With Sudo, a root password is not needed.  Other distributions don't use Sudo and therefore need root passwords.  Simple as that.

Cheers,

Herman

---

### Post by Fixman on 2008-01-01
I actually ment having a root password only in case you forget the normal password.

---

### Post by shad0w_walker on 2008-01-01
If you have forgotten your password you can reset it from recovery mode. You don't need a root password. Do you honestly think that the Ubuntu developers wouldn't have thought 'Gee, what happens when you forget your password?'

---

### Post by aysiu on 2008-01-01
> **Fixman said:**
> I mean, probably you will never use it, only if you lose your original password, where the only problem would be forgetting also the root password. But, isn't **very** exploitable an Ubuntu without a root password? I mean, somebody could just su and access your root account! Wouldn't be easier if somebody had a very easy to remember root password, and have lots more of security?
You can't *su* to root in Ubuntu unless you activate the root account and set up a password for it.

Why don't you understand the security setup before criticizing it?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

