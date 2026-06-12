---
title: "how to change the username on ubuntu 12.04 server"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by mmx233 on 2012-09-19
hi friends,
how to change username in ubuntu 12:04 server, and everything associated with it, such as home folder ?

---

### Post by jrog on 2012-09-19
> **mmx233 said:**
> hi friends,
how to change username in ubuntu 12:04 server, and everything associated with it, such as home folder ?
Do the following things, removing the brackets and inserting appropriate stuff in those spaces:

1. Log in as a different user. You should not be logged in as the user you want to change.
2. sudo usermod -l <new username> <old username that you want to change> 
3. sudo usermod -md <path to new home directory that you want for the user> <new username that you created in #2>

^ Step 2 will change the username, and step 3 will associate a new home directory with that username and move everything from the old home directory into it.

If you also want to change the user's group, you can use groupmod:

sudo groupmod -n <new group name> <old group name>

[EDIT: Removed an unnecessary step.]

---

