---
title: "Please help with Puppy Linux user accounts"
date: 2008-05-12
forum: Other OS Talk
---

### Post by Ripfox on 2008-05-12
Puppy seems to log straight into a root account. How do you set up a regular user account? I tried to start xchat and it called me stupid. lol.

---

### Post by unutbu on 2008-05-12
Have you tried opening a terminal and typing

```
adduser <username>
```

---

### Post by Ripfox on 2008-05-12
Yes and it says 
> 
/home/(newuser): No such file or directory
passwd: unknown user (newuser)

How do i get a home for it? How do i set a password?

Thanks, btw...I'm lost in the puppy world still. :)

Oh, and...what about a graphical log in?

---

### Post by Ripfox on 2008-05-12
You still here? :)

---

### Post by unutbu on 2008-05-12
I'm kind of shocked, but it seems according to

[http://www.murga-linux.com/puppy/viewtopic.php?t=22543](http://www.murga-linux.com/puppy/viewtopic.php?t=22543)

that you need to download tinylogin to add a user under Puppy! Please note that I could be very very wrong -- I've only used (er played) with Puppy for 15 minutes and most of that time was spent with the Rubik's cube :)

---

### Post by wolfen69 on 2008-05-13
puppy is made for those that dont mind that kind of linux setup. if you are even a somewhat knowledgeable user, you shouldnt have any problems. i guess the developer has removed what he saw as annoyances. i dont care, it works great for me and im going to leave as is.

---

### Post by unutbu on 2008-05-13
Now that I think about it, it makes a lot of sense to remove a program like adduser -- it takes up space and it's used rarely by most users.

---

### Post by Ripfox on 2008-05-13
> **wolfen69 said:**
> puppy is made for those that dont mind that kind of linux setup. if you are even a somewhat knowledgeable user, you shouldnt have any problems. i guess the developer has removed what he saw as annoyances. i dont care, it works great for me and im going to leave as is.

Well I agree for the most part, and I have like 7 machines running dragon puppy...but one of them is like a "main" machine at a small business and I just thought it would be nice to have a non-admin account just for that machine. :)

---

### Post by regomodo on 2008-05-14
> **Ripfox said:**
> Yes and it says 


How do i get a home for it? How do i set a password?



$ man useradd

once you've installed it

---

