---
title: "User profile access level issues"
date: 2015-10-02
forum: New to Ubuntu
---

### Post by nikhil16 on 2015-10-02
Hi guys,I am new to the Linux environment so please bear with me.I have two user profiles, Profile A and Profile B. A was created before B. B was created not the regular UI way, but using  command line (in the terminal). Now, my problem is, when I am in Profile A and when I go /home I can get into the Profile B (and access its files and folders), but not vice versa. When in Profile B, if I try to access the Profile A folder, it says I do not have enough permission.  This is what I wish to accomplish: When in Profile A I wish not to be able to access the contents in Profile B. Please help!Thanks in advance :)Nikhil

Just so you know, I made Profile B as an admin, but still the same thing. How can I have Profile A not access the files and folders of profile B?

---

### Post by steeldriver on 2015-10-02
"profile" meaning what exactly? what command did you use to create B? what is the output of the command
```

id

```
for each of the users?

---

### Post by sisco311 on 2015-10-02
Please check out:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
and
[http://www.howtogeek.com/190084/how-to-prevent-other-users-from-accessing-your-home-directory-in-ubuntu-14.04/](http://www.howtogeek.com/190084/how-to-prevent-other-users-from-accessing-your-home-directory-in-ubuntu-14.04/)

You have to change the permissions of the second user's home directory to 0750 (read/write/execute for user, read/execute for group and non for others) or 0700 (read/write/execute for user and none for group and others).

Note: Admin users as root will still be able to access any user's home directory unless it's encrypted.

---

### Post by nikhil16 on 2015-10-02
Profile, meaning User Accounts, sorry.

This is Profile A: uid=1000(nkhl) gid=1000(nkhl) groups=1000(nkhl),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
Will give you Profile B in a sec.

Ok, here it is. Profile B: uid=1001(testaccount) gid=1001(testaccount) groups=1001(testaccount),27(sudo)

---

