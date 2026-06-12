---
title: "My server compromised [ How I found it]"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by vishal_agarwal2 on 2014-02-08
Hi.
Just now logged in to my server and found that it is compromised.
How did I checked it.

1. log n to my box.
2. run > last  command.
3. see all the logged in user details. I found that the user test logged in; which was not supposed to log in to the system.
4. use the >  find . /  -user (unwanted user name found with last command.)
5. use > ps -ef | grep (unwanted user name found with last command.)
6. use > kill  command to stop process started by unwanted user.

That's it. This is what I have performed till now. Now I am trying/planning to get the idea of hacker; What was his idea to get done with my box.

Regards,
Vishal Agarwal

---

### Post by Habitual on 2014-02-08
> **vishal_agarwal2 said:**
> I found that the user test logged in; which was not supposed to log in to the system.
Now *that* it what you need to "fix". ;)

---

### Post by deadflowr on 2014-02-08
Have you tried deleting the user?

---

### Post by vishal_agarwal2 on 2014-02-08
No, I have locked the user. > passwd -l test 

---

### Post by deadflowr on 2014-02-08
Did you enable root?
(meaning did you unlock and give root a new password?)
This might help more
[https://help.ubuntu.com/10.04/serverguide/user-management.html](https://help.ubuntu.com/10.04/serverguide/user-management.html)

---

