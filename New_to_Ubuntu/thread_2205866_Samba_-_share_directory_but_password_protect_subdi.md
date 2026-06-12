---
title: "Samba - share directory but password protect subdirectories"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by david_brown on 2014-02-16
Hello!

So the situation is as follows - I have a server running 12.04.4, with Samba installed.
What I want to do is have a directory called "Users" which everyone on the network can access - however the subdirectories are password protected (e.g. user1 can access folder1 in directory "Users" using password1, but user2 can't access folder1 using password2. You can do this to a certain extent through smb.conf however using 
```
[user1]	comment = user1's Files
	path = /var/Users/user1
	read only = no
	valid users = user1

```
makes it appear in the root, and can still be accessed by going to var/users/user1. I want it so it doesn't appear in the root, and when going to var/users/user1 you're asked for a password. Thanks!

---

### Post by tfrue on 2014-02-16
What do you mean by in the root? I don't quite understand what you want...What I'm getting is that you don't want the folder to show that the user and group owner is root?

---

