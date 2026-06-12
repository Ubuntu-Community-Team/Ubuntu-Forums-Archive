---
title: "password token manipulation error or something like that"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by tamir7 on 2012-01-16
Hi, there! I'm new user of ubuntu (11.10). I  recently forgot my root password and have resetted it by root menu (from recovery mode). Now I have a new password and when I tried yesterday to install something it asks authentication and I typed my password and it worked fine :) But today, when it asks for authenticatin, I type my password and it doesn't accept it. So I enter the root menu(from recovery mode). type *passwd* and type the new password nut it says authentication password token manipulation error or something like that. What should I do? plz help ;((((
extra information! I tried to change my password by running terminal (ctrl=alt=t) and it works correctly but when I try to type it in root menu or in users menu it errors :(

---

### Post by lechien73 on 2012-01-16
Hi & welcome to the forums,

This can happen if your /etc/shadow file doesn't have the same entries as /etc/passwd, or doesn't have the correct permissions.

To recreate /etc/shadow, run:

```
sudo pwconv
```

Also, when you're running *passwd* in recovery mode, you are running it as *passwd your_user_name*, aren't you?

---

### Post by tamir7 on 2012-01-16
it errors again. i know my user account name and i know my password but it errors :(
ar@ar-EP43-S3L:~$ sudo pwconv
[sudo] password for ar: 
ar is not in the sudoers file.  This incident will be reported.

---

### Post by tamir7 on 2012-01-16
Ah, now I see what's wrong!! Yesterday I for expiriment set my user account as standard and created another user and set it as admin. later. i deleted that new user and realized that i forgot to set my user as administrator :O

---

