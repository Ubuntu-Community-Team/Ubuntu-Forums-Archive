---
title: "[SOLVED] How can I make a user which cannot use 'sudo'?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Masoris on 2008-07-28
I want to make a user(account) which cannot be a administrator like a guest user. How can I make it?

---

### Post by markjensen on 2008-07-28
Just create a new account.  If you don't add it into sudoers, it will not be able to authorize.  I have a kids account for just that purpose on my computer, so the kids can use it when I am here at work.


EDIT:  The new account must have a password.   I am sure there are ways to turn that feature off, but I just told my kids what the kid account password is.

---

### Post by eightmillion on 2008-07-28
I think that new users can't sudo by default. You normally have to specifically allow them.

---

### Post by halitech on 2008-07-28
System - Administration - users and groups

click add user

fill in the information, set type to Unpriviledged and click okay

---

### Post by hrod beraht on 2008-07-28
System --> Administration --> Users and Groups

*Add User*, but on the *User Privileges* tab of the new user, uncheck which privileges that you don't want them to have. e.g. *Administer the System*.

Bob

---

### Post by Masoris on 2008-07-28
> **markjensen said:**
> Just create a new account.  If you don't add it into sudoers, it will not be able to authorize.  I have a kids account for just that purpose on my computer, so the kids can use it when I am here at work.
You mean new account cannot use 'sudo' default. So what should I do to make user which can do 'sudo'?

---

### Post by markjensen on 2008-07-28
As above, the abilites of the new user can be set at time of creation.

If they are a "sudoer", then they are allowed to use "sudo" to perform system tasks.   It sounds like you don't want this.

---

### Post by bodhi.zazen on 2008-07-28
With Ubuntu sudo is configured such that members of the admin group have root access (via sudo).

By default, the first user on the system is a member of the admin group. 

By default, new users are not.

To give new users admin access , add them to the admin group (you need to log out and back in for changes to take effect).

The alternate is to configure sudo (sudo can be configured to give access to alternate groups or single commands).

---

