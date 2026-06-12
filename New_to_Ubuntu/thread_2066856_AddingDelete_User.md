---
title: "Adding/Delete User"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by termvrl on 2012-10-05
Hi all,  
i can add user using useradd *user1*. 
but, when i ls /cd/home, no dir for my new user.
another thing is, i cannot set passwd to my new user, it ask me to key in current passwd. (which is i dont have)

Thnks!!

---

### Post by papibe on 2012-10-05
Hi termvrl.

I would recommend NOT using 'useradd' and 'userdel', as they are low level utilities.

If I were you, I'd use the commands 'adduser' and deluser instead.

Let us know how it goes.
Regards.

---

### Post by NikTh on 2012-10-05
> **papibe said:**
> hi termvrl.
If i were you, i'd use the commands 'adduser' and deluser instead.

+1

---

### Post by Pletched on 2012-10-05
Three things you need to know before you use useradd. I think this is how it's done. Emphasis on the think. 

user a add

```
useradd me # me is you
```give the user a directory

```
useradd -d /home/me me
```give the user a password

```
passwd me
```

---

### Post by honeybear on 2012-10-05
might try :  deluser or rmuser ...

---

### Post by daslinkard on 2012-10-05
I'm assuming that you are trying to add the user through the use of the terminal?  What about going through the Dash Home?  I found a good tutorial [here]("http://www.ubuntugeek.com/how-to-createdisable-and-delete-new-user-account-in-ubuntu-11-10-oneiric-ocelot.html") on how to add the account.

---

### Post by termvrl on 2012-10-05
Hi All ! Good day!

first i remove current user and group.
i create a group using addgroup [I]group1. 
[/I]then, i use adduser --ingroup [I]group1 user1.
[/I]set the password and info.

Thanks for your help!

---

### Post by daslinkard on 2012-10-05
Glad you got it solved!

---

