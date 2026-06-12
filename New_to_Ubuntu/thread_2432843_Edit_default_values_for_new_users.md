---
title: "Edit default values for new users"
date: 2019-12-09
forum: New to Ubuntu
---

### Post by pruteins on 2019-12-09
Hi!!

I want to make some default options as I make a new user with useradd.

First i edit the /etc/default/useradd and i do a defuault bash and home.

But now I need to do some default more optioms.

When I set a password, that must expire in 30 days
Show a message like a 3 days before that expire
Wait for change the password, i mean, wait 3 days before I can change the pass again.

I'm asking what I need to edit, i was looking for Internet but I have no idea. 
I must do that for all new users as default, I can't edit every new user, must be from default.

Do u have a Idea??

---

### Post by SeijiSensei on 2019-12-09
I'd start by looking at the options in /etc/login.defs.

---

### Post by pruteins on 2019-12-10
Ty!!

---

