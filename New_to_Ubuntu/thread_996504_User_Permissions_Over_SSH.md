---
title: "User Permissions Over SSH"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by abeisgreat on 2008-11-28
Hello, I just setup a server and I can ssh into it with my admin account all fine, then I added a user named 'private', then I made him a home dir, now when I ssh in as him I get 'Permission Denied' when i try to do anything, how can I change it so he has full permissions of his home dir, but nowhere else? And can someone link me to a tutorial about file permissions in general as I would like each user except my main account to only be able to see and edit folders under there home dir.

Thanks
Abe

---

### Post by Xiong Chiamiov on 2008-11-29
There are some fairly good explanations [here]("http://ubuntuforums.org/showthread.php?t=425260") and [here]("http://www.zzee.com/solutions/linux-permissions.shtml").

You'll be wanting your "private" user (which, btw, **may** be some sort of reserved keyword that you don't want to use) to have full permissions on his home directory, but not have any for anything else.  That means, you'll probably want everything to be chmod-ed to 700.

---

