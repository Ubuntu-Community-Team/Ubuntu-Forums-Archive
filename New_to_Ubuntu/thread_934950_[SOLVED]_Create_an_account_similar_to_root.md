---
title: "[SOLVED] Create an account similar to root"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-10-01
Hi!

Question: How do I create an account that has EXACTLY the same permission as UID 0 (root)?

Basically what I want is just renaming the root account to admin or something like this.

I think I cannot just create a user called admin, and add it to the root user group, because that would not give me privileges to modify files created by root..., or not?

---

### Post by hyper_ch on 2008-10-01
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by anotherdisciple on 2008-10-01
What are you trying to accomplish? People on the forums aren't supposed to tell you how to log in as root, but they can help you to do whatever you are trying to do. They'll just suggest a sudo command though.

---

### Post by WitchCraft on 2008-10-02
> **anotherdisciple said:**
> 
What are you trying to accomplish? People on the forums aren't supposed to tell you how to log in as root, but they can help you to do whatever you are trying to do. They'll just suggest a sudo command though.


No, I don't want to know how to enable the root account, I've already done so (and locked it again afterwards, btw), so I certainly don't want to know that. 

What I wanted to know is how to make a clone of root with ALL it's rights, and not just create a new user and add this new user to the root group.

Because when I did:
System->Administration->Users_And_Groups
Then clicked on add user, added a username and a password, allowed all privileges, set the home directory, added it to the group root, and set User ID to 0, it did not create the account.

But my problem is solved. It's possible via the console command:
```

useradd --non-unique --create-home --uid 0 --home /home/MY_USERNAME --password MY_PASSWORD  MY_USERNAME

```

**But I have a few other questions now:**
In the process of figuring out how to do it, i created the users:
**user_name**, and **username**

both with uid 0 as non unique. 
Now they show up in:
System->Administration->Users_And_Groups
That's not much of a problem, everything works as it should, but I just wanted to remove them, because I don't use them, since I created them while experimenting.

But I get the following error message when trying to delete them:
> 
Administrator account cannot be deleted
This would leave the system unusable.


And when I try to modify user_name i get:
> 
User name has invalid characters
Please set a valid user name consisting of a lower case letter followed by lower case letters and numbers.

Well, I see that the underscore is the problem.


Now basically I want to remove those two users, but I don't want to render the system unusable ;-)

Anybody knows how?

something like: **userdel **--**non-unique user_name**

or does **userdel user_name** just work, and not render my system unusable?

---

### Post by hyper_ch on 2008-10-02
Do this:

(1) add a new user

(2) edit /etc/passwd
```

gksu gedit /etc/passwd

```
change the user ID of the new user to the one of the root user (I think that's "1")

That should do it.

---

### Post by WitchCraft on 2008-10-02
> **hyper_ch said:**
> Do this:

(1) add a new user

(2) edit /etc/passwd
```

gksu gedit /etc/passwd

```
change the user ID of the new user to the one of the root user (I think that's "1")

That should do it.

thanks, i edited /etc/passwd

set 0 to 1001
and the other 0 to 1002

then it was possible to delete both accounts.

---

### Post by hyper_ch on 2008-10-02
not sure what you did... the user id would be 1001 and 1002 (for the first two new users created. That 1001 and 1002 would be needed to be set to the user id of root which I think is "1"

---

### Post by sisco311 on 2008-10-02
the user id of root is 0

the user id of the first user created is 1000 (ubuntu)
if i remember well in arch is 500

---

### Post by WitchCraft on 2008-10-02
> **sisco311 said:**
> the user id of root is 0

the user id of the first user created is 1000 (ubuntu)
if i remember well in arch is 500

yes, root is 0, 1000 is the other user that get's created while installation, and 1001 and 1002 where user_name and username respectively.

I just changed the non-unique uids of zero to their normal uid's, then it was possible to delete the accounts as normal - that's what I did.

Many thanks for the /etc/passwd tip, that showed me what get's done when I create a new user.

Problem solved.

---

