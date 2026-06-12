---
title: "logging in as second user at command prompt"
date: 2007-11-02
forum: Programming Talk
---

### Post by roncrump on 2007-11-02
I have created a second user account on my system.

I want to use this to set up and test a software system at home which runs as a user account on the production system at work.

So, I want to logon as the second user from the command line - I do not want to logout and log in as the new user at the gnome login prompt. 

That is, I want to have myself logged in within gnome, then in a terminal be logged in as the second account and accessing the directories etc within that space.

I tried just typing "login two" and just got a message about having to use login at the lowest sh level and something about no utmp empty.

Any suggestions? I'm sure this is ridiculously simple, really.

Ron.

---

### Post by LaRoza on 2007-11-02
You can run something as another user with "sudo".

---

### Post by roncrump on 2007-11-02
> **LaRoza said:**
> You can run something as another user with "sudo".

I don't just want to run something as that user, rather be that user within that terminal window in order to do a lot of things.

Ron.

---

### Post by ruibernardo on 2007-11-03
Maybe you want su:

```
su another_username
<password>
```

---

### Post by roncrump on 2007-11-06
> **epimeteo said:**
> Maybe you want su:

```
su another_username
<password>
```

Would that be equivalent to 
```
sudo login another_username
<password>
```[/QUOTE]
or different?

---

