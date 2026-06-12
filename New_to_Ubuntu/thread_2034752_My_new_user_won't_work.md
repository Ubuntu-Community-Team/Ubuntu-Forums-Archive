---
title: "My new user won't work"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by l1ghtchaos on 2012-07-28
I think I may have screwed something up haha. 

I was logged in to root and i created a new user and a new password for that user. I then tried to login to that user and for some reason, it won't bring me to any directories. It keeps me at $. Also, when I try to logout of ubuntu and then login to that new user a created it lets me type in the password and then it brings me right back to the login screen. 

This never happened to me before on any of my boxes. I deleted the account and created a new one and I am still getting the same error.

---

### Post by Wim Sturkenboom on 2012-07-29
What does the entry for the user look like in */etc/passwd*?
Does the home directory exist?
Does the user have permissions on the home directory?

How did you create the user?

---

### Post by l1ghtchaos on 2012-07-29
Well, it says "No directory, logging in with HOME/=", but then it just leads me to a line that has only $. I can't do anything with that login either for some reason. 


I created the new user by logging in to root and then using adduser.

---

### Post by cariboo on 2012-07-29
It looks like you didn't use the:

```
--home <DIR>
```

option with adduser.

You can still create a home directory with the name of the new user as root:

```
mkdir <New_User>
```

then set the ownership to the new user:

```
chown -R New_User:New_User /home/<New_User>
```

then set the permissions so that then new user can access the files and directories

```
chmod -R 755 /home/<New_User>
```

---

### Post by l1ghtchaos on 2012-07-29
Hey dude that's awesome! Thanks a lot! I actually figured it out but that's some good info there. 

Thanks!

---

### Post by vipulkumar7 on 2012-07-29
1st check which shell you new account has /bin/sh or /bin/bash

> cat /etc/passwd | grep "/home"if it is in bin/bash then su - user-name and give the password.
 then go to root and install a package call finger
> sudo apt-get install fingerand check which shell and home directory it has, if the home Directory does not assigned,then go for

> mkdir user-name you must create it in home directory

Then set the ownership to the user name 
>  chown -R user-namer:user-name /home/user-namethen set the permissions so that then new user can access the files and directories
> chmod -R 755 /home/user-name Try to login after that it will work
and check the details of user via
> finger user-name
 :):)

---

### Post by Wim Sturkenboom on 2012-07-29
If the problem is solved, please mark the thread as such using the thread tools just above the first post on the page.

---

