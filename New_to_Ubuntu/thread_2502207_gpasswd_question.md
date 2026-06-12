---
title: "gpasswd question"
date: 2024-11-05
forum: New to Ubuntu
---

### Post by jmkmx on 2024-11-05
Hello Forum,

Is there a way to remove multiple users from a group with gpasswd or any other tool?
I know you can add multiple users by entering the following:

```
sudo [COLOR=#E0DDD9][FONT=inherit]gpasswd -M userA,userB,userC mygroup[/FONT][/COLOR]
```

But can I don't know if you can do the opposite.

Any suggestions would be highly appreciate it!!!

---

### Post by grahammechanical on 2024-11-05
Open a terminal and type

```
man gpasswd
```

That will tell you what you can do with gpasswd.

Regards

---

### Post by yancek on 2024-11-05
If the man pages aren't good for you, do an online search for sites which might be a little more informative and easy to follow, one such site at the link below.

[https://www.geeksforgeeks.org/how-to-remove-all-users-from-a-group-in-linux/](https://www.geeksforgeeks.org/how-to-remove-all-users-from-a-group-in-linux/)

---

### Post by Holger_Gehrke on 2024-11-05
You misunderstand the way the '-M' option works. It doesn't add members to the group, it sets the group to have these (and only these) members. If mygroup has the users UserB,UserC,UserD, and UserE then the result of 'gpasswd -M UserA,UserB,UserC' is that UserA is added to the group and UserD and UserE are removed from it.

Another way to remove multiple users from a group is looping over a list of users you want removed and run the command to remove each user like so:
```

for user in username anotheruser onemore ; do gpasswd -d $user mygroup; done

```

Holger

---

### Post by TheFu on 2024-11-05
This may seem old school, but I'd use **sudoedit** on the 3 relevant files in /etc/.  What each field means is well documented in the manpage for each.  The file formats are pretty simple.

---

