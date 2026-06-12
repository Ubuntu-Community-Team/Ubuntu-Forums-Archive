---
title: "Administrator/Admin account help"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by MaxxABillion on 2013-02-17
I have an admin account and a user account I just created.  I want to install some software onto the user account, however, it will not allow me to.  What commands do I need to use in order to download software under user account as the administrator? 

I thought about adding the user to the sudoers group but I'm not sure I want to do that unless its the only option.  Or maybe log is as the administrator and install the software that way.  I'm not sure about that either.  Any help will be greatly appreciated.

---

### Post by snowpine on 2013-02-17
You can use 'su' to (s)witch (u)ser. So for example if my user is named snowpine and my admin is named daddy, and I'm logged in as snowpine:

```
su daddy
sudo apt-get install whatever
exit
```

---

### Post by MaxxABillion on 2013-02-17
So you're saying that I need to be logged in as admin from the start and then su (user)  and install the software? 

Fyi, im trying to install Truecrypt

---

### Post by MaxxABillion on 2013-02-17
as the normal user it goes through the process for the install then it says "Enter you password to perform administrator tasks" Then it gives me an error when I enter the password for the user.  I tried entering the password for admin and it won't accept it

when I su (administrator) it gives me a "no protocol specified" error...

---

### Post by snowpine on 2013-02-17
I'm sorry, I am not familiar with truecrypt and don't know how to install it (or even what it does). Is there an application in the stable & supported Ubuntu repositories that accomplishes the same task?

I'm afraid I've reached the limits of what I, as a non-Ubuntu user, can teach you.

---

### Post by MaxxABillion on 2013-02-17
I figured it out...

I had to su (administrator)
then sudo ./truecrypt...

---

### Post by bab1 on 2013-02-17
> **MaxxABillion said:**
> I figured it out...

I had to su (administrator)
then sudo ./truecrypt...

This really isn't how the system is supposed to be used by a typical user.  The only truly administrative account is the 'root user" account.  This account is accessed in Ubuntu by anyone that is assigned administrative privileges (i.e. the first user created at install) by using sudo.  Any user can have access to sudo if they are added to the "sudoers group" (or admin on earlier systems).  This means a user with sudo privileges can add any another user to this group.

When you install applications they are available to all users unless you restrict particular  users.  You do not have to install applications as a specific user for them to work by default.  When you did this ```
then sudo ./truecrypt...
```...you were working as the "root user".

I have always (20+ years) had one account for me on my systems (a mortal user) then used sudo or su to become the root user only when needed.  If you administer (verb) the system you really don't need a user account that can't use sudo.  What advantage would that gain you?  On the other hand, for most users, there is no need to be able to use the root account for normal usage.

---

