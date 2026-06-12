---
title: "diff of orig user vs root user"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by railyarddog on 2012-09-03
New to ubuntu coming from OSX.

when trying to do a:

mv file_ive_already_unzipped.zip /dev/null

I get:

mv: inter-device move failed:  'file_ive_already_unzipped.zip' to '/dev/null'; unable to remove target: Permission denied

I am logged in with the original user which should have admin permissions I thought.

Of coarse I just used sudo and was able to get this done. Mac is this way to, but I thought that linux has a root user, whereas mac does not and that the original user on a linux box has super user privileges.

So my questions are:
Does the first user just have the same privileges as all the users that come after?
Is there a root user and does it have the same password as the original user?

Thank you.
RailYardDog

---

### Post by papibe on 2012-09-03
Hi railyarddog. Welcome to the forums ):P

Trying to remove a file by moving it to /dev/null does not work in Linux.

To remove it use 'rm':
```
rm file_ive_already_unzipped.zip
```
Let us know how it goes.
Regards.

---

### Post by uRock on 2012-09-03
Hello and welcome to the forums,

The root account is disabled by default. Check out the following link for more info, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by railyarddog on 2012-09-03
I should have known that, I'm a moron tonight.  Thanks

---

