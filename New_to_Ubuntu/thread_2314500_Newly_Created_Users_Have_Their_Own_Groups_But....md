---
title: "Newly Created Users Have Their Own Groups But..."
date: 2016-02-21
forum: New to Ubuntu
---

### Post by kazz2 on 2016-02-21
I was really torn on what title to give this post. I'm fine-tuning permissions on shares and have found an odd "anomaly" associated with the groups that are automatically created when you create a user. For instance, if you create 'user1' a group called 'user1' is also created. All well and good. But I'm trying to implement a sort of private directory for users and I've either arrived at the wrong paradigm or I'm not understanding how groups and permissions in Ubuntu work. And, yes, it could be both.

Let's say I created my own administration user called 'myadmin'. Then I create a user of the server called 'user1'. In order to give them their own space on the server I create a directory called 'user1data'. In order to give them full rights to their directory I can execute 'sudo chgrp user1 user1data'. With a chmod statement using '770' I'll give the directory owner and the user's group all rights while not allowing anyone else access.

In my mind, I should be able to add the 'myadmin' user to the user's group named 'user1' and have all access. But this doesn't work. The user 'myadmin' gets no access while the user, 'user1' gets all access. If I create a new group, such as 'user1datagroup' and make 'user1' as well as 'myadmin' users, then 'sudo chgrp user1datagroup user1data'. All will work fine.

Clearly, the group created for each user when the user itself is created doesn't behave like a normal group when it comes to permissions.

Why is that?

I'll assume I can't fix that and will think about another way to manage shares and private directories. But, for now, I'd at least like to have my observation affirmed with an explanation of the odd-seeming-to-me (noob) behavior.

Thanks!

---

### Post by HermanAB on 2016-02-22
Howdy,

It can be a little confusing.  A user has one primary group (usually the same as his user name) and several secondary groups.  By default a new file will be created with the primary group.

if you want to set up a shared directory, then make a special group for that and setGID on the directory so that all new files will be created with that group:

[http://terokarvinen.com/2011/shared-folder-with-chmod-setgid](http://terokarvinen.com/2011/shared-folder-with-chmod-setgid)

The other confounding thing is that when you added a group to a user, the user has to log out and log in again, in order for the desktop environment to refresh itself and take note of the new group.

---

### Post by Azdour on 2016-02-22
> **HermanAB said:**
> Howdy,

It can be a little confusing.  A user has one primary group (usually the same as his user name) and several secondary groups.  By default a new file will be created with the primary group.

if you want to set up a shared directory, then make a special group for that and setGID on the directory so that all new files will be created with that group:

[http://terokarvinen.com/2011/shared-folder-with-chmod-setgid](http://terokarvinen.com/2011/shared-folder-with-chmod-setgid)

The other confounding thing is that when you added a group to a user, the user has to log out and log in again, in order for the desktop environment to refresh itself and take note of the new group.

I would definitely echo HermanAB's reply. When I first started, not knowing about the logging in and out before a user is recognised as part of a group caused me all sort of issues.

---

### Post by kazz2 on 2016-02-23
Thanks much. I'll get into this once I get past a new hurdle and will post and update!  :D

---

### Post by kazz2 on 2016-03-09
I'm finally getting back to this. And thanks again for the support!

So, create a group for each "top-level" shared directory. Then use the set GUID feature of chmod (s) on the directory itself. That way, when ANY user in the shared directory's group creates a file it will belong to the same group as the directory regardless of the user's default group.

That about it? My example:

Users: Bob, Mary, and Joey each with their own default group of the same name respectively.
Shared directory: House
Shared directory's group: Family

Set the GID of House to Family.
When any of the three users create a file in the House directory, the file's group will be Family.

Thanks!

---

### Post by bab1 on 2016-03-09
> **kazz2 said:**
> I'm finally getting back to this. And thanks again for the support!

So, create a group for each "top-level" shared directory. Then use the set GUID feature of chmod (s) on the directory itself. That way, when ANY user in the shared directory's group creates a file it will belong to the same group as the directory regardless of the user's default group.

That about it? My example:

Users: Bob, Mary, and Joey each with their own default group of the same name respectively.
Shared directory: House
Shared directory's group: Family

Set the GID of House to Family.
When any of the three users create a file in the House directory, the file's group will be Family.

Thanks!
You have to add the users (Bob, Mary, and Joey) to the user-group Family so they have access  and read/write permissions in the shared directory.

---

### Post by kazz2 on 2016-03-09
Absolutely! I see I left that out.

I'll proceed as above. Thanks!

---

### Post by SeijiSensei on 2016-03-09
You can use utilities like adduser to add users to groups, but sometimes I just edit the file /etc/group instead.  You can add users by entering their usernames at the end of the group's definition like this:
```

users:x:999:bill,sue,bobby,fred,harriet

```
That puts all those users in the "users" group with group ID 999.

---

### Post by kazz2 on 2016-03-09
Thanks, I recently found that information myself. In my case I have a handful of users and a handful of top-level folders so I've done it all through the command line. But /etc/group is a great reference.

Note to anyone who's stumbled onto this and is migrating data like I have been. If you already have data in place before you set up this type of permissions and access, you have to set the group ID of all the sub-folders and it makes sense to do the same to the files, as well. I used sudo chgrp groupname * -R. And, has been noted, when you want to test the access you have to log your user out and back in for it to all be in effect.

Thanks again, everyone!

---

